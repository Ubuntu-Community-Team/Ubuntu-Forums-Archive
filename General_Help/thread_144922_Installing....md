---
title: "Installing..."
date: 2006-03-15
forum: General Help
---

### Post by baysl on 2006-03-15
Can anybody please tell how do I install applications?
I know how to install *.deb (does anybody know http of archive of *.deb files?)

How do I install *.rpm?
How to install *.tar.gz?

---

### Post by SpEcIeS on 2006-03-15
Very large question..  for now just use synaptic package manager.

---

### Post by Ramses de Norre on 2006-03-15
.rpm: sudo apt-get install alien to install alien, then sudo alien -i *.rpm

.tar.gz: tar -xvzf *.tar.gz and then it depends on what's in the archive..

---

### Post by baysl on 2006-03-15
I just want to listen to mp3 and play avi files...

does anybody have link to download .deb file...
i dont know how to install anything...
please please

---

### Post by baysl on 2006-03-15
Or lets do it this way:
Can you please tell me exactly how do I install a mp3 player for linux, anyone you choose. Tell me where to download it ....
please im desparate and i'm loosing my mind.

---

### Post by Ramses de Norre on 2006-03-15
I can advice amaroK for mp3, works very good for me even under gnome.
Try xine-ui or mplayer-i386 for video.
All are in the repo's.
(sudo apt-get install package_name)

For all the codecs: [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by Perfect Storm on 2006-03-15
I'll recommend Beep-media-player (bmp) for mp3 playing, it's avaible in the universe if you enable it in your sourcelist.

---

### Post by baysl on 2006-03-15
I was trying to install:


rok@Linux:~$ sudo dpkg -i xmms-xmmplayer_0.3.3-1_i386.deb

Selecting previously deselected package xmms-xmmplayer.
(Reading database ... 66775 files and directories currently installed.)
Unpacking xmms-xmmplayer (from xmms-xmmplayer_0.3.3-1_i386.deb) ...
dpkg: dependency problems prevent configuration of xmms-xmmplayer:
 xmms-xmmplayer depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 xmms-xmmplayer depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
 xmms-xmmplayer depends on mplayer; however:
  Package mplayer is not installed.
dpkg: error processing xmms-xmmplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xmms-xmmplayer

What do i do now????????????

---

### Post by Ramses de Norre on 2006-03-15
Guess you'll need to install mplayer first. But if I were you I'd use apt.
Installing from downloaded .deb's doesn't always work as well as the .deb's in the repo's.

---

### Post by baysl on 2006-03-15
Can you tell me a program on sourcelist, that plays divx movies.
I installed beep-media-player and now i can listen to mp3...
And about apt... what is that, i tottaly clueless...

---

### Post by noswal on 2006-03-15
As someone also new I would take what SpEcIeS says above and use synaptic package manager, you just open it up and search for mp3 player and it gives a whole bunch of programs with descriptions to choose from.

my 2 cents

---

### Post by baysl on 2006-03-15
I try to install software from Synaptic and it writes this:

xmp-xmms:
 Odvisen od: libglib1.2 (>=1.2.0) but it is not installable
 Odvisen od: libgtk1.2 (>=1.2.10-4) but it is not installable
 Odvisen od: xmms  but it is not installable

what to do?

---

### Post by Ramses de Norre on 2006-03-15
Does "sudo apt-get -f install" help?

---

### Post by baysl on 2006-03-15
No still doesnt work.
Looks like something is missing.

dpkg: dependency problems prevent configuration of xmms-xmmplayer:
 xmms-xmmplayer depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 xmms-xmmplayer depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed

Always when i try to install something is missing......

---

### Post by cjazz on 2006-03-15
Please open a terminal and type

```
cat /etc/apt/sources.list
```

and post the results.

---

