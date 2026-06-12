---
title: "Video Card Question"
date: 2006-04-04
forum: General Help
---

### Post by aznchong91 on 2006-04-04
Hello, I am rather ignorant about video cards, and I am very confused. How do I see what Video Card I am using? What are ATI and Nvidia? Are they hardware or software? Do I have either of them by default or something? Thx to anyone that can help me!

---

### Post by Stealth on 2006-04-04
I believe typing "glxinfo" in commandline should give you a clue. :)

---

### Post by taurus on 2006-04-04
Is it a desktop or a laptop (manufacture)?  If it's a desktop and not build-on mobo, then just open the case and look at it...

---

### Post by aznchong91 on 2006-04-04
Wow, thx for those fast replies, I really appreciate it! it's a laptop. Sony VAIO to be exact. I ran the glxinfo command, but i don't understand a word!!! here it is, if you can help me, sorry! :D

> root@dy090-040:/# glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 830M 20050225
OpenGL version string: 1.3 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1,
    GL_APPLE_client_storage, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

EDIT:: So, am I running ATI, Nvidia, or nothing at all? Do I install ATI or Nvidia or something? Thx!

---

### Post by taurus on 2006-04-04
The easiest thing to do is head over to Sony's site and look up your model.  It should tell you everything you need about your laptop!!!  I recommand you print out the spec sheet of your laptop so you don't have to look it up again later...  That's probably the best way to go!

p.s.  Looks like an nVidia video card from the message above!!!

---

### Post by aznchong91 on 2006-04-04
thx for the suggestion, I'll do it right away. Can you just answer another question? What exactly is ATI and Nvidia? Are they software or hardware? Thx again!

---

### Post by taurus on 2006-04-04
That would be hardware.  Some video cards use nVidia technology while other companies use ATI.  Some even use Intel intergrated video controller, onboard and crappy like hell, as it video controller.  If you have to choose, always go with nVidia since it works better in Linux and other manufactures...

---

### Post by aznchong91 on 2006-04-04
o no... i am using a REALLY old laptop for linux... I went into xorg.conf , and saw i810 somewhere. I also saw it somewhere else in this forum, in the same post as a video card thread of some sorts... is my video card using Intel integrated video controller technology??? Thx again, I'm sorry if I am being a bother.

---

### Post by taurus on 2006-04-04
Yip!  If you are using i810 driver for your video card, then you are using one of those Intel intergrated video controllers thing just like my new Dell that I have in my office!!!  ](*,)   You can check for it if you look in /etc/X11/xorg.conf from a terminal, Applications -> Accessories -> Terminal...
```

more /etc/X11/xorg.conf

```

---

### Post by aznchong91 on 2006-04-04
ok, thx for all your help! I really appreciate it, and I wish I could pay you back somehow.

---

### Post by taurus on 2006-04-04
You can get me an nVidia card for that new Dell BUT even if you did, I couldn't install on that sucker because it's a space saver box so there is no room to add anything inside!!!  I need to talk to those in charge of purchasing computers in the ITS department!  It's time for some head slapping around here...  :twisted:

---

### Post by Toxicity999 on 2006-04-04
Even if it were full sized is your office so cool as to let you crack open the box? lol.

---

### Post by taurus on 2006-04-04
[QUOTE=Toxicity999]Even if it were full sized is your office so cool as to let you crack open the box? lol.[/QUOTE]
Yes because I added a second harddrive to my old Dell which by the way came with nVidia video card--mid tower.  In fact, they supposed to put XP on it but they knew that I would wipe that sucker off my computer anyway so they just dropped of the computer in my office with no OS on it at all...  That was the way I want it...  ;)

---

