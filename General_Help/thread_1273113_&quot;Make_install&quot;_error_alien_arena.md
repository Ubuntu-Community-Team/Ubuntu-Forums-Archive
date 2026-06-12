---
title: "&quot;Make install&quot; error alien arena"
date: 2009-09-23
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-09-23
I downloaded the zip file for alien arena. Got a couple errors on the "make". Found my way through that but now for "make install" I'm getting another error I cannot seem to figure out, heres the output...


k-dawg@k-dawg-desktop:/media/my****/alienarena2009/source$ sudo make install
[sudo] password for k-dawg: 
cp release/cr* ../
cp: cannot create regular file `../crded': Text file busy
make: *** [install] Error 1

Any help on this would be great, thanx in advance

---

### Post by P4man on 2009-09-23
Sounds like something is running that is locking that file. Game server running perhaps?

---

### Post by tgeer43 on 2009-09-23
Does the precompiled package in the repositories not work for you?
Or do you have some other reason for compiling from source?

I'm just curious because I've run it on Hardy, Intrepid, and Jaunty, both 32 and 64-bit without any issues.

tgeer

---

### Post by Feelin_froggy8877 on 2009-09-23
It was the server running, checked out system monitor when I noticed higher than normal cpu usage :-). And the repo's have the 7.00, want to check out the "09" release. Thanx for the reply's.

---

### Post by Feelin_froggy8877 on 2009-09-23
Got a new error, I'm still a bit of a noob when it comes to compiling, some errors I can figure out, but some are beyond me...

k-dawg@k-dawg-desktop:/media/myshit/alienarena2009/source$ sudo make install
cp release/cr* ../
cp release/game.so ../data1/
cp release/game.so ../arena/
cp: cannot create regular file `../arena/': Is a directory
make: *** [install] Error 1

Edit, O.k seems I jumped the gun a bit, this is the best I could come up w/ on my own, the arena dir was not in the alien arena2009 dir but the data1 dir was. I moved the data1 dir out and tried the make install, got the same error, only it was trying to create the data1 dir/file. So I put the data1 dir back, created the arena dir and the make install finished (no errors) seems the arena dir was missing from the download.

---

### Post by NoaHall on 2009-09-23
There it can't make a directory because it's already been made/copied to.
It should be working now.
Try launching it from the terminal, and if that fails, "sudo make uninstall"

---

### Post by Feelin_froggy8877 on 2009-09-23
Well it was trying to create the "game.so file in the "arena" dir that didnt exist.(for some unknown reason) Either way, I cant run the game...


k-dawg@k-dawg-desktop:/media/myshit/alienarena2009$ ./crx
using /home/k-dawg/.codered/data1/ for writing
using /home/k-dawg/.codered/arena/ for writing
couldn't exec default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
OpenAL info:
  Vendor:     OpenAL Community
  Version:    1.1
  Renderer:   OpenAL Soft
  AL Extensions: AL_EXT_EXPONENT_DISTANCE AL_EXT_FLOAT32 AL_EXT_IMA4 AL_EXT_LINEAR_DISTANCE AL_EXT_MCFORMATS AL_EXT_OFFSET AL_LOKI_quadriphonic
  ALC Extensions: ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT ALC_EXT_CAPTURE ALC_EXT_EFX
  Default Device: ALSA Software on default
  Available Devices:
    ALSA Software on default
    ALSA Software on Audigy 2 ZS [SB0353]
    OSS Software
    Wave File Writer
  ALC Frequency: 44100
  ALC Mono Sources: 255
  ALC Stereo Sources: 1
  Generated Source Count: 128
  Generated Buffer Count: 256
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting mode 3: 1024 768
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX 440 with AGP8X/AGP/SSE2
GL_VERSION: 1.5.8 NVIDIA 96.43.10
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum 
...allowing CDS
...enabling GL_EXT_compiled_vertex_array
...ignoring GL_EXT_point_parameters
...3DFX_set_global_palette not found
...ignoring GL_EXT_shared_texture_palette
...using GL_ARB_multitexture
...GL_SGIS_multitexture deprecated in favor of ARB_multitexture
...using GL_ARB_texture_env_combine
...GL_NV_texture_shader not found
...GL_ARB_fragment_program not found
...One or more GL_ARB_shader_objects functions were not foundReceived signal 11, exiting...
AL lib: ALc.c:1302: exit() 1 device(s) and 1 context(s) NOT deleted
AL lib: alSource.c:2291: alcDestroyContext(): 128 Source(s) NOT deleted
AL lib: alBuffer.c:1097: exit() 256 Buffer(s) NOT deleted
k-dawg@k-dawg-desktop:/media/myshit/alienarena2009$

---

