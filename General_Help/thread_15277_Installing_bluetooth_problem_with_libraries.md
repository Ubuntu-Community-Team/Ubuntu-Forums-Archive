---
title: "Installing bluetooth: problem with libraries"
date: 2005-02-13
forum: General Help
---

### Post by Syzygy on 2005-02-13
Hi there!. I am a newbie to Ubuntu and Linux in general and I'm trying to install gnome-bluetooth on my system. I have downloaded it from its official web page and have installed libbtctl first as it is indicated. The problem is that when I try to run ./configure I get an error message saying that there are some libraries missing: I have tried with synaptic but have found only some of the required ones, not all. The missing ones I can't find are gobject-2.0 and pygtk-2.2. Where can I find them?. Is there any way in Ubuntu to prevent so many problems with libraries when installing applications from source code? (something like a package with all the libraries needed...).

Thanks!

---

### Post by scoon on 2005-02-14
Hey there,

So what you are looking for are the dev (short for development) debs for whatever package you want.  For example, if you are tring to compile some source that require libbluetooth you would need to have the libbluetooth-dev installed.  


scoon

---

### Post by kamstrup on 2005-02-15
Good news for you Syzygy...

The [GNOME Bluetooth](http://www.usefulinc.com/software/gnome-bluetooth) project website has prepacked .deb's for you ready to install! Just scroll all the way to the bottom of the page... There's a link for the collection. You might consider clicking [here](http://debian.usefulinc.com/gnome/) also... :-)

For the GNOME Phone Manager you need libgsmme1c102. You'll find this in universe...

This stuff is working *perfectly* for me (and my Sony Ericsson T610)... Hope that it will for you too.

---

### Post by Syzygy on 2005-02-16
Great!. Thanks!. I've successfully installed it and now it's working almost perfectly with my SE z600. The only problem I've noticed is that the Properties tab of the Bluetooth Manager simply does not work, so I can't take a look at the settings of the program and devices (that's the very first thing I do after installing any piece of software!), and there's no possibility of pairing my phone with the computer (something very useful I did under Windows), but, apart from that, the file transfers work quite well.

Now I've finished with image scanning, mp3 playing and Bluetooth...time to install mplayer to watch video files! (I'll probably come back here crying in a couple of days with a stack of doubts :D).

---

### Post by Syzygy on 2005-02-16
Oh, yeah. For pairing I need Phone Manager, of course. I've just realized.

---

