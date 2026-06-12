---
title: "Cannot get 1680x1050 &amp; Empty xorg.conf"
date: 2010-01-30
forum: General Help
---

### Post by RRF2525 on 2010-01-30
HelloWorld --

Have been working this problem for several days and have learned a ton reading through the forums but have yet to find a solution (or input for that matter).  Just learning a lot about Linux (which is always good!)  : )

Here's the general issues:

First issue...new installation of 9.10 karmic cannot get NVIDIA GPU(s) running with supplied NIVIDIA drivers.  Tried the (190) driver from NVIDIA but that also has hit snags.  

Second issue...when issue command "gedit /etc/X11/xorg.conf" in terminal I get an empty file (nothing!)

Here's the deets:  ASUS A8N, Athlon 4200+, 2G/250G/1TB, dual XFX 6800GT (SLI).  Not running SLI features for now, dual boot x64 XP and 9.10 Karmic (x64 on /dev/sda1 ntfs) and (9.10 on /dev/sdb5 ext swap at /dev/sdb6).  Monitor is Sceptre X20 (trying to get 1680x1050 WSXGA+ output from my GPU's but no soap so far)

First issue deets...new installation detects the NVIDIA cards and advises use of supplied restricted drivers.  First two attempts at installation yield inability to boot machine after installation of restricted drivers.  Reboot yields loss of signal to monitor and system goes into some low-power mode or something...kinda wierd.  I recreated the issue on another installation and blew that install up too...started again and DID NOT install the restricted drivers.  I'm just dealing w/a stretched screen for now...

Second issue deets...in my reading of these forum pages I have been digging into the system and could not find my xorg.conf file.  The system responded to commands to make a backup of the file and I can ls the file (no problem).  When viewing it w/gedit it is an EMPTY file.  Nothing there...so, I'm guessing this is where part of my problem lies?

I have noted that the (190) restricted driver from NVIDIA is not included in this build of 9.10.  And at this point my system doesn't even indicate that there's a device that requires restricted drivers anyway.  I assume this goes back to the xorg.conf file?  

As you can see I'm new to Ubuntu and haven't driven Linux in a decade.  Making the switch from Windows once-and-for all.  

Thanks and looking for any and all constructive input!  : )

---

### Post by efflandt on 2010-01-30
X in Ubuntu 9.10 does not have an xorg.conf file unless you (or something you install) creates one.  Otherwise X just tries to figure out things by itself.

I cannot help you with anything nVidia specific.  But if X does not recognize a resolution that you know your monitor is capable of, I have used xrandr and cvt in a terminal to determine and test what works with standard modules.  In my case it was laptop external VGA HDTV which says it is 1366x768, but WinXP thinks it is 1360x764, and /var/log/Xorg.0.log came up with a 1360x765 mode that it did not use, maybe because bigger than 1280x800 laptop screen.  But I was able to configure a 1360x765 VGA mode, disable laptop screen, and that works great.

See what resolutions /var/log/Xorg.0.log sees, and possibly why it does not use some.  And xrandr may give a clue of horiz/vertical pixel limits.  You may need to use less color depth if high resolution is limited by RAM.

---

### Post by frankwakeman on 2010-01-30
Similar problem to what I encounter with my nvidia fx5200. The workaround I use is to paste the contents of the last working xorg.conf file, from Ubuntu 6.10* (_after_ installing the restricted driver and rebooting), and then reboot.

To get xorg.conf I press alt F2, type gksu nautilus and then navigate to /etc/X11/xorg.conf whether or not that's the right way.

But how much trouble could it be for Canonical to notice this ultra-recurrent problem and rectify it?

*Because I'm not a very good archivist I usually have to boot a 6.10 live cd and copy the xorg.conf onto a usb stick.

---

