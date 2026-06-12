---
title: "sorry for another &quot;dvd doesn't work&quot; thread, but..."
date: 2006-02-26
forum: General Help
---

### Post by raul on 2006-02-26
i ran automatix, so have all the relevant codecs and activated dma. also, i installed libdvdcss2 manually. still, i'm not able to play dvd's with mplayer or totem. when i try to open mplayer from the terminal, it just displays the following messages: 

"Can't opem VGM info!"vo: X11 running at 1600x1200 with depth 16 and 16 bpp (":0.0" => local display)
86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
Reading disc structure, please wait...
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
Can't open VMG info!
File not found: '1'
Failed to open dvd://1

after that, mplyer crashes. 

when i try to use totem, i get the following message:

Totem could not play 'dvd:/'.
The source seems encrypted, and can't be read. Are you trying to play an encrypted without libdvdcss?

any ideas?

---

### Post by Stinger on 2006-02-26
Did you remember to install the totem-xine package ?

---

### Post by raul on 2006-02-26
yeah:

raul@compu:~$ sudo apt-get install totem-xine
Password:
Reading package lists... Done
Building dependency tree... Done
totem-xine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
raul@compu:~$

---

### Post by Stinger on 2006-02-26
-[QUOTE=raul]i installed libdvdcss2 manually.[/QUOTE]

Mine says 1.2.9-1plf3.

You could try the Gxine or Xfmedia players too.

This is how it works for me:
I load a DVD in my DVD-drive , after a short while totem pops up and starts playing the DVD.

Could be your DVD-play drive setup in xine too.

---

### Post by raul on 2006-02-26
yeah, i can't get it to work. i don't know what's up.

---

### Post by Stinger on 2006-02-27
Do you get a DVDVolume icon on your desktop when you have a 
DVD in the drive ?

---

