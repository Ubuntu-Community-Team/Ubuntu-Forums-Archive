---
title: "Disable integrated graphics without BIOS?"
date: 2012-08-04
forum: General Help
---

### Post by Stonecold1995 on 2012-08-04
I have a laptop with hybrid graphics, but obviously it isn't working with Nvidia's proprietary drivers.  Nvidia says "notebook and all-in-one desktop designs with switchable (hybrid) or Optimus graphics will not work if means to disable the integrated graphics in hardware are not available.", but I'm pretty sure there is a way to do it even though my BIOS doesn't have an option to.  Is there a script that can do that for me or something, or something I can do with GRUB that'll disable integrated graphics so I can install proprietary drivers?

**So does anyone know how I can disable Intel Integrated graphics if my BIOS doesn't have the option?**

I have an Nvidia GeForce GTX 675M GPU, btw, and I'm trying to install [this]("http://www.nvidia.com/object/linux-display-amd64-302.17-driver.html") driver.  I've tried in the past, but it's never worked (it just breaks Xorg and forces me to reinstall it) because of the stupid Optimus technology.

My laptop is plugged in 24/7, so I don't need something like Bumblebee and would like everything to run on my GPU if it's possible.

In case it is of any help, here is the output of "lspci | grep VGA":
```
alex@kubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1212 (rev ff)
```

And here is the output of "glxinfo":
```
alex@kubuntu:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 8.0.3
OpenGL shading language version string: 1.30
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, GL_ARB_multitexture, 
    GL_EXT_framebuffer_sRGB, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_ARB_depth_texture, GL_ARB_occlusion_query, GL_ARB_shadow, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ATI_envmap_bumpmap, GL_EXT_stencil_two_side, 
    GL_EXT_texture_cube_map, GL_NV_depth_clamp, GL_NV_vertex_program1_1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_ARB_depth_clamp, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_EXT_packed_float, GL_EXT_pixel_buffer_object, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_APPLE_object_purgeable, GL_ARB_vertex_array_object, 
    GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_array, 
    GL_EXT_texture_integer, GL_EXT_texture_sRGB_decode, GL_EXT_timer_query, 
    GL_OES_EGL_image, GL_MESA_texture_array, GL_ARB_copy_buffer, 
    GL_ARB_depth_buffer_float, GL_ARB_half_float_vertex, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_ARB_ES2_compatibility, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_robustness, GL_EXT_transform_feedback

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0aa 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ab 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0ac 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ae 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0af 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ba 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x06d 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x06e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x070  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x071  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x074 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x076 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x078 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x079 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x07a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x080  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x081  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x082 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x084 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x085 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x086  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x087  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x088  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x089  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x091 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x092 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x095 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x097 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x098  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x099  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x09a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
```

---

### Post by GJ1234 on 2012-08-04
Exactly my problem :(

---

### Post by Stonecold1995 on 2012-08-20
There has to be a way to do this!  I mean, the BIOS is just software, and it's not active as soon as the computer finishes booting, so it's not like it locks down the GPU or something.  If a computer can be overclocked using software even if the BIOS doesn't support overclocking, then why can't the integrated graphics be disabled using software?  Are there any programs like that, that allow you to disable devices, or at least change variables (I'm not sure if that's what their called in this case) set by the BIOS at boot?  I know vga_switcheroo (or whatever it's called) does something like that, but if I'm right it doesn't work unless the BIOS already has the option.

I'm always bummed out to read about the awesome specs of my GPU yet have to realize that my laptop can't even play Touhou Project at full speed (even a $500 laptop should be able to play that, and mine cost over $3,000 yet still can't ;_; )...  This is really weird because my laptop *should* be advanced enough to support common BIOS features, but the only settings in the BIOS are boot options, system time, passwords, and rapid-start.  Stupid American Megatrends is too lazy to implement even the simplest of features...

Also, bump.

---

### Post by Stonecold1995 on 2012-09-13
Is there a way I can flash my BIOS to a version that supports disabling integrated graphics (flashrom doesn't work because I'm using a laptop)?  The information about the BIOS says that it's flashable, but I'm hesitant to simply overwrite it with a BIOS ROM that supports disabling integrated graphics because I don't want to brick my computer.

I find it very hard to believe that there isn't a way to disable integrated graphics without the BIOS...

Here's the info I got from using "sudo biosdecode", "sudo hwinfo --bios", and "sudo dmidecode --type bios":
```
**alex@kubuntu:~$** sudo biosdecode
[sudo] password for alex: 
# biosdecode 2.11
ACPI 2.0 present.
        OEM Identifier: MIDERN
        RSD Table 32-bit Address: 0xCA61C028
        XSD Table 64-bit Address: 0x00000000CA61C080
SMBIOS 2.7 present.
        Structure Table Length: 2005 bytes
        Structure Table Address: 0xC9EC6018
        Number Of Structures: 31
        Maximum Structure Size: 210 bytes
PNP BIOS 1.0 present.
        Event Notification: Not Supported
        Real Mode 16-bit Code Address: F000:BC16
        Real Mode 16-bit Data Address: F000:0000
        16-bit Protected Mode Code Address: 0x000FBC3E
        16-bit Protected Mode Data Address: 0x000F0000
PCI Interrupt Routing 1.0 present.
        Router ID: 00:1f.0
        Exclusive IRQs: None
        Compatible Router: 8086:27b8
        Slot Entry 1: ID 00:1f, on-board
        Slot Entry 2: ID 00:14, on-board
        Slot Entry 3: ID 00:1d, on-board
        Slot Entry 4: ID 00:1a, on-board
        Slot Entry 5: ID 00:1b, on-board
        Slot Entry 6: ID 00:16, on-board
        Slot Entry 7: ID 00:1c, on-board
        Slot Entry 8: ID 02:00, slot number 33
        Slot Entry 9: ID 03:00, slot number 34                                                                                                                                                                                                                                 
        Slot Entry 10: ID 04:00, slot number 8                                                                                                                                                                                                                                 
        Slot Entry 11: ID 05:00, slot number 9                                                                                                                                                                                                                                 
        Slot Entry 12: ID 00:01, on-board                                                                                                                                                                                                                                      
        Slot Entry 13: ID 00:06, on-board                                                                                                                                                                                                                                      
        Slot Entry 14: ID 01:00, slot number 16                                                                                                                                                                                                                                
        Slot Entry 15: ID 00:04, on-board                                                                                                                                                                                                                                      
        Slot Entry 16: ID 00:02, on-board

-------------------------

**alex@kubuntu:~$** sudo hwinfo --bios                                                                                                                                                                                                                                             
> hal.1: read hal dataprocess 26038: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.                                                                                
This is normally a bug in some application using the D-Bus library.                                                                                                                                                                                                            
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files                                                                                                                                                      
01: None 00.0: 10105 BIOS                                                                                                                                                                                                                                                      
  [Created at bios.190]                                                                                                                                                                                                                                                        
  Unique ID: rdCR.lZF+r4EgHp4                                                                                                                                                                                                                                                  
  Hardware Class: bios                                                                                                                                                                                                                                                         
  BIOS Keyboard LED Status:                                                                                                                                                                                                                                                    
    Scroll Lock: off                                                                                                                                                                                                                                                           
    Num Lock: off                                                                                                                                                                                                                                                              
    Caps Lock: off                                                                                                                                                                                                                                                             
  Base Memory: 630 kB                                                                                                                                                                                                                                                          
  PnP BIOS: @@@0000                                                                                                                                                                                                                                                            
  MP spec rev 1.4 info:
    OEM id: "MIDERN"
    Product id: "MIDERN"
    4 CPUs (0 disabled)
  SMBIOS Version: 2.7
  BIOS Info: #0
    Vendor: "American Megatrends Inc."
    Version: "4.6.5"
    Date: "04/14/2012"
    Start Address: 0xf0000
    ROM Size: 4096 kB
    Features: 0x0d03000000013f8b9880
      PCI supported
      BIOS flashable
      BIOS shadowing allowed
      CD boot supported
      Selectable boot supported
      BIOS ROM socketed
      EDD spec supported
      1.2MB Floppy supported
      720kB Floppy supported
      2.88MB Floppy supported
      Print Screen supported
      8042 Keyboard Services supported
      Serial Services supported
      Printer Services supported
      ACPI supported
      USB Legacy supported
      BIOS Boot Spec supported
  System Info: #1
    Manufacturer: "CLEVO"
    Product: "P15xEMx"
    Version: "Not Applicable"
    Serial: "Not Applicable"
    UUID: 000000000000000000003198ccf59000
    Wake-up: 0x06 (Power Switch)
  Board Info: #2
    Manufacturer: "CLEVO"
    Product: "P15xEMx"
    Version: "Not Applicable"
    Serial: "Not Applicable"
    Asset Tag: "Not Applicable"
    Type: 0x0a (Motherboard)
    Features: 0x09
      Hosting Board
      Replaceable
    Location: "Not Applicable"
    Chassis: #3
  Chassis Info: #3
    Manufacturer: "CLEVO"
    Version: "Not Applicable"
    Serial: "Not Applicable"
    Asset Tag: "Not Applicable"
    Type: 0x0a (Notebook)
    Bootup State: 0x03 (Safe)
    Power Supply State: 0x03 (Safe)
    Thermal State: 0x03 (Safe)
    Security Status: 0x03 (None)
  On Board Devices: #4
    Video: "To Be Filled By O.E.M."
  OEM Strings: #5
    1558
  System Config Options (Jumpers & Switches) #6:
    To Be Filled By O.E.M.
  Type 32 Record: #7
    Data 00: 20 14 07 00 00 00 00 00 00 00 00 00 00 00 00 00
    Data 10: 00 00 00 00
  Type 26 Record: #8
    Data 00: 1a 16 08 00 01 6a 00 80 00 80 00 80 00 80 00 80
    Data 10: 00 00 00 00 00 80
    String 1: "LM78A"
  Type 28 Record: #9
    Data 00: 1c 16 09 00 01 6a 00 80 00 80 00 80 00 80 00 80
    Data 10: 00 00 00 00 00 80
    String 1: "LM78A"
  Type 27 Record: #10
    Data 00: 1b 0f 0a 00 09 00 67 01 00 00 00 00 00 80 01
    String 1: "Cooling Dev 1"
  Type 29 Record: #11
    Data 00: 1d 16 0b 00 01 6a 00 80 00 80 00 80 00 80 00 80
    Data 10: 00 00 00 00 00 80
    String 1: "ABC"
  Type 39 Record: #12
    Data 00: 27 16 0c 00 01 01 02 03 04 05 06 07 00 80 a2 11
    Data 10: 08 00 0a 00 0b 00
    String 1: "To Be Filled By O.E.M."
    String 2: "To Be Filled By O.E.M."
    String 3: "To Be Filled By O.E.M."
    String 4: "To Be Filled By O.E.M."
    String 5: "To Be Filled By O.E.M."
    String 6: "To Be Filled By O.E.M."
    String 7: "To Be Filled By O.E.M."
  Type 41 Record: #13
    Data 00: 29 0b 0d 00 01 83 01 00 00 00 10
    String 1: "Onboard IGD"
  Type 41 Record: #14
    Data 00: 29 0b 0e 00 01 85 01 00 00 00 c8
    String 1: "Onboard LAN"
  Type 41 Record: #15
    Data 00: 29 0b 0f 00 01 81 01 00 00 03 e2
    String 1: "Onboard 1394"
  Cache Info: #16
    Designation: "CPU Internal L2"
    Level: L2
    State: Enabled
    Mode: 0x00 (Write Through)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x06 (Multi-bit)
    Type: 0x03 (Instruction)
    Associativity: 0x08 (16-way Set-Associative)
    Max. Size: 1024 kB
    Current Size: 1024 kB
    Supported SRAM Types: 0x0002 (Unknown)
    Current SRAM Type: 0x0002 (Unknown)
  Cache Info: #17
    Designation: "CPU Internal L1"
    Level: L1
    State: Enabled
    Mode: 0x00 (Write Through)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x04 (Parity)
    Type: 0x01 (Other)
    Associativity: 0x08 (16-way Set-Associative)
    Max. Size: 128 kB
    Current Size: 128 kB
    Supported SRAM Types: 0x0002 (Unknown)
    Current SRAM Type: 0x0002 (Unknown)
  Cache Info: #18
    Designation: "CPU Internal L3"
    Level: L3
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x06 (Multi-bit)
    Type: 0x03 (Instruction)
    Associativity: 0x0c (Other)
    Max. Size: 6144 kB
    Current Size: 6144 kB
    Supported SRAM Types: 0x0002 (Unknown)
    Current SRAM Type: 0x0002 (Unknown)
  Physical Memory Array: #19
    Use: 0x03 (System memory)
    Location: 0x03 (Motherboard)
    Slots: 4
    Max. Size: 32 GB
    ECC: 0x03 (None)
  Processor Info: #20
    Socket: "SOCKET 0"
    Socket Type: 0x21 (Other)
    Socket Status: Populated
    Type: 0x03 (CPU)
    Family: 0xc6 (Other)
    Manufacturer: "Intel(R) Corporation"
    Version: "Intel(R) Core(TM) i7-2760QM CPU @ 2.40GHz"
    Asset Tag: "Fill By OEM"
    Part Number: "Fill By OEM"
    Processor ID: 0xbfebfbff000206a7
    Status: 0x01 (Enabled)
    Voltage: 1.2 V
    External Clock: 100 MHz
    Max. Speed: 3800 MHz
    Current Speed: 2400 MHz
    L1 Cache: #17
    L2 Cache: #16
    L3 Cache: #18
  Memory Device: #21
    Location: "ChannelA-DIMM0"
    Bank: "BANK 0"
    Manufacturer: "029E"
    Serial: "00000000"
    Asset Tag: "9876543210"
    Part Number: "CMSX8GX3M1A1600C1"
    Memory Array: #19
    Form Factor: 0x0d (SODIMM)
    Type: 0x18 (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 8 GB
    Speed: 1600 MHz
  Memory Device Mapping: #22
    Memory Device: #21
    Array Mapping: #27
    Interleave Pos: 1
    Interleaved Depth: 2
    Start Address: 0x0000000000000000
    End Address: 0x0000000200000000
  Memory Device: #23
    Location: "ChannelA-DIMM1"
    Bank: "BANK 1"
    Manufacturer: "[Empty]"
    Serial: "[Empty]"
    Asset Tag: "9876543210"
    Part Number: "[Empty]"
    Memory Array: #19
    Form Factor: 0x09 (DIMM)
    Type: 0x02 (Unknown)
    Data Width: 0 bits
    Size: No Memory Installed
  Memory Device: #24
    Location: "ChannelB-DIMM0"
    Bank: "BANK 2"
    Manufacturer: "029E"
    Serial: "00000000"
    Asset Tag: "9876543210"
    Part Number: "CMSX8GX3M1A1600C1"
    Memory Array: #19
    Form Factor: 0x0d (SODIMM)
    Type: 0x18 (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 8 GB
    Speed: 1600 MHz
  Memory Device Mapping: #25
    Memory Device: #24
    Array Mapping: #27
    Interleave Pos: 2
    Interleaved Depth: 2
    Start Address: 0x0000000200000000
    End Address: 0x0000000400000000
  Memory Device: #26
    Location: "ChannelB-DIMM1"
    Bank: "BANK 3"
    Manufacturer: "[Empty]"
    Serial: "[Empty]"
    Asset Tag: "9876543210"
    Part Number: "[Empty]"
    Memory Array: #19
    Form Factor: 0x09 (DIMM)
    Type: 0x02 (Unknown)
    Data Width: 0 bits
    Size: No Memory Installed
  Memory Array Mapping: #27
    Memory Array: #19
    Partition Width: 4
    Start Address: 0x0000000000000000
    End Address: 0x0000000400000000
  Type 131 Record: #30
    Data 00: 83 40 1e 00 35 00 00 00 00 00 00 00 00 00 00 00
    Data 10: f8 00 57 1e ff ff ff ff 01 20 00 00 00 00 08 00
    Data 20: a1 05 04 00 00 00 00 00 c8 00 ff ff 00 00 00 00
    Data 30: 00 00 00 00 f6 00 00 00 76 50 72 6f 00 00 00 00
  Language Info: #31
    Languages: en|US|iso8859-1
    Current: en|US|iso8859-1
  Config Status: cfg=new, avail=yes, need=no, active=unknown

-------------------------

**alex@kubuntu:~$** sudo dmidecode --type bios
# dmidecode 2.11
SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: American Megatrends Inc.
        Version: 4.6.5
        Release Date: 04/14/2012
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 4096 kB
        Characteristics:
                PCI is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 kB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                ACPI is supported
                USB legacy is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
                UEFI is supported
        BIOS Revision: 4.6

Handle 0x001F, DMI type 13, 22 bytes
BIOS Language Information
        Language Description Format: Long
        Installable Languages: 1
                en|US|iso8859-1
        Currently Installed Language: en|US|iso8859-1
```

---

