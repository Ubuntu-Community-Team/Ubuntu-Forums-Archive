---
title: "mplayer tries to load obsolete libjack"
date: 2006-06-02
forum: General Help
---

### Post by pyromithrandir on 2006-06-02
When I try to start up mplayer, it won't start. I just get this error. 
> $ mplayer
mplayer: error while loading shared libraries: libjack-0.80.0.so.0: cannot open shared object file: No such file or directory

I have the latest packages for mplayer and libjack0.100.0-0 and the other jack libraries. 
libjack0.80.0 isn't in the repos anymore, so I really don't think the latest mplayer should be trying to use it.
I haven't seen anyone else complaining about this, so I guess it's something on my end, but I don't know how to fix it. Any insight would be appreciated.

---

### Post by pyromithrandir on 2006-06-03
Any ideas?

---

### Post by RFScheer on 2006-06-23
I am struggling to get mplayer and jack working on dapper.  Have you succeeded yet?

---

### Post by joshrobinson on 2006-06-23
[QUOTE=RFScheer]I am struggling to get mplayer and jack working on dapper.  Have you succeeded yet?[/QUOTE]

have you tried compiling from source code from the mplayer website?

---

### Post by pyromithrandir on 2006-06-23
Well, actually, I was successful. Here's what happened for me:
I had tried to uninstall and reinstall mplayer with apt-get, but nothing changed. I tried this numerous times. Then, I uninstalled it again, and noticed that it wasn't actually removing all of the files that it should have (essentially, it was only saying that it was uninstalling, but the outdated pieces of it weren't going anywhere). I went through and deleted all of the files that needed to go, and did an apt-get install mplayer again. This time it worked without a hitch.

I think the problem probably happened when I upgraded from Breezy to Dapper, as I had had a few problems with package breakage then.

---

### Post by RFScheer on 2006-06-23
pyro - I just wiped everything relating to mplayer and installed again using Synaptic.  The problem is the same.  It runs but does not have a jack driver.  

Are you using Mplayer with Jack?

josh - I've been trying to bring in 1.0pre8 from mplayerhq.hu but it fails on make.  Here's the end of the listing where it fails:

cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=k8 -mtune=k8 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I.. -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include        -I/usr/include/SDL -D_REENTRANT   -o ao_jack.o ao_jack.c
ao_jack.c:28:23: error: jack/jack.h: No such file or directory
ao_jack.c:42: error: syntax error before '*' token
ao_jack.c:42: warning: data definition has no type or storage class
ao_jack.c:44: error: syntax error before '*' token
ao_jack.c:44: warning: data definition has no type or storage class
ao_jack.c:176: error: syntax error before 'nframes'
ao_jack.c: In function 'outputaudio':
ao_jack.c:180: error: 'nframes' undeclared (first use in this function)
ao_jack.c:180: error: (Each undeclared identifier is reported only once
ao_jack.c:180: error: for each function it appears in.)
ao_jack.c:180: warning: assignment makes pointer from integer without a cast
ao_jack.c: In function 'init':
ao_jack.c:226: error: 'JackPortIsInput' undeclared (first use in this function)
ao_jack.c:241: warning: assignment makes pointer from integer without a cast
ao_jack.c:251: error: 'JackPortIsPhysical' undeclared (first use in this function)
ao_jack.c:252: warning: assignment makes pointer from integer without a cast
ao_jack.c:265: error: 'JACK_DEFAULT_AUDIO_TYPE' undeclared (first use in this function)
ao_jack.c:265: error: 'JackPortIsOutput' undeclared (first use in this function)
ao_jack.c:265: warning: assignment makes pointer from integer without a cast
make[1]: *** [ao_jack.o] Error 1
make[1]: Leaving directory `/home/rfs/Downloads/mplayer/libao2'
make: *** [libao2/libao2.a] Error 2

---

### Post by pyromithrandir on 2006-06-23
Yeah, I'm using it with Jack. Do you have the latest libjack installed?

---

### Post by RFScheer on 2006-06-24
I already had libjack version 0.100.0-4, but based on your question I also added the dev lib and recompiled.  Now it errors this way:

```

cc -I../libvo -I../../libvo  -fno-PIC -O4 -march=k8 -mtune=k8 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/     -I/usr/include/freetype2  -I/usr/include/SDL -D_REENTRANT    -I./libavutil -I./libavcodec   -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a input/libinput.a  vidix/libvidix.a Gui/libgui.a libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a postproc/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit  libavcodec/libavcodec.a  libavformat/libavformat.a  libavutil/libavutil.a  libpostproc/libpostproc.a  -lmad -ldv -ltheora -logg     -lmp3lame   -ldts -lpng -lz -lz -ljpeg -lasound -ldl -lpthread  -lx264 -lpthread -lmpcdec   -lfaac -lfreetype -lz -lncurses  -lnsl       -lfontconfig  libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lglib-2.0   -laa -lGL -ldl  -lXv   -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread -lnsl -L/usr/lib -lSDL -lpthread      -L/usr/lib -lcaca -lslang -lX11 -L/usr/X11R6/lib -lncurses -lncurses   -L/usr/lib -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/lib -lesd -laudiofile -lm   -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread    -Wl,-z,noexecstack     -lpthread -ldl -rdynamic  -lm
libao2/libao2.a(ao_jack.o): In function `outputaudio':ao_jack.c:(.text+0x1db): undefined reference to `jack_port_get_buffer'
libao2/libao2.a(ao_jack.o): In function `init':ao_jack.c:(.text+0x4f8): undefined reference to `jack_client_new'
:ao_jack.c:(.text+0x545): undefined reference to `jack_set_process_callback'
:ao_jack.c:(.text+0x572): undefined reference to `jack_get_ports'
:ao_jack.c:(.text+0x603): undefined reference to `jack_port_register'
:ao_jack.c:(.text+0x628): undefined reference to `jack_activate'
:ao_jack.c:(.text+0x64f): undefined reference to `jack_port_name'
:ao_jack.c:(.text+0x664): undefined reference to `jack_connect'
:ao_jack.c:(.text+0x682): undefined reference to `jack_get_sample_rate'
:ao_jack.c:(.text+0x69a): undefined reference to `jack_port_get_total_latency'
:ao_jack.c:(.text+0x6a9): undefined reference to `jack_get_buffer_size'
:ao_jack.c:(.text+0x7a5): undefined reference to `jack_client_close'
libao2/libao2.a(ao_jack.o): In function `uninit':ao_jack.c:(.text+0x99b): undefined reference to `jack_client_close'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```


This is not the latest from jackaudio.org, which is now up to 0.101.1 but I'm assuming you mean latest in the dapper repo's.

Greatly appreciate your help!!!!

---

