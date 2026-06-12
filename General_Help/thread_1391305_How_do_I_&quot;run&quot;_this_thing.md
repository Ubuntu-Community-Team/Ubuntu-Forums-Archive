---
title: "How do I &quot;run&quot; this thing???"
date: 2010-01-26
forum: General Help
---

### Post by Acradon on 2010-01-26
Hello there, 

I am trying to get my iPod connected to Rhythmbox and found out what I have to do so that the iPod actually shows the songs after syncing....darn Apple Corp and their security features. Anyhow, some smart people have found an answer which can be found here:

[http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=README.SysInfo;hb=HEAD](http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=README.SysInfo;hb=HEAD)

So I have the necessary programs installed (they were all already installed when checking Synaptic) Hal, libgpod and libsgutils. But HOW on earth am I supposed to "run" configure/autogen.sh??? Not in the terminal apparently, cos that just says that the directory or file was not found. I understand that there are autogen.sh files for many programs, so how do I run the one that I need? I am not completely inept, but when it comes to compiling, programming etc. I really have no idea. I checked the compiling software from ubuntu community and installed the automake and checkinstall programms/files or whatever they are. But what now?

HELP PLEASE!!!!! I am about to get a brainbubble and whither up and die in front of this thing. But I would like to go with music.....

Acradon

---

### Post by SuperSonic4 on 2010-01-26
Doesn't repo gtkpod work? ```
sudo apt-get install gtkpod
```

If you're compiling from source ensure you're in the right directory. If, for example you downloaded to the desktop in a folder called gtkpod

```
cd ~/Desktop/gtkpod/configure
./autogen
```

---

### Post by Acradon on 2010-01-26
I had problems with gtkpod before. It deleted random songs from my iPod and shuffled everything up badly. Plus I kinda grew attached to Rhythmbox and have over 14000 songs on there by now.

I don;t understand this compiling stuff. First I thoght this is a kind of install thing, now I don't know. What do I have to do after I installed the programs (which they are) what's this compiling from source. This is my problem. I guess I am a layman trying to do pro stuff.

---

### Post by hhlp on 2010-01-26
maybe this little guide can help you:

[http://www.howtoforge.com/linux_rhythmbox_ipod]("http://www.howtoforge.com/linux_rhythmbox_ipod")

---

### Post by Acradon on 2010-01-26
This does not work. I understand that Apple incorporated a new thing to prevent people using 3rd party software. That is my problem. My IPod syncs OK, but then it says that there is no music on it. Although there is. It clearly shows up when connected to the computer. My old iPod works perfectly. The new one has this problem. 

So I am trying to get it to get the firewire ID and therefore I need to do these steps...but I simply don't know what I am supposed to type into where

---

