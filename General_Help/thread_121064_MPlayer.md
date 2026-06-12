---
title: "MPlayer"
date: 2006-01-24
forum: General Help
---

### Post by jerris86 on 2006-01-24
I installed Mplayer through Synaptic but i cannot seem to get the video playing in full screen. I double clicked the screen the it got maximise but the actual video playin area is still the same. Anybody has any idea on what can be happening?

---

### Post by jazzgossen on 2006-01-24
Just wanted to add that it's the same for me.

With xine I do get fullscreen. I think xine seems to be a better video player anyway, although a bit more ugly...

---

### Post by sunny_nwho on 2006-01-24
try changing ur display type in the preferences...i had the same problem but later i changed my display to Xv/X11 and it is working well

---

### Post by ajgreeny on 2006-01-24
Backup your mplayer.conf
(sudo cp etc/mplayer/mplayer.conf etc/mplayer/mplayer.backup)
Then open it as root.
(sudo gedit /etc/mplayer/mplayer.conf)
Find the section zoom=no and change it to zoom=yes and then save it.
You should then find that mplayer will go full screen properly.

---

### Post by jerris86 on 2006-01-24
I tried that and Mplayer refuses to start

---

### Post by njzillest on 2006-01-24
also you can try using XINE its alot easier, and you can download it through synaptic or automatix. Automatix allows you to install the codecs along with Xine.

---

### Post by Khanater on 2006-02-02
Here is the solution! Thats works for my

[http://ubuntuforums.org/showthread.php?t=122918&highlight=mplayer+fullscreen](http://ubuntuforums.org/showthread.php?t=122918&highlight=mplayer+fullscreen)

---

### Post by hw-tph on 2006-02-02
[QUOTE=ajgreeny]Backup your mplayer.conf
(sudo cp etc/mplayer/mplayer.conf etc/mplayer/mplayer.backup)
Then open it as root.
(sudo gedit /etc/mplayer/mplayer.conf)
Find the section zoom=no and change it to zoom=yes and then save it.
You should then find that mplayer will go full screen properly.[/QUOTE]

I don't see much use in editing the global configuration file. Sure, it will change it for everyone using the computer but preferences should be set per user, right? So edit ~/.mplayer/config instead.

I must also say that current Mplayer CVS releases are incredibly good. I like the new GTK2 GUI (about time, some might say) and above all - you can actually play the inline WMA audio from NHL.com to listen to live games. :D


Håkan

---

### Post by Khanater on 2006-02-04
[QUOTE=hw-tph]I must also say that current Mplayer CVS releases are incredibly good. I like the new GTK2 GUI (about time, some might say) and above all - you can actually play the inline WMA audio from NHL.com to listen to live games. :D

Håkan[/QUOTE]

GTK2 GUI Interface? where can download that? Thanks in advance!

---

### Post by henok on 2006-02-04
I can't get mplayer to download:

sudo apt-get install mplayer

gives...

Reading package l ists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate

Can anyone help?

---

