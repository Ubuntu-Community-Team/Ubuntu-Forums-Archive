---
title: "how do u bring songbird up?"
date: 2009-09-12
forum: General Help
---

### Post by Arminius on 2009-09-12
I installed songbird songbird_1.2.0-1~getdeb1_i386.deb, seemed to install fine.
ran songbird in the applications/sound & Video, it seems to execute then vanishes, can't find it anywhere on the display.

I go to run it again and it says no its already running but not responding.
how do I shut it down?

I tried reinstalling with the deb file, but same problem

---

### Post by ithinkitschad on 2009-09-12
> **Arminius said:**
> I installed songbird songbird_1.2.0-1~getdeb1_i386.deb, seemed to install fine.
ran songbird in the applications/sound & Video, it seems to execute then vanishes, can't find it anywhere on the display.

I go to run it again and it says no its already running but not responding.
how do I shut it down?

I tried reinstalling with the deb file, but same problem


to kill it open a terminal and write "sudo pkill songbird"
Try running it from a terminal and see if you get errors
To run it from a terminal go to the folder its in and type "./songbird"

---

### Post by ithinkitschad on 2009-09-12
[Heres]("http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html") a really good tutorial on installing it. It worked great for me.

---

### Post by Arminius on 2009-09-12
./songbird
came up with no such file or directory

---

### Post by vinutux on 2009-09-12
Install from **[http://getsongbird.com/]("http://getsongbird.com/")**...Download and install 32 bit songbird (not probe if you are in 32 or 64 bit os).....coz 64 bit app is not working for me but 32 bit does....

---

### Post by ithinkitschad on 2009-09-12
> **Arminius said:**
> ./songbird
came up with no such file or directory

You would need to be in the folder that songbird is installed in. And it could be './songbird' or './Songbird'

---

### Post by chriskin on 2009-09-12
> **Arminius said:**
> I installed songbird songbird_1.2.0-1~getdeb1_i386.deb, seemed to install fine.
ran songbird in the applications/sound & Video, it seems to execute then vanishes, can't find it anywhere on the display.

I go to run it again and it says no its already running but not responding.
how do I shut it down?

I tried reinstalling with the deb file, but same problem

can you try opening it via terminal and tell us what happens?

---

### Post by ithinkitschad on 2009-09-12
> **chriskin said:**
> can you try opening it via terminal and tell us what happens?

I tried asking that last night, but they still haven't shown us the output from running it in the terminal.

---

### Post by amitso on 2009-09-12
Hi,

I've tried to install Songbird 1.2 with the ready made deb package on Ubuntu 9.04 and am getting the same result. It does not load although the process is running. I've removed libvisual-0.4-plugins and that makes no difference. When I load up songbird through the command I get the following output:

AddonMetadata: Constructor Error: TypeError: location is null

Any suggestions which could help my cause will be much appreciated.

---

### Post by ithinkitschad on 2009-09-12
> **amitso said:**
> Hi,

I've tried to install Songbird 1.2 with the ready made deb package on Ubuntu 9.04 and am getting the same result. It does not load although the process is running. I've removed libvisual-0.4-plugins and that makes no difference. When I load up songbird through the command I get the following output:

AddonMetadata: Constructor Error: TypeError: location is null

Any suggestions which could help my cause will be much appreciated.

Re-install libvisual-0.4-plugins, then follow the link I gave you. That .deb file obviously isn't working.

---

### Post by ithinkitschad on 2009-09-12
:D
[Heres the link again]("http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html"), trust me, just do it. It will work fine after.

---

### Post by amitso on 2009-09-13
Thanks for the response.

I've followed the install guide, from the link, word for word and am still having issues.

When I install without libvisual-0.4-plugins installed I get the same error as before. If this plugin is installed I get the following output when I execute songbird:

*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0x00007f0c93f53d10 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f0cac609cb8]
/lib/libc.so.6(cfree+0x76)[0x7f0cac60c276]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0xe)[0x7f0c93ad44ce]
/usr/lib/libvisual-0.4.so.0[0x7f0c93acd646]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x48)[0x7f0c93acd7d8]
/usr/lib/libvisual-0.4.so.0(visual_init+0x243)[0x7f0c93ada703]
/usr/lib64/gstreamer-0.10/libgstlibvisual.so[0x7f0c93cfbcb1]
/opt/Songbird/lib/libgstreamer-0.10.so[0x7f0c9659a383]
/opt/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x98c)[0x7f0c9659af7d]
/opt/Songbird/lib/libgstreamer-0.10.so[0x7f0c965a6904]
/opt/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x11f)[0x7f0c965a6b7e]
/opt/Songbird/lib/libgstreamer-0.10.so[0x7f0c9655259b]
/opt/Songbird/lib/libgstreamer-0.10.so[0x7f0c96552a09]
/opt/Songbird/lib/libgstreamer-0.10.so[0x7f0c96552fd7]
/opt/Songbird/lib/libgstreamer-0.10.so[0x7f0c96553568]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x540)[0x7f0ca8950020]
/opt/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xd6)[0x7f0c96551936]
/opt/Songbird/lib/libgstreamer-0.10.so(gst_init+0x29)[0x7f0c96551a23]
/opt/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0xacc)[0x7f0c941ceb04]
/opt/Songbird/lib/sbGStreamerMediacore.so[0x7f0c941d65e5]
/opt/Songbird/xulrunner/libxul.so[0x7f0caa49659f]
/opt/Songbird/xulrunner/libxul.so[0x7f0caa4960e9]
/opt/Songbird/lib/sbGStreamerMediacore.so[0x7f0c941e492b]
/opt/Songbird/lib/sbGStreamerMediacore.so[0x7f0c941e4958]
/opt/Songbird/lib/sbGStreamerMediacore.so[0x7f0c941e4140]
/opt/Songbird/lib/sbGStreamerMediacore.so[0x7f0c941d502e]
/opt/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x4b)[0x7f0c941d5601]
/opt/Songbird/lib/sbGStreamerMediacore.so[0x7f0c941d6555]
/opt/Songbird/xulrunner/libxul.so[0x7f0caa49659f]
/opt/Songbird/components/sbMediacoreManager.so[0x7f0c997e3613]
/opt/Songbird/components/sbMediacoreManager.so[0x7f0c997e3650]
/opt/Songbird/components/sbMediacoreManager.so[0x7f0c997e2f32]
/opt/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x1c)[0x7f0c997ce154]
/opt/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1ff)[0x7f0c997cb729]
/opt/Songbird/components/sbMediacoreManager.so[0x7f0c997cbb17]
/opt/Songbird/xulrunner/libxul.so[0x7f0caa476eba]
/opt/Songbird/xulrunner/libxul.so[0x7f0caa47738c]
/opt/Songbird/xulrunner/libxul.so[0x7f0ca9d47f86]
/opt/Songbird/xulrunner/libxul.so(XRE_main+0x177d)[0x7f0ca9d45c57]
././songbird-bin[0x401417]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f0cac5b05a6]
././songbird-bin[0x401009]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:06 711420                             /opt/Songbird/songbird-bin
00608000-00609000 rw-p 00008000 08:06 711420                             /opt/Songbird/songbird-bin
01954000-01975000 rw-p 01954000 00:00 0                                  [heap]
7f0c92066000-7f0c92067000 r-xp 00000000 08:06 25560                      /usr/lib/tls/libnvidia-tls.so.180.44
7f0c92067000-7f0c92167000 ---p 00001000 08:06 25560                      /usr/lib/tls/libnvidia-tls.so.180.44
7f0c92167000-7f0c92168000 rw-p 00001000 08:06 25560                      /usr/lib/tls/libnvidia-tls.so.180.44
7f0c93abb000-7f0c93af8000 r-xp 00000000 08:06 1433354                    /usr/lib/libvisual-0.4.so.0.0.0
7f0c93af8000-7f0c93cf7000 ---p 0003d000 08:06 1433354                    /usr/lib/libvisual-0.4.so.0.0.0
7f0c93cf7000-7f0c93cf8000 r--p 0003c000 08:06 1433354                    /usr/lib/libvisual-0.4.so.0.0.0
7f0c93cf8000-7f0c93cf9000 rw-p 0003d000 08:06 1433354                    /usr/lib/libvisual-0.4.so.0.0.0
7f0c93cf9000-7f0c93cff000 r-xp 00000000 08:06 703186                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f0c93cff000-7f0c93efe000 ---p 00006000 08:06 703186                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f0c93efe000-7f0c93eff000 r--p 00005000 08:06 703186                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f0c93eff000-7f0c93f00000 rw-p 00006000 08:06 703186                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f0c93f00000-7f0c94100000 rw-p 7f0c93f00000 00:00 0 
7f0c941ad000-7f0c941fd000 r-xp 00000000 08:06 711380                     /opt/Songbird/lib/sbGStreamerMediacore.so
7f0c941fd000-7f0c943fc000 ---p 00050000 08:06 711380                     /opt/Songbird/lib/sbGStreamerMediacore.so
7f0c943fc000-7f0c94401000 rw-p 0004f000 08:06 711380                     /opt/Songbird/lib/sbGStreamerMediacore.so
7f0c94401000-7f0c94407000 r-xp 00000000 08:06 711386                     /opt/Songbird/lib/libgstvideo-0.10.so
7f0c94407000-7f0c94606000 ---p 00006000 08:06 711386                     /opt/Songbird/lib/libgstvideo-0.10.so
7f0c94606000-7f0c94607000 rw-p 00005000 08:06 711386                     /opt/Songbird/lib/libgstvideo-0.10.so
7f0c94607000-7f0c9460f000 r-xp 00000000 08:06 711378                     /opt/Songbird/lib/libgstsdp-0.10.so
7f0c9460f000-7f0c9480e000 ---p 00008000 08:06 711378                     /opt/Songbird/lib/libgstsdp-0.10.so
7f0c9480e000-7f0c9480f000 rw-p 00007000 08:06 711378                     /opt/Songbird/lib/libgstsdp-0.10.so
7f0c9480f000-7f0c94821000 r-xp 00000000 08:06 711392                     /opt/Songbird/lib/libgstrtsp-0.10.so
7f0c94821000-7f0c94a21000 ---p 00012000 08:06 711392                     /opt/Songbird/lib/libgstrtsp-0.10.so
7f0c94a21000-7f0c94a23000 rw-p 00012000 08:06 711392                     /opt/Songbird/lib/libgstrtsp-0.10.so
7f0c94a23000-7f0c94a37000 r-xp 00000000 08:06 711395                     /opt/Songbird/lib/libgstrtp-0.10.so
7f0c94a37000-7f0c94c37000 ---p 00014000 08:06 711395                     /opt/Songbird/lib/libgstrtp-0.10.so
7f0c94c37000-7f0c94c39000 rw-p 00014000 08:06 711395                     /opt/Songbird/lib/libgstrtp-0.10.so
7f0c94c39000-7f0c94c45000 r-xp 00000000 08:06 711384                     /opt/Songbird/lib/libgstriff-0.10.so
7f0c94c45000-7f0c94e44000 ---p 0000c000 08:06 711384                     /opt/Songbird/lib/libgstriff-0.10.so
7f0c94e44000-7f0c94e45000 rw-p 0000b000 08:06 711384                     /opt/Songbird/lib/libgstriff-0.10.so
7f0c94e45000-7f0c94e52000 r-xp 00000000 08:06 711375                     /opt/Songbird/lib/libgstpbutils-0.10.so
7f0c94e52000-7f0c95052000 ---p 0000d000 08:06 711375                     /opt/Songbird/lib/libgstpbutils-0.10.so
7f0c95052000-7f0c95054000 rw-p 0000d000 08:06 711375                     /opt/Songbird/lib/libgstpbutils-0.10.so
7f0c95054000-7f0c95056000 r-xp 00000000 08:06 711371                     /opt/Songbird/lib/libgstnetbuffer-0.10.so
7f0c95056000-7f0c95255000 ---p 00002000 08:06 711371                     /opt/Songbird/lib/libgstnetbuffer-0.10.so
7f0c95255000-7f0c95256000 rw-p 00001000 08:06 711371                     /opt/Songbird/lib/libgstnetbuffer-0.10.so
7f0c95256000-7f0c95264000 r-xp 00000000 08:06 711372                     /opt/Songbird/lib/libgstfft-0.10.so
7f0c95264000-7f0c95463000 ---p 0000e000 08:06 711372                     /opt/Songbird/lib/libgstfft-0.10.so
7f0c95463000-7f0c95464000 rw-p 0000d000 08:06 711372                     /opt/Songbird/lib/libgstfft-0.10.so
7f0c95464000-7f0c95471000 r-xp 00000000 08:06 711373                     /opt/Songbird/lib/libgstcdda-0.10.so
7f0c95471000-7f0c95670000 ---p 0000d000 08:06 711373                     /opt/Songbird/lib/libgstcdda-0.10.so
7f0c95670000-7f0c95671000 rw-p 0000c000 08:06 711373                     /opt/Songbird/lib/libgstcdda-0.10.so
7f0c95671000-7f0c95682000 r-xp 00000000 08:06 711387                     /opt/Songbird/lib/libgsttag-0.10.so
7f0c95682000-7f0c95881000 ---p 00011000 08:06 711387                     /opt/Songbird/lib/libgsttag-0.10.so
7f0c95881000-7f0c95883000 rw-p 00010000 08:06 711387                     /opt/Songbird/lib/libgsttag-0.10.so
7f0c95883000-7f0c958a8000 r-xp 00000000 08:06 711381                     /opt/Songbird/lib/libgstaudio-0.10.so
7f0c958a8000-7f0c95aa8000 ---p 00025000 08:06 711381                     /opt/Songbird/lib/libgstaudio-0.10.so
7f0c95aa8000-7f0c95aaa000 rw-p 00025000 08:06 711381                     /opt/Songbird/lib/libgstaudio-0.10.so
7f0c95aaa000-7f0c95ab6000 r-xp 00000000 08:06 711390                     /opt/Songbird/lib/libgstinterfaces-0.10.so
7f0c95ab6000-7f0c95cb6000 ---p 0000c000 08:06 711390                     /opt/Songbird/lib/libgstinterfaces-0.10.so
7f0c95cb6000-7f0c95cb7000 rw-p 0000c000 08:06 711390                     /opt/Songbird/lib/libgstinterfaces-0.10.so
7f0c95cb7000-7f0c95cbe000 r-xp 00000000 08:06 711388                     /opt/Songbird/lib/libgstnet-0.10.so
7f0c95cbe000-7f0c95ebd000 ---p 00007000 08:06 711388                     /opt/Songbird/lib/libgstnet-0.10.so
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

