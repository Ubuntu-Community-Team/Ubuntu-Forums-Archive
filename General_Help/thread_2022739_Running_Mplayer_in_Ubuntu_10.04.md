---
title: "Running Mplayer in Ubuntu 10.04"
date: 2012-07-11
forum: General Help
---

### Post by linux_dream on 2012-07-11
Hi guys,
I've just installed Mplayer following [http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html). In other words I typed ```
sudo apt-get update
``` and then sudo ```
apt-get install mplayer
```. The installation went well. The next step should be to go to application then Video and Sound and I should find "Mplayer" there, however it does not appear.
My question is... how do I run MPlayer?

---

### Post by papibe on 2012-07-11
Hi linux_dream.

'mplayer' is command line application, so it won't appear on the dashboard searches. In that sense it is like 'ls' or 'cp'.

I see a couple of options to make it easy:
[LIST=1]
[*]Install SMplayer, which is just a nice GUI that uses mplayer underneath. This will appear on the searches, or
[*]Call mplayer as a command line application by pressing Alt+F2.
[/LIST]
I hope that helps, and tell us how it goes.
Regards.

---

### Post by ajgreeny on 2012-07-11
Install **mplayer-gui** and mplayer will appear in your menus.  The command for that mplayer with gui is actually **gmplayer**, but don't worry about that.

---

### Post by SeijiSensei on 2012-07-11
> **papibe said:**
> Install SMplayer, which is just a nice GUI that uses mplayer underneath. This will appear on the searches

+1000 for SMPlayer

---

### Post by tumutanzi.com on 2012-07-11
install the front UI smplayer, then you will see it and use it.

---

### Post by andrew.46 on 2012-07-12
If you run into limits with MPlayer as packaged by others you might consider compiling your own copy. This is the preferred model of the MPlayer developers....

---

### Post by SeijiSensei on 2012-07-12
These days I prefer compiling [mplayer2]("http://www.mplayer2.org/").  I thought you did, too, Andrew.  Having just done so recently using their git repository, it's pretty straightforward.

---

### Post by asmoore82 on 2012-07-12
+1000 for mplayer command line only :P

Did you know that when the take an American film (@24 FPS) to show in European standards (@25 FPS) they simply speed it up? This makes the movie's running time shorter and shifts the pitch of all sounds slightly higher.

mplayer to the rescue!

```
mplayer -speed 0.96 some_euro_edition.avi
```

---

### Post by SeijiSensei on 2012-07-12
You can pass any command-line options you want to mplayer from within smplayer via Options > Preferences > Advanced > Options for MPlayer. 

I use mplayer from the command-line sometimes, too, but I prefer having an easy interface for things like screenshots, changing audio and subtitle tracks, managing playlists, rescaling the video, etc.  All of which are simple to do on-the-fly with smplayer.  I know there are keystroke options for some of these, but who can remember them all.

---

### Post by andrew.46 on 2012-07-13
> **SeijiSensei said:**
> These days I prefer compiling [mplayer2]("http://www.mplayer2.org/").  I thought you did, too, Andrew.  

Not me, I am sticking to the original :).

---

### Post by ajgreeny on 2012-07-15
The main problem I found with mplayer2 was that the video was set to vdpau which will not work on any of my machines.  I have to change that to xv and all is great again.

---

