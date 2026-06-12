---
title: "Compiling zoneminder need to use /usr/local/libs"
date: 2011-08-17
forum: General Help
---

### Post by zSeries on 2011-08-17
Hi,

I installed Zoneminder 1.24.2 and current ffmpeg modules in from the main repository via synaptic. When I try to view the image from my USB cam I get an empty white box and a "waiting for host" message, the source link is yellow, I have never seen it green. I turned on debugging and see I am getting a Seqmentation faults like this one:-

08/17/11 18:33:58.894551 zmc_dvideo0[12078].DB4-zm_local_camera.cpp/421 [ v4l2_data.fmt.fmt.pix.priv = 00000000]
08/17/11 18:33:58.894563 zmc_dvideo0[12078].DB3-zm_local_camera.cpp/432 [Setting up request buffers]
08/17/11 18:33:58.894786 zmc_dvideo0[12078].DB3-zm_local_camera.cpp/460 [Setting up 8 data buffers]
08/17/11 18:33:58.894844 zmc_dvideo0[12078].DB3-zm_local_camera.cpp/498 [Configuring video source]
08/17/11 18:33:58.894863 zmc_dvideo0[12078].WAR-zm_local_camera.cpp/1337 [Hue control is not suppported]
08/17/11 18:33:58.895010 zmc_dvideo0[12078].WAR-zm_local_camera.cpp/1395 [Saturation control is not suppported]
08/17/11 18:33:58.895102 zmc_dvideo0[12078].DB3-zm_local_camera.cpp/696 [Setting up static colour tables]
08/17/11 18:33:58.895124 zmc_dvideo0[12078].DB2-zm_local_camera.cpp/1500 [Priming capture]
08/17/11 18:33:58.895136 zmc_dvideo0[12078].DB3-zm_local_camera.cpp/1504 [Queueing buffers]
08/17/11 18:33:58.895151 zmc_dvideo0[12078].DB3-zm_local_camera.cpp/1520 [Starting video stream]
08/17/11 18:33:59.637392 zmc_dvideo0[12078].DB2-zm_local_camera.cpp/1547 [Pre-capturing]
08/17/11 18:33:59.637423 zmc_dvideo0[12078].DB3-zm_local_camera.cpp/1553 [Capturing]
08/17/11 18:33:59.637441 zmc_dvideo0[12078].DB3-zm_local_camera.cpp/1578 [Capturing 1 frames]
08/17/11 18:33:59.838269 zmc_dvideo0[12078].DB3-zm_local_camera.cpp/1602 [Captured frame 0/1 from channel 0]
08/17/11 18:33:59.838430 zmc_dvideo0[12078].INF-zm_signal.cpp/72 [Got signal 11 (Segmentation fault), crashing]

I also installed Ununtu 11.04 and and have exactly the same problem but I want to stick to the 10.04 LTS if possible. I get similar problems with Fedora 15.

The camera is a USB Creative model PD1110, not on on the official Zoneminder support list but it works fine with CHEESE & XAWTV on all Ubuntu and Fedora.

Next I ran Zoneminder from the LiveCD ArchLinux and everything works fine so that makes me think it simply a compatability issue so I am trying to compile ZM 2.42.4 using the ffmpeg 0.8.1.

I followed the link [http://ubuntuforums.org/showthread.php?t=786095&highlight=install+latest+ffmpeg+x264](http://ubuntuforums.org/showthread.php?t=786095&highlight=install+latest+ffmpeg+x264) and and added a "make install-libs" between the make and ldconfig. The install-libs seems to place files in /usr/local/libs.

When I try to compile zoneminder it is not searching that location for libavcedec.a etc. No matter what I specify on the zm configure it points to an included sub folder and fails.

g++ -DHAVE_CONFIG_H -I. -I..  -I/usr/include -I/usr/local/lib/include -Wall -Wno-sign-compare -fno-inline -I/usr/local/lib/include -D__STDC_CONSTANT_MACROS  -g -O2 -MT zm_ffmpeg_camera.o -MD -MP -MF .deps/zm_ffmpeg_camera.Tpo -c -o zm_ffmpeg_camera.o zm_ffmpeg_camera.cpp
mv -f .deps/zm_ffmpeg_camera.Tpo .deps/zm_ffmpeg_camera.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I/usr/include -I/usr/local/lib/include -Wall -Wno-sign-compare -fno-inline -I/usr/local/lib/include -D__STDC_CONSTANT_MACROS  -g -O2 -MT zm_image.o -MD -MP -MF .deps/zm_image.Tpo -c -o zm_image.o zm_image.cpp
zm_image.cpp: In member function &#8216;void Image::Blend(const Image&, int) const&#8217;:
zm_image.cpp:777: warning: operation on &#8216;pdest&#8217; may be undefined
mv -f .deps/zm_image.Tpo .deps/zm_image.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I/usr/include -I/usr/local/lib/include -Wall -Wno-sign-compare -fno-inline -I/usr/local/lib/include -D__STDC_CONSTANT_MACROS  -g -O2 -MT zm_local_camera.o -MD -MP -MF .deps/zm_local_camera.Tpo -c -o zm_local_camera.o zm_local_camera.cpp
In file included from zm_local_camera.cpp:24:
zm_local_camera.h:101: error: &#8216;PixelFormat&#8217; does not name a type
zm_local_camera.h:102: error: &#8216;PixelFormat&#8217; does not name a type
zm_local_camera.h:103: error: ISO C++ forbids declaration of &#8216;AVFrame&#8217; with no type

I am not an experienced C programmer on Linux but I am familiar with assemblies, complies and links on many other platforms. I haven't changed anything related to GCC, it is installed out-of-the-box. These are my config files

In /etc/ld.so.conf :-
include /etc/ld.so.conf.d/*.conf

And in /etc/ls.so.conf.d/libc.conf :-
# libc default configuration
/usr/local/lib

tony@host:~$ gcc -print-search-dirs shows :-
install: /usr/lib/gcc/i486-linux-gnu/4.4.3/
programs: =/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/:/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/:/usr/libexec/gcc/i486-linux-gnu/4.4.3/:/usr/libexec/gcc/i486-linux-gnu/:/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/:/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../i486-linux-gnu/bin/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../i486-linux-gnu/bin/
libraries: =/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../i486-linux-gnu/lib/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../i486-linux-gnu/lib/../lib/:/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/:/lib/i486-linux-gnu/4.4.3/:/lib/../lib/:/usr/lib/i486-linux-gnu/4.4.3/:/usr/lib/../lib/:/usr/lib/i486-linux-gnu/i486-linux-gnu/4.4.3/:/usr/lib/i486-linux-gnu/../lib/:/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../i486-linux-gnu/lib/:/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../:/lib/:/usr/lib/:/usr/lib/i486-linux-gnu/
tony@host:~$

I have been trying to get ZM working for weeks and read loads of forum pages but nothing works. Somewhere I am missing a step to point ZM at the right folder for the compile can anyone give me a clue?

Thank you,
Tony.

---

### Post by willem.devil on 2011-11-27
I met the same problem while compiling the source. I am currently trying to make ZoneMinder-1.25.0 working. Anyone got any idea? Cheers.

---

### Post by mrtsmith on 2011-12-03
Follow this link ,
[http://www.youtube.com/watch?v=l-nIUgB35OQ](http://www.youtube.com/watch?v=l-nIUgB35OQ)

I was able to get it working with my logitech webcam. Going through remote. I'm still trying to do as local. But remote worked. 

Give that a try.

---

