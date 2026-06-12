---
title: "Ext TV tuner &amp; another capture card wont work in Lucid"
date: 2010-05-01
forum: General Help
---

### Post by inameiname on 2010-05-01
Upon a fresh and clean installation of Ubuntu Lucid, I noticed neither of my two cards to hook up analog or digital work. They are simply not even found. One is a digital/analog usb tv tuner, which worked just fine in Karmic and Jaunty, and the other is a TV capture PCI card, which worked fine too. 

I read TVtime, which I use for cable channels, is already screwy due to the bad version in the Lucid repos, but simply by downloading and updating it with the latest Debian repos one, it works fine...anyway, so that doesn't seem to be the issue, unlike usual. Actually, SMPlayer, Gnome-Mplayer, nor TVtime even senses either card. 

I'm curious if anybody has any TV capture/tuner cards working with Lucid yet.

Any help would be grande. :)

---

### Post by oldos2er on 2010-05-01
My Hauppauge WinTV-PVR USB2 seems to work fine with 10.04, fwiw.

---

### Post by jimmers on 2010-05-01
My AVerMedia Volar A815 works flawlessly in Lucid

---

### Post by inameiname on 2010-05-02
Thanks for the input. Guess it's either mine (a ATI TV Wonder 600 USB Tuner) or perhaps some glitch that's keeping it from getting recognized.

---

### Post by inameiname on 2010-05-02
I found the problem and solution. It's the v4l-dvb drivers that weren't installed correctly with the tar file. And to anybody that has a similar problem, do the following:

In the 'v4l' folder, open the .config file in the 'v4l' subfolder (created only after you 'make' it first),
find the line:

CONFIG_DVB_FIREDTV=m

and change it to

CONFIG_DVB_FIREDTV=n

and then 'make' (again) and 'sudo make install'

and then when finished, restart.

---

### Post by jimmers on 2010-05-02
Glad you got it sorted

---

