---
title: "Vlc seg fault"
date: 2009-11-12
forum: General Help
---

### Post by FFGANDALF on 2009-11-12
when wathching video in VLC after upgrading to 9.10 I noticed that it would randomly quit. Running it in a terminal I get the following output:

VLC media player 1.0.2 Goldeneye
[0x88a4e88] main interface error: no interface module matched "globalhotkeys,none"
[0x88a4e88] main interface error: no suitable interface module
[0x8803140] main libvlc error: interface "globalhotkeys,none" initialization failed
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[***] Init
Fontconfig error: Cannot load config file "&#65533;&#65533;&#65533;"
[***] No usable fontconfig configuration file found, using fallback.
[0x8bf36e0] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[***] PlayResX undefined, setting to 1024
[***] Glyph bounding box too large: 542208x18px
Segmentation fault

Any ideas.

---

### Post by amcsi on 2009-11-29
Hello, I am having the same problem with very similar output. This only happens with mkv files, and I think it may have to do with the .*** subtitles.

I am using VLC 1.02 under Ubuntu 9.10. Someone please help.

---

### Post by Iztari on 2009-12-09
Hi,

I'm having the same problem and it does seem to be cause by the subtitles as I disabled them and vlc didn't crash.

---

### Post by john newbuntu on 2009-12-10
I read in this forum:
[http://ubuntuforums.org/showthread.php?t=1308235&page=2](http://ubuntuforums.org/showthread.php?t=1308235&page=2)
that you can get more verbose information if you start vlc from a terminal using the command:
```
vlc -vv
```Also, check that the output of:
ls -la /var/cache/fontconfig/
The files in this directory needs to be owned by root and should have permissions like:
-rw-r--r--

Also make sure that 
ls -la $HOME/.fontconfig
is similar to the above permission but is owned by you.

Oh, you might also want to install the "ubuntu-restricted-extras" package from synaptic package manager.
[apt:ubuntu-restricted-extras?section=universe?section=multiverse](apt:ubuntu-restricted-extras?section=universe?section=multiverse)

---

### Post by tobiasly on 2010-02-09
Getting very similar error, whether I try to open network stream (my wifi webcam) or a local .avi.

Tried logging in as a different user, and didn't get the segfault. So it's something about my user setup, but what?

Tried deleting ~/.config/vlc and ~/.fontconfig. Tried turning off visual effects (compiz). Still getting the segfault.

This worked fine a couple weeks ago so it's either a package I updated/installed or some setting I changed since then. Very frutstrating!

Following is the output. When starting "vlc -v" as the other user (the one that doesn't crash), I get the same 2 warnings, so don't think those are relevant.

```
$ vlc -v http://my/camera/stream
VLC media player 1.0.2 Goldeneye
[0x2636618] main demux warning: no access_demux module matching "file" could be loaded
[0x2537888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x26503e8] access_http access warning: unimplemented query in control
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102

```

---

