---
title: "ubuntu crashing! shuts down totally drops power off, dead."
date: 2009-06-26
forum: General Help
---

### Post by hoboboot on 2009-06-26
So... i am now running just ubuntu 8.10 intrepid ibex on my laptop, i de-windows'ed it finally, and i really like ubuntu, but...

it seems to crash... probably due to javascript or flash, im not sure, i have adobe flash 10 i believe, i just installed it 2 weeks ago...
and it seems like well, its got to be triggered by web pages i'm figureing, i can go days without it happening, but, if i wanted it to do it right now, i could probably load 4 web pages, and start multi-task surfing intensively, and it would eventually crash, im not any more percisely sure about what exactly is triggering it, and couldnt say wether it be a java or flash thing, but, i mean... it would be convienient if firefox just crashed, instead of, my laptop spontaneously dropping power completely...


i'd love it if i could multi-task and (by the way, sometimes it does it without multi-tasking, on occasion i've seen it drop the power and die just from opening one page...) i really want my ubuntu to be reliable, and stable... 

what should i do...

p.s. also, i'm thinking about updating it to jaunty via the update manager... i've got my sound, everything hooked up and working though now... and i dont want everything to be all screwed again... im wondering if anyone has any information for me about updating to jaunty? does it keep everything i've got now good and working? i'd kind of like to try it, to see wether it is more stable yanno... but... this is something of a risk for more issues i keep thinking...

thanks for any help.

---

### Post by t4thfavor on 2009-06-26
type of machine?

Does it seem abnormally hot when this happens, I had a laptop that didn't detect the fans properly, and would overheat, and then power off.

Check to see that the fans are running, and maybe install some temperature monitoring stuff. There are plenty of sensors on most modern laptops/desktops that will tell you how hot something is.

I eventually updated to a version where the sensors were detected, and my overheating stopped.

---

### Post by robobart on 2009-06-26
This sounds like a hardware problem. 

From your description - the computer just turns off right?

As far as updating goes, go ahead and burn a 9.04 cd - and then try the live install. It might just work. 

Each time the installation process gets smoother.

---

### Post by hoboboot on 2009-06-27
well guys... the fans are working just fine... 
and im running a gateway mx3210 (not exactly the most linux-fine computer out there i know...) no nvidia  : (

but... the cpu is rated to run hotter than all the other cpus in my friends laptops from the same generation... (2005/2006 i believe)... and im pretty sure that, if its going to overheat, it'd beep as it kills out.


so, im not sure, i'm going to try and make it crash again right now and see...

going to open multiple pages with flash and javascript and see if it will die again, it hasnt for about a week, but... i had pidgin and something open on one desk, and my buddy had webmessenger.msn.com(java, web) open on a 2nd desk, and facebook(flash/java), etc was all running...along with gmail...

im pretty sure seperately, they all function alright, but, that day, it did it twice, and then when i booted back in after a 3rd time, again it happened so... that was at... i think gmail or facebook mid surfing... 

a real : (

---

### Post by hoboboot on 2009-06-27
anyway guys, i was wondering...

it could have to do with my videocard... its not fully functional i've read, because, the drivers via released for unichrome pro igp finally, i guess dont work with any versions of ubuntu since 6 or 5 im not sure which one, but i found that running live cd's of 7.10 and 8.04 in 8.10 though it detects and i am able to view things rendered with gl, however... im thinking that, the video card is somehow screwing up with live video streams...

i was able to get it to crash about 5 times already, youtube can do it pretty damn fast... heres some copy and pastes from my terminal, lspci & glxinfo

hobo@metaverse:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0c.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
00:0c.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
00:0c.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
00:0e.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)


hobo@metaverse:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

2 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x3b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

24 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x3c  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x3d  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x3e  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x3f  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x40  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x41  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x42  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x43  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x44  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x45  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x46  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x47  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x48  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x49  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x4a  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x4b  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x4c  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x4d  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x4e  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x4f  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x50  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x52  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x53  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

hobo@metaverse:~$ glxgears
3664 frames in 5.0 seconds = 732.709 FPS
3716 frames in 5.0 seconds = 743.166 FPS
4121 frames in 5.0 seconds = 824.013 FPS
3693 frames in 5.0 seconds = 738.462 FPS
3783 frames in 5.0 seconds = 756.532 FPS
4055 frames in 5.0 seconds = 810.907 FPS
3694 frames in 5.0 seconds = 738.765 FPS
4073 frames in 5.0 seconds = 814.511 FPS
3711 frames in 5.0 seconds = 742.127 FPS

---

### Post by hoboboot on 2009-06-28
actually. it seems like, there just was 8.10 drivers released for this chipset finally. i've been running whatever 8.10 does initially, which, well, if this is the actual factory driver then great, i've downloaded that, dont know how long it'll take me to make it work right, haha. but i've got it, awesome. it even has compiz instructions inside the readme file from VIA! for the beasty crappy s3 unichrome pro igp chip. stoked to get this driver working. finally via updates it! if only they were prepared to move forward with a 9.04 driver right now, ahhh wellz.

---

