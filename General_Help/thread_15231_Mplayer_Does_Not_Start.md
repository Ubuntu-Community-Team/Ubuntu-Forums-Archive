---
title: "Mplayer Does Not Start"
date: 2005-02-13
forum: General Help
---

### Post by Dana on 2005-02-13
Totem could not play a wmv file so I installed mplayer. But mplayer will not start, neither gui or command line. Indication of an illegal statement in mplayer.conf.
Don't begin to know what to look for.

The interesting thing is with the codecs installed as part of mplayer installation, Totem now can run the wmv file now that it sees the codecs. I did not point Totem to the codecs, it seems to have found them itself.

---

### Post by ups on 2005-02-13
What errors do u get on trying to run mplayer?

On the terminal, try executing:
$ gmplayer

and see/post what messages are printed there, there should be some error that mplayer encountered.

---

### Post by Dana on 2005-02-13
All I get is "reading /etc/mplayer/mplayer.conf and then "Illegal instruction." It would appear something in the mplayer.conf file is not as it should be. Having read some docs I am no closer to understanding what I need to do. Guess I'm fortunate that Totem decided to work suddenly. How often does an application decide to work after not working... with no user intervention?

Dana

---

### Post by piedamaro on 2005-02-13
If you post your mplayer.conf file, maybe someone will be able to find some errors in it.

---

### Post by Dana on 2005-02-13
Well, the mplayer.conf below is as created during the install. I haven't touched it since my newbie's ignorance is profound. As I said from the command line invoking mplayer or gmplayer simply reports Reading /etc/mplayer/mplayer.conf and then illegal instruction. Nothing happens starting from the Gnome application menu either.

##
## MPlayer config file
##
## This file can be copied to /etc/mplayer.conf and/or ~/.mplayer/config .
## If both exist, the ~/.mplayer/config's settings override the
## /etc/mplayer.conf ones. And, of course command line overrides all.
## The options are the same as in the command line, but they can be specified
## more flexibly here. See below.
##

vo=x11,			# To specify default video driver (see -vo help for
			# list)

ao=alsa,		# To specify default audio driver (see -ao help for
			# list)

fs=no			# Enlarges movie window to your desktop's size.
			# Used by drivers: all

vm=no			# Tries to change to a different videomode
			# Used by drivers: dga2, x11, sdl

bpp=0			# Force changing display depth.
			# Valid settings are: 0, 15, 16, 24, 32
			# may need 'vm=yes' too.
			# Used by drivers: fbdev, dga2, svga

zoom=no			# Enable software scaling (powerful CPU needed)
			# Used by drivers: svga, aalib

double=yes		# use double-buffering (recommended for xv with
			# SUB/OSD usage)

# x=800			# scale movie to <x> pixels width
# y=600			# scale movie to <y> pixels height

osdlevel=1		# don't display OSD at stratup

monitoraspect=4:3	# standard monitor size, with square pixels
# monitoraspect=16:9	# use this for widescreen monitor! non-square pixels

cache = 1024		# Disk cache 1 MB

##
## Specify your preferred default skin here
## (skins are searched in /usr/share/mplayer/Skin/yourskin
##  and ~/.mplayer/Skin/yourskin)
##

skin = default


##
## Multiple languages are available :)
##
## Hungarian	igen	nem
## English	yes	no
## German	ja	nein
## Spanish	si	no
## Binary	1	0
##
## You can also use spaces and/or tabs.
##

#sound		= 1
#nosound	= nein
#mixer		= /dev/mixer

##
## resample the fonts' alphamap
## 0	plain white fonts
## 0.75	very narrow black outline (default)
## 1	narrow black outline
## 10	bold black outline
##

#ffactor = 0.75

##
## FBdev driver: 

# fb = /dev/fb0				# framebuffer device to use
# fbmode = 640x480-120			# use this mode (read from fb.modes!)
# fbmodeconfig = /etc/fb.modes		# the fb.modes file

## VESA and FBdev driver: specify your monitor's timings
## 
## (see for example /etc/X11/XF86Config for timings!)
## ** CAUTION! IF YOUR DISPLAY DOESN'T SUPPORT AUTOMATICALLY TURNING OFF WHEN
##    OVERDRIVED (AND EVEN IF IT DOES), THIS MAY CAUSE DAMAGE TO YOUR DISPLAY!
##    WE AREN'T RESPONSIBLE, IT'S YOUR DECISION! **
##
## k, K : means multiply by 1000
## m, M : means multiply by 1.000.000
##
# monitor_hfreq = 31.5k-50k,70k		# horizontal frequency range
# monitor_vfreq = 50-90			# vertical frequency range
# monitor_dotclock = 30M-300M		# dotclock (or pixelclock) range

##
## SDL driver
##

# vo = sdl:aalib	# use SDL video driver by default
			# use "vo = sdl:aalib" or "vo sdl:dga" and so on,
			# for specifying SDL subdrivers
# ao = sdl:esd		# use SDL audio driver by default
			# use "ao = sdl:esd" to use SDL's ESD driver
# noxv = no		# whether to use XVideo hardware acceleration or not
# forcexv = yes		# force XVideo even if not detected

##
## Other (preferred to be default from configfile) switches
##

framedrop=no		# drop frames, when not in sync (slow CPU, videocard,
			# etc)

#vfm=ffmpeg		# use FFmpeg's libavcodec video codec family
			# See "mplayer -vfm help" for all available codecs

#bps=yes		# use this method for playing AVIs (if have problems,
			# try removing this)

# slang= en		# DVD : display english subtitles if available
# alang= en		# DVD : play english audio tracks if available

## This is the correct way to use "subconfig" type options in the
## configuration file. In the command line you use :
## -aop list=resample:fout=44100 , but here it is :
# aop=list=resample:fout=44100

# From Fedora
# the default mpeg audio decoder is currently broken, let's try libmad
# first:
afm=libmad

# get a default OSD font from fontconfig
#fontconfig = yes
#font = "Sans"
#subfont-text-scale = 3

---

### Post by piedamaro on 2005-02-13
These lines are suspicious:
vo=x11, # To specify default video driver (see -vo help for
# list)

ao=alsa, # To specify default audio driver (see -ao help for
# list)

try to remove the commas after x11 and alsa. However mplayer should work fine event w/o a config file. You could try to rename it as mplayer.conf.old for ex. and see.

---

### Post by Dana on 2005-02-14
Renaming the conf file got me further along, thanks. But it still did not run. Won't have time to look over the output for a couple days. Video problem? At least totem now works since the codecs were installed by mplayer. Output running mplayer from the command line:

dana@thinkpad:~ $ sudo mplayer Voting_Machine.wmv
MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville 969.7 MHz (Family: 6, Stepping: 10)
Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Reading config file /etc/mplayer/mplayer.conf: No such file or directory
Reading config file /home/dana/.mplayer/config
Reading /home/dana/.mplayer/codecs.conf: Can't open '/home/dana/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: 73 audio & 180 video codecs
font: can't open file: /home/dana/.mplayer/font/font.desc
Font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using Linux hardware RTC timing (1024Hz).
Can't open input config file /home/dana/.mplayer/input.conf: No such file or directory
Input config file /etc/mplayer/input.conf parsed: 53 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing Voting_Machine.wmv.
ASF file format detected.
VIDEO:  [MP43]  320x240  24bpp
Clip info:
 name:
 author:
 copyright:
 comments:
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, 16 bit (0x10), ratio: 8005->176400 (64.0 kbit)
Selected audio codec: [ffwmav2] afm:ffmpeg (DivX audio v2 (ffmpeg))
==========================================================================
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdivx] vfm:ffmpeg (FFmpeg DivX ;-) (MS MPEG-4 v3))
==========================================================================
Checking audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 44100 hz, little endian signed int
AF_pre: 44100Hz 2ch Signed 16-bit (Little-Endian)
AO: [oss] 44100Hz 2ch Signed 16-bit (Little-Endian) (2 bps)
Building audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
Starting playback...


MPlayer interrupted by signal 4 in module: play_audio
- MPlayer crashed by an 'Illegal Instruction'.
  It usually happens when you run it on a CPU different than the one it was
  compiled/optimized for.
  Verify this!
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

### Post by ups on 2005-02-14
Which package of mplayer did u install? (k7/k6 or 686)

Also, what CPU do u have (AMD Athlon or Intel Pentium III/IV) ?

---

### Post by piedamaro on 2005-02-14
I'm glad totem worked :)
But, why did you run mplayer as root? (with sudo)
The error message says that maybe you have installed a package for a different cpu, which is your processor? And wht mplayer package did you install? You should have installed the one from marillat repository, take a look here [http://ubuntuguide.org/](http://ubuntuguide.org/) under "How to install Multimedia Plug-in for Mozilla Firefox"

---

### Post by Dana on 2005-02-14
Sigh... I probably installed the wrong mplayer. Got it from [http://people.debian.org/~sgran/debian/](http://people.debian.org/~sgran/debian/). It was the newest version I could find. Guess I need to start over.

FWIW the laptop has a Pentium III so that is probably not the problem. As for using sudo, I never know for certain whether I need to use it. I'll run something from the command line and discover I needed to do sudo so I generally use it... of course sometimes that is wrong. I can't win. I'll add the marillat repository and try again. Of course totem is now working so maybe I'll just use it unless to gives me problems.

I haven't tried to set up any Firefox plugins yet, saving that for sometime when I don't need any sleep.  :grin: 

Thanks for the help.

Dana

---

### Post by Dana on 2005-02-15
I went ahead and added the marillat repositories but both the mplayer 386 and 686 packages show unresolvable dependencies. totem is "still" working so I presume the codecs installed by the first mplayer installation were not removed. Doesn't seem to be much point fighting with this at the moment. Maybe I'll have better luck with the next Ubuntu release.

Dana

---

### Post by ups on 2005-02-15
[QUOTE=Dana]Sigh... I probably installed the wrong mplayer. Got it from [http://people.debian.org/~sgran/debian/](http://people.debian.org/~sgran/debian/). It was the newest version I could find. Guess I need to start over.

FWIW the laptop has a Pentium III so that is probably not the problem. As for using sudo, I never know for certain whether I need to use it. I'll run something from the command line and discover I needed to do sudo so I generally use it... of course sometimes that is wrong. I can't win. I'll add the marillat repository and try again. Of course totem is now working so maybe I'll just use it unless to gives me problems.

I haven't tried to set up any Firefox plugins yet, saving that for sometime when I don't need any sleep.  :grin: 

Thanks for the help.

Dana[/QUOTE]
Since totem is working fine, you dont need to bother with mplayer ofcourse. Anyway, as for the sudo stuff, basically anything that does some change system-wide will need root privilages. So, installing a program needs sudo. But running a geenral program doesn't, so u dont have to run it using sudo.

If u need to change some config file (like ones under /etc), you'll need to do sudo. But modifying anything under your HOME (like /home/dana) doesnt need sudo).

Hope that clears it a bit. :D

---

### Post by Dana on 2005-02-15
Yes, the comments on using sudo are logical and helpful. I get most annoyed when I want to copy files somewhere only to discover I need root privileges to write to that particular directory. I understand why that is but it is a new way of working and it takes some adjustment.

Dana

---

### Post by ups on 2005-02-15
Yes, you might need a little time to get adjusted. Just remember if u want to write to anything outside your home, you'll need sudo. This is because you're expected to do everything within your home directory, and only write outside home when doing system setting changes & stuff.

---

### Post by piedamaro on 2005-02-15
You're welcome! Yes, stick with totem (I've always used totem too), I needed mplayer just for the firefox plugin, thus the link to the ubuntuguide. :)

---

### Post by Gtaylor on 2005-03-21
Has any progress been made on this thus far since the last post? Any possible ETA for a fixed package from the devs?

---

