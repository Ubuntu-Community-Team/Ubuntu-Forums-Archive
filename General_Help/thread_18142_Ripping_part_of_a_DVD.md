---
title: "Ripping part of a DVD"
date: 2005-03-04
forum: General Help
---

### Post by LordCantenberry on 2005-03-04
I desire to rip about a five minute segment of video from a dvd I own for use in a presentation I have to give.  I need however a program that can do this, instead of just ripping the entire DVD.  

Any help would be appreciated.

---

### Post by p!=f on 2005-03-04
How about this package?
```

[~] > wajig show dvdrip
Package: dvdrip
Priority: optional
Section: multiverse/graphics
Installed-Size: 1640
Maintainer: Christian Marillat <marillat@debian.org>
Architecture: i386
Source: video-dvdrip
Version: 1:0.52.2-0.0
Depends: perl (>= 5.6.0-16), transcode (>= 2:0.6.14), perl-modules (>= 5.8.1-1) | libstorable-perl, libgtk-perl, libgtk-pixbuf-perl, imagemagick, fping, libevent-perl, liblocale-gettext-perl, libintl-perl
Recommends: xine-ui, subtitleripper, dvdrip-doc
Suggests: mjpegtools, ogmtools (>= 0.972), cdrdao, mkisofs, cdrecord, vcdimager, mplayer, rar-2.80
Conflicts: video-dvdrip (<= 0.50.18-0.0)
Filename: pool/multiverse/v/video-dvdrip/dvdrip_0.52.2-0.0_i386.deb
Size: 360978
MD5sum: eea987963f411ba605653d886a44e92e
Description: perl front end for transcode
 dvd::rip is a full featured DVD copy program written in Perl. It provides
 an easy to use but feature-rich Gtk+ GUI to control almost all aspects of
 the ripping and transcoding process. It uses the widely known video
 processing swissknife transcode and many other Open Source tools.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```
You must have multiverse repositories enabled in /etc/apt/sources.list

---

### Post by Ste on 2005-03-05
[QUOTE=LordCantenberry]I desire to rip about a five minute segment of video from a dvd I own for use in a presentation I have to give.  I need however a program that can do this, instead of just ripping the entire DVD.  

Any help would be appreciated.[/QUOTE]
 If dvdrip won't work because of transcode (it has been known to happen) try acidrip. gui for mencoder from the mplayer package. I prefer it over dvdrip.

---

### Post by psypher on 2005-03-06
Does anyone know HOW to get DVDRIP installed?? I need it for the batch and cluster funtions. I have tried everything on this thread: [http://www.ubuntuforums.org/showthread.php?t=548&highlight=dvdrip](http://www.ubuntuforums.org/showthread.php?t=548&highlight=dvdrip) the so called dvdrip howto but nothing as you can see from my frantic posts. Everybody claims to have gotten it to work (as one person said: muy easily) but only post half complete instuctions or incorrect ones. Not even experts can make sense. if you have any info please post it at that thread. would greatly appreciate it.  pls step by step, what repositories are activated and what are deactivated and what ACTUALLY works! I am not a linux newbie but whatever everybody is saying does not work.

thanks

---

### Post by MetalMusicAddict on 2005-03-06
[QUOTE=LordCantenberry]I desire to rip about a five minute segment of video from a dvd I own for use in a presentation I have to give.  I need however a program that can do this, instead of just ripping the entire DVD.  

Any help would be appreciated.[/QUOTE]
Honestly man I think the best app for this is [DVD Decrypter](http://www.dvddecrypter.com/).

---

