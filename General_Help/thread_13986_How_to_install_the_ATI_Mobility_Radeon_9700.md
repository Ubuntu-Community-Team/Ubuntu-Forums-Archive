---
title: "How to install the ATI Mobility Radeon 9700 ?"
date: 2005-02-04
forum: General Help
---

### Post by ulefr01 on 2005-02-04
How to install the ATI Mobility Radeon 9700 driver ?

---

### Post by mirtux on 2005-02-08
You can have a look at this thread: [http://www.ubuntuforums.org/showthread.php?t=13226](http://www.ubuntuforums.org/showthread.php?t=13226). Here you'll find all the necessary information on how to do this. Please note that, on the ATI site, if you are searching for drivers for you mobility, you'll have to take the driver for the normal version!!
 
 Regards,
 MC

---

### Post by ulefr01 on 2005-02-09
I have tried it with the fglrx driver and module fglrx is not used (0 counter for fglrx in lsmod | grep fglrx) and   
fglrxinfo gives me the still the OpenGL : Mesa project Mesa GLX indirect [www.mesa3d.org](www.mesa3d.org)

I think that you can use the fglrx driver for the ATI Radeon 9700 but not for the ATI Mobility Radeon 9700.

I have more success with the ati driver

root@franz3:/etc/X11 # glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  1 24  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  1 24  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  1 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  1 24  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  1 24  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
root@franz3:/etc/X11 # glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
842 frames in 5.0 seconds = 168.400 FPS
780 frames in 5.0 seconds = 156.000 FPS
780 frames in 5.0 seconds = 156.000 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by mirtux on 2005-02-09
Well, i'm using warty and i've got running the fglrx driver (old version, downloaded from repositories) with my *mobilit**y *radeon 9700. I would like to try with the new drivers from ATI since i've got some problem with glittering. However this is my  [b]fglrxinfo:
  [/b] ```

  display: :0.0  screen: 0
  OpenGL vendor string: ATI Technologies Inc.
  OpenGL renderer string: MOBILITY RADEON 9700 Generic
  OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)
  
``` 
  Regards,
  MC

---

### Post by ulefr01 on 2005-02-09
which version of fglrx are you using ?
with the following command i get :
modinfo fglrx
filename:       /lib/modules/2.6.9/kernel/drivers/video/fglrx.ko
author:         Fire GL - ATI Research GmbH, Germany
description:    ATI Fire GL
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
vermagic:       2.6.9 preempt 686 gcc-3.3
depends:

---

### Post by mirtux on 2005-02-09
This is mine:
  
    ```

  filename:	   /lib/modules/2.6.8.1-4-686/kernel/drivers/video/fglrx.ko
  author:		 Fire GL - ATI Research GmbH, Germany
  description:	ATI Fire GL
  license:		Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
  vermagic:	   2.6.8.1-4-686 preempt 686 gcc-3.3
  depends:
  
``` 
 Are you using Warty or Hoary? Maybe you've built your own vanilla kernel? However this evening or tomorrow i'll try with ati drivers 8.8.25.
  
  Regards,
  MC

---

### Post by ulefr01 on 2005-02-09
./make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
skipping patch for 'drmP.h', not needed
skipping patch for 'drm_os_linux.h', not needed
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /usr/src/kernel-source-2.6.9 SUBDIRS=/lib/modules/fglrx-4.3.0-3.14.6 modules
make[1]: Entering directory `/usr/src/kernel-source-2.6.9'
  CC [M]  /lib/modules/fglrx-4.3.0-3.14.6/agp3.o
  CC [M]  /lib/modules/fglrx-4.3.0-3.14.6/nvidia-agp.o
  CC [M]  /lib/modules/fglrx-4.3.0-3.14.6/agpgart_be.o
  CC [M]  /lib/modules/fglrx-4.3.0-3.14.6/i7505-agp.o
  CC [M]  /lib/modules/fglrx-4.3.0-3.14.6/firegl_public.o
  LD [M]  /lib/modules/fglrx-4.3.0-3.14.6/fglrx.o
  Building modules, stage 2.
  MODPOST
  CC      /lib/modules/fglrx-4.3.0-3.14.6/fglrx.mod.o
  LD [M]  /lib/modules/fglrx-4.3.0-3.14.6/fglrx.ko
make[1]: Leaving directory `/usr/src/kernel-source-2.6.9'
build succeeded with return value 0
done.
==============================
You must copy fglrx.ko to /lib/modules/2.6.9/misc
and then call 'depmod -ae' in order to install the built module.

afterwards i did the copy and the 'depmod -ae'

As you can , I am using the linux kernel 2.6.9 !

The fglrx 3.14.6 is not for the kernel 2.6.9; 
i get :
fglrx : kernel module version does not match driver

Is there a version of fglrx available for the 2.6.9 kernel ?

---

### Post by mirtux on 2005-02-11
Hi,
 i would suggest you moving to ATI drivers 8.8.25. I've installed it quite smoothly, better than the old version. Have a look here [http://www.ubuntuforums.org/showthread.php?t=13226](http://www.ubuntuforums.org/showthread.php?t=13226)
  Regards,
  MC

---

### Post by ulefr01 on 2005-02-12
ATI drivers 8.8.25 on [http://www2.ati.com/drivers/linux/linux_8.8.25.html](http://www2.ati.com/drivers/linux/linux_8.8.25.html) :
mention only the support for :
ATI MOBILITY™ Product Support

The ATI Proprietary Linux driver is designed to support the following ATI MOBILITY™ products:
MOBILITY™ RADEON™ X700
	MOBILITY™ RADEON™ 9800
MOBILITY™ RADEON™ 9600
	MOBILITY™ RADEON™ 9200
MOBILITY™ RADEON™ 9000
	
I don't see the Mobility Radeon 9700

---

### Post by Kareema on 2005-02-12
[QUOTE=ulefr01]I don't see the Mobility Radeon 9700[/QUOTE]

That's true, but the drivers work for Mobility Radeon 9700 nevertheless. It's a good idea to use the search function of this forum! For your convenience here's another link to a thread related to ATI Mobility Radeon 9700 (but under AMD64 and Hoary): [http://www.ubuntuforums.org/showthread.php?t=8993](http://www.ubuntuforums.org/showthread.php?t=8993).

---

### Post by ulefr01 on 2005-02-12
[QUOTE=Kareema]That's true, but the drivers work for Mobility Radeon 9700 nevertheless. It's a good idea to use the search function of this forum! For your convenience here's another link to a thread related to ATI Mobility Radeon 9700 (but under AMD64 and Hoary): [http://www.ubuntuforums.org/showthread.php?t=8993](http://www.ubuntuforums.org/showthread.php?t=8993).[/QUOTE]

I have installed the Radeon 9700 driver from the ATI site 
fglrx_4.3.0-8.8.25-1.i386.rpm for XFree86 4.3
Now i get :

Feb 12 17:49:47 localhost kernel: fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb 12 17:49:47 localhost kernel: [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
Feb 12 17:49:47 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 217
Feb 12 17:49:47 localhost kernel: [fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
Feb 12 17:49:47 localhost kernel: [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
Feb 12 17:49:47 localhost kernel: [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
Feb 12 17:49:47 localhost kernel: agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Feb 12 17:49:47 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Feb 12 17:49:47 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Feb 12 17:49:47 localhost kernel: [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
Feb 12 17:49:47 localhost kernel: [fglrx] free  AGP = 256126976
Feb 12 17:49:47 localhost kernel: [fglrx] max   AGP = 256126976
Feb 12 17:49:47 localhost kernel: [fglrx] free  LFB = 119828480
Feb 12 17:49:47 localhost kernel: [fglrx] max   LFB = 119828480
Feb 12 17:49:47 localhost kernel: [fglrx] free  Inv = 0
Feb 12 17:49:47 localhost kernel: [fglrx] max   Inv = 0
Feb 12 17:49:47 localhost kernel: [fglrx] total Inv = 0
Feb 12 17:49:47 localhost kernel: [fglrx] total TIM = 0
Feb 12 17:49:47 localhost kernel: [fglrx] total FB  = 0
Feb 12 17:49:47 localhost kernel: [fglrx] total AGP = 65536


glxgears
6323 frames in 5.0 seconds = 1264.600 FPS
7282 frames in 5.0 seconds = 1456.400 FPS
7281 frames in 5.0 seconds = 1456.200 FPS
7282 frames in 5.0 seconds = 1456.400 FPS
7272 frames in 5.0 seconds = 1454.400 FPS

Thank you very much

---

### Post by mirtux on 2005-02-12
Do you get these frames per second with the window of fgl_gears opened or not?
 
 Thanks,
 MC

---

### Post by ulefr01 on 2005-02-12
In a terminal i start the command 'glxgears'
and i see a window with three gear-wheels
after a while is stop and i see in the terminal session the numbers of frames = +- 1450 FramesPerSec

---

### Post by mirtux on 2005-02-13
That's ok..... i was thinking to fgl_glxgears.... for glxgears i also get some 1400 fps.
 
 Sorry, and thanks,
 MC

---

### Post by ulefr01 on 2005-02-13
i tried fgl_glxgears.
I get :
 fgl_glxgears
1248 frames in 5.0 seconds = 249.600 FPS
1455 frames in 5.0 seconds = 291.000 FPS
1452 frames in 5.0 seconds = 290.400 FPS
1444 frames in 5.0 seconds = 288.800 FPS
1439 frames in 5.0 seconds = 287.800 FPS
2013 frames in 5.0 seconds = 402.600 FPS
2036 frames in 5.0 seconds = 407.200 FPS
2038 frames in 5.0 seconds = 407.600 FPS
2035 frames in 5.0 seconds = 407.000 FPS
2035 frames in 5.0 seconds = 407.000 FPS

---

### Post by mirtux on 2005-02-13
Ok, thanks, that's compatible with my results!
  
  Just another question: have you tried working with Celestia? In case of yes, do you have some sort of glittering effect?
  
  Regards,
  MC

---

