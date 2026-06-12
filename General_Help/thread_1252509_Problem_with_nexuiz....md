---
title: "Problem with nexuiz..."
date: 2009-08-28
forum: General Help
---

### Post by bulls_eye on 2009-08-28
hey,

i installed nexuiz in ubuntu 9.04.
i am using a lenovo laptop y-500 series, 1gb ram and core duo processor...

as i launch nexuiz, a screen appears which asks for single player or multiplayer...

i choose single player and then instant action...

and then a black screen appeared and then it was gone...

i ran it on the terminal to find out what was goin on and this is what i obtianed

owner@ubuntu:~$ nexuiz
Nexuiz Linux 08:21:26 Jun  6 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data.pk3 (4066 files)
Added packfile /usr/share/games/nexuiz/data/music.pk3 (10 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
couldn't exec config.cfg
execing config_update.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
get fences failed: -1
param: 6, val: 0
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.4
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_multisample GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
SDL_EXTENSIONS: 
0 SDL joystick(s) found:
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
Shader 'textures/Reaptxt/sun' already defined
S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
Wanted audio Specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 48000
	Samples   : 4096
Obtained audio specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 48000
	Samples   : 4096
Sound format: 48000Hz, 2 channels, 16 bits per sample
Found 1 cdrom drives.
No CD in drive 0.
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:50865
Fake CD track 1 playing...
execing mutator_reset.cfg
Shader 'textures/Reaptxt/sun' already defined
Server using port 26000
Server listening on address local:1
Server listening on address 0.0.0.0:26000
Loaded maps/downer.ent

Trying to connect...
Segmentation fault


what does it mean??
system requirements are not met or these is some other error??

Thanks...

---

