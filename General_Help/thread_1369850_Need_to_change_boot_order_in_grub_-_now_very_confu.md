---
title: "Need to change boot order in grub - now very confused"
date: 2010-01-01
forum: General Help
---

### Post by Sticky on 2010-01-01
Hi

I share my computer with my wife and she keeps getting frustrated when she misses the choice of windoze on boot. I'm looking for a way to make it default to windoze so I select ubuntu from the list. I thought I'd found how to do it by editing grub.cfg after following instructions found online but apparently I can't edit this file (or rather I can't save the changes). Surely there must be a simple way to achieve this?

Can someone point me to a howto?

Many thanks

---

### Post by Revolutionary101 on 2010-01-01
You could install a program called Start Up Manager. It is a very useful program that lets you edit your GRUB menu. To install it enter this into terminal.

```
sudo apt-get install startupmanager
```

---

### Post by Leppie on 2010-01-01
open the grub defaults file with an editor:
```
gksudo gedit /etc/default/grub
```

change the line:
```
GRUB_DEFAULT=0
```
to something like:
```
GRUB_DEFAULT="Microsoft Windows XP"
```

You will need the exact menu entry name there, so you may want to check that like this:
```
$cat /boot/grub/grub.cfg | grep Windows
```

NOTE: Very often the first windows partition is a recovery partition.

Once modified and saved, regenerate the grub.cfg file:
```
$sudo update-grub
```

Now windows is the default selection.

---

### Post by Sticky on 2010-01-06
Thank you very much - that worked perfectly for me :D

---

