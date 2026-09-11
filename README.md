# SIGHTLINE – Barrio (map only)

The barrio map from SIGHTLINE: level geometry, terrain, sky, lighting and the art it uses.
**No scripts at all** and no MFPS gameplay objects (Game Manager, spawn points, UI, bots,
killcam). Nothing in here can cause a compile error in a stock MFPS project.

## Before you import

**Unity 6000.3.x** (made with 6000.3.10f1) and **URP** are required.

Every material in the Leartes favela pack is a Shader Graph that only has URP and HDRP
versions, so in a Built-in project the whole map renders pink. A stock MFPS project is
Built-in: MFPS ships its own `GraphicsSettings.asset`, so importing MFPS switches a project
back to Built-in even if you created it from the URP template. Set up URP **after** MFPS is in:

1. **Window › Package Manager › Unity Registry › Universal RP › Install**
   (Shader Graph comes with it).
2. **Assets › Create › Rendering › URP Asset (with Universal Renderer)**.
3. **Edit › Project Settings › Graphics** → set **Default Render Pipeline** to that asset.
4. Select the `…_Renderer` asset that was created next to it → **Add Renderer Feature › Decal**
   (the map's grime and graffiti are URP decals).
5. **Window › Rendering › Render Pipeline Converter** → *Built-in to URP* → tick
   **Material Upgrade** → **Initialize And Convert**. This fixes MFPS's own materials.

If the project already has errors from an earlier package, start from a fresh MFPS import
first. That package contained modified MFPS scripts.

## Import

1. **Code › Download ZIP** (or `git clone`).
2. Copy the `Assets` folder from the download into your project folder and merge it.
   **Keep the `.meta` files.** They carry the IDs the scene uses to find everything.
3. Open **`Assets/BarrioMap/BarrioMap.unity`**.

## What's inside

| Folder | What |
| --- | --- |
| `Assets/BarrioMap` | The scene, plus the FPS Blockout / ProBuilder meshes baked into `Baked/BarrioMap Meshes.asset` |
| `Assets/LeartesStudios/…` | The parts of *South American Slums – Favela* the map uses |
| `Assets/NatureManufacture Assets/…`, `Assets/TexturesPart01`, `Assets/YughuesFreeConcreteMaterials` | Terrain layers and textures |
| `Assets/Animated Tropical Vegetation` | The two tree/bush types painted on the terrain |
| `Assets/FPSBlockout/GreyboxMaterials` | Greybox materials on the blockout buildings |
| `Assets/MFPS/Scenes/New Maps/…` | Sky material + HDRI, the post-processing profile, a futsal goal model |
| `Assets/New Terrain 7.asset` | The terrain data |

## Making it an MFPS map

The scene is level-only. Add the MFPS map objects the usual MFPS way (Game Manager, spawn
points, etc.), then add the scene to Build Settings and to MFPS's map list.

Two things that look like bugs but aren't:

- **Offline, the sky and fog look different.** MFPS loads maps additively and keeps the
  RoomUI scene active offline, so the map's own sky/fog only apply online.
- **No bloom / color grading in game.** Tick **Post Processing** (and **HDR** on the URP
  asset) on MFPS's player camera. The map's Global Volume does the rest.

## Licensing

Contains paid Unity Asset Store content (Leartes Studios, NatureManufacture and others).
Shared privately for playtesting. Don't make this repo public or redistribute it.
