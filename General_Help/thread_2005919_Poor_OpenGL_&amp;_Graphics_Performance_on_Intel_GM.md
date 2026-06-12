---
title: "Poor OpenGL &amp; Graphics Performance on Intel GMA945 w/kernel &gt;/= 3.2.0-24"
date: 2012-06-18
forum: General Help
---

### Post by wolf_3d on 2012-06-18
I am using a remix of Xubuntu 12.04 called Voyager 12.04 on a Dell Latitude D620.

When I installed Voyager to begin with things were OK and I was able to play Wolfenstein Enemy Territory reasonably well. The laptop has shared graphics so it is not brilliant but the point is it was playable. Voyager came with the 3.2.0-23 kernel.

Problem is, that since there has been kernel updates with the 3.2.0-24 and most recently 3.2.0-25 Wolfenstein Enemy Terriotory is now unplayable even on the lowest possible settings and the desktop is stuck in 1024x768 resolution where as it should be able to go up to 1280x800.

The game loads but the sound stutters terribly as though it is crawling along. The terminal output for et says that it is using the MESA driver which apparently is not great for gaming. No idea how to change this.

Here's a run-down of what I have tried;

This is the graphics chip the laptop uses:
```
lspci | grep VGA
:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

Direct-rendering is enabled;
```
glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
```

GLXGears works;

```
glxgears
frames in 5.0 seconds = 277.547 FPS
frames in 5.0 seconds = 324.607 FPS
frames in 5.0 seconds = 314.244 FPS
```

Those results above are much higher since the kernel updates.

Here's the terminal output for Wolfenstein: ET

```
et
Read /usr/share/games/enemy-territory/et.x86 (1604328 bytes)
0x8188250: e9 ab 72 29 f8 
0x8188840: e9 fb 6c 29 f8 
0x81888d0: e9 ab 6c 29 f8 
0x81888f0: e9 cb 6c 29 f8 
0x81888e0: e9 1b 6d 29 f8 
Found ET 2.60b (CRC32 = 0x6ab49f82)
Using SDL backend.
et-sdl-sound-r29 (Apr 13 2008 13:59:02, 3.4.6 (Gentoo 3.4.6-r2 p1.5, ssp-3.4.6-1.0, pie-8.7.10)) loaded.
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/rguk/.etwolf/etmain/~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Uce.pk3 (4 files)
/home/rguk/.etwolf/etmain/z_pak_directplay_01.pk3 (3 files)
/home/rguk/.etwolf/etmain/z_LL_etmain_20120603.pk3 (238 files)
/home/rguk/.etwolf/etmain/sw_battery.pk3 (32 files)
/home/rguk/.etwolf/etmain/pirates.pk3 (154 files)
/home/rguk/.etwolf/etmain/leningrad_b2.pk3 (135 files)
/home/rguk/.etwolf/etmain/greenlee_et.pk3 (60 files)
/home/rguk/.etwolf/etmain/goldrush-gals.pk3 (34 files)
/home/rguk/.etwolf/etmain/escape_final.pk3 (82 files)
/home/rguk/.etwolf/etmain/axislab_final_fixed.pk3 (172 files)
/home/rguk/.etwolf/etmain
/usr/share/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/share/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/share/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/share/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/share/games/enemy-territory/etmain

----------------------
4677 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/TCassatt/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Gallium 0.4 on llvmpipe (LLVM 0x300)
*** IGNORING OPENGL EXTENSIONS ***
XF86 Gamma extension initialized

GL_VENDOR: VMware, Inc.
GL_RENDERER: Gallium 0.4 on llvmpipe (LLVM 0x300)
GL_VERSION: 2.1 Mesa 8.0.2
GL_EXTENSIONS: GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_fog_distance GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_primitive_restart GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_compression_latc GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_AMD_draw_buffers_blend GL_ARB_ES2_compatibility GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_shader_texture_lod GL_ARB_vertex_type_2_10_10_10_rev GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_robustness GL_ARB_texture_storage 
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_multithread_makecurrent GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_EXT_texture_from_pixmap 
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 0

PIXELFORMAT: color(24-bits) Z(16-bit) stencil(0-bits)
MODE: 4, 800 x 600 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 2
texture bits: 16
multitexture: disabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "pulse"
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
 8192 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0xf8aa5f0 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/rguk/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/rguk/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/rguk/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/share/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaff6ef40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: jn-Latitude-D620
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: Attempting to resolve master3.evenbalance.com
^5PunkBuster Client: Resolved to [216.240.146.139] (0)
^5PunkBuster Client: PunkBuster Client (v2.213 | A0) Enabled
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

```

I've tried re-installing the intel drivers;
```
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

Tried reconfiguring the xserver but it does not help;
```
sudo dpkg-reconfigure xserver-xorg
```

I have edited grub so that it now has the line: GRUB_CMDLINE_LINUX=" nomodeset "

Only other thing I can do is go back to the older kernel but then what happens with future kernel updates?

---

### Post by wolf_3d on 2012-06-19
Bump #1

---

### Post by wolf_3d on 2012-06-20
Bump #2

---

### Post by wolf_3d on 2012-06-22
Bump #3

---

### Post by wolf_3d on 2012-06-25
Bump #4

---

### Post by wolf_3d on 2012-08-05
Still a problem on 3.2.0-27-generic.

I have created an xorg.conf using:

```
sudo X :1 -configure
```

I have attached the file that it has created.

I don't understand why there are 3 screens. Ultimately I just want to be able to achieve more than 1 resolution greater than 1024x768.

---

