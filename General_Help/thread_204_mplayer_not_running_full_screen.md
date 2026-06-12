---
title: "mplayer not running full screen"
date: 2004-10-11
forum: General Help
---

### Post by roongpatoong on 2004-10-11
Hi people

I installed mplayer by adding the following to my sources.lst ...

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

I works fine until I try fullscreen and then the image remains the same size and the border around the image goes black. So I have fullscreen - but with a regular sized image in the middle :(

I have an ati radeon 8500 and have installed the ati binary drivers as specified here ...

[http://www.ubuntufaq.org/document_details.php?c=4&amp;d=3](http://www.ubuntufaq.org/document_details.php?c=4&amp;d=3)

but even before installing the ati drivers I was having the same problem. Totem hasn't ever worked for me either - all I get is a black square in the movie window as the timeline bar moves along its path as if the movie is actually playing.

Any ideas about what could be preventing totem and fullscreen mplayer from functioning properly?

pantz

---

### Post by FLeiXiuS on 2004-10-11
Try taking a look here

[http://ubuntuforums.org/viewtopic.php?t=112](http://ubuntuforums.org/viewtopic.php?t=112)

That helped me out with a relevant problem.  Give it a shot.  If not, please post again.  Include errors if possible!

---

### Post by daniels on 2004-10-11
[quote=roongpatoong]I works fine until I try fullscreen and then the image remains the same size and the border around the image goes black. So I have fullscreen - but with a regular sized image in the middle :([/quote]

Try running mplayer 'mplayer -vo xv -fs -zoom filename'.

[quote=roongpatoong]I have an ati radeon 8500 and have installed the ati binary drivers as specified here ...[/quote]

I'd strongly recommend you stick with our normal drivers, which support the 8500 just fine.  I think this is more of a configuration issue than a driver issue.

---

### Post by triad169 on 2004-10-11
as a side note.  Instead of having to type alot at the terminal to load correct video driver for mplayer.  You can set up a config file located under .mplayer in your home directory to remember your setting for you.

The format and a brief explanation of the options is as follows:

> 
##
## MPlayer config file
##
## This file can be copied to /usr/local/etc/mplayer.conf and/or ~/.mplayer/config .
## If both exist, the ~/.mplayer/config's settings override the
## /usr/local/etc/mplayer.conf ones. And, of course command line overrides all.
## The options are the same as in the command line, but they can be specified
## more flexibly here. See below.
##

vo=xv			# To specify default video driver (see -vo help for
			# list)
ao=oss		# To specify default audio driver (see -ao help for
			# list)

fs=no			# Enlarges movie window to your desktop's size.
			# Used by drivers: all

vm=yes			# Tries to change to a different videomode
			# Used by drivers: dga2, x11, sdl

bpp=24			# Force changing display depth.
			# Valid settings are: 0, 15, 16, 24, 32
			# may need 'vm=yes' too.
			# Used by drivers: fbdev, dga2, svga, vesa

zoom=yes		# Enable software scaling (powerful CPU needed)
			# Used by drivers: svga, x11, vesa

#double=yes		# use double-buffering (recommended for xv with
			# SUB/OSD usage)

# monitoraspect=4:3	# standard monitor size, with square pixels
# monitoraspect=16:9	# use this for widescreen monitor! non-square pixels

##
## Use GUI mode by default
##

gui = yes

Triad

---

### Post by roongpatoong on 2004-10-12
Thanks for the replies - I haven't yet resorted to building mplayer from source but I did try out some of the other tips.

daniels - this is what I get when I run 'mplayer -vo xv -fs -zoom filename'

---snip---
pantz@faramir /media/movies/The Office Xmas Special $ mplayer -vo xv -fs -zoom The.Office.2003.Xmas.Special.Part.1.pdtv.ws.XviD-TVEP.avi
MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Advanced Micro Devices Athlon MP/XP/XP-M Barton 1834 MHz (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX

Reading config file /etc/mplayer/mplayer.conf
Reading config file /home/pantz/.mplayer/config
Reading /home/pantz/.mplayer/codecs.conf: Can't open '/home/pantz/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: 73 audio &amp; 180 video codecs
Failed to open /dev/rtc: Device or resource busy (it should be readable by the user.)
Using usleep() timing
Can't open input config file /home/pantz/.mplayer/input.conf: No such file or directory
Input config file /etc/mplayer/input.conf parsed: 53 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing The.Office.2003.Xmas.Special.Part.1.pdtv.ws.XviD-TVEP.avi.
AVI file format detected.
VIDEO:  [XVID]  640x360  24bpp  25.000 fps  1032.5 kbps (126.0 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 32000 Hz, 2 ch, 16 bit (0x10), ratio: 14000-&gt;128000 (112.0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" =&gt; local display)
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/devices.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.


Exiting... (End of file)
---snip---

Following the error messages and running xvinfo gives me

---snip---
$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
---snip---

I don't understand why I am having trouble. I have never had any problems with mplayer on Fedora 1 or 2. Can I get any useful info from booting into Fedora and checking the mplayer config there?

thanks again

pantz

---

### Post by Perfect Storm on 2004-10-13
I have installed Mplayer from source and done it 100% by the book. But it seems that some of the files are misplaced. Got some same error as you described.

Try run mplayer from commands.

Open /usr/local/etc/mplayer  (either in consol or via browser) then also open /home/&lt;your username&gt;/.mplayer and you'll see that some of the files are switched around.

copy  input.conf from /usr/local/etc/mplayer to home/&lt;your username&gt;/.mplayer  etc. etc. You can see from the Mplayer command output which kind of files and what to look for. Plus make what  Triad said.

That should do the trick
The only error I have now is 
'Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied'
Which I don't know what's about, anyone?

I will suggest your to install directly from the source, more saver IMHO.
By the way what kind of Video card do you have? Did you remember to set up the video driver?

---

### Post by oddabe19 on 2004-10-26
I hate bringing this back from the dead... but I just can't seem to get the doublesize feature to work. In XV or X11 or -zoom or anything.... fullscreen works fine though.  I compiled it from source... but i've never had this problem before.
Can someone help me? I don't get any error messages sorry.

---

### Post by ntlam on 2007-08-11
> **triad169 said:**
> as a side note.  Instead of having to type alot at the terminal to load correct video driver for mplayer.  You can set up a config file located under .mplayer in your home directory to remember your setting for you.

The format and a brief explanation of the options is as follows:



Triad

Thanks. It helped

---

### Post by mfh_ck on 2007-10-02
here is something my friend told me and it works well

mplayer -vo sdl filename

you can  get a list of output options by pressing tab after typing in mplayer -vo
one of them will work
see the one that works and edit the config file in .mplaye

thanks for the info on config editing

---

