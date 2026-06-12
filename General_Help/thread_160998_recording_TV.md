---
title: "recording TV"
date: 2006-04-16
forum: General Help
---

### Post by Vinger on 2006-04-16
Hello,

I'm searching a program to record my tv.
I installed TVTime, and that works fine.

MythTV is (i thought) such a program, but i wondered if there were any others...

tx

grz.

---

### Post by andlinux21 on 2006-04-16
here I think this should help you

Here are a few other PVR-related links suggested by other folks who visited this website. Note that none of them are directly related to my little project: 

Poor Man's PVR with GUI 
eBox 
VDR 
Freevo 
MythTV 
A list of TV cards (apparently now broken) 
Supported TV cards with module card numbers from SuSE 7.2 
The Mandrake Audio Workstation HowTo (not directly related, but it might be of interest) 
How to Turn a $2000 Computer into a $100 VCR if you want something similar using Windows 
PVR Hardware and Resources 
VPVision for Windows

---

### Post by Rog131 on 2006-04-16
I'm using mencoder (mplayer). [http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)

This (script) grabs 2 hours 720x576 mjpeg. Puts it in outfile.avi. Sound (pcm) from line in plug. More: man mencoder. Note ! I'm using composite: inputs: 0 = Television; 1 = Composite1; 2 = S-Video; 3 = Composite3;

mencoder tv:// -v -tv  driver=v4l:width=720:height=576:input=1:device=/dev/video0:immediatemode=0:alsa:adevice=hw.0,0:outfmt=yv12  -o /media/sata/sat1/Vcr/outfile.avi -af volume=10:0 -ovc lavc -lavcopts vcodec=mjpeg:aspect=4/3 -aspect 4:3 -oac pcm  -endpos 02:00:00

I put the start time in the kcron.

Picture on the screen:
mplayer -tv input=1:driver=v4l2:width=720:height=576 -vo xv tv://

(Same (almost) with gui - i haven't tried though !)
Kalva:
Kalva is a simple to use and easy to setup videorecorder for the K Desktop
Environment. It is using the console tool MEncoder from the MPlayer package
to do the real work.
[http://www.kde-apps.org/content/show.php?content=23381](http://www.kde-apps.org/content/show.php?content=23381)

More multimedia/video aplications for KDE
[http://www.kde-apps.org/index.php?xcontentmode=221](http://www.kde-apps.org/index.php?xcontentmode=221)

For cutting and packing (xvid) i use avidemux:
Avidemux 2.0.42 Breezy package (also Avidemux 2.1 Final)
[http://www.ubuntuforums.org/showthread.php?t=68832](http://www.ubuntuforums.org/showthread.php?t=68832)

---

### Post by Rog131 on 2006-04-16
Damn smileys 

Should be double colon and o not :o.

---

