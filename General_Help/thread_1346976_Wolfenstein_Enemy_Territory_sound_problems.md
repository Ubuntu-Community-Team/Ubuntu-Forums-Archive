---
title: "Wolfenstein Enemy Territory sound problems"
date: 2009-12-05
forum: General Help
---

### Post by Canucker25 on 2009-12-05
Going crazy with this. I have been trying for hours to get the sound to work I have searched forum after forum and googled this around 100 times none of the solutions work for me. Can anyone help?

This is what is says in my terminal


```
 ___________________________________
( You will triumph over your enemy. )
 -----------------------------------
  o
   o   \_\_    _/_/
    o      \__/
           (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
owen@owen-desktop ~/My Games/enemy-territory $ '/home/owen/My Games/enemy-territory/et.x86' 
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/owen/.etwolf/etmain
/home/owen/My Games/enemy-territory/etmain/pak2.pk3 (22 files)
/home/owen/My Games/enemy-territory/etmain/pak1.pk3 (10 files)
/home/owen/My Games/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/owen/My Games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/home/owen/My Games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Canucker25/etconfig.cfg
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
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI R300 (RV350 4153) 20090101 AGP 4x x86/MMX/SSE2 TCL
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: DRI R300 Project
GL_RENDERER: Mesa DRI R300 (RV350 4153) 20090101 AGP 4x x86/MMX/SSE2 TCL
GL_VERSION: 1.5 Mesa 7.6
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_MESAX_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_bgra GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_MESA_swap_control GLX_MESA_swap_frame_usage GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGI_video_sync GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xa5bae000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/owen/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owen/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owen/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/home/owen/My Games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0x9574f40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: owen-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
owen@owen-desktop ~/My Games/enemy-territory $ 


```

---

### Post by pbrane on 2009-12-05
Try this:
[http://ubuntuforums.org/showthread.php?t=1337353]("http://ubuntuforums.org/showthread.php?t=1337353")

this has fixed choppy and no sound issues for me.

---

### Post by Canucker25 on 2009-12-05
Yeah... I don't understand any of that

---

### Post by pbrane on 2009-12-05
oh.

run Text Editor and type **drivers = oss**

save the file as **.alsoftrc** in your home directory. like /home/owen/.alsoftrc

don't forget the dot (period) in front of the filename.

then run Wolfenstein and maybe that will help.

**Actually upon reading the output closer I noticed that the sound system is muted. Maybe you have to turn on the sound in the game.**

---

### Post by Canucker25 on 2009-12-05
Didn't do anything. Thanks for the suggestion though.

---

### Post by Canucker25 on 2009-12-05
> **pbrane said:**
> 
**Actually upon reading the output closer I noticed that the sound system is muted. Maybe you have to turn on the sound in the game.**

Everything is as it should be. Volume is up full-blast actually, still no sound in game. No problems with anything else though.

---

### Post by mcswilly on 2009-12-26
Go here... [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/)
Grab the et-sdl-sound.gz file.  
Unpack the file into your ET dir.
Change your shortcut/launcher to start with et-sdl-sound instead of et.

If your Sound Preferences are setup to simultaneously output to two devices then you will have chopping problems, i.e. I have an analog sound card and usb headphones.  If I try to output to both it all gets ugly.  Change the settings in the Preferences' Output tab if you have this type of setup so that you only go to one device.

p.s. The web page suggests you edit the et-sdl-sound file and change the driver from alsa to pulse.  Do not do this.  Doing so did not work for me.

---

### Post by afrodeity on 2010-08-13
> Go here... [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/)
Grab the et-sdl-sound.gz file.
Unpack the file into your ET dir.
Change your shortcut/launcher to start with et-sdl-sound instead of et.


It didn't start up right away. I had to do the following:

synaptic tells me:


```

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/enemy-territory-data
/usr/share/doc/enemy-territory-data/changelog.Debian.gz
/usr/share/doc/enemy-territory-data/copyright
/usr/share/games
/usr/share/games/enemy-territory
/usr/share/games/enemy-territory/etmain
/usr/share/games/enemy-territory/etmain/campaigncycle.cfg
/usr/share/games/enemy-territory/etmain/cgame.mp.i386.so
/usr/share/games/enemy-territory/etmain/description.txt
/usr/share/games/enemy-territory/etmain/hunkusage.dat
/usr/share/games/enemy-territory/etmain/lmscycle.cfg
/usr/share/games/enemy-territory/etmain/mp_bin.pk3
/usr/share/games/enemy-territory/etmain/objectivecycle.cfg
/usr/share/games/enemy-territory/etmain/pak0.pk3
/usr/share/games/enemy-territory/etmain/pak1.pk3
/usr/share/games/enemy-territory/etmain/pak2.pk3
/usr/share/games/enemy-territory/etmain/punkbuster.cfg
/usr/share/games/enemy-territory/etmain/qagame.mp.i386.so
/usr/share/games/enemy-territory/etmain/server.cfg
/usr/share/games/enemy-territory/etmain/stopwatchcycle.cfg
/usr/share/games/enemy-territory/etmain/ui.mp.i386.so
/usr/share/games/enemy-territory/etmain/video
/usr/share/games/enemy-territory/etmain/video/etintro.roq

```

gedit et-sdl-sound

```

# You can set this in GAME_PATH environment variable
GAME_PATH="/usr/share/games/enemy-territory"

```

starts but no sound. Stuck here:
```

# libSDL.so
#
# You can set this in LIBSDL environment variable
# LIBSDL=""

```

There is a libsdl1.2debian

libsdl1.2debian-pulseaudio

libsdl-sound1.2 

libsdl-mixer1.2

on my system, but no libSDL.so

Any ideas?

---

### Post by afrodeity on 2010-08-14
Solved the issue:

libsdl1.2-dev must be installed.

```

/.
/usr
/usr/bin
/usr/bin/sdl-config
/usr/include
/usr/include/SDL
/usr/include/SDL/SDL.h
/usr/include/SDL/SDL_active.h
/usr/include/SDL/SDL_audio.h
/usr/include/SDL/SDL_byteorder.h
/usr/include/SDL/SDL_cdrom.h
/usr/include/SDL/SDL_config.h
/usr/include/SDL/SDL_cpuinfo.h
/usr/include/SDL/SDL_endian.h
/usr/include/SDL/SDL_error.h
/usr/include/SDL/SDL_events.h
/usr/include/SDL/SDL_getenv.h
/usr/include/SDL/SDL_joystick.h
/usr/include/SDL/SDL_keyboard.h
/usr/include/SDL/SDL_keysym.h
/usr/include/SDL/SDL_loadso.h
/usr/include/SDL/SDL_main.h
/usr/include/SDL/SDL_mouse.h
/usr/include/SDL/SDL_mutex.h
/usr/include/SDL/SDL_name.h
/usr/include/SDL/SDL_opengl.h
/usr/include/SDL/SDL_platform.h
/usr/include/SDL/SDL_quit.h
/usr/include/SDL/SDL_rwops.h
/usr/include/SDL/SDL_stdinc.h
/usr/include/SDL/SDL_syswm.h
/usr/include/SDL/SDL_thread.h
/usr/include/SDL/SDL_timer.h
/usr/include/SDL/SDL_types.h
/usr/include/SDL/SDL_version.h
/usr/include/SDL/SDL_video.h
/usr/include/SDL/begin_code.h
/usr/include/SDL/close_code.h
/usr/lib
/usr/lib/libSDL.a
/usr/lib/libSDL.la
/usr/lib/libSDL.so
/usr/lib/libSDLmain.a
/usr/lib/pkgconfig
/usr/lib/pkgconfig/sdl.pc
/usr/share
/usr/share/aclocal
/usr/share/aclocal/sdl.m4
/usr/share/doc
/usr/share/doc-base
/usr/share/doc-base/libsdl1.2-dev
/usr/share/doc/libsdl1.2-dev
/usr/share/doc/libsdl1.2-dev/BUGS
/usr/share/doc/libsdl1.2-dev/CREDITS
/usr/share/doc/libsdl1.2-dev/README
/usr/share/doc/libsdl1.2-dev/README-SDL.txt
/usr/share/doc/libsdl1.2-dev/changelog.Debian.gz
/usr/share/doc/libsdl1.2-dev/copyright
/usr/share/doc/libsdl1.2-dev/docs
/usr/share/doc/libsdl1.2-dev/docs.html
/usr/share/doc/libsdl1.2-dev/docs/html
/usr/share/doc/libsdl1.2-dev/docs/html/audio.html
/usr/share/doc/libsdl1.2-dev/docs/html/cdrom.html
/usr/share/doc/libsdl1.2-dev/docs/html/event.html
/usr/share/doc/libsdl1.2-dev/docs/html/eventfunctions.html
/usr/share/doc/libsdl1.2-dev/docs/html/eventstructures.html
/usr/share/doc/libsdl1.2-dev/docs/html/general.html
/usr/share/doc/libsdl1.2-dev/docs/html/guide.html
/usr/share/doc/libsdl1.2-dev/docs/html/guideaboutsdldoc.html
/usr/share/doc/libsdl1.2-dev/docs/html/guideaudioexamples.html
/usr/share/doc/libsdl1.2-dev/docs/html/guidebasicsinit.html
/usr/share/doc/libsdl1.2-dev/docs/html/guidecdromexamples.html
/usr/share/doc/libsdl1.2-dev/docs/html/guidecredits.html
/usr/share/doc/libsdl1.2-dev/docs/html/guideeventexamples.html
/usr/share/doc/libsdl1.2-dev/docs/html/guideexamples.html
/usr/share/doc/libsdl1.2-dev/docs/html/guideinput.html
/usr/share/doc/libsdl1.2-dev/docs/html/guideinputkeyboard.html
/usr/share/doc/libsdl1.2-dev/docs/html/guidepreface.html
/usr/share/doc/libsdl1.2-dev/docs/html/guidethebasics.html
/usr/share/doc/libsdl1.2-dev/docs/html/guidetimeexamples.html
/usr/share/doc/libsdl1.2-dev/docs/html/guidevideo.html
/usr/share/doc/libsdl1.2-dev/docs/html/guidevideoopengl.html
/usr/share/doc/libsdl1.2-dev/docs/html/index.html
/usr/share/doc/libsdl1.2-dev/docs/html/joystick.html
/usr/share/doc/libsdl1.2-dev/docs/html/reference.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlactiveevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdladdtimer.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlaudiocvt.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlaudiospec.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlblitsurface.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlbuildaudiocvt.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcd.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdclose.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdeject.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdname.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdnumdrives.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdopen.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdpause.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdplay.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdplaytracks.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdresume.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdstatus.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdstop.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcdtrack.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcloseaudio.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcolor.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcondbroadcast.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcondsignal.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcondwait.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcondwaittimeout.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlconvertaudio.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlconvertsurface.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcreatecond.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcreatecursor.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcreatemutex.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcreatergbsurface.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcreatergbsurfacefrom.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcreatesemaphore.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcreatethread.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlcreateyuvoverlay.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdldelay.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdldestroycond.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdldestroymutex.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdldestroysemaphore.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdldisplayformat.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdldisplayformatalpha.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdldisplayyuvoverlay.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlenablekeyrepeat.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlenableunicode.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlenvvars.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdleventstate.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlexposeevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlfillrect.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlflip.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlfreecursor.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlfreesurface.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlfreewav.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlfreeyuvoverlay.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetappstate.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetaudiostatus.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetcliprect.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetcursor.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgeterror.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgeteventfilter.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetgammaramp.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetkeyname.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetkeystate.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetmodstate.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetmousestate.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetrelativemousestate.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetrgb.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetrgba.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetthreadid.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetticks.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetvideoinfo.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlgetvideosurface.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlglattr.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlglgetattribute.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlglgetprocaddress.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlglloadlibrary.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlglsetattribute.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlglswapbuffers.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlinit.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlinitsubsystem.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoyaxisevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoyballevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoybuttonevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoyhatevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickclose.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickeventstate.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickgetaxis.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickgetball.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickgetbutton.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickgethat.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickindex.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickname.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoysticknumaxes.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoysticknumballs.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoysticknumbuttons.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoysticknumhats.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickopen.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickopened.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdljoystickupdate.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlkey.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlkeyboardevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlkeysym.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlkillthread.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdllistmodes.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlloadbmp.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlloadwav.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdllockaudio.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdllocksurface.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdllockyuvoverlay.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlmaprgb.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlmaprgba.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlmixaudio.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlmousebuttonevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlmousemotionevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlmutexp.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlmutexv.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlnumjoysticks.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlopenaudio.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdloverlay.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlpalette.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlpauseaudio.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlpeepevents.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlpixelformat.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlpollevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlpumpevents.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlpushevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlquit.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlquitevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlquitsubsystem.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlrect.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlremovetimer.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlresizeevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsavebmp.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsempost.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsemtrywait.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsemvalue.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsemwait.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsemwaittimeout.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsetalpha.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsetcliprect.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsetcolorkey.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsetcolors.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsetcursor.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlseteventfilter.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsetgamma.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsetgammaramp.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsetmodstate.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsetpalette.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsettimer.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsetvideomode.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlshowcursor.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsurface.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlsyswmevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlthreadid.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlunlockaudio.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlunlocksurface.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlunlockyuvoverlay.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlupdaterect.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlupdaterects.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdluserevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlvideodrivername.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlvideoinfo.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlvideomodeok.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlwaitevent.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlwaitthread.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlwarpmouse.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlwasinit.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlwmgetcaption.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlwmgrabinput.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlwmiconifywindow.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlwmsetcaption.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlwmseticon.html
/usr/share/doc/libsdl1.2-dev/docs/html/sdlwmtogglefullscreen.html
/usr/share/doc/libsdl1.2-dev/docs/html/thread.html
/usr/share/doc/libsdl1.2-dev/docs/html/time.html
/usr/share/doc/libsdl1.2-dev/docs/html/video.html
/usr/share/doc/libsdl1.2-dev/docs/html/wm.html
/usr/share/doc/libsdl1.2-dev/docs/images
/usr/share/doc/libsdl1.2-dev/docs/images/rainbow.gif
/usr/share/doc/libsdl1.2-dev/docs/index.html
/usr/share/doc/libsdl1.2-dev/examples
/usr/share/doc/libsdl1.2-dev/examples/examples.tar.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/sdl-config.1.gz
/usr/share/man/man3
/usr/share/man/man3/SDLKey.3.gz
/usr/share/man/man3/SDL_ActiveEvent.3.gz
/usr/share/man/man3/SDL_AddTimer.3.gz
/usr/share/man/man3/SDL_AudioCVT.3.gz
/usr/share/man/man3/SDL_AudioSpec.3.gz
/usr/share/man/man3/SDL_BlitSurface.3.gz
/usr/share/man/man3/SDL_BuildAudioCVT.3.gz
/usr/share/man/man3/SDL_CD.3.gz
/usr/share/man/man3/SDL_CDClose.3.gz
/usr/share/man/man3/SDL_CDEject.3.gz
/usr/share/man/man3/SDL_CDName.3.gz
/usr/share/man/man3/SDL_CDNumDrives.3.gz
/usr/share/man/man3/SDL_CDOpen.3.gz
/usr/share/man/man3/SDL_CDPause.3.gz
/usr/share/man/man3/SDL_CDPlay.3.gz
/usr/share/man/man3/SDL_CDPlayTracks.3.gz
/usr/share/man/man3/SDL_CDResume.3.gz
/usr/share/man/man3/SDL_CDStatus.3.gz
/usr/share/man/man3/SDL_CDStop.3.gz
/usr/share/man/man3/SDL_CDtrack.3.gz
/usr/share/man/man3/SDL_CloseAudio.3.gz
/usr/share/man/man3/SDL_Color.3.gz
/usr/share/man/man3/SDL_CondBroadcast.3.gz
/usr/share/man/man3/SDL_CondSignal.3.gz
/usr/share/man/man3/SDL_CondWait.3.gz
/usr/share/man/man3/SDL_CondWaitTimeout.3.gz
/usr/share/man/man3/SDL_ConvertAudio.3.gz
/usr/share/man/man3/SDL_ConvertSurface.3.gz
/usr/share/man/man3/SDL_CreateCond.3.gz
/usr/share/man/man3/SDL_CreateCursor.3.gz
/usr/share/man/man3/SDL_CreateMutex.3.gz
/usr/share/man/man3/SDL_CreateRGBSurface.3.gz
/usr/share/man/man3/SDL_CreateRGBSurfaceFrom.3.gz
/usr/share/man/man3/SDL_CreateSemaphore.3.gz
/usr/share/man/man3/SDL_CreateThread.3.gz
/usr/share/man/man3/SDL_CreateYUVOverlay.3.gz
/usr/share/man/man3/SDL_Delay.3.gz
/usr/share/man/man3/SDL_DestroyCond.3.gz
/usr/share/man/man3/SDL_DestroyMutex.3.gz
/usr/share/man/man3/SDL_DestroySemaphore.3.gz
/usr/share/man/man3/SDL_DisplayFormat.3.gz
/usr/share/man/man3/SDL_DisplayFormatAlpha.3.gz
/usr/share/man/man3/SDL_DisplayYUVOverlay.3.gz
/usr/share/man/man3/SDL_EnableKeyRepeat.3.gz
/usr/share/man/man3/SDL_EnableUNICODE.3.gz
/usr/share/man/man3/SDL_Event.3.gz
/usr/share/man/man3/SDL_EventState.3.gz
/usr/share/man/man3/SDL_ExposeEvent.3.gz
/usr/share/man/man3/SDL_FillRect.3.gz
/usr/share/man/man3/SDL_Flip.3.gz
/usr/share/man/man3/SDL_FreeCursor.3.gz
/usr/share/man/man3/SDL_FreeSurface.3.gz
/usr/share/man/man3/SDL_FreeWAV.3.gz
/usr/share/man/man3/SDL_FreeYUVOverlay.3.gz
/usr/share/man/man3/SDL_GL_GetAttribute.3.gz
/usr/share/man/man3/SDL_GL_GetProcAddress.3.gz
/usr/share/man/man3/SDL_GL_LoadLibrary.3.gz
/usr/share/man/man3/SDL_GL_SetAttribute.3.gz
/usr/share/man/man3/SDL_GL_SwapBuffers.3.gz
/usr/share/man/man3/SDL_GLattr.3.gz
/usr/share/man/man3/SDL_GetAppState.3.gz
/usr/share/man/man3/SDL_GetAudioStatus.3.gz
/usr/share/man/man3/SDL_GetClipRect.3.gz
/usr/share/man/man3/SDL_GetCursor.3.gz
/usr/share/man/man3/SDL_GetError.3.gz
/usr/share/man/man3/SDL_GetEventFilter.3.gz
/usr/share/man/man3/SDL_GetGamma.3.gz
/usr/share/man/man3/SDL_GetGammaRamp.3.gz
/usr/share/man/man3/SDL_GetKeyName.3.gz
/usr/share/man/man3/SDL_GetKeyState.3.gz
/usr/share/man/man3/SDL_GetModState.3.gz
/usr/share/man/man3/SDL_GetMouseState.3.gz
/usr/share/man/man3/SDL_GetRGB.3.gz
/usr/share/man/man3/SDL_GetRGBA.3.gz
/usr/share/man/man3/SDL_GetRelativeMouseState.3.gz
/usr/share/man/man3/SDL_GetThreadID.3.gz
/usr/share/man/man3/SDL_GetTicks.3.gz
/usr/share/man/man3/SDL_GetVideoInfo.3.gz
/usr/share/man/man3/SDL_GetVideoSurface.3.gz
/usr/share/man/man3/SDL_Init.3.gz
/usr/share/man/man3/SDL_InitSubSystem.3.gz
/usr/share/man/man3/SDL_JoyAxisEvent.3.gz
/usr/share/man/man3/SDL_JoyBallEvent.3.gz
/usr/share/man/man3/SDL_JoyButtonEvent.3.gz
/usr/share/man/man3/SDL_JoyHatEvent.3.gz
/usr/share/man/man3/SDL_JoystickClose.3.gz
/usr/share/man/man3/SDL_JoystickEventState.3.gz
/usr/share/man/man3/SDL_JoystickGetAxis.3.gz
/usr/share/man/man3/SDL_JoystickGetBall.3.gz
/usr/share/man/man3/SDL_JoystickGetButton.3.gz
/usr/share/man/man3/SDL_JoystickGetHat.3.gz
/usr/share/man/man3/SDL_JoystickIndex.3.gz
/usr/share/man/man3/SDL_JoystickName.3.gz
/usr/share/man/man3/SDL_JoystickNumAxes.3.gz
/usr/share/man/man3/SDL_JoystickNumBalls.3.gz
/usr/share/man/man3/SDL_JoystickNumButtons.3.gz
/usr/share/man/man3/SDL_JoystickNumHats.3.gz
/usr/share/man/man3/SDL_JoystickOpen.3.gz
/usr/share/man/man3/SDL_JoystickOpened.3.gz
/usr/share/man/man3/SDL_JoystickUpdate.3.gz
/usr/share/man/man3/SDL_KeyboardEvent.3.gz
/usr/share/man/man3/SDL_KillThread.3.gz
/usr/share/man/man3/SDL_ListModes.3.gz
/usr/share/man/man3/SDL_LoadBMP.3.gz
/usr/share/man/man3/SDL_LoadWAV.3.gz
/usr/share/man/man3/SDL_LockAudio.3.gz
/usr/share/man/man3/SDL_LockSurface.3.gz
/usr/share/man/man3/SDL_LockYUVOverlay.3.gz
/usr/share/man/man3/SDL_MapRGB.3.gz
/usr/share/man/man3/SDL_MapRGBA.3.gz
/usr/share/man/man3/SDL_MixAudio.3.gz
/usr/share/man/man3/SDL_MouseButtonEvent.3.gz
/usr/share/man/man3/SDL_MouseMotionEvent.3.gz
/usr/share/man/man3/SDL_NumJoysticks.3.gz
/usr/share/man/man3/SDL_OpenAudio.3.gz
/usr/share/man/man3/SDL_Overlay.3.gz
/usr/share/man/man3/SDL_Palette.3.gz
/usr/share/man/man3/SDL_PauseAudio.3.gz
/usr/share/man/man3/SDL_PeepEvents.3.gz
/usr/share/man/man3/SDL_PixelFormat.3.gz
/usr/share/man/man3/SDL_PollEvent.3.gz
/usr/share/man/man3/SDL_PumpEvents.3.gz
/usr/share/man/man3/SDL_PushEvent.3.gz
/usr/share/man/man3/SDL_Quit.3.gz
/usr/share/man/man3/SDL_QuitEvent.3.gz
/usr/share/man/man3/SDL_QuitSubSystem.3.gz
/usr/share/man/man3/SDL_RWFromFile.3.gz
/usr/share/man/man3/SDL_Rect.3.gz
/usr/share/man/man3/SDL_RemoveTimer.3.gz
/usr/share/man/man3/SDL_ResizeEvent.3.gz
/usr/share/man/man3/SDL_SaveBMP.3.gz
/usr/share/man/man3/SDL_SemPost.3.gz
/usr/share/man/man3/SDL_SemTryWait.3.gz
/usr/share/man/man3/SDL_SemValue.3.gz
/usr/share/man/man3/SDL_SemWait.3.gz
/usr/share/man/man3/SDL_SemWaitTimeout.3.gz
/usr/share/man/man3/SDL_SetAlpha.3.gz
/usr/share/man/man3/SDL_SetClipRect.3.gz
/usr/share/man/man3/SDL_SetColorKey.3.gz
/usr/share/man/man3/SDL_SetColors.3.gz
/usr/share/man/man3/SDL_SetCursor.3.gz
/usr/share/man/man3/SDL_SetEventFilter.3.gz
/usr/share/man/man3/SDL_SetGamma.3.gz
/usr/share/man/man3/SDL_SetGammaRamp.3.gz
/usr/share/man/man3/SDL_SetModState.3.gz
/usr/share/man/man3/SDL_SetPalette.3.gz
/usr/share/man/man3/SDL_SetTimer.3.gz
/usr/share/man/man3/SDL_SetVideoMode.3.gz
/usr/share/man/man3/SDL_ShowCursor.3.gz
/usr/share/man/man3/SDL_Surface.3.gz
/usr/share/man/man3/SDL_SysWMEvent.3.gz
/usr/share/man/man3/SDL_ThreadID.3.gz
/usr/share/man/man3/SDL_UnlockAudio.3.gz
/usr/share/man/man3/SDL_UnlockSurface.3.gz
/usr/share/man/man3/SDL_UnlockYUVOverlay.3.gz
/usr/share/man/man3/SDL_UpdateRect.3.gz
/usr/share/man/man3/SDL_UpdateRects.3.gz
/usr/share/man/man3/SDL_UserEvent.3.gz
/usr/share/man/man3/SDL_VideoDriverName.3.gz
/usr/share/man/man3/SDL_VideoInfo.3.gz
/usr/share/man/man3/SDL_VideoModeOK.3.gz
/usr/share/man/man3/SDL_WM_GetCaption.3.gz
/usr/share/man/man3/SDL_WM_GrabInput.3.gz
/usr/share/man/man3/SDL_WM_IconifyWindow.3.gz
/usr/share/man/man3/SDL_WM_SetCaption.3.gz
/usr/share/man/man3/SDL_WM_SetIcon.3.gz
/usr/share/man/man3/SDL_WM_ToggleFullScreen.3.gz
/usr/share/man/man3/SDL_WaitEvent.3.gz
/usr/share/man/man3/SDL_WaitThread.3.gz
/usr/share/man/man3/SDL_WarpMouse.3.gz
/usr/share/man/man3/SDL_WasInit.3.gz
/usr/share/man/man3/SDL_keysym.3.gz
/usr/share/man/man3/SDL_mutexP.3.gz
/usr/share/man/man3/SDL_mutexV.3.gz

```

/usr/lib/libSDL.so


changed this: 
LIBSDL="/usr/lib/libSDL.so"

run et-sdl-sound

---

### Post by ztealmax on 2012-01-24
dont work for me im affraid :(

---

### Post by nothingspecial on 2012-01-24
Old thread.

Closed.

---

