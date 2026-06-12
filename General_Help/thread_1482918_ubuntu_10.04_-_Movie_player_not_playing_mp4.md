---
title: "ubuntu 10.04 - Movie player not playing mp4"
date: 2010-05-14
forum: General Help
---

### Post by SyAu on 2010-05-14
Movie Player in ubuntu 10.04 is not playing mp4 files. How to fix this?

---

### Post by Grenage on 2010-05-14
It's possible that the codecs are included in the restricted extras package:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SyAu on 2010-05-14
Sorry it didn't work

---

### Post by parn on 2010-05-14
have you installed gstramer ugly and bad plugins?

sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly

---

### Post by Grenage on 2010-05-14
I only use mplayer for my movies, but VLC is also highly rated.  Both come with codecs in-built:

```
apt-get install mplayer-gui
```

OR

```
apt-get install vlc
```

---

### Post by SyAu on 2010-05-14
> **Grenage said:**
> I only use mplayer for my movies, but VLC is also highly rated.  Both come with codecs in-built:

```
apt-get install mplayer-gui
```OR

```
apt-get install vlc
```


Thanks. I installed VLC and could play mp4 files.

---

### Post by Lyo.g on 2011-03-14
Hi there

I'm experiencing the same problem, unable to read mp4 files, and am running out of ideas..
When attempting to play a mp4, the player (movie player) requests to  install a plugin (gstreamer0.10-plugins-bad), but after trying to  install it an error message pops up saying 'Could not apply changes, fix  broken packages first'.

I've ran a search on the hard drive and could not find a file of the  same name, I've tried running the code mentioned above in this post: 

```
sudo apt-get install ubuntu-restricted-extras
```

Have tried removing/reinstalling the codec library (GStreamer ffmpeg video plug in)
And I have tried installing vlc through the software center --> error message:Package dependencies cannot be resolved, etc
..and using code in terminal :

```
leo@leo-laptop:~$ apt-get install vlc
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
leo@leo-laptop:~$
```

So, yeah, I'm running out of ideas, and more questions come out of those  attempts.. (I'm the only user of this computer, how can I not have  restricted access?)

I would love some help on this one, I'm new to ubuntu and I'm finding it uneasy to break through..

Thanks

L

---

### Post by post4pavan on 2011-11-01
You forgot to add sudo

sudo allows you to install softwares as a "root"

Regards

---

