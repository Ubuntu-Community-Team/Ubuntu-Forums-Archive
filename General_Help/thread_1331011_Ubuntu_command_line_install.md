---
title: "Ubuntu command line install?"
date: 2009-11-18
forum: General Help
---

### Post by doixanh on 2009-11-18
Is there anybody trying to install command line ubuntu with wubi? I mean, without GNOME, or ubuntu-desktop, etc...

I just want to have a minimal ubuntu with wubi, but no luck. I tried to install wubi with karmic desktop CD, modify preseed.cfg file before restarting windows, but tons of gnome stuffs are still installed.

Any suggestion is appreciated.

---

### Post by fluffman86 on 2009-11-18
I don't think that's really the point of wubi.  Wubi is really designed to let people try ubuntu before going to a full install.  So if you already know you want Ubuntu, why not just go with a full install?

That being said, I'm sure we can figure something out.  First, download wubi from wubi-installer.org/ and run it.  Then, you probably want to download the server edition of Karmic, or possibly Ubuntu Minimal.  I would probably go with the server.  Finally, point wubi to your server iso, and see what happens! :)

---

### Post by doixanh on 2009-11-18
From the wubi FAQ
> 
Yes, physical CDs will be detected automatically, pre-downloaded ISOs should be placed in the same folder as Wubi.exe. Please note tha Wubi 8.10 requires the Desktop 8.10 CD/ISO. The DVD and Altrenate CD/ISO will not work. You can find the 8.10 ISO [here]("http://releases.ubuntu.com/8.10/"). If Wubi does not find an appropriate ISO/CD and/or if the ISO/CD is corrupted, it will automatically download a new ISO. It is recommended to let Wubi download the ISO for you.I think wubi accepts desktop cd only ~.~

Anyway, will try. Thanks for your suggestion.

/edit : I tried putting the server iso in the same place with wubi, but it doesn't accept the iso and automatically downloads the desktop iso.

Kinda stuck...

---

### Post by lavinog on 2009-11-19
> **doixanh said:**
> Is there anybody trying to install command line ubuntu with wubi? I mean, without GNOME, or ubuntu-desktop, etc...

I just want to have a minimal ubuntu with wubi, but no luck. I tried to install wubi with karmic desktop CD, modify preseed.cfg file before restarting windows, but tons of gnome stuffs are still installed.

Any suggestion is appreciated.

What is your goal?

---

### Post by doixanh on 2009-11-19
> **lavinog said:**
> What is your goal?

My goal is to have a minimal but working command line ubuntu with wubi.

I'm studying shell programming and my hard drive doesn't have much space left. I also got some problems with resizing partitions so I'm trying to avoid doing so.

Those're the reasons I don't like full ubuntu with gnome installation under wubi.

Any help please?

---

### Post by marshag63 on 2009-11-19
You could try minimal install in a virtual machine.

You could also try INX in a virtual machine (INX = Is Not X) a command line version based on Ubuntu - you can download the VM version, or you could put it on a jump drive and run it with persistence.

INX main page:
[http://inx.maincontent.net/index.html](http://inx.maincontent.net/index.html)

Virtual Machine INX:
[http://inx.maincontent.net/download.html](http://inx.maincontent.net/download.html)

Good Luck and Welcome to Linux

MarshaG.

---

### Post by lavinog on 2009-11-20
If you are just wanting to study shell programing you could install cygwin in windows. it should take up no more than 100mb and doesn't require rebooting.
VM would be another option...at least much better than wubi.

---

### Post by doixanh on 2009-11-20
Thanks for the suggestions. I will try Cygwin.

But i'm still wondering if there is any way to install only ubuntu-minimal within wubi or not :D

---

### Post by lavinog on 2009-11-20
I really don't think so.

---

### Post by Vock on 2009-11-21
Is there anyway to install a minimal 9.10 without wubi? I can't seem to find it...

---

### Post by oldos2er on 2009-11-21
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

