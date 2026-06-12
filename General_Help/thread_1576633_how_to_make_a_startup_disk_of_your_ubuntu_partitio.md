---
title: "how to make a startup disk of your ubuntu partition?"
date: 2010-09-17
forum: General Help
---

### Post by aala on 2010-09-17
Hi Everyone, I was wondering if anyone can help me with this. I would like to put my ubuntu system (the one on my partition) in a usb drive, so that way I can take it everywhere I go. The reason for this is because all of the programs I have and the configuration I currently have in my ubuntu (I should say "macbuntu"). That is:


[LIST]
[*][I]burg boot loader (I probably don't need this one!)
[/I]
[*][I]x system plymouth theme || also windows 7 original plymouth theme
[/I]
[*]*mac4lin 1.0 aqua GTK theme and emerald theme*
[*]*mac ultimate icon theme*
[*]*mac4lin 1.0 cursor theme (working even with compiz)*
[*]*gnome global menu*
[*]*compiz packagers ppawith all the extra stuff*
[*]*telepathy ppa for empathy, having all the extra stuff working*
[*]*also win2-7-pack_v-9.1*
[/LIST]
And lots more stuff!

I don't want my personal documents though (text docs, music, videos, pics 'maybe few pics'), just configuration files and programs. [B]Can this even be possible?...

Thank you all for your help!
[/B]

---

### Post by C.S.Cameron on 2010-09-17
How big is your Ubuntu partition?
I have cloned a hard drive to a flash drive using dd:

```
sudo dd if=/dev/sda of=/dev/sdb
```

The target drive must be larger than the drive you are cloning, you might have to shrink the Ubuntu partition using gparted.
You can not clone the drive you are booting from, booting from a Live CD works.

Clonezilla might also work, dd is very powerful and can screw things up if not used correctly.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Alternatively, Remastersys might be what you are looking for:

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by aala on 2010-09-21
thanks C.S.Cameron!...

RemasterSys did the trick!

---

