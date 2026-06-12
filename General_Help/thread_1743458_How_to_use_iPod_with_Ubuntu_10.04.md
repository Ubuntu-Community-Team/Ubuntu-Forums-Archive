---
title: "How to use iPod with Ubuntu 10.04?"
date: 2011-04-29
forum: General Help
---

### Post by Ertai87 on 2011-04-29
Hi all!  I used Ubuntu way back in the 6.X days, then quit for a while, and now I'm back, and boy have things changed!

Anyway, I'm trying to get my parents to use Ubuntu, since Windoze runs super-slow (and my mom is a "download everything on the Internet and I won't get viruses, right?" type), and one of my concerns is getting my mom's iPod to work properly under Ubuntu.

Now, I know that there is no iTunes for *Nix (tragic but unfortunately true), so I'm trying to use a Ubuntu-native program to do this (of course, if anyone knows how to make iTunes work, that would probably be optimal, but until that...).  I've tried using Amarok and gtkpod, and run into a couple of problems.  If anyone can help me out, that would be fantastic.

1) I read various guides for using Amarok (including [this one](http://amarok.kde.org/wiki/Media_Device:IPod), [this one](http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/), and [this one](http://www.howtogeek.com/howto/4791/how-to-use-amarok-to-manage-your-ipod/)), and I get to the point at which you go Settings -> Configure Amarok.  I am told there should be a "Media Devices" item on the list on the left, and it is simply not there.  What's the deal?

2) I tried using gtkpod, and while it seemed to work a bit, I tried using the "Copy files from iPod to music library" feature, and it segfaulted in the middle.  I'm not entirely confident using programs that are prone to segfaults, and I was wondering if anyone can shed some light.

My mom's iPod is a 3rd gen iPod Nano 8GB Silver (with video).  My OS is Ubuntu 10.04 LTS.  My Amarok version is 2.3.0.  My gtkpod version is 0.99.14.

Thanks.

---

### Post by hwttdz on 2011-04-29
Personally I'm fond of rhythmbox, which is pretty nearly an itunes clone.  I think there's a box to check under plugins for one sort of device or another.

---

### Post by darthchaosofrspw on 2011-04-29
My iPod Touch 4G works perfectly in Rhythmbox on Ubuntu 11.04.

---

### Post by Ertai87 on 2011-04-29
Fantastic.  Rhythmbox seems to work better than both Amarok and gtkpod.  I don't know why the Ubuntu devs recommend Amarok [here](https://help.ubuntu.com/community/PortableDevices/iPod).

On a related note, I know gtkpod can pull songs off my iPod onto my computer.  This functionality would save me a TON of time trying to re-add all the CDs to my computer.  If not I guess that's OK...

Additionally, as part of the process of installing Amarok, I was instructed to set the default program for iPod to Amarok.  Since Amarok appears to not be as good as Rhythmbox, how can I reset the default application?

---

### Post by chattanoga on 2011-04-29
What IOS version are you guys using?

I unfortunately upgraded to 4.2.1, and now Ubuntu does not recognize my iPod.

---

### Post by Ertai87 on 2011-04-29
I'm using an iPod Nano, not Touch.

---

### Post by netwerkingnut on 2011-04-29
I'm using Ubuntu 10.04 LTS and an iPOD Shuffle 1st gen and Rythmbox 0.12.8, but I cannot get it to mount. Any clues?

---

### Post by __Ryan__ on 2011-04-30
I had similar problems and managed to find a solution. The shuffle is a pain to get working sometimes. I did a writeup of all the steps here. 

[wiredrevolution.com/guides/sync-your-ipod-shuffle-with-linux]("http://www.wiredrevolution.com/guides/sync-your-ipod-shuffle-with-linux")

Good Luck!

---

