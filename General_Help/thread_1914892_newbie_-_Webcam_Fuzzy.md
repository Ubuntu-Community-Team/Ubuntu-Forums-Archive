---
title: "newbie - Webcam Fuzzy"
date: 2012-01-25
forum: General Help
---

### Post by Quarkrad on 2012-01-25
I'm running 10.10 and use to have very good video from my rather old Logitech webcam via Cheese and Skype.  Some time ago I did a rebuild and now need to use my webcam again.  Unfortunately the video though Cheese is awful - there is a picture in the background but the picture is dark, there are numerous horizontal lines and a number of other artefacts on the screen. It looks to me like the video driver is wrong but last time I used it, before the rebuild, it just worked 'out of the box'. I have read **[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)** and followed the instructions, here is the output using vlc and mplayer as per the community doc:

dad@dadubuntu:~$ vlc c412:///dev/video0
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x206b120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f530d56eb20, 0x7f530d56ea80)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1327434518)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:20044): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
[0x7f5310000a70] main input error: open of `c412:///dev/video0' failed: (null)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
dad@dadubuntu:~$ mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: USB Camera (046d:0920)
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = tv8532;
 Current input: 0
 Current format: unknown (0x31384142)
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: Cannot get fps
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Cannot find codec matching selected -vo and video format 0x31384142.
==========================================================================

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 1 frames dropped.

Exiting... (End of file)


Does this output give any clues to what could be wrong?

---

### Post by Quarkrad on 2012-01-25
Just tested on windozeXP and it works OK - it's a Quickcam Express

---

### Post by Quarkrad on 2012-02-04
I installed guvcview from software centre and get a reasonable picture,   but cheese still gives me a rubbish picture - see attached. Ultimately I'm looking to use Skype but logically I would like to get cheese working.  I'm intrigued that I can get a good picture but not with cheese (which I thought worked with most things) - I'm guessing guvcview must load software that cheese needs.  This webcam used to 'just work' even though it is an old model.  I have just tried **LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese** but that made no difference.

---

### Post by Quarkrad on 2012-02-06
bump

---

### Post by Quarkrad on 2012-02-06
I'm jumping the gun a bit here as I haven't solved the cheese problem - but can anybody help me with this output from terminal please?

[B]dad@dadubuntu:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

(<unknown>:10199): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:10199): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:10199): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:10199): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:10199): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:10199): Gtk-WARNING **: Loading IM context type 'ibus' failed[/B]

I have the file (im-ibus.so) and the directory structure - I'm not sure what the ELF class ref is though.

---

### Post by Quarkrad on 2012-02-06
Silly me - a bit embarrassed now!  The problem I had re the picture quality using cheese was the resolution.  Cheese was set to 352 x 288 but when I changed it to 176 x 144 the picture is OK.  My issues are now Skype related and there is a lot of info on that so I'm going to mark this post as solved.

---

