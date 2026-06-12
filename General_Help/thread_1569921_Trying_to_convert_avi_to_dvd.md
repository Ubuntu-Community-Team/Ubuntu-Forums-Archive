---
title: "Trying to convert avi to dvd"
date: 2010-09-07
forum: General Help
---

### Post by smarmytime on 2010-09-07
Edit - I just realized I should have posted this in the multimedia forum. I tried to delete it, but did not find an option for that under edit.

Hi there - I'm trying to convert an avi file into an ISO that I can burn to DVD. I found a page that gave really good, step by step instructions, on this site:

[http://www.ubuntugeek.com/howto-convert-avi-to-dvd-iso-in-ubuntu.html](http://www.ubuntugeek.com/howto-convert-avi-to-dvd-iso-in-ubuntu.html)

But things did not go quite according to plan.

When I tried the first step, it said couldn't find any package whose name or description matched "lame-extras". 

I then got the following output, followed by all the installation stuff:


The following NEW packages will be installed:
  dvdauthor ffmpeg lame libavdevice52{a} libavfilter0{a} liblzo2-2{a} 
  libmp3lame0{a} libsvga1{a} libxvidcore4{a} mencoder mplayer{a} 
0 packages upgraded, 11 newly installed, 0 to remove and 2 not upgraded.

Undaunted, I plowed ahead (what's the worst that could happen?), and went through with the rest of the steps. Finally, I created the dir to do the conversion, cd'ed into it, and ran the script, as instructed, and got the following (the file that I was using was an episode of Entourage, just as a test, as it was the shortest avi file I had):


smarmy@smarmy-desktop:~$ cd Downloads/avi/
smarmy@smarmy-desktop:~/Downloads/avi$ ls
Entourage.S07E08.Sniff.Sniff.Gang.Bang.HDTV.XviD-FQM.avi
smarmy@smarmy-desktop:~/Downloads/avi$ avi2dvd Entourage.S07E08.Sniff.Sniff.Gang.Bang.HDTV.XviD-FQM.avi 
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
File not found: '“Entourage.S07E08.Sniff.Sniff.Gang.Bang.HDTV.XviD-FQM.avi”'
Failed to open “Entourage.S07E08.Sniff.Sniff.Gang.Bang.HDTV.XviD-FQM.avi”.
Cannot open file/device.

Exiting...
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
output.mpg: no such file or directory
rm: cannot remove `output.mpg': No such file or directory
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing output2.mpg...
ERR:  Error opening output2.mpg: No such file or directory
rm: cannot remove `output2.mpg': No such file or directory
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating table of contents
ERR:  No .IFO files to process
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
genisoimage: Can't open VMG info for 'dvd/'.
genisoimage: Unable to parse DVD-Video structures.
genisoimage: Could not find correct 'VIDEO_TS' directory.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
smarmy@smarmy-desktop:~/Downloads/avi$ 


I'm not sure what to make of the first error message, that the file couldn't be found...I didn't write the file name out by hand, I just hit E and tab, for the auto-complete. Beyond that, I'm wondering if not installing lame-extras was the problem.

So what's my next move? Find lame-extras somewhere else? Find another method? I'll be honest, I'm hoping to use this method - though I'm no command line ninja, I do love to do things from a script and the command line, but in the end, I just want to get this conversion done with, so if there's a better method, I'm certainly open to it.

Thanks for any help you guys can offer!

---

### Post by lambro on 2010-09-07
Well, I missed the most part of that, but to convert films, from any format, to any other format, do this:
Google: brothersoft avi to DVD
Then download that program, it was te easiest one I found, and it's completely free, a rarity in these types of programs.
They also do other conversions, eg. DVD to iPod, mp4 to DVD, etc etc, the list goes on

Hope it works for you :)

---

### Post by smarmytime on 2010-09-07
> **lambro said:**
> Well, I missed the most part of that, but to convert films, from any format, to any other format, do this:
Google: brothersoft avi to DVD
Then download that program, it was te easiest one I found, and it's completely free, a rarity in these types of programs.
They also do other conversions, eg. DVD to iPod, mp4 to DVD, etc etc, the list goes on

Hope it works for you :)

That seems to take me to a search engine for programs, I couldn't seem to find one that worked with linux. What's the exact name of the program you are using?

---

### Post by NigelD on 2010-09-07
The program you need is devede it can be found in the software centre under Sound & Video. This is the program I use and its really easy. Just use the defaults and it creates a ISO to be burnt to disc.:D

---

### Post by MooPi on 2010-09-07
You can break it down to individual steps first. Convert avi to mpg:
```
ffmpeg -i input.avi -target ntsc-dvd  -aspect 16:9 -b 3000k output.mpg
```-b = bitrate and you can adjust to desired rate this is important when your trying to fit a large avi onto 4.7 GB DVD
-aspect = aspect ratio and choices 4:3, 16:9,  other choices I believe are obsolete
-target can use pal-dvd or ntsc-dvd that all depends on where you live

```
dvdauthor -o DVD/ -t output.mpg
``````
dvdauthor -o DVD/ -T
``````
mkisofs -dvd-video -v -o DVD.iso DVD
```Your .iso should be ready to burn 
Or you can combine them for a complete script

---

### Post by smarmytime on 2010-09-07
> **NigelD said:**
> The program you need is devede it can be found in the software centre under Sound & Video. This is the program I use and its really easy. Just use the defaults and it creates a ISO to be burnt to disc.:D

That seems to have done the trick, thank you. Though if anyone could help me troubleshoot that shell script, I would like to get that figured out...

---

### Post by ron999 on 2010-09-07
@MooPi
I usually use tovid for this job.
But your method with dvdauthor and mkisofs seems more straightforward.:popcorn:

---

