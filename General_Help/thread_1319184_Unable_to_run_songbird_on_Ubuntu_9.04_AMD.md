---
title: "Unable to run songbird on Ubuntu 9.04 AMD"
date: 2009-11-08
forum: General Help
---

### Post by Sapfeer on 2009-11-08
I've downloaded songbird compressed archive from the [_site_]("http://www.getsongbird.com/"), but when I try to run it, it shows a lot of error messages...

```
/usr/local/songbird $ ./songbird
*** glibc detected *** ././songbird-bin: munmap_chunk(): invalid pointer: 0x00007fd4eb8a0e80 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fd511665cb8]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0xe)[0x7fd4e6a754ce]
/usr/lib/libvisual-0.4.so.0[0x7fd4e6a6e646]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x48)[0x7fd4e6a6e7d8]
/usr/lib/libvisual-0.4.so.0(visual_init+0x243)[0x7fd4e6a7b703]
/usr/lib64/gstreamer-0.10/libgstlibvisual.so[0x7fd4e6c9ccb1]
/usr/local/songbird/lib/libgstreamer-0.10.so[0x7fd4fbb9a383]
/usr/local/songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x98c)[0x7fd4fbb9af7d]
/usr/local/songbird/lib/libgstreamer-0.10.so[0x7fd4fbba69fb]
/usr/local/songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x11f)[0x7fd4fbba6b7e]
/usr/local/songbird/lib/libgstreamer-0.10.so[0x7fd4fbb5259b]
/usr/local/songbird/lib/libgstreamer-0.10.so[0x7fd4fbb52a09]
/usr/local/songbird/lib/libgstreamer-0.10.so[0x7fd4fbb52fd7]
/usr/local/songbird/lib/libgstreamer-0.10.so[0x7fd4fbb53568]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x540)[0x7fd50d950020]
/usr/local/songbird/lib/libgstreamer-0.10.so(gst_init_check+0xd6)[0x7fd4fbb51936]
/usr/local/songbird/lib/libgstreamer-0.10.so(gst_init+0x29)[0x7fd4fbb51a23]
/usr/local/songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0xacc)[0x7fd4f97ceb04]
/usr/local/songbird/lib/sbGStreamerMediacore.so[0x7fd4f97d65e5]
/usr/local/songbird/xulrunner/libxul.so[0x7fd50f49659f]
/usr/local/songbird/xulrunner/libxul.so[0x7fd50f4960e9]
/usr/local/songbird/lib/sbGStreamerMediacore.so[0x7fd4f97e492b]
/usr/local/songbird/lib/sbGStreamerMediacore.so[0x7fd4f97e4958]
/usr/local/songbird/lib/sbGStreamerMediacore.so[0x7fd4f97e4140]
/usr/local/songbird/lib/sbGStreamerMediacore.so[0x7fd4f97d502e]
/usr/local/songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x4b)[0x7fd4f97d5601]
/usr/local/songbird/lib/sbGStreamerMediacore.so[0x7fd4f97d6555]
/usr/local/songbird/xulrunner/libxul.so[0x7fd50f49659f]
/usr/local/songbird/components/sbMediacoreManager.so[0x7fd4fed0e613]
/usr/local/songbird/components/sbMediacoreManager.so[0x7fd4fed0e650]
/usr/local/songbird/components/sbMediacoreManager.so[0x7fd4fed0df32]
/usr/local/songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x1c)[0x7fd4fecf9154]
/usr/local/songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1ff)[0x7fd4fecf6729]
/usr/local/songbird/components/sbMediacoreManager.so[0x7fd4fecf6b17]
/usr/local/songbird/xulrunner/libxul.so[0x7fd50f476eba]
/usr/local/songbird/xulrunner/libxul.so[0x7fd50f47738c]
/usr/local/songbird/xulrunner/libxul.so[0x7fd50ed47f86]
/usr/local/songbird/xulrunner/libxul.so(XRE_main+0x177d)[0x7fd50ed45c57]
././songbird-bin[0x401417]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fd51160c5a6]
././songbird-bin[0x401009]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:05 1264711                            /usr/local/songbird/songbird-bin
00608000-00609000 rw-p 00008000 08:05 1264711                            /usr/local/songbird/songbird-bin
0138c000-013ad000 rw-p 0138c000 00:00 0                                  [heap]
7fd4e5007000-7fd4e5008000 r-xp 00000000 08:05 443285                     /usr/lib/tls/libnvidia-tls.so.180.44
7fd4e5008000-7fd4e5108000 ---p 00001000 08:05 443285                     /usr/lib/tls/libnvidia-tls.so.180.44
7fd4e5108000-7fd4e5109000 rw-p 00001000 08:05 443285                     /usr/lib/tls/libnvidia-tls.so.180.44
7fd4e6a5c000-7fd4e6a99000 r-xp 00000000 08:05 371852                     /usr/lib/libvisual-0.4.so.0.0.0
7fd4e6a99000-7fd4e6c98000 ---p 0003d000 08:05 371852                     /usr/lib/libvisual-0.4.so.0.0.0
7fd4e6c98000-7fd4e6c99000 r--p 0003c000 08:05 371852                     /usr/lib/libvisual-0.4.so.0.0.0
7fd4e6c99000-7fd4e6c9a000 rw-p 0003d000 08:05 371852                     /usr/lib/libvisual-0.4.so.0.0.0
7fd4e6c9a000-7fd4e6ca0000 r-xp 00000000 08:05 378199                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fd4e6ca0000-7fd4e6e9f000 ---p 00006000 08:05 378199                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fd4e6e9f000-7fd4e6ea0000 r--p 00005000 08:05 378199                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fd4e6ea0000-7fd4e6ea1000 rw-p 00006000 08:05 378199                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fd4e6ea1000-7fd4e6ede000 r-xp 00000000 08:05 1083467                    /usr/lib/libfaad.so.0.0.0
7fd4e6ede000-7fd4e70dd000 ---p 0003d000 08:05 1083467                    /usr/lib/libfaad.so.0.0.0
7fd4e70dd000-7fd4e70de000 r--p 0003c000 08:05 1083467                    /usr/lib/libfaad.so.0.0.0
7fd4e70de000-7fd4e70e1000 rw-p 0003d000 08:05 1083467                    /usr/lib/libfaad.so.0.0.0
7fd4e70e1000-7fd4e70e9000 r-xp 00000000 08:05 312306                     /usr/lib/gstreamer-0.10/libgstfaad.so
7fd4e70e9000-7fd4e72e8000 ---p 00008000 08:05 312306                     /usr/lib/gstreamer-0.10/libgstfaad.so
7fd4e72e8000-7fd4e72e9000 r--p 00007000 08:05 312306                     /usr/lib/gstreamer-0.10/libgstfaad.so
7fd4e72e9000-7fd4e72ea000 rw-p 00008000 08:05 312306                     /usr/lib/gstreamer-0.10/libgstfaad.so
7fd4e72ea000-7fd4e72ef000 r-xp 00000000 08:05 312354                     /usr/lib/gstreamer-0.10/libgstvmnc.so
7fd4e72ef000-7fd4e74ef000 ---p 00005000 08:05 312354                     /usr/lib/gstreamer-0.10/libgstvmnc.so
7fd4e74ef000-7fd4e74f0000 r--p 00005000 08:05 312354                     /usr/lib/gstreamer-0.10/libgstvmnc.so
7fd4e74f0000-7fd4e74f1000 rw-p 00006000 08:05 312354                     /usr/lib/gstreamer-0.10/libgstvmnc.so
7fd4e74f1000-7fd4e74fb000 r-xp 00000000 08:05 312336                     /usr/lib/gstreamer-0.10/libgstrawparse.so
7fd4e74fb000-7fd4e76fa000 ---p 0000a000 08:05 312336                     /usr/lib/gstreamer-0.10/libgstrawparse.so
7fd4e76fa000-7fd4e76fb000 r--p 00009000 08:05 312336                     /usr/lib/gstreamer-0.10/libgstrawparse.so
7fd4e76fb000-7fd4e76fc000 rw-p 0000a000 08:05 312336                     /usr/lib/gstreamer-0.10/libgstrawparse.so
7fd4e76fc000-7fd4e7708000 r-xp 00000000 08:05 378203                     /usr/lib/gstreamer-0.10/libgstsubparse.so
7fd4e7708000-7fd4e7907000 ---p 0000c000 08:05 378203                     /usr/lib/gstreamer-0.10/libgstsubparse.so
7fd4e7907000-7fd4e7908000 r--p 0000b000 08:05 378203                     /usr/lib/gstreamer-0.10/libgstsubparse.so
7fd4e7908000-7fd4e7909000 rw-p 0000c000 08:05 378203                     /usr/lib/gstreamer-0.10/libgstsubparse.so
7fd4e7909000-7fd4e790e000 r-xp 00000000 08:05 312352                     /usr/lib/gstreamer-0.10/libgstvideosignal.so
7fd4e790e000-7fd4e7b0d000 ---p 00005000 08:05 312352                     /usr/lib/gstreamer-0.10/libgstvideosignal.so
7fd4e7b0d000-7fd4e7b0e000 r--p 00004000 08:05 312352                     /usr/lib/gstreamer-0.10/libgstvideosignal.so
7fd4e7b0e000-7fd4e7b0f000 rw-p 00005000 08:05 312352                     /usr/lib/gstreamer-0.10/libgstvideosignal.so
7fd4e7b0f000-7fd4e7b13000 r-xp 00000000 08:05 312346                     /usr/lib/gstreamer-0.10/libgstspeed.so
7fd4e7b13000-7fd4e7d12000 ---p 00004000 08:05 312346                     /usr/lib/gstreamer-0.10/libgstspeed.so
7fd4e7d12000-7fd4e7d13000 r--p 00003000 08:05 312346                     /usr/lib/gstreamer-0.10/libgstspeed.so
7fd4e7d13000-7fd4e7d14000 rw-p 00004000 08:05 312346                     /usr/lib/gstreamer-0.10/libgstspeed.so
7fd4e7d14000-7fd4e7d30000 r-xp 00000000 08:05 370028                     /usr/lib/libdvdread.so.4.1.3
7fd4e7d30000-7fd4e7f2f000 ---p 0001c000 08:05 370028                     /usr/lib/libdvdread.so.4.1.3
7fd4e7f2f000-7fd4e7f30000 r--p 0001b000 08:05 370028                     /usr/lib/libdvdread.so.4.1.3
7fd4e7f30000-7fd4e7f31000 rw-p 0001c000 08:05 370028                     /usr/lib/libdvdread.so.4.1.3
7fd4e7f31000-7fd4e7f48000 r-xp 00000000 08:05 370135                     /usr/lib/libdvdnav.so.4.1.3
7fd4e7f48000-7fd4e8147000 ---p 00017000 08:05 370135                     /usr/lib/libdvdnav.so.4.1.3
7fd4e8147000-7fd4e8148000 r--p 00016000 08:05 370135                     /usr/lib/libdvdnav.so.4.1.3
7fd4e8148000-7fd4e8149000 rw-p 00017000 08:05 370135                     /usr/lib/libdvdnav.so.4.1.3
7fd4e8149000-7fd4e8171000 r-xp 00000000 08:05 312358                     /usr/lib/gstreamer-0.10/libresindvd.so
7fd4e8171000-7fd4e8371000 ---p 00028000 08:05 312358                     /usr/lib/gstreamer-0.10/libresindvd.so
7fd4e8371000-7fd4e8372000 r--p 00028000 08:05 312358                     /usr/lib/gstreamer-0.10/libresindvd.so
7fd4e8372000-7fd4e8374000 rw-p 00029000 08:05 312358                     /usr/lib/gstreamer-0.10/libresindvd.so
7fd4e8374000-7fd4e838f000 r-xp 00000000 08:05 371163                     /usr/lib/libdv.so.4.0.3
7fd4e838f000-7fd4e858e000 ---p 0001b000 08:05 371163                     /usr/lib/libdv.so.4.0.3
7fd4e858e000-7fd4e858f
```I'm stucked... Any suggestions and advices are appreciated

---

### Post by Sapfeer on 2009-11-08
Solved

---

