---
title: "Screen Flickering During Game Play"
date: 2006-06-08
forum: General Help
---

### Post by Ted_Smith on 2006-06-08
My screen is fine normally, I have several resolutions to choose from, and the Nvidia drivers are all installed OK. 

However, whenever I play Americas Army, it starts off fine for about 5 minutes, then all of a sudden the screen goes blank for a second and then comes back flickering. If I exit, the screen remains flickering for a few seconds when I'm back in Gnome then it goes blank again and comes back fine. Very odd. 

Anyone know why and how I fix it? 

Thanks

Ted

---

### Post by Ted_Smith on 2006-06-08
Sync rates have been suggested on IRC but I'm not sure how to adjust them. I've tunred off 'VSync' in AA but no difference.

---

### Post by Ted_Smith on 2006-06-08
Researched the vertical & horizontal sync rates for my Dell E771p CRT monitor, added them to xorg.conf, restarted X, but still not working. Flickering began about 10 minutes into game. Very frustrating.

---

### Post by sean3k on 2006-06-08
if it's only happening when you're using 3d acceleration, it might be because your graphics card is overheating.  try dusting once in a while :)

oh, and my old GEM crt used to flicker, but thats because it was junk and had bad wiring.  I doubt that's the same problem you're having.

---

### Post by Ted_Smith on 2006-06-09
Opened up the box, cleaned out the dust (there wasn't much in it), upgraded to Dapper this morning and re-installed the Nvidia drivers. Problem persists. 

Darn. Very annoying.

---

### Post by Ted_Smith on 2006-06-09
Incidentally, output for my card :

ted@mainunit:~$ cat /proc/driver/nvidia/agp/status
Status: Enabled
Driver: AGPGART
AGP Rate: 8x
Fast Writes: Enabled
SBA: Enabled
ted@mainunit:~$ glxgears -printfps
11206 frames in 5.0 seconds = 2241.075 FPS
11204 frames in 5.0 seconds = 2240.742 FPS

I've tried to take some screenshots but they all look clear as screenshots so won't be of any use - they don't illustrate the problem. 

Interestingly, having installed Tux Racer, the problem occurs in that too so it not specific to Americas Army. Quite clearly a hardware fault my end. 

Here is output of glxinfo : 

```

ted@mainunit:~$ glxinfo name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5600/AGP/SSE/3DNOW!
OpenGL version string: 2.0.2 NVIDIA 87.62
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_sRGB,
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_HP_occlusion_test,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color,
    GL_NV_depth_clamp, GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance,
    GL_NV_fragment_program, GL_NV_fragment_program_option, GL_NV_half_float,
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint,
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range,
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess 

```

Does that help anyone, anyone at all? I am desperate to play 3D games on my new Dapper rig!!

---

### Post by Ted_Smith on 2006-06-11
Interestingly, I booted into Windows XP, installed the Windows version of AA, and it does it on that too. 

So it's not an OS issue (Linux or Windows), or game specific. It's either my graphics card, or the monitor that's causing the problem. The monitor is actually about 5 years old, standard 17" Dell CRT that came with my old Dewll Dimension 4100. And it's had a lot of use in that time. Maybe it's that. The card is newer (about 3 years old). Not really sure how to eliminate either though. 

The only other thing I can think of the KVM switch I use but that's always been fine in the past....

---

### Post by Ted_Smith on 2006-06-16
I thought the problem must have been either the graphics card or VDU. So, I swapped the VDU for one from work, but the problem persists! Darn!!

So I assumed it must be a hardware component of the tower unit. The graphics card is the obvious assumption, but odly, my PC keeps turning itself off randomly quite frequently (almost daily if left running 24\7), so I'm begining to wonder if it might be something else, not necessarily the graphics card. Unfortunately, when I look at the logs in var/logs they don't tell me anything that gives me any clues to the problem. For example, the last one I read related to obtaining a DHCP IP address from the router - I doubt that would shut my PC down. So something is worng somewhere, but I don't know where.

Is there a Linux utility that I can run to test ALL hardware (other than just the RAM for example for which I'd use MemTest on a bootable CD) before I fork out on a new GC? I'd hate to waste money on a new card needlesly (I can't afford to either!)

---

