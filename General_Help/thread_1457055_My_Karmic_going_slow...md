---
title: "My Karmic going slow.."
date: 2010-04-18
forum: General Help
---

### Post by Click-dot-Bejo on 2010-04-18
Hi, anyone can help me Solve this problem?
My Problem :
1. My Ubuntu 9.10 Karmic Koala always going slow when i Open OPERA Browser. Is it Normal?
2. Sometimes i got my Karmic Animation like a... i dont know, just play it slower than usual. Is it Normal?
Sorry, im Newbie with this Karmic..
I was using Compiz Animation. [minimize, maximize, close, etc] Is that thing make my Karmic running slow?

My Notebook : Acer 4715 Intel Dual Core 1.86Ghz, 1Gb Memory DDR2, Intel Graphic Media Accelerator X3100 [intel 965GM].. 
Thanks ):P
I was Running Wind*** 7 Ultimate with no Problem or nothing run too slow like now with my Ubuntu..
Whats wrong?
HDD was not Full.. 40% Use, 60% Free..
So, Whats the Problem? :(

---

### Post by chris.jericho on 2010-04-18
this should not happen..... you said you are using compiz animations right?

what is your computer's specs???

---

### Post by Click-dot-Bejo on 2010-04-18
> **chris.jericho said:**
> this should not happen..... you said you are using compiz animations right?

what is your computer's specs???

Intel Dual Core 1,86Ghz
1Gb Memory DDR2
Intel GMA X3100 [Intel 965GM]

ya, im running compiz amination everyday..

---

### Post by chris.jericho on 2010-04-18
compiz eats up a lot amount of ram.... probably increase your Ram and get a higher graphic card.. and your computer will run smooth as butter.... otherwise just disable the advance compiz animations...

---

### Post by Click-dot-Bejo on 2010-04-18
Ok, i was stop all animation with compiz, but nothing change..
Why?

---

### Post by Bungler on 2010-04-18
I think your computer is well powerful enough to run Ubuntu smoothly. I've seen Ubuntu with Compiz being run smoothly on a lot less powerful computers.
Check the processes in the system monitor and see if one eats all the resources. Furthermore it might has something to do with your graphics driver. I have to admit I don't know whether there are separate Intel drivers, but the problems you describe are typical for a not properly working graphics driver.

---

### Post by meho_r on 2010-04-18
Just to add about Opera: after starting the system, on my machine Opera takes about a minute to start up and I have no idea why is that. But that doesn't impact performance of the system in any way. In your case, I agree with Bungler, smells like graphic card driver problem.

---

### Post by klemes on 2010-04-18
If it is a graphics driver vs Compiz issue try the following that might help :

open /etc/environment :```
sudo nano /etc/environment
```and add this line:```
INTEL_BATCH=1
```and save(CTRL-X/y/ENTER)

Then install fusion-icon:```
sudo apt-get install fusion-icon
```and then reboot.
When dropped again in graphical environment run fusion-icon and right click it then choose indirect-rendering.
Also it would be good to provide your glxinfo command output.
For me the above settings worked good in a similar configuration machine running 9.10 with compiz.

---

### Post by Click-dot-Bejo on 2010-04-18
@ Klemes : Thanks so much, i've tried it, but havent restarted yet. :)
Coz im Downloading new Linux Mint.. :)
i Hope it works :)

---

### Post by Click-dot-Bejo on 2010-04-18
@ Meho_r : i think so, but is there any driver Graphic Intel for Ubuntu? :S

---

### Post by Click-dot-Bejo on 2010-04-18
@ Bungler : Thanks bro, ill check this problem with linux mint, if same problem exist, i don't know what's next, maybe ill back to Wind***. :( [Hopefully not]

---

### Post by Click-dot-Bejo on 2010-04-18
This is my result for Compiz-Check..
[[IMG]http://img101.imageshack.us/img101/3127/compizcheck.png[/IMG]]("http://img101.imageshack.us/i/compizcheck.png/")



Anyone can tell me whats the Problem?

---

### Post by klemes on 2010-04-18
All are OK accordind to compiz-check.You are running the intel driver (no vesa or other workarounds) you are using AIGLX and all needed glx extension (texture_from_pixmap) are present (of course since you are running on an Intel board)
No problems there.
Could you provide your glxinfo output?If you are not having glxinfo installed get it by typing in a shell:
```
sudo apt-get install mesa-utils
```
Also you could  run glxgears and see if it gives any kind of problems and while at it could you take note of the number of frames in 5.0 secs your card outpus?

---

### Post by Click-dot-Bejo on 2010-04-18
glxinfo :
click@Bejo-CeLk:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.6
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_half_float_pixel, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_fog_coord, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_envmap_bumpmap, 
    GL_ATI_texture_env_combine3, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_texture_signed_rgba, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_point_sprite, GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

72 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xb6 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xb7 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xb8 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xb9 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xba 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xbb 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xbc 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xbd 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xbe 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xbf 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xc0 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xc1 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xc2 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xc3 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xc4 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xc5 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xc6 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xc7 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xc8 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xc9 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xca 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xcb 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xcc 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xcd 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xce 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xcf 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xd0 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xd1 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xd2 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xd3 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xd4 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xd5 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xd6 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xd7 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xd8 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xd9 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xda 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xdb 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xdc 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xdd 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xde 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xdf 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xe0 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xe1 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xe2 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xe3 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xe4 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xe5 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xe6 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xe7 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xe8 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xe9 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xea 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xeb 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xec 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xed 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xee 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xef 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf0 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xf1 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xf2 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xf3 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xf4 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xf5 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xf6 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xf7 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xf8 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xf9 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xfa 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x55 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

96 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x56  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x57  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x58  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x59  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x5a  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x5b  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x5c  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x5d  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x5e  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x5f  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x60  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x61  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x62  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x63  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x64  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x65  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x66  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x67  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x68  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x69  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x6a  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x6b  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x6c  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x6d  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x6e  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x6f  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x70  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x71  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x72  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x73  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x74  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x75  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x76  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x77  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x78  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x79  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x7a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x7b  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x7c  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x7d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x7e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x7f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x80  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x81  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x82  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x83  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x84  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x85  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x86  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x87  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x88  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x89  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x8a  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x8b  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x8c  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x8d  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x8e  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x8f  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x90  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x91  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x92  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x93  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x94  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x95  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x96  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x97  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x98  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x99  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x9a  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x9b  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x9c  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x9d  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x9e  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x9f  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xa0  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xa1  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xa2  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xa3  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xa4  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xa5  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xa6  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xa7  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xa8  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xa9  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xaa  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xab  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xac  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xad  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xae  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xaf  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xb0  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xb1  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xb2  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xb3  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xb4  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xb5  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow


Glxgears :
[[IMG]http://img255.imageshack.us/img255/2764/glxgears.png[/IMG]](http://img255.imageshack.us/i/glxgears.png/)

Is there a Problem? :)
[thank u so much want help me]

1 Question [last :p] : if i using Linux Mint 8 [based with ubuntu 9.10], this problem will exist in Linux Mint or not? b'coz Mint 8 based from Ubuntu 9.10 :roll:

---

### Post by klemes on 2010-04-18
Glxinfo data looks OK.
But you are getting pretty low fps from glxgears.
In a completely similar machine albeit with an Intel 945GM graphics card I get consistently  >2500 frames per 5.0 sec.
As for your question pertaining Linux Mint since it is Ubuntu 9.10 based you can easily assume that you 'll have the same problems,but only trial will confirm that.Boot into the LiveCD and perform the same tests so you can see for yourself the results.
Also it's true that the 965 Intel board is relatively new hardware and is not being supported at the moment as well as the older 945 ,915 and 810 hardware in Linux.
Nevertheless I will post you my tweaked xorg.conf file for you to give it a try and see if it boost up the graphics driver performance.
Try posting your /var/log/Xorg.0.log as well if you like.......

---

### Post by klemes on 2010-04-18
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier      "Default Layout"
        screen 0        "Default Screen"  0 0
        Inputdevice    "Generic Keyboard" "CoreKeyboard"
        Inputdevice    "Configured Mouse" "CorePointer"
        Option          "AIGLX"  "True"
        Option          "AllowEmptyInput"  "on"
EndSection

Section "Module"
       Load             "dri"
       Load             "glx"
       Load             "dbe"
       Load             "extmod"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
#       Option          "CoreKeyboard"
#       Option          "XkbRules"      "evdev"
#       Option          "XkbModel"      "pc105"
#       Option          "XkbLayout"     "us,gr"
#       Option          "XkbVariant"    ""
#       Option          "XkbOptions"    "grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons""true"
EndSection


Section "Device"
    Identifier    "Intel 965G"
    Driver          "intel"
    Option          "DRI"  "true"
    Option          "XAANoOffscreenPixmaps" "true"
    Option          "AccelMethod" "uxa"
    Option          "MigrationHeuristic" "greedy"

EndSection

Section "Monitor"
     Identifier    "Default Monitor"
     Option          "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Default Monitor"
    Device         "Intel 965G"
        SubSection      "Display"
                 Viewport  0 0
                 Depth     24
#               Modes   "1280x1024"
        EndSubSection
EndSection

Section "Extensions"
        Option           "Composite"   "Enable"
EndSection

Section "DRI"
        Group            "video"
        Mode              0666
EndSection


```

Copy Paste the above into any text editor and save it as root in file /etc/X11/xorg.conf.Backup this file if it exist first.
ie:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

sudo nano /etc/X11/xorg.conf

copy/paste the above

then save it by hitting CTRL-X then y and then ENTER.

Give it a shot and tell us how it is going.

---

### Post by Bungler on 2010-04-18
Have you also checked the systems processes? See if you see some abnormal CPU usage and mem usage? This can also really slow down your computer

---

### Post by Click-dot-Bejo on 2010-04-18
> **klemes said:**
> Copy Paste the above into any text editor and save it as root in file /etc/X11/xorg.conf.Backup this file if it exist first.
ie:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

sudo nano /etc/X11/xorg.conf

copy/paste the above

then save it by hitting CTRL-X then y and then ENTER.

Give it a shot and tell us how it is going.

How it is going?
Nothings change :confused:
im starting confused with this problem @_@

---

### Post by Click-dot-Bejo on 2010-04-18
> **Bungler said:**
> Have you also checked the systems processes? See if you see some abnormal CPU usage and mem usage? This can also really slow down your computer

Everything is Normal :)
top 3 memory usage : Firefox, Compiz, & Rythmbox. :confused:

---

### Post by klemes on 2010-04-18
There is a bug in launchpad about performance issues in Ubuntu 9.10 and the intel driver with that specific card that you are using.
Maybe taht will interest you :[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073)

---

### Post by Click-dot-Bejo on 2010-04-18
> **klemes said:**
> There is a bug in launchpad about performance issues in Ubuntu 9.10 and the intel driver with that specific card that you are using.
Maybe taht will interest you :[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073)

Thanks bro for the Information..
ill check it out..

So, what should i do brother? :(

---

### Post by klemes on 2010-04-18
There's two things I would do :

1.Either stay with Ubuntu 9.10 for the time being and try the newest intel drivers from Xorg-edgers.

or 

2. possibly upgrade to 10.4 Lucid Lynx which is currently in beta2 form but stable enough for not mission critical PC's,and will be in final LTS form in April 29th.

I would try both of this in the order I wrote them and if still no luck I would go to Debian or Ubuntu 8.04  whose xorg-server is quiet old and it is not affected by this specific bug with the Intel drivers or Ubuntu not newer than 8.04   for the same reasons.(Yes however silly this might appear downgrading WILL SOLVE your problem).
But I am sure this will be addressed sooner or later so depending on the severity of the problem that affects you I would choose whether to stay still and wait or move to Debian or an older edition of Ubuntu.
These are your options I am afraid except if someone else knows something more about your issue..

---

### Post by Serpher on 2010-04-18
This is the biggest problem with Linux, although by no means is a fault of the OS, rather than hardware manufactures just making sure their hardware works fine with Windows which is understandable since it's most of the market-share. If you have the time, and you're feeling adventurous, maybe downloading and installing Fedora 12. It's a more cutting edge Linux, as TBH it's kind of RedHat's (A commercial server distro) bug-testing distro. Because it's so cutting edge, it's a little ahead of all the other distros and probably uses a more cutting edge Kernal. Back when I first started using Ubuntu in 8.04, my wireless card didn't work without a ton of wok and my motherboard just ended up causing a lot of errors and a really long boot time, but when 9.04 came out, everything worked perfectly out of the box. Basically the newer the kernal, the more hardware it will work with.

---

### Post by Click-dot-Bejo on 2010-04-18
> **klemes said:**
> There's two things I would do :

1.Either stay with Ubuntu 9.10 for the time being and try the newest intel drivers from Xorg-edgers.

or 

2. possibly upgrade to 10.4 Lucid Lynx which is currently in beta2 form but stable enough for not mission critical PC's,and will be in final LTS form in April 29th.

I would try both of this in the order I wrote them and if still no luck I would go to Debian or Ubuntu 8.04  whose xorg-server is quiet old and it is not affected by this specific bug with the Intel drivers or Ubuntu not newer than 8.04   for the same reasons.(Yes however silly this might appear downgrading WILL SOLVE your problem).
But I am sure this will be addressed sooner or later so depending on the severity of the problem that affects you I would choose whether to stay still and wait or move to Debian or an older edition of Ubuntu.
These are your options I am afraid except if someone else knows something more about your issue..

Maybe ill Move On to 10.04 after finishing test this linux Mint 8..
i don't know how to say Thank you, thanks for u'r Time! :)

---

### Post by Click-dot-Bejo on 2010-04-19
New Solution!
Ive got no problem with my Graphic Card, the problem is "My last Ubuntu Running with just 800Mhz Processor", lets see when i was Change it to Max CPU use. :)
Take a look at my attachment.. :)

---

