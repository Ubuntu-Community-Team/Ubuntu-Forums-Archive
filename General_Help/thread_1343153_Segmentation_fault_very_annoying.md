---
title: "Segmentation fault very annoying"
date: 2009-12-01
forum: General Help
---

### Post by domagoj91 on 2009-12-01
Hi.:biggrin:

Okay, I am using Ubuntu now for several weeks and I am trying to figure out how to fix this problem. 

Whenever I start any 3D application ubuntu just dont won't let it start . After I've tryed to start these same applications (blender, stellarium) via terminal I am getting these messages.

> altair@altair-laptop:~$ stellarium
QProcess: Destroyed while process is still running.
 ------------------------------------------------------- 
[ This is Stellarium 0.10.2 - [http://www.stellarium.org](http://www.stellarium.org) ] 
[ Copyright (C) 2000-2009 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/altair/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/altair/.stellarium" 
  1 .  "/usr/share/stellarium" 
Config file is:  "/home/altair/.stellarium/config.ini" 
Segmentation fault
This is what i get for stellarium

> altair@altair-laptop:~$ blender
Compiled with Python version 2.6.4.
Checking for installed Python... got it!
Segmentation fault
This is what I get for running Blender

My graphic card is ATI Mobility Radeon 7500. Drivers are latest i could find that support this card.

Glxinfo output
> altair@altair-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R100 (RV200 4C57) 20090101 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.6
OpenGL extensions:
    GL_ARB_draw_buffers, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

8 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x69 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5f 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon

8 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x60  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x62  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x63  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x65  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x66  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x67  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

Compiz video effect works almost without a problem (fire effect is crushing my computer, water effect doesent work and some advace effects are crushing).
Disabling compiz doesn't affect the problem.
This PC was alredy runing these applications on ubuntu system a year ago (8.04. or 8.10.)

I will apriciate all help and advices I can get...

Thank you.!

---

### Post by otchie1 on 2009-12-01
As no 3D apps work and as things like Compliz Fire & water are crushing your box I'd suggest re-doing your video card driver installation.
I've never used ATi but I'm sure a glance through your xorg.conf will tell you if you're actually running a proper ATi driver or just the ATi equivalent of nv.

---

### Post by otchie1 on 2009-12-01
duplicate.

---

### Post by ibuclaw on 2009-12-01
Can you open a terminal and paste in the following:
```
dmesg | grep segfault
```

Then paste the output in your next post?

Regards
Iain

---

### Post by domagoj91 on 2009-12-01
> **otchie1 said:**
> As no 3D apps work and as things like Compliz Fire & water are crushing your box I'd suggest re-doing your video card driver installation.
I've never used ATi but I'm sure a glance through your xorg.conf will tell you if you're actually running a proper ATi driver or just the ATi equivalent of nv.

i tryed that, no results, but i can add that my xorg.conf doesent exist in /etc/X11/

I am quite noob in this area what do you mean by > ATi equivalent of nv.

---

### Post by domagoj91 on 2009-12-01
> **tinivole said:**
> Can you open a terminal and paste in the following:
```
dmesg | grep segfault
```Then paste the output in your next post?

Regards
Iain

> altair@altair-laptop:~$ dmesg | grep segfault
[  196.393773] python[1775]: segfault at a41d0bc ip 00199217 sp bfc563b4 error 4 in libc-2.10.1.so[129000+13e000]
[  204.482414] stellarium[1790]: segfault at 79ac677 ip 07958b43 sp bff1e0a0 error 7 in radeon_dri.so[7908000+24f000]
[  243.129225] stellarium[1842]: segfault at 7595677 ip 07541b43 sp bfd54480 error 7 in radeon_dri.so[74f1000+24f000]
[  864.086742] stellarium[1997]: segfault at 4b72677 ip 04b1eb43 sp bf82ea60 error 7 in radeon_dri.so[4ace000+24f000]
[  872.603084] stellarium[2000]: segfault at 9b41677 ip 09aedb43 sp bf8c9760 error 7 in radeon_dri.so[9a9d000+24f000]
[ 1364.880745] blender-bin[2035]: segfault at 22222222 ip 00935f8d sp bfa0e798 error 4 in ld-2.10.1.so[92d000+1b000]
altair@altair-laptop:~$ 


here this is what i get

---

### Post by cagey5 on 2009-12-01
I've had this problem too with Blender 2.5, though not with 2.49.

Strangely I was able to run 2.5 several times and then it suddenly wouldn't start at all. I was able to run it under a new user profile but not the default.

It appeared to me that it was the splash screen that was a problem for some reason.

On another forum someone suggested starting Blender with 'blender 1' but without the quotes. Apparently it will work with any character and Blender then runs but does skip the initial splash screen so perhaps that was the problem. The character doesn't actually initiate anything in Blender, it's not a recognized modifier.  Still doesn't get to the bottom of the actual problem though.

Here's a link to the other discussion for info..

[http://www.blender.org/forum/viewtopic.php?t=16258](http://www.blender.org/forum/viewtopic.php?t=16258)

---

### Post by domagoj91 on 2009-12-01
[SIZE=1]> **cagey5 said:**
> I've had this problem too with Blender 2.5, though not with 2.49.

Strangely I was able to run 2.5 several times and then it suddenly wouldn't start at all. I was able to run it under a new user profile but not the default.

It appeared to me that it was the splash screen that was a problem for some reason.

On another forum someone suggested starting Blender with 'blender 1' but without the quotes. Apparently it will work with any character and Blender then runs but does skip the initial splash screen so perhaps that was the problem. The character doesn't actually initiate anything in Blender, it's not a recognized modifier.  Still doesn't get to the bottom of the actual problem though.

Here's a link to the other discussion for info..

[http://www.blender.org/forum/viewtopic.php?t=16258](http://www.blender.org/forum/viewtopic.php?t=16258)[/SIZE]      
> altair@altair-laptop:~$ blender 1
Compiled with Python version 2.6.4.
Checking for installed Python... got it!
Segmentation fault
altair@altair-laptop:~$ 


doesn't work, thanks for a try to help..

---

### Post by ibuclaw on 2009-12-01
> **domagoj91 said:**
> here this is what i get

Firstly - if you have anything like **prelink** or **preload**, I suggest you remove it.
```
sudo apt-get purge preload prelink
```
Secondly - reinstall libgl1-mesa-dri
```
sudo aptitude libgl1-mesa-dri
```
And reboot your workstation.

If that doesn't work - as per above, create a new user and try it to see if the problem is with the profile, or the workstation.

Regards
Iain

---

### Post by domagoj91 on 2009-12-01
> **tinivole said:**
> Firstly - if you have anything like **prelink** or **preload**, I suggest you remove it.
```
sudo apt-get purge preload prelink
```Secondly - reinstall libgl1-mesa-dri
```
sudo aptitude libgl1-mesa-dri
```And reboot your workstation.

If that doesn't work - as per above, create a new user and try it to see if the problem is with the profile, or the workstation.

Regards
Iain

I reinstalled the libgl1-mesa-dri and rebooted the workstation but there was no result.](*,)
thanx for a try... If something cross over your mind just say...

Regards Domagoj.

---

### Post by NoaHall on 2009-12-01
Maybe a weird fix - the problem seems to be in the graphics card, but try running memtest and see if there are any errors. A good test is usually about one hour+

---

### Post by domagoj91 on 2009-12-01
> **NoaHall said:**
> Maybe a weird fix - the problem seems to be in the graphics card, but try running memtest and see if there are any errors. A good test is usually about one hour+

How to run it.....
:confused:

---

### Post by NoaHall on 2009-12-01
> **domagoj91 said:**
> How to run it.....
:confused:

From the grub boot up menu. Use either esc/shift to get there(before ubuntu starts loading, after the BIOS)

---

### Post by domagoj91 on 2009-12-01
what if memtest find something...

---

### Post by NoaHall on 2009-12-01
> **domagoj91 said:**
> what if memtest find something...

Then you need new RAM.

---

### Post by domagoj91 on 2009-12-01
> **noahall said:**
> then you need new ram.

"great" ](*,)

---

### Post by ibuclaw on 2009-12-01
> **domagoj91 said:**
> "great" ](*,)

Have you tried a new user account?

To create one, go to System -> Administration -> Users & Groups.

---

### Post by domagoj91 on 2009-12-03
> **tinivole said:**
> Have you tried a new user account?

To create one, go to System -> Administration -> Users & Groups.

Yes I have, apparently I have problems with RAMs, memtest is crushing but not showing problems.

With new user account there was no change in softwares behaviour.

I dont have money for RAMs right now and its an older laptop so i don't know will it pay out if i invest in it.

Thanx for your concern.
Regards Domagoj.

---

### Post by domagoj91 on 2009-12-03
Hi again I've managed to install and run unreal tournament 1999 GOTY   . It was little glitchy on the hardware rendering so i switch it on a software rendering. It is running faster than on my other PC (2GB RAM this has 512MB). So i was thinkin this must be graphic card error.

I will apriciate all opnions an advices, thanks.
Regars Domagoj

---

### Post by hurdevan on 2010-01-11
I had the same issue and came across away to get somewhat around it. Although I still don't know what the problem is I got around it running it in another X session.

I downloaded blender and dumped it someplace then I switched to tty1(Crtl+alt+F1) and logged in. I ran xinit -- :1 to run another xsession and after that I went to the folder where I dumped blender and ran it; and it ran. BUT.... it does not register mouse clicks,,,,, darnit](*,). It does however register the keyboard.

---

