---
title: "Can't get Descent game working (D1X, DXX-Rebirth)"
date: 2009-07-30
forum: General Help
---

### Post by Dave_Jackson on 2009-07-30
Hi all.
For the past few days, I have been trying to install d1x and/or dxx-rebirth. Both are ports of the classic Descent games to Linux. I got dxx-rebirth to compile the binaries, but it produces no data directory for the game files. So no dice with dxx-rebirth. ([http://www.dxx-rebirth.com/]("http://www.dxx-rebirth.com/"))

So I tried d1x instead. 
Here is the link to the RPM package I used: ([http://download1.rpmfusion.org/nonfree/fedora/releases/11/Everything/x86_64/os/repoview/d1x-full.html]("http://download1.rpmfusion.org/nonfree/fedora/releases/11/Everything/x86_64/os/repoview/d1x-full.html"))
 D1X is offered in the Fedora Fusion repos and that is what I used when I used Fedora. So I downloaded the D1x-full package and converted it to a debian file using alien -k. I get a binary file and a data directory. When I put the files descent.hog and descent.pig (yes, they are lowercase) in /usr/share/d1x/full, the game crashes when I try to load a level. This happens on both the GL and SDL versions. 

The console output is as follows: 
> d1x-gl-full
D1X v1.43
This is a MODIFIED version of DESCENT which is NOT supported by Parallax or
Interplay. Use at your own risk!
Based on: DESCENT   Registered v1.5 Jan 5, 1996
Copyright (C) 1994, 1995 Parallax Software Corporation
DESCENT is a trademark of Interplay Productions, Inc.

Type 'DESCENT -help' for a list of command-line options.
/dev/modem: No such file or directory
gl vendor:NVIDIA Corporation renderer:GeForce 8400M GS/PCI/SSE2 version:3.0.0 NVIDIA 185.18.14 extensions:GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_instanced GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_geometry_shader4 GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NV_vertex_buffer_unified_memory GL_NV_shader_buffer_load GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
gl_arb_multitexture:0 gl_sgis_multitexture:0
gl_intensity4:1 gl_luminance4_alpha4:1 gl_rgba2:1 gl_readpixels:1 gl_gettexlevelparam:1
**sh: playmus: not found**


Descent is one of my favorite games and I was really happy that Fedora had made it's installation so simple by putting it in the repos. Maybe Ubuntu could do the same. Then I wouldn't have to go through all this. 
 
If anyone has gotten these games working under Ubuntu, please tell me how you did it. I've been very creative, but so far nothing I try is working. 

Thanks in advance for your time.

---

### Post by Dave_Jackson on 2009-08-03
BUMP?:(

C'mon people, surely someone knows something that I don't about this. 
These are fairly popular games, even today, so someone else must have tried to install these on Ubuntu. 

If anyone has anything to offer, please do.

---

### Post by anaconda on 2009-08-03
The original DOS versions of descent1 and descent2 work flawlessly with dosbox, so why would anyone need a linux port?

EDIT: I just noticed that they have made some improvements and new features... Maybe I will try the linux version sometime.

---

### Post by lazerblade on 2009-08-06
I don't know about the RPM package.
But, I just finished setting up "d1x-rebirth-gl" on Ubuntu 9.04.

I think I'll just give you a complete rundown of how I did it:


First, I got the source for d1x-rebirth 0.55 from here:
[http://sourceforge.net/projects/dxx-rebirth/files/dxx-rebirth/d1x-rebirth_v0.55.1-src.tar.gz](http://sourceforge.net/projects/dxx-rebirth/files/dxx-rebirth/d1x-rebirth_v0.55.1-src.tar.gz)

Then I extracted it. 
#tar -xvzf d1x-rebirth_v0.55.1-src.tar.gz


Installed scons.
#sudo apt-get install scons


Compiled and installed physfs. (if I tell you how to do this, that'll take all the fun out of it)


Following instructions, compiled d1x-rebirth.
#scons

Installed it.
#scons install


Then, I copied my hog files into ~/.d1x-rebirth.
(rename them to lowercase if they aren't already)


Then, I had to copy "libphysfs.so.1" from "/usr/local/lib" to "/lib" and to "/usr/lib"
#sudo cp /usr/local/lib/libphysfs.so.1 /lib/
#sudo cp /usr/local/lib/libphysfs.so.1 /usr/lib/



After all of this, I could run it at the snap of a finger.

#d1x-rebirth-gl




Try this out!

If this doesn't do it, I can write a compete guide with shell scipts, and instructions on how to install physfs.

---

### Post by evoka0 on 2009-09-23
Lazerblade, 
  Sorry to take the fun out, but i need your help to compile and install physfs, i have no idea how to do it, already downloaded it trhough synaptic, Im using jaunty.  
  > **lazerblade said:**
>  Compiled and installed physfs. (if I tell you how to do this, that'll take all the fun out of it)


 Regards, evoka

---

### Post by lazerblade on 2009-09-30
Aw drat.:)


Basically, grab this file: 
[http://icculus.org/physfs/downloads/physfs-2.0.0.tar.gz](http://icculus.org/physfs/downloads/physfs-2.0.0.tar.gz)


untar/gzip it
# tar -xvzf physfs-2.0.0.tar.gz

go into that directory
# cd physfs-2.0.0

and cmake it (installing cmake is easy, use "apt-get install cmake")
# cmake .

and then make it
# make

and then install
# sudo make install


After all this, physfs should be installed, and you can continue
with installing d1x-rebirth-gl. Don't forget to copy "libphysfs.so.1"
from "/usr/local/lib" to "/lib" and to "/usr/lib"


P.S.
Sorry for the late reply.

P.P.S
I just noticed you will need the packages "libsdl1.2debian-all" and "libsdl1.2-dev".
If you don't have them, than when using "scons" to compile d1x-rebirth-gl, it will give you
errors.
Installing them is easy.

---

### Post by evoka0 on 2009-10-01
Lazerblade,

Thanks a lot for your help, I couldnt download physfs 2.0 from the website, but the one on synaptic worked ok. It seems that what fixed my problem was installing the packages "libsdl1.2debian-all" and "libsdl1.2-dev".

Now I am already playing level 3 !! 

Best

---

### Post by lazerblade on 2009-10-01
Thats great!:popcorn:
Enjoy your game!

---

