---
title: "Google Earth does not run."
date: 2010-04-25
forum: General Help
---

### Post by egruber on 2010-04-25
I just installed the latest Google Earth from Medibuntu on my IBM Thinkpad T40.  When it starts up, the globe appears, starts to get bigger, then it just crashes and the screen disappears.  I also ran it from the terminal and got this.  Any suggestions?  Is my laptop just too old to run it?

Thanks!


*********************************WARN_ONCE*********************************
File radeon_tcl.c function radeon_run_tcl_render line 499
Rendering was 103 commands larger than predicted size. We might overflow  command buffer.
***************************************************************************
*** glibc detected *** /usr/lib/googleearth/googleearth-bin: realloc(): invalid next size: 0xad61db80 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x4ffff1]
/lib/tls/i686/cmov/libc.so.6[0x5054d0]
/lib/tls/i686/cmov/libc.so.6(realloc+0xdd)[0x50585d]
/usr/lib/dri/radeon_dri.so[0x3cd8cd4]
/usr/lib/dri/radeon_dri.so(rcommonBeginBatch+0x5d)[0x3cd836d]
/usr/lib/dri/radeon_dri.so(radeonEmitState+0x6db)[0x3cd828b]
/usr/lib/dri/radeon_dri.so(radeonAllocEltsOpenEnded+0x38)[0x3cb2c08]
/usr/lib/dri/radeon_dri.so[0x3cc2686]
/usr/lib/dri/radeon_dri.so[0x3cc304b]
/usr/lib/dri/radeon_dri.so(radeonEmitEltPrimitive+0x39)[0x3cc1c99]
/usr/lib/dri/radeon_dri.so[0x3cc2065]
/usr/lib/dri/radeon_dri.so(_tnl_run_pipeline+0x163)[0x3d7d863]
/usr/lib/dri/radeon_dri.so[0x3cb8d12]
/usr/lib/dri/radeon_dri.so(_tnl_draw_prims+0xc54)[0x3d7e594]
/usr/lib/dri/radeon_dri.so(_tnl_vbo_draw_prims+0x79)[0x3d7e879]
/usr/lib/dri/radeon_dri.so[0x3e4511f]
/usr/lib/dri/radeon_dri.so(vbo_split_copy+0x4e3)[0x3e458c3]
/usr/lib/dri/radeon_dri.so(vbo_split_prims+0xbf)[0x3e4502f]
/usr/lib/dri/radeon_dri.so(_tnl_draw_prims+0x2c1)[0x3d7dc01]
/usr/lib/dri/radeon_dri.so(_tnl_vbo_draw_prims+0x79)[0x3d7e879]
/usr/lib/dri/radeon_dri.so(vbo_rebase_prims+0x16f)[0x3e44baf]
/usr/lib/dri/radeon_dri.so(_tnl_draw_prims+0x6d1)[0x3d7e011]
/usr/lib/dri/radeon_dri.so(_tnl_vbo_draw_prims+0x79)[0x3d7e879]
/usr/lib/dri/radeon_dri.so[0x3d75f30]
/usr/lib/dri/radeon_dri.so[0x3d75fee]
/usr/lib/dri/radeon_dri.so[0x3d6928e]
/usr/lib/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext11genericDrawEiiiii+0x2ad)[0x47fc18d]
/usr/lib/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext12internalDrawENS0_11IG_GFX_DRAWEiiii+0xc8)[0x4815db8]
/usr/lib/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext11drawIndexedENS0_11IG_GFX_DRAWEiiii+0x30)[0x4815df0]
/usr/lib/googleearth/libevll.so(_ZN5earth4evll20DrawableDataRenderer12DrawGeomListERSt6vectorIPNS0_12DrawableDataENS_7MMAllocIS4_EEERKNS_4Vec3IdEEPN3Gap3Gfx15igVisualContextENS1_10OffsetModeEPKNS_11BoundingBoxIdEE+0x84d)[0xb55d2b4d]
/usr/lib/googleearth/libevll.so(_ZN5earth4evll20DrawableDataRenderer13DrawGeomListsEPN3Gap3Gfx15igVisualContextEbi+0xce)[0xb55d2d6e]
/usr/lib/googleearth/libevll.so(_ZN5earth4evll20DrawableDataRenderer16DrawDrawableListEPN3Gap3Gfx15igVisualContextENS1_12SurfaceStageE+0x231)[0xb55d3001]
/usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContext6RenderEb+0x97f)[0xb55a078f]
/usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContext4DrawEbb+0x454)[0xb55a17d4]
/usr/lib/googleearth/libevll.so(_ZN5earth4evll17RenderContextImpl4drawEv+0x7e)[0xb54a49ce]
/usr/lib/googleearth/librender.so(_ZN12RenderWidget10paintEventEP11QPaintEvent+0x2a)[0x5e4542a]
/usr/lib/googleearth/librender.so(_ZN5earth6render11RenderTimer4FireEv+0x1d)[0x5e2f47d]
/usr/lib/googleearth/libbase.so(_ZN5earth5Timer8dispatchEv+0x33)[0x18d483]
/usr/lib/googleearth/libbase.so(_ZN5earth11QtFramework18CommandCustomEvent8dispatchEv+0x23)[0x1bf653]
/usr/lib/googleearth/libbase.so(_ZN5earth11QtFramework11customEventEP6QEvent+0x39)[0x1bcff9]
/usr/lib/libQtCore.so.4(_ZN7QObject5eventEP6QEvent+0x31f)[0xe2165f]
/usr/lib/libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xb4)[0x1025f54]
/usr/lib/libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x18c)[0x102d67c]
/usr/lib/libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x7b)[0xe116cb]
/usr/lib/libQtCore.so.4(_ZN23QCoreApplicationPrivate16sendPostedEventsEP7QObjectiP11QThreadData+0x2d2)[0xe122b2]
/usr/lib/libQtCore.so.4(_ZN16QCoreApplication16sendPostedEventsEP7QObjecti+0x2d)[0xe1247d]
/usr/lib/libQtCore.so.4[0xe3c3ff]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f8)[0x39fe88]
/lib/libglib-2.0.so.0[0x3a3730]
/lib/libglib-2.0.so.0(g_main_context_iteration+0x73)[0x3a3863]
/usr/lib/libQtCore.so.4(_ZN20QEventDispatcherGlib13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x5c)[0xe3c02c]
/usr/lib/libQtGui.so.4[0x10c6be5]
/usr/lib/libQtCore.so.4(_ZN10QEventLoop13processEventsE6QFlagsINS_17ProcessEventsFlagEE+0x49)[0xe0fc79]
/usr/lib/libQtCore.so.4(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0xfa)[0xe100ca]
/usr/lib/libQtCore.so.4(_ZN16QCoreApplication4execEv+0xaf)[0xe1253f]
/usr/lib/libQtGui.so.4(_ZN12QApplication4execEv+0x27)[0x1025dd7]
/usr/lib/googleearth/libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x436)[0x319e86]
/usr/lib/googleearth/googleearth-bin[0x805c77a]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x4abb56]
/usr/lib/googleearth/googleearth-bin[0x805be71]
======= Memory map: ========
00110000-00134000 r-xp 00000000 08:01 877        /lib/tls/i686/cmov/libm-2.10.1.so
00134000-00135000 r--p 00023000 08:01 877        /lib/tls/i686/cmov/libm-2.10.1.so
00135000-00136000 rw-p 00024000 08:01 877        /lib/tls/i686/cmov/libm-2.10.1.so
00136000-001e7000 r-xp 00000000 08:01 527607     /usr/lib/googleearth/libbase.so
001e7000-001ec000 rw-p 000b1000 08:01 527607     /usr/lib/googleearth/libbase.so
001ec000-001ed000 rw-p 00000000 00:00 0 
001ed000-001f1000 r-xp 00000000 08:01 6276       /usr/lib/libgthread-2.0.so.0.2200.3
001f1000-001f2000 r--p 00003000 08:01 6276       /usr/lib/libgthread-2.0.so.0.2200.3
001f2000-001f3000 rw-p 00004000 08:01 6276       /usr/lib/libgthread-2.0.so.0.2200.3
001f3000-001fa000 r-xp 00000000 08:01 938        /lib/tls/i686/cmov/librt-2.10.1.so
001fa000-001fb000 r--p 00006000 08:01 938        /lib/tls/i686/cmov/librt-2.10.1.so
001fb000-001fc000 rw-p 00007000 08:01 938        /lib/tls/i686/cmov/librt-2.10.1.so
001fe000-00219000 r-xp 00000000 08:01 2033       /lib/ld-2.10.1.so
00219000-0021a000 r--p 0001a000 08:01 2033       /lib/ld-2.10.1.so
0021a000-0021b000 rw-p 0001b000 08:01 2033       /lib/ld-2.10.1.so
0021b000-0035e000 r-xp 00000000 08:01 527621     /usr/lib/googleearth/libgoogleearth_lib.so
0035e000-00366000 rw-p 00143000 08:01 527621     /usr/lib/googleearth/libgoogleearth_lib.so
00366000-00367000 rw-p 00000000 00:00 0 
00367000-0041c000 r-xp 00000000 08:01 3633       /lib/libglib-2.0.so.0.2200.3
0041c000-0041d000 r--p 000b4000 08:01 3633       /lib/libglib-2.0.so.0.2200.3
0041d000-0041e000 rw-p 000b5000 08:01 3633       /lib/libglib-2.0.so.0.2200.3
0041e000-00433000 r-xp 00000000 08:01 925        /lib/tls/i686/cmov/libpthread-2.10.1.so
00433000-00434000 r--p 00014000 08:01 925        /lib/tls/i686/cmov/libpthread-2.10.1.so
00434000-00435000 rw-p 00015000 08:01 925        /lib/tls/i686/cmov/libpthread-2.10.1.so
00435000-00437000 rw-p 00000000 00:00 0 
00437000-00439000 r-xp 00000000 08:01 875        /lib/tls/i686/cmov/libdl-2.10.1.so
00439000-0043a000 r--p 00001000 08:01 875        /lib/tls/i686/cmov/libdl-2.10.1.so
0043a000-0043b000 rw-p 00002000 08:01 875        /lib/tls/i686/cmov/libdl-2.10.1.so
0043b000-00453000 r-xp 00000000 08:01 1380       /usr/lib/libaudio.so.2.4
00453000-00454000 r--p 00017000 08:01 1380       /usr/lib/libaudio.so.2.4
00454000-00455000 rw-p 00018000 08:01 1380       /usr/lib/libaudio.so.2.4
00455000-00478000 r-xp 00000000 08:01 3629       /usr/lib/libpng12.so.0.37.0
00478000-00479000 r--p 00022000 08:01 3629       /usr/lib/libpng12.so.0.37.0
00479000-0047a000 rw-p 00023000 08:01 3629       /usr/lib/libpng12.so.0.37.0
0047a000-00491000 r-xp 00000000 08:01 4318       /usr/lib/libICE.so.6.3.0
00491000-00492000 r--p 00016000 08:01 4318       /usr/lib/libICE.so.6.3.0
00492000-00493000 rw-p 00017000 08:01 4318       /usr/lib/libICE.so.6.3.0
00493000-00495000 rw-p 00000000 00:00 0 
00495000-005d3000 r-xp 00000000 08:01 837        /lib/tls/i686/cmov/libc-2.10.1.so
005d3000-005d4000 ---p 0013e000 08:01 837        /lib/tls/i686/cmov/libc-2.10.1.so
005d4000-005d6000 r--p 0013e000 08:01 837        /lib/tls/i686/cmov/libc-2.10.1.so
005d6000-005d7000 rw-p 00140000 08:01 837        /lib/tls/i686/cmov/libc-2.10.1.so
005d7000-005da000 rw-p 00000000 00:00 0 
005da000-005dc000 r-xp 00000000 08:01 527613     /usr/lib/googleearth/libapiloader.so
005dc000-005dd000 rw-p 00002000 08:01 527613     /usr/lib/googleearth/libapiloader.so
005dd000-005f1000 r-xp 00000000 08:01 961        /lib/libz.so.1.2.3.3
005f1000-005f2000 r--p 00013000 08:01 961        /lib/libz.so.1.2.3.3
005f2000-005f3000 rw-p 00014000 08:01 961        /lib/libz.so.1.2.3.3
005f3000-0066d000 r-xp 00000000 08:01 4661       /usr/lib/libfreetype.so.6.3.20
0066d000-00671000 r--p 00079000 08:01 4661       /usr/lib/libfreetype.so.6.3.20
00671000-00672000 rw-p 0007d000 08:01 4661       /usr/lib/libfreetype.so.6.3.20
00672000-006ae000 r-xp 00000000 08:01 3636       /usr/lib/libgobject-2.0.so.0.2200.3
006ae000-006af000 r--p 0003b000 08:01 3636       /usr/lib/libgobject-2.0.so.0.2200.3
006af000-006b0000 rw-p 0003c000 08:01 3636       /usr/lib/libgobject-2.0.so.0.2200.3
006b0000-006db000 r-xp 00000000 08:01 4653       /usr/lib/libfontconfig.so.1.3.0
006db000-006dc000 r--p 0002a000 08:01 4653       /usr/lib/libfontconfig.so.1.3.0
006dc000-006dd000 rw-p 0002b000 08:01 4653       /usr/lib/libfontconfig.so.1.3.0
006dd000-006eb000 r-xp 00000000 08:01 4368       /usr/lib/libXext.so.6.4.0
006eb000-006ec000 r--p 0000d000 08:01 4368       /usr/lib/libXext.so.6.4.0
006ec000-006ed000 rw-p 0000e000 08:01 4368       /usr/lib/libXext.so.6.4.0
006ed000-00773000 r-xp 00000000 08:01 5283       /usr/lib/libsqlite3.so.0.8.6
00773000-00774000 r--p 00086000 08:01 5283       /usr/lib/libsqlite3.so.0.8.6
00774000-00775000 rw-p 00087000 08:01 5283       /usr/lib/libsqlite3.so.0.8.6
00775000-00798000 r-xp 00000000 08:01 527587     /usr/lib/googleearth/libIGUtils.so
00798000-0079b000 rw-p 00023000 08:01 527587     /usr/lib/googleearth/libIGUtils.so
0079b000-007a0000 r-xp 00000000 08:01 527622     /usr/lib/googleearth/libcomponentframework.so
007a0000-007a1000 rw-p 00005000 08:01 527622     /usr/lib/googleearth/libcomponentframework.so
007a1000-007ab000 r-xp 00000000 08:01 527604     /usr/lib/googleearth/libmoduleframework.so
007ab000-007ac000 rw-p 00009000 08:01 527604     /usr/lib/googleearth/libmoduleframework.so
007ac000-007b5000 r-xp 00000000 08:01 527596     /usr/lib/googleearth/libport.so
007b5000-007b6000 rw-p 00008000 08:01 527596     /usr/lib/googleearth/libport.so
007b7000-007be000 r-xp 00000000 08:01 4347       /usr/lib/libSM.so.6.0.0
007be000-007bf000 r--p 00006000 08:01 4347       /usr/lib/libSM.so.6.0.0
007bf000-007c0000 rw-p 00007000 08:01 4347       /usr/lib/libSM.so.6.0.0
007c0000-007c6000 r-xp 00000000 08:01 527602     /usr/lib/googleearth/libminizip.so
007c6000-007c7000 rw-p 00005000 08:01 527602     /usr/lib/googleearth/libminizip.so
007c7000-007c9000 r-xp 00000000 08:01 4355       /usr/lib/libXau.so.6.0.0
007c9000-007ca000 r--p 00001000 08:01 4355       /usr/lib/libXau.so.6.0.0
007ca000-007cb000 rw-p 00002000 08:01 4355       /usr/lib/libXau.so.6.0.0
007cb000-007ce000 r-xp 00000000 08:01 954        /lib/libuuid.so.1.3.0
007ce000-007cf000 r--p 00002000 08:01 954        /lib/libuuid.so.1.3.0
007cf000-007d0000 rw-p 00003000 08:01 954        /lib/libuuid.so.1.3.0
007d0000-007d3000 r-xp 00000000 08:01 527585     /usr/lib/googleearth/libfusioncommon.so
007d3000-007d4000 rw-p 00002000 08:01 527585     /usr/lib/googleearth/libfusioncommon.soGoogle Earth has caught signal 6.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

---

### Post by Serpher on 2010-04-25
Try

```
$sudo apt-get install glibc
```

---

### Post by egruber on 2010-04-25
> **Serpher said:**
> Try

```
$sudo apt-get install glibc
```

I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glibc

Am I missing something?

---

### Post by Colo2 on 2010-04-25
try enabling all of the software sources.

---

### Post by egruber on 2010-04-25
I thought they were.  What do I check?

---

### Post by dcstar on 2010-04-26
Make your own package:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by egruber on 2010-04-27
Perhaps trying 4.2 would be a good idea.  Anyone know where I can find the linux download?  I haven't had any luck searching for it.  I can only find the Windows version.

---

