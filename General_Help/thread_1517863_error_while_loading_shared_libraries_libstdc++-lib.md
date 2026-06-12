---
title: "error while loading shared libraries: libstdc++-libc6.2-2.so.3"
date: 2010-06-25
forum: General Help
---

### Post by Cleveland Rock on 2010-06-25
I'm trying to run [the Linux version of Return to Castle Wolfenstein]("ftp://ftp.idsoftware.com/idstuff/wolf/linux/"), but I get the following errors:
```
clevelandrock@Centurion:~$ wolf
./wolf.x86: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
clevelandrock@Centurion:~$ apt-file search libstdc++-libc6.2-2.so.3
clevelandrock@Centurion:~$ uname -a
Linux Centurion 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
clevelandrock@Centurion:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid
clevelandrock@Centurion:~$ 
```[This thread]("http://ubuntuforums.org/showthread.php?t=927183&highlight=error+loading+shared+libraries%3A+libstdc+-libc6.2-2.so.3") did not seem to help.

Any ideas? Try not to confuse me; I'm no expert. Thanks in advance.

---

### Post by gzarkadas on 2010-06-25
Go to page [http://packages.debian.org/etch/libstdc%2B%2B2.10-glibc2.2](http://packages.debian.org/etch/libstdc%2B%2B2.10-glibc2.2) and from the table with heading `Download libstdc++2.10-glibc2.2' select the appropriate for your architecture package. From what I saw in your post, this is the `i386' link.

After you have downloaded the package file (a .deb file), open a terminal window and type:
```

cd <path-to-directory-where-the-deb-is>
sudo dpkg -i <name-of-the-deb-file>

```You 'll have of course to put the real path and name in the placeholders.

---

### Post by Cleveland Rock on 2010-06-25
@gzarkadas:
I get a 404 error trying to download the package from any of the mirrors.

---

### Post by gzarkadas on 2010-06-25
Yes, it seems they have removed versions of gcc previous to 3. The library you want is from gcc CVS 2.95.4-27, dated 2001-10-02. Now your options are:

1. Use this page: [http://packages.debian.org/lenny/libstdc++5](http://packages.debian.org/lenny/libstdc++5) to get the .deb for the next version of libstc++ and install it with the procedure outlined in my previous post. In the thread you linked the last post states that this is a solution. So, it may work.

2. If next version won't work, try to get a close match of libstc++ from older versions and compile it from source (the ./configure, make, make install stuff). The closest ones I found are:
[ftp://ftp.ntua.gr/pub/gnu/gcc/libstdc++/old-releases/libstdc++-2.92.tar.gz](ftp://ftp.ntua.gr/pub/gnu/gcc/libstdc++/old-releases/libstdc++-2.92.tar.gz) [2001-04-06]
[ftp://ftp.ntua.gr/pub/gnu/gcc/libstdc++/old-releases/libstdc++-3.0.tar.gz](ftp://ftp.ntua.gr/pub/gnu/gcc/libstdc++/old-releases/libstdc++-3.0.tar.gz) [2001-06-26]
This may work if changes till the CVS snapshot where minimal, or it may not.

3. Download gcc sources from CVS. Goto [http://www.gnu.org/software/gcc](http://www.gnu.org/software/gcc) and follow the links in the `**"Live" Sources**' box. Since this is an old gcc version, the instructions for CVS is those that are of interest to you. This path will give you the exact sources, but it is an involved one.

---

### Post by Cleveland Rock on 2010-06-25
Since I already have libstdc++5 installed, and method #2 didn't work (it told me I didn't have install-sh or something like that), I tried method #3 and get this.

```
objc-parse.y:1428.19-20: $$ for the midrule at $4 of `structsp' has no declared type
objc-parse.y:1440.19-20: $$ for the midrule at $4 of `structsp' has no declared type
objc-parse.y:1451.19-20: $$ for the midrule at $4 of `structsp' has no declared type
objc-parse.y:1457.19-20: $$ for the midrule at $3 of `structsp' has no declared type
make[1]: *** [objc/objc-parse.c] Error 1
make[1]: Leaving directory `/home/clevelandrock/gcc/gcc'
make: *** [all-gcc] Error 2

```

---

### Post by gzarkadas on 2010-06-26
Unfortunately, since you are trying to build an obsolete version coming from a cvs tree, you 'll have to trace the error and modify the code. This has always been a lonely trip...

But before fiddling with sources, you could use `ldd' to figure out what libraries your executable needs (it may not be just libstdc++-...) and, for those missing, create symlinks with the same path that point to installed versions of the same libraries (most probably newer ones). It is a hack and it may just lead you to seg faults, but it may also work and is easier than debugging the gcc tree.

---

### Post by Cleveland Rock on 2010-06-26
libstdc++-libc6.2-2.so.3 is apparently the only one I need that I don't have.

How do I create the symlinks? If it helps, I currently have the following related packages installed:
libstdc++5
libstdc++6
libstdc++6-4.4-dev

---

### Post by gzarkadas on 2010-06-26
Open a terminal and type (not the comments, these are for your information):
```

[COLOR=DimGray]# go to where the libstdc* libraries are located 
[/COLOR]cd /usr/lib
[COLOR=DimGray]# locate them
[/COLOR]ls -la libstdc*

[COLOR=DimGray]# now write down the filename of the library that corresponds 
# to libstdc++5, ie the oldest version
[/COLOR]
[COLOR=DimGray]# make the symbolic link; replace <lib> 
# with the name you wrote down above
[/COLOR]sudo ln  -s -T  <lib>  libstdc++-libc6.2-2.so.3

```

---

### Post by Cleveland Rock on 2010-06-26
Okay, I did that and then tried to run the game.
```
./wolf.x86: symbol lookup error: ./wolf.x86: undefined symbol: __builtin_new
```

---

### Post by gzarkadas on 2010-06-26
So, the binary interface of the newer version of the library is incompatible with the older one; no luck. Remove the symlink (don't leave it there if not working) and go back to compilation of gcc from source. 

Another option is to try contact the Debian project to find a way to get this older (etch) binary; its hard to believe they have purged all of their previous version backups.

---

### Post by Cleveland Rock on 2010-06-26
I can't do jack with source code, so, do you know how I could contact Debian?

---

### Post by gzarkadas on 2010-06-26
I think the quickest route is to post an appropriate request at the debian forums:[ http://forums.debian.net/]("http://forums.debian.net/").
There is also the option to use IRC. The page [http://www.debian.org/support](http://www.debian.org/support) has a section on how to proceed with that.

---

### Post by Cleveland Rock on 2010-06-27
> **gzarkadas said:**
> There is also the option to use IRC. The page [http://www.debian.org/support](http://www.debian.org/support) has a section on how to proceed with that.
```
[10:50]    <will>    we support Debian here
[10:50]    <ClevelandRock>    The Ubuntu forums actually asked me to ask you guys.
[10:50]    <ansgar>    !ubuntu
[10:50]    <dpkg>    Ubuntu is based on Debian, but it is not  Debian, and it is unlikely to live up to Debian's standards (see  <Debian policy>). Only Debian is supported on #debian. Use #ubuntu  (irc.freenode.net) instead. Even if the channel happens to be less  helpful, support for distributions other than Debian is offtopic on  #debian. See also <based on debian>.
[10:50]    <will>    ask at #ubuntu
[10:50]    <will>    for ubuntu
[10:50]    <abrotman>    ClevelandRock: that's just silly, really it is
[10:50]    <will>    wow
[10:51]    <will>    crazy guys at #ubuntu
[10:51]    <will>    :-D
[10:51]    <ClevelandRock>    But I apparently need this package,  and I get a 404 error on all of the mirrors:  http://packages.debian.org/etch/libstdc%2B%2B2.10-glibc2.2
[10:51]    <bartm>    ClevelandRock: you could try installing  debian, reproduce the problem (if you can), and come back to ask the  question here :)
[10:51]    <will>    may be you just misunderstood
[10:51]    <themill>    ClevelandRock: (a) don't mix distros like that and (b) /topic.
[10:51]    <abrotman>    ClevelandRock: that will likely break  your system, and this still is not an ubuntu support channel
[10:52]    <ClevelandRock>    Well, alright.
[10:52]    <ansgar>    ClevelandRock: Etch is no longer on the  normal mirrors, only on archive.debian.org. And installing packages for a  different distribution (or even just a different release) will often  not work anyway.
[10:53]    <ClevelandRock>    Thanks. I'll let the forum know.
```

Edit: #ubuntu was no help. They, too, recommended not installing Debian packages on Ubuntu. I found the guy who ported the game to Linux on Facebook, so, hopefully he'll respond. I doubt he will. Haha.

---

### Post by gzarkadas on 2010-06-27
You can get the package from this link: [http://archive.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb](http://archive.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb). After downloading you can proceed to installation.

The package only has the following files in /usr/lib:

[LIST]
[*]libstdc++-3-libc6.2-2-2.10.0.so
[*]libstdc++-libc6.2-2.so.3
[/LIST]
and a documentation folder in /usr/share/doc. You can browse its contents with the standard graphical archiver app shipped with Ubuntu.

I do not believe it can break your system. Although the advice is valid as a general rule,  in this particular case (a simple package that does not override existing binaries in your distro) the warning can be ignored.

---

### Post by Cleveland Rock on 2010-06-27
I've gotten farther than I could before, but now I get this error when I try to load the single-player game. I think it's a game-specific error, unfortunately.

```
clevelandrock@Centurion:~$ wolfsp
Wolf 1.41 linux-i386 Dec  4 2002
----- FS_Startup -----
Current search path:
/home/clevelandrock/.wolf/main
/usr/local/games/wolfenstein/main/sp_pak4.pk3 (21 files)
/usr/local/games/wolfenstein/main/sp_pak3.pk3 (14 files)
/usr/local/games/wolfenstein/main/sp_pak2.pk3 (232 files)
/usr/local/games/wolfenstein/main/sp_pak1.pk3 (1342 files)
/usr/local/games/wolfenstein/main/pak0.pk3 (4775 files)
/usr/local/games/wolfenstein/main

----------------------
6384 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec wolfconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Bypassing CD checks
----- Client Initialization -----
Cmd_AddCommand: map_restart already defined
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 9500 GT/PCI/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...using GL_NV_fog_distance
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 9500 GT/PCI/SSE2
GL_VERSION: 3.2.0 NVIDIA 195.36.24
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_seamless_cube_map GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_parameter_buffer_object2 GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_shader_buffer_load GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_buffer_unified_memory GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program
Received signal 11, exiting...
clevelandrock@Centurion:~$ 

```

Edit: After some searching, I eventually found a fix for this. For the record, the above error was fixed by editing wolfxp.x86 in a hex editor, replacing the string "GL_EXTENSIONS: %s" with "GL_EXTENSIONS: % " (the last character in the string is a space). That would mean I can finally mark this thread as "solved". Thank you so very much for your help.

---

