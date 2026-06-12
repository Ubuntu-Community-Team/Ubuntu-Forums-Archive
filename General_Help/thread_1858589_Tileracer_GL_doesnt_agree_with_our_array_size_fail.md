---
title: "Tileracer: GL doesnt agree with our array size: failed"
date: 2011-10-12
forum: General Help
---

### Post by elliotn on 2011-10-12
I am Trying to run a game I downloaded today, but it open but when it suppose to run it crashes.

here is the terminal output, Its long
```
 * VET_UBYTE4 vertex element type: yes
 * Infinite far plane projection: yes
 * Hardware render-to-texture: yes
 * Floating point textures: no
 * Non-power-of-two textures: yes
 * Volume textures: yes
 * Multiple Render Targets: 1
 * Point Sprites: yes
 * Extended point parameters: yes
 * Max Point Size: 255
 * Vertex texture fetch: yes
   - Max vertex textures: 16
   - Vertex textures shared: yes
Registering ResourceManager for type Texture
ResourceBackgroundQueue - threading disabled
Particle Renderer Type 'billboard' registered
SceneManagerFactory for type 'OctreeSceneManager' registered.
SceneManagerFactory for type 'TerrainSceneManager' registered.
Creating resource group Bootstrap
Added resource location '../media/packs/OgreCore.zip' of type 'Zip' to resource group 'Bootstrap'
Added resource location '../media/models/default/BigRamp' of type 'FileSystem' to resource group 'General'
Added resource location '../media/models/default/road1' of type 'FileSystem' to resource group 'General'
Added resource location '../media/models/default/BankedRoad' of type 'FileSystem' to resource group 'General'
Added resource location '../media/models/default/CheckPoint' of type 'FileSystem' to resource group 'General'
Added resource location '../media/models/default/Loop' of type 'FileSystem' to resource group 'General'
Added resource location '../media/models/default/car_datsun' of type 'FileSystem' to resource group 'General'
Added resource location '../media/models/default/tunnel' of type 'FileSystem' to resource group 'General'
Added resource location '../media/models/default/car_nissan' of type 'FileSystem' to resource group 'General'
Added resource location '../media/models/default/pagedgeometry/trees' of type 'FileSystem' to resource group 'General'
Added resource location '../media/models/default/pagedgeometry/grass' of type 'FileSystem' to resource group 'General'
Added resource location '../media/models/default/ElevatedRoad' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/default/car_datsun' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/default/car_nissan' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/pagedgeometry/trees' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/pagedgeometry/grass' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/BankedRoad' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/BigRamp' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/CheckPoint' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/Loop' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/road1' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/tunnel' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/terrain/map1' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/terrain/map3' of type 'FileSystem' to resource group 'General'
Added resource location '../media/textures/LowRes/ElevatedRoad' of type 'FileSystem' to resource group 'General'
Added resource location '../media/cubemaps/cubemapSkySmall' of type 'FileSystem' to resource group 'General'
Added resource location '../media/cubemaps/cubemapSky_lowres' of type 'FileSystem' to resource group 'General'
Added resource location '../media/overlay' of type 'FileSystem' to resource group 'General'
Added resource location '../media/overlay/Arrow' of type 'FileSystem' to resource group 'General'
Added resource location '../media/terrain/map1' of type 'FileSystem' to resource group 'General'
Added resource location '../media/terrain/map2' of type 'FileSystem' to resource group 'General'
Added resource location '../media/terrain/map3' of type 'FileSystem' to resource group 'General'
Added resource location '../media/terrain/map4' of type 'FileSystem' to resource group 'General'
Added resource location '../media/gui' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/BankedRoad' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/BankedRoadCorner' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/BankedRoadOff' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/BankedRoadOn' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/RoadCorner' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/CheckPoint' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/Finish' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/Road1' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/RoadCross' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/Start' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/StartFinish' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/Loop' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/Spin' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/tunnel' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/BigRamp' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/Delete' of type 'FileSystem' to resource group 'General'
Added resource location '../media/tiles/ElevatedRoad' of type 'FileSystem' to resource group 'General'
Added resource location '../media/fonts/default' of type 'FileSystem' to resource group 'General'
Added resource location '../media/fonts/LowRes' of type 'FileSystem' to resource group 'General'
Added resource location '../media/' of type 'FileSystem' to resource group 'General'
Added resource location '../media/NxOgre/images/' of type 'FileSystem' to resource group 'General'
Added resource location '../media/NxOgre/materials/' of type 'FileSystem' to resource group 'General'
Added resource location '../media/NxOgre/meshes/' of type 'FileSystem' to resource group 'General'
Added resource location '../media/NxOgre/particles/' of type 'FileSystem' to resource group 'General'
Added resource location '../media/compositor/MotionBlur' of type 'FileSystem' to resource group 'General'
Added resource location '../media/compositor/HDR' of type 'FileSystem' to resource group 'General'
Added resource location '../media/compositor/' of type 'FileSystem' to resource group 'General'
Added resource location '../media/caelum' of type 'FileSystem' to resource group 'General'
Added resource location '../media/particles' of type 'FileSystem' to resource group 'General'
Parsing scripts for resource group Autodetect
Finished parsing scripts for resource group Autodetect
Parsing scripts for resource group Bootstrap
Parsing script OgreCore.material
Parsing script OgreProfiler.material
Parsing script Ogre.fontdef
Parsing script OgreDebugPanel.overlay
Texture: New_Ogre_Border_Center.png: Loading 1 faces(PF_A8R8G8B8,256x128x1) with 8 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x128x1.
Texture: New_Ogre_Border.png: Loading 1 faces(PF_A8R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x256x1.
Texture: New_Ogre_Border_Break.png: Loading 1 faces(PF_A8R8G8B8,32x32x1) with 5 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,32x32x1.
Font TrebuchetMSBoldusing texture size 512x256
Info: Freetype returned null for character 160 in font TrebuchetMSBold
Texture: TrebuchetMSBoldTexture: Loading 1 faces(PF_BYTE_LA,512x256x1) with  hardware generated mipmaps from Image. Internal format is PF_BYTE_LA,512x256x1.
Parsing script OgreLoadingPanel.overlay
Finished parsing scripts for resource group Bootstrap
Parsing scripts for resource group General
Parsing script StdQuad_vp.program
Parsing script BigRamp.material
Parsing script road02.material
Parsing script Road1.material
Parsing script RoadCross.material
Parsing script BankedRoad.material
Parsing script BankedRoadOn.material
Parsing script BankedRoadOff.material
Parsing script bankedRoad01.material
Parsing script StartFinish.material
Parsing script StartPoint.material
Parsing script Spin.material
Parsing script Loop.material
Parsing script Datsun_Rally_Tire.material
Parsing script Datsun_Rally.material
Parsing script tunnel01.material
Parsing script nissan_tire_left.material
Parsing script nissan.material
Parsing script nissan_tire_right.material
Parsing script palmtree.material
Parsing script pinetree.material
Parsing script NormalTree.material
Parsing script grass.material
Parsing script ElevatedRoad.material
Parsing script CubeMapSky_small.material
Parsing script CubeMapSky.material
Parsing script Stats_bg.material
Parsing script terrain1.material
Parsing script terrain3.material
Parsing script Editor.material
Parsing script nx.zones.material
Parsing script nx.shapes.material
Parsing script nx.stairs.material
Parsing script nx.grid.material
Parsing script nx.particles.material
Parsing script nx.track.material
Parsing script nx6.material
Parsing script heightmap.material
Parsing script nx.shapes.material
Parsing script MotionBlur.material
Parsing script hdr.material
GLSL compiled : Ogre/Compositor/HDR/downscale2x2LuminenceGLSL_fp
GLSL compiled : Ogre/Compositor/StdQuad_GLSL_vp
GLSL compiled : Ogre/Compositor/HDR/downscale3x3GLSL_fp
GLSL compiled : Ogre/Compositor/HDR/utils_fp
GLSL compiled : Ogre/Compositor/HDR/downscale3x3brightpassGLSL_fp
GLSL compiled : Ogre/Compositor/HDR/bloomGLSL_fp
GLSL compiled : Ogre/Compositor/HDR/utils_fp
GLSL compiled : Ogre/Compositor/HDR/finaltonemappingGLSL_fp
Parsing script dirt.material
Parsing script rubber.material
Parsing script smoke.material
Parsing script MotionBlur.compositor
Parsing script hdr.compositor
Parsing script vrinda.fontdef
Parsing script LAvaFont.fontdef
Parsing script dirt.particle
Parsing script smoke.particle
Parsing script TextPanel.overlay
Parsing script ai-debug.overlay
Texture: overlay_ai_bg.png: Loading 1 faces(PF_A8R8G8B8,200x150x1) with 7 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,200x150x1.
Font ArialFontusing texture size 1024x512
Info: Freetype returned null for character 160 in font ArialFont
Texture: ArialFontTexture: Loading 1 faces(PF_BYTE_LA,1024x512x1) with  hardware generated mipmaps from Image. Internal format is PF_BYTE_LA,1024x512x1.
Parsing script Stats.overlay
Texture: overlay_time_bg.png: Loading 1 faces(PF_A8R8G8B8,200x150x1) with 7 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,200x150x1.
Texture: overlay_speed_bg.png: Loading 1 faces(PF_A8R8G8B8,129x146x1) with 7 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,129x146x1.
Font LAvaFontusing texture size 512x256
Texture: LAvaFontTexture: Loading 1 faces(PF_BYTE_LA,512x256x1) with  hardware generated mipmaps from Image. Internal format is PF_BYTE_LA,512x256x1.
Finished parsing scripts for resource group General
Parsing scripts for resource group Internal
Finished parsing scripts for resource group Internal


Initialising InputManager...
creating InputSystem
creating keyboard
creating mouse
setting window extents: width: 1024, height: 768
Creating resource group MapTempFolderlightmaps
Added resource location '/home/elliotn/.TileRacer/0.7/tmp/lightmaps/.' of type 'FileSystem' to resource group 'MapTempFolderlightmaps'


Creating [GameScene]...
creating TerrainSceneManager
TerrainSceneManager: Registered a new PageSource for type Heightmap
creating PhysicBase
Registering ResourceManager for type NxSCM
Creating material (from index) default
Creating material (manually) terrainMaterial
Creating material (manually) roadMaterial
creating scene object managers

Creating [GameScene]...done



Creating [GuiScene]...
creating static geometry
creating CEGUI renderer
creating GUI system
get window manager
configure GUI
Texture: TaharezLook.tga: Loading 1 faces(PF_A8R8G8B8,512x512x1) with  hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,512x512x1.
loading resources
Texture: background.jpg: Loading 1 faces(PF_R8G8B8,1024x1024x1) with  hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,1024x1024x1.
Texture: map1_Level.jpg: Loading 1 faces(PF_R8G8B8,1024x1024x1) with  hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,1024x1024x1.
Texture: map3_Level.jpg: Loading 1 faces(PF_R8G8B8,1024x1024x1) with  hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,1024x1024x1.
set font

Creating [GuiScene]...done

Creating viewport on target 'Tile Racer', rendering from camera 'Default_Camera', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 20
Texture: _cegui_ogre_0: Loading 1 faces(PF_A8R8G8B8,256x256x1) with  hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x256x1.
enter LevelMenuState
Creating viewport on target 'Tile Racer', rendering from camera 'Default_Camera', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 20
enter LevelMenuState: layout
enter LevelMenuState: setup event handlers
enter LevelMenuState: setup gui elements
enter LevelMenuState: read TerrainDescMap
enter loadTerrainDescMap
enter loadTerrainDescMap: load file
enter loadTerrainDescMap: read file
enter loadTerrainDescMap: new TerrainDesc
enter loadTerrainDescMap: save TerrainDesc
enter loadTerrainDescMap: new TerrainDesc
enter loadTerrainDescMap: save TerrainDesc
enter loadTerrainDescMap: done!
populate MapList ...
populate MapList [done]
enter LevelMenuState: done!
Creating viewport on target 'Tile Racer', rendering from camera 'Default_Camera', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 20
Enable GameScene...
Creating viewport on target 'Tile Racer', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 10


***********************************************
Load [GameScene]...



Creating World...
Initialising Caelum system...
Creating resource group Caelum
Created Caelum resource group (Caelum)
System attributes set up.
Generating sky dome material...
        Material not found; creating...
                Material [OK]
before load...
after load...
after setVertexProgram...
after getVertexProgramParameters...
                Pass [OK]
                TextureUnit [OK]
        DONE
DONE
Creating CaelumSphericDome sphere mesh resource...
WARNING: Mesh instance 'CaelumSphericDome' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
DONE
Sky Dome created.
Generating sun material...
        Material not found; creating...
                Material [OK]
                Pass [OK]
        DONE
DONE
Mesh: Loading sphere.mesh.
Sun created.
Generating starfield material...
        Material not found; creating...
                Material [OK]
                Pass [OK]
                TextureUnit [OK]
        DONE
DONE
Creating CaelumStarfieldDome sphere mesh resource...
WARNING: Mesh instance 'CaelumStarfieldDome' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
DONE
Starfield created.
Texture: Starfield.jpg: Loading 1 faces(PF_R8G8B8,1024x1024x1) with 10 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,1024x1024x1.
DONE
Texture: EarthClearSky2.png: Loading 1 faces(PF_A8R8G8B8,64x64x1) with 6 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,64x64x1.
enter loadTerrainDescMap
enter loadTerrainDescMap: load file
enter loadTerrainDescMap: read file
enter loadTerrainDescMap: new TerrainDesc
enter loadTerrainDescMap: save TerrainDesc
enter loadTerrainDescMap: new TerrainDesc
enter loadTerrainDescMap: save TerrainDesc
enter loadTerrainDescMap: done!
TerrainSceneManager: Activated PageSource Heightmap
Texture: map1_TX_new3.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: terrain_detail_1.jpg: Loading 1 faces(PF_R8G8B8,512x512x1) with 9 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,512x512x1.


Building Track...
Texture: spot_shadow_fade.png: Loading 1 faces(PF_R8G8B8,128x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x128x1.
WARNING: Texture instance 'Ogre/ShadowTexture0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Creating viewport on target 'rtt/Ogre/ShadowTexture0/2861329640', rendering from camera 'Ogre/ShadowTexture0Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Mesh: Loading BankedRoad_N.mesh.
Texture: banked_road01.jpg: Loading 1 faces(PF_R8G8B8,256x128x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x128x1.
Texture: banked_road02.jpg: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: banked_road03.jpg: Loading 1 faces(PF_R8G8B8,128x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x256x1.
Texture: elevated_concrete01.jpg: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
WARNING: Mesh instance 'Banked Road.0.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Banked Road.0.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading ElevatedSolid_N.mesh.
Texture: 007_small.jpg: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: elevated_concrete02.jpg: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Mesh: Loading ElevatedSolid_PhysicSolid.mesh.
Mesh: Loading ElevatedSolid_PhysicSmooth.mesh.
WARNING: Mesh instance 'Elevated Solid.1.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.1.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.1.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading BankedRoadCorner_N.mesh.
Mesh: Loading BankedRoadCorner_PhysicSolid.mesh.
Can't assign material pasted__pasted__concrete01 to SubEntity of Banked Corner.2_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked03 to SubEntity of Banked Corner.2_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked02 to SubEntity of Banked Corner.2_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Mesh: Loading BankedRoadCorner_PhysicSmooth.mesh.
Can't assign material pasted__banked02 to SubEntity of Banked Corner.2_PhysicSmoothEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked01 to SubEntity of Banked Corner.2_PhysicSmoothEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Banked Corner.2.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Banked Corner.2.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__pasted__concrete01 to SubEntity of Banked Corner.2.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked03 to SubEntity of Banked Corner.2.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked02 to SubEntity of Banked Corner.2.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Banked Corner.2.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__banked02 to SubEntity of Banked Corner.2.0_PhysicSmoothEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked01 to SubEntity of Banked Corner.2.0_PhysicSmoothEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Mesh: Loading Road1_N.mesh.
WARNING: Mesh instance 'Road.3.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.3.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading RoadCorner_N.mesh.
WARNING: Mesh instance 'Turn.4.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Turn.4.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.5.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.5.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Turn.6.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Turn.6.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.7.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.7.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Turn.8.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Turn.8.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__pasted__concrete01 to SubEntity of Banked Corner.9_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked03 to SubEntity of Banked Corner.9_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked02 to SubEntity of Banked Corner.9_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked02 to SubEntity of Banked Corner.9_PhysicSmoothEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked01 to SubEntity of Banked Corner.9_PhysicSmoothEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Banked Corner.9.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Banked Corner.9.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__pasted__concrete01 to SubEntity of Banked Corner.9.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked03 to SubEntity of Banked Corner.9.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked02 to SubEntity of Banked Corner.9.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Banked Corner.9.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__banked02 to SubEntity of Banked Corner.9.0_PhysicSmoothEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked01 to SubEntity of Banked Corner.9.0_PhysicSmoothEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Mesh: Loading ElevatedLongramp_N.mesh.
Mesh: Loading ElevatedLongramp_PhysicSolid.mesh.
Mesh: Loading ElevatedLongramp_PhysicSmooth.mesh.
WARNING: Mesh instance 'Elevated long Ramp.10.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated long Ramp.10.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated long Ramp.10.0_PhysicMesh1' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.11.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.11.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.12.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.12.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading BankedRoadOff_N.mesh.
Mesh: Loading BankedRoadOff_PhysicSolid.mesh.
Can't assign material pasted__banked06 to SubEntity of End/Start Banked Road.13_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked05 to SubEntity of End/Start Banked Road.13_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__concrete02 to SubEntity of End/Start Banked Road.13_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Mesh: Loading BankedRoadOff_PhysicSmooth.mesh.
Can't assign material pasted__pasted__banked011 to SubEntity of End/Start Banked Road.13_PhysicSmoothEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked010 to SubEntity of End/Start Banked Road.13_PhysicSmoothEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'End/Start Banked Road.13.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'End/Start Banked Road.13.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__banked06 to SubEntity of End/Start Banked Road.13.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked05 to SubEntity of End/Start Banked Road.13.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__concrete02 to SubEntity of End/Start Banked Road.13.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'End/Start Banked Road.13.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__pasted__banked011 to SubEntity of End/Start Banked Road.13.0_PhysicSmoothEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked010 to SubEntity of End/Start Banked Road.13.0_PhysicSmoothEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Elevated long Ramp.14.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated long Ramp.14.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated long Ramp.14.0_PhysicMesh1' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading CheckPoint_N.mesh.
Texture: CheckPoint.jpg: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
WARNING: Mesh instance 'Checkpoint.15.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.15.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.16.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.16.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.17.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.17.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading ElevatedOpen_N.mesh.
Mesh: Loading ElevatedOpen_PhysicSolid.mesh.
Mesh: Loading ElevatedOpen_PhysicSmooth.mesh.
WARNING: Mesh instance 'Elevated w. Column.18.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.18.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.18.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.19.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.19.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.19.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading Finish_N.mesh.
Texture: StartPoint.jpg: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
WARNING: Mesh instance 'Finish.20.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Finish.20.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.21.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.21.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.21.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.22.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.22.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading Start_N.mesh.
WARNING: Mesh instance 'Start.23.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Start.23.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.24.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.24.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.24.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.25.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.25.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.25.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Turn.26.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Turn.26.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.27.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.27.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated long Ramp.28.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated long Ramp.28.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated long Ramp.28.0_PhysicMesh1' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.29.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.29.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.30.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.30.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.30.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Banked Road.31.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Banked Road.31.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading ElevatedBridge_N.mesh.
Mesh: Loading ElevatedBridge_PhysicSolid.mesh.
Mesh: Loading ElevatedBridge_PhysicSmooth.mesh.
WARNING: Mesh instance 'Elevated Bridge.32.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Bridge.32.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Bridge.32.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.33.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.33.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.34.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.34.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.35.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.35.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.36.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.36.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.37.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.37.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.37.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading BigRamp_N.mesh.
Texture: BigRamp.jpg: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Mesh: Loading BigRamp_N_PhysX.mesh.
WARNING: Mesh instance 'Big Ramp.38.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Big Ramp.38.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Turn.39.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Turn.39.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.40.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.40.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.41.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.41.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.41.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__pasted__concrete01 to SubEntity of Banked Corner.42_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked03 to SubEntity of Banked Corner.42_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked02 to SubEntity of Banked Corner.42_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked02 to SubEntity of Banked Corner.42_PhysicSmoothEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked01 to SubEntity of Banked Corner.42_PhysicSmoothEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Banked Corner.42.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Banked Corner.42.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__pasted__concrete01 to SubEntity of Banked Corner.42.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked03 to SubEntity of Banked Corner.42.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__pasted__banked02 to SubEntity of Banked Corner.42.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Banked Corner.42.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__banked02 to SubEntity of Banked Corner.42.0_PhysicSmoothEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked01 to SubEntity of Banked Corner.42.0_PhysicSmoothEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Elevated w. Column.43.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.43.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.43.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading ElevatedRamp_N.mesh.
Mesh: Loading ElevatedRamp_PhysicSolid.mesh.
Mesh: Loading ElevatedRamp_PhysicSmooth.mesh.
WARNING: Mesh instance 'Elevated Ramp.44.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Ramp.44.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Ramp.44.0_PhysicMesh1' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.45.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.45.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.46.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.46.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.46.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.47.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.47.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Ramp.48.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Ramp.48.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Ramp.48.0_PhysicMesh1' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.49.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.49.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated w. Column.49.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.50.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.50.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.51.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.51.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Banked Road.52.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Banked Road.52.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Banked Road.53.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Banked Road.53.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.54.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.54.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.55.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.55.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.55.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading ElevatedCorner_N.mesh.
Mesh: Loading ElevatedCorner_PhysicSolid.mesh.
Mesh: Loading ElevatedCorner_PhysicSmooth.mesh.
WARNING: Mesh instance 'Elevated Turn.56.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Turn.56.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Turn.56.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Bridge.57.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Bridge.57.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Bridge.57.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Mesh: Loading BankedRoadOn_N.mesh.
Mesh: Loading BankedRoadOn_PhysicSolid.mesh.
Can't assign material pasted__banked09 to SubEntity of Start/End Banked Road.58_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked08 to SubEntity of Start/End Banked Road.58_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__concrete03 to SubEntity of Start/End Banked Road.58_PhysicEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Mesh: Loading BankedRoadOn_PhysicSmooth.mesh.
Can't assign material pasted__banked011 to SubEntity of Start/End Banked Road.58_PhysicSmoothEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked010 to SubEntity of Start/End Banked Road.58_PhysicSmoothEntity_Template0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Start/End Banked Road.58.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Start/End Banked Road.58.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__banked09 to SubEntity of Start/End Banked Road.58.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked08 to SubEntity of Start/End Banked Road.58.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__concrete03 to SubEntity of Start/End Banked Road.58.0_PhysicEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Start/End Banked Road.58.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material pasted__banked011 to SubEntity of Start/End Banked Road.58.0_PhysicSmoothEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
Can't assign material pasted__banked010 to SubEntity of Start/End Banked Road.58.0_PhysicSmoothEntity0 because this Material does not exist. Have you forgotten to define it in a .material script?
WARNING: Mesh instance 'Elevated Ramp.59.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Ramp.59.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Ramp.59.0_PhysicMesh1' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Turn.60.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Turn.60.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Turn.60.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.61.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.61.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.62.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.62.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated Solid.62.0_PhysicSmoothMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated long Ramp.63.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated long Ramp.63.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Elevated long Ramp.63.0_PhysicMesh1' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.64.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.64.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.65.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Road.65.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.66.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.66.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.67.0_RenderMesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Mesh instance 'Checkpoint.67.0_PhysicMesh0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.


Loading Lightmap...
Creating resource group MapTempFolder
Added resource location '/home/elliotn/.TileRacer/0.7/tmp/stdmapdata/.' of type 'FileSystem' to resource group 'MapTempFolder'
WARNING: Mesh instance 'Terrain_Mesh' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
Can't assign material Terrain to SubEntity of Terrain_Entity because this Material does not exist. Have you forgotten to define it in a .material script?


Creating Static Geometry...
BakeLightMap for TrackTiles...
Texture: Banked Corner_0.png: Loading 1 faces(PF_R8G8B8,128x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x128x1.
Texture: Banked Corner_1.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Banked Corner_2.png: Loading 1 faces(PF_R8G8B8,128x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x128x1.
Texture: Banked Corner_3.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated Ramp_0.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated Ramp_1.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated Ramp_2.png: Loading 1 faces(PF_R8G8B8,128x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x128x1.
Texture: Elevated w_0.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated w_1.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated w_2.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Big Ramp_0.png: Loading 1 faces(PF_R8G8B8,16x16x1) with 4 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,16x16x1.
Texture: Big Ramp_1.png: Loading 1 faces(PF_R8G8B8,512x512x1) with 9 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,512x512x1.
Texture: Elevated long Ramp_0.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated long Ramp_1.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated long Ramp_2.png: Loading 1 faces(PF_R8G8B8,128x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x128x1.
Texture: Elevated Bridge_0.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated Bridge_1.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated Bridge_2.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Banked Road_0.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Banked Road_1.png: Loading 1 faces(PF_R8G8B8,128x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x128x1.
Texture: Banked Road_2.png: Loading 1 faces(PF_R8G8B8,128x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x128x1.
Texture: Banked Road_3.png: Loading 1 faces(PF_R8G8B8,128x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x128x1.
Texture: Elevated Turn_0.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated Turn_1.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated Turn_2.png: Loading 1 faces(PF_R8G8B8,512x512x1) with 9 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,512x512x1.
Texture: Elevated Solid_0.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: Elevated Solid_1.png: Loading 1 faces(PF_R8G8B8,128x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x128x1.
Texture: Elevated Solid_2.png: Loading 1 faces(PF_R8G8B8,128x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,128x128x1.
setPaging...
createStatic...


Building Building PagedGeometry...
init trees ... 
Mesh: Loading NormalTree.mesh.
Texture: tree2.png: Loading 1 faces(PF_A8R8G8B8,64x128x1) with 7 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,64x128x1.
Mesh: Loading pinetree_01.mesh.
Texture: pinetree_texture.png: Loading 1 faces(PF_A8R8G8B8,128x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,128x256x1.
Mesh: Loading pinetree_02.mesh.
Mesh: Loading pinetree_03.mesh.
init trees ... done
init grass ...
init grass [load image]...
Texture: ElevatedRoads.map.GrassColorMap100.png: Loading 1 faces(PF_A8R8G8B8,1024x1024x1) with 10 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,1024x1024x1.
init grass [last steps]...
init grass ... done
Creating viewport on target 'rtt/ImpostorTexture1/2734777000', rendering from camera 'ImpostorCam2', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Creating resource group BinFolder
Added resource location '/home/elliotn/.TileRacer/0.7/tmp/.' of type 'FileSystem' to resource group 'BinFolder'
Texture: Impostor.General.NormalTree.mesh.64.png: Loading 1 faces(PF_A8R8G8B8,512x256x1) with 9 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,512x256x1.
Render Target 'rtt/ImpostorTexture1/2734777000' Average FPS: 0 Best FPS: 0 Worst FPS: 999
Creating viewport on target 'rtt/ImpostorTexture35/2735057720', rendering from camera 'ImpostorCam36', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Added resource location '/home/elliotn/.TileRacer/0.7/tmp/.' of type 'FileSystem' to resource group 'BinFolder'
Texture: Impostor.General.pinetree_01.mesh.64.png: Loading 1 faces(PF_A8R8G8B8,512x256x1) with 9 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,512x256x1.
Render Target 'rtt/ImpostorTexture35/2735057720' Average FPS: 0 Best FPS: 0 Worst FPS: 999
Creating viewport on target 'rtt/ImpostorTexture69/2735128480', rendering from camera 'ImpostorCam70', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Added resource location '/home/elliotn/.TileRacer/0.7/tmp/.' of type 'FileSystem' to resource group 'BinFolder'
Texture: Impostor.General.pinetree_02.mesh.64.png: Loading 1 faces(PF_A8R8G8B8,512x256x1) with 9 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,512x256x1.
Render Target 'rtt/ImpostorTexture69/2735128480' Average FPS: 0 Best FPS: 0 Worst FPS: 999
Creating viewport on target 'rtt/ImpostorTexture103/2735206416', rendering from camera 'ImpostorCam104', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Added resource location '/home/elliotn/.TileRacer/0.7/tmp/.' of type 'FileSystem' to resource group 'BinFolder'
Texture: Impostor.General.pinetree_03.mesh.64.png: Loading 1 faces(PF_A8R8G8B8,512x256x1) with 9 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,512x256x1.
Render Target 'rtt/ImpostorTexture103/2735206416' Average FPS: 0 Best FPS: 0 Worst FPS: 999
Texture: gras4.png: Loading 1 faces(PF_A8R8G8B8,511x362x1) with 8 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,511x362x1.
SetMaterial...
TerrainSceneManager: Activated PageSource Heightmap


Creating Cars...
Mesh: Loading nissan_convex.mesh.
WARNING: nissan_convex.mesh is an older format ([MeshSerializer_v1.30]); you should upgrade it as soon as possible using the OgreMeshUpgrade tool.
Creating material (manually) Car1_NissanconvexMaterial
Mesh: Loading nissan.mesh.
WARNING: nissan.mesh is an older format ([MeshSerializer_v1.30]); you should upgrade it as soon as possible using the OgreMeshUpgrade tool.
Texture: skySmall05.png: Loading 6 faces(PF_A8R8G8B8,128x128x1) with 7 hardware generated mipmaps from multiple Images. Internal format is PF_A8R8G8B8,128x128x1.
Texture: head_light.jpg: Loading 1 faces(PF_R8G8B8,323x158x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,323x158x1.
Texture: back_light.jpg: Loading 1 faces(PF_R8G8B8,156x72x1) with 7 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,156x72x1.
Texture: back_lplane.jpg: Loading 1 faces(PF_R8G8B8,276x43x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,276x43x1.
Texture: NAM006F.jpg: Loading 1 faces(PF_R8G8B8,58x42x1) with 5 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,58x42x1.
Texture: NAM006.jpg: Loading 1 faces(PF_R8G8B8,104x25x1) with 6 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,104x25x1.
Texture: head_light1.jpg: Loading 1 faces(PF_R8G8B8,323x158x1) with 8 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,323x158x1.
Creating material (manually) Car1_NissanWheel0TireMat
Mesh: Loading Datsun_Rally_Tire_left.mesh.
Texture: Tyre_Texture.tga: Loading 1 faces(PF_A8R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x256x1.
Creating material (manually) Car1_NissanWheel1TireMat
Mesh: Loading Datsun_Rally_Tire_right.mesh.
Creating material (manually) Car1_NissanWheel2TireMat
Creating material (manually) Car1_NissanWheel3TireMat
Mesh: Loading Arrow.mesh.
WARNING: Arrow.mesh is an older format ([MeshSerializer_v1.30]); you should upgrade it as soon as possible using the OgreMeshUpgrade tool.
Can't assign material Arrow to SubEntity of Arrow because this Material does not exist. Have you forgotten to define it in a .material script?
Mesh: Loading sphere.1m.mesh.
WARNING: sphere.1m.mesh is an older format ([MeshSerializer_v1.30]); you should upgrade it as soon as possible using the OgreMeshUpgrade tool.
FANN Error 1: Unable to open configuration file "NNOperationalSpeed.net" for reading.
FANN Error 1: Unable to open configuration file "NNOperationalSteer.net" for reading.
FANN Error 1: Unable to open configuration file "NNOperationalSpeed.net" for reading.
FANN Error 1: Unable to open configuration file "NNOperationalSteer.net" for reading.

Load [GameScene]...done
***********************************************

Creating viewport on target 'Tile Racer', rendering from camera 'Default_Camera', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 20
Disable GameScene...
Texture: smoke.png: Loading 1 faces(PF_A8R8G8B8,256x256x1) with 8 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x256x1.
Enable GameScene...
Creating viewport on target 'Tile Racer', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 10
Creating MotionBlur Effect...
DONE
Creating HDR Effect...
Creating viewport on target 'rtt/CompositorInstanceTexture0/2732804592', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Creating viewport on target 'rtt/CompositorInstanceTexture1/2734576480', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Creating viewport on target 'rtt/CompositorInstanceTexture2/2734563752', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Creating viewport on target 'rtt/CompositorInstanceTexture3/2734045416', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Creating viewport on target 'rtt/CompositorInstanceTexture4/2721535040', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Creating viewport on target 'rtt/CompositorInstanceTexture5/2721547944', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Creating viewport on target 'rtt/CompositorInstanceTexture6/2721532216', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Creating viewport on target 'rtt/CompositorInstanceTexture7/2733780648', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Creating viewport on target 'rtt/CompositorInstanceTexture8/2734027984', rendering from camera 'Default_Cam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Testing HDR...
WARNING: Texture instance 'CompositorInstanceTexture0' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Texture instance 'CompositorInstanceTexture5' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Texture instance 'CompositorInstanceTexture4' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Texture instance 'CompositorInstanceTexture3' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Texture instance 'CompositorInstanceTexture2' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Texture instance 'CompositorInstanceTexture1' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Texture instance 'CompositorInstanceTexture6' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Texture instance 'CompositorInstanceTexture8' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
WARNING: Texture instance 'CompositorInstanceTexture7' was defined as manually loaded, but no manual loader was provided. This Resource will be lost if it has to be reloaded.
GLSL link result : 
i915_program_error: Exceeded max nr indirect texture lookups (5 out of 4)
GLSL link result : 
i915_program_error: Exceeded max nr indirect texture lookups (10 out of 4)
GLSL link result : 
i915_program_error: Exceeded max nr indirect texture lookups (11 out of 4)
GLSL link result : 
TileRacer: OgreGLSLLinkProgramManager.cpp:373: void Ogre::GLSLLinkProgramManager::extractUniforms(GLhandleARB, const Ogre::GpuConstantDefinitionMap*, const Ogre::GpuConstantDefinitionMap*, Ogre::GLUniformReferenceList&): Assertion `arraySize == newGLUniformReference.mConstantDef->arraySize && "**GL doesn't agree with our array size!"' failed.**
Aborted
elliotn@elliotn:~$ 

```

---

### Post by elliotn on 2011-10-13
anyone

---

### Post by elliotn on 2011-10-13
last bump

---

### Post by elliotn on 2011-10-15
weird very weird

---

### Post by elliotn on 2011-10-15
ok I just fixed the crashing by disabling HDR in graphic option but the car won't move, whole system unusable  even the mouse, had to restart

---

### Post by elliotn on 2011-10-15
the game is **** so I will continue with supertuxkart works better
unistalling tilerscer

---

