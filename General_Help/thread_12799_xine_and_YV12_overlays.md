---
title: "xine and YV12 overlays"
date: 2005-01-26
forum: General Help
---

### Post by enquiry on 2005-01-26
I am attempting to use xine (or gxine) for DVD playback. I have installed xine using apt-get, and playing DVD's works to a certain degree, but it's slow and uses 100 % of the CPU.

I've run xine-check and I get the following output:
```

[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.8.1-4-386)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ good ] found /usr/bin/xine-config in your PATH
[ good ] plugin directory /usr/lib/xine/plugins/1.0.0 exists.
[ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/hdc
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to to color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         http://www.linuxvideo.org/gatos/
         press <enter> to continue...
```
So apparently the problem has something to do with me not having an accelerated X server? How can I resolve this? I have an ATI card (Radeon 9500), but [www.linuxvideo.org](www.linuxvideo.org) is dead.

Playing DVD's using Mplayer works flawlessly, and requires little of the CPU (but there's no menu support).

---

### Post by enquiry on 2005-02-04
Does anyone know?

---

### Post by enquiry on 2005-02-15
I've solved the problem by adding the following lines to XF86Config-4, under Section "Device":
```
	Option		"UseInternalAGPGART" 	"no"
	Option		"RenderAccel" 		"true"
	Option		"VideoOverlay"		"on"
```
Both Xine and gXine now have smooth full screen playback of DVD when using the xv driver (which is selected in the setup for Xine and gXine). The picture quality in MPlayer also benefited by using the xv driver (before, I was using the gl driver).

This also works in xorg (but then it's the xorg.conf you'll be adding the lines to).

---

