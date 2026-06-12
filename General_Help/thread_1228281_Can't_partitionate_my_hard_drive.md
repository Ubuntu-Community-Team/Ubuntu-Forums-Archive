---
title: "Can't partitionate my hard drive"
date: 2009-07-31
forum: General Help
---

### Post by drymedar on 2009-07-31
So, I'm running Ubuntu 9.04 and was thinking "Hmm, maybe I should create a partition on my other hard drive and install Windows so I can do some gaming", so I looked up a guide how to create a partition using GParted and at the first step things went bad. I can't press "Change size/move", it's all grayed out. The only things I can press are "Demount", "Handle flags" and "Information". 

Here are screenshots of both my hard drives in GParted: 
[IMG]http://data.fuskbugg.se/skalman01/250.jpg[/IMG][IMG]http://data.fuskbugg.se/skalman01/500.jpg[/IMG]
As you can see on the 500GB drive (or "Extra" as I've named it), it says "boot" under flags. In one way it makes sense and in another it doesn't, I installed Ubuntu on my 250GB drive, but the 500GB drive does indeed have priority in my BIOS and when I tried to change the priority to the 250GB drive I couldn't boot anymore (which I thought was strange since I had indeed installed Ubuntu on my 250GB drive).

There's also these keys next to the drives which I guess means they're locked.

So, what should I do? Is there any hope for me to create a partition to install Windows on?

---

### Post by pastalavista on 2009-07-31
You can't make changes to a mounted drive. That is why it is greyed out and the key symbol is there. It is best to use a live CD version of Gparted (it's on the Ubuntu live CD) because you can't unmount a drive that is in use. When you run a live CD gparted, you'll be able to right-click the partition and select 'unmount' and then be able to resize, shrink or even delete and/or reformat... so be careful.

---

### Post by merlinus on 2009-07-31
You cannot unmount the partition you are working on, in this case sda1.

Use gparted live instead:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by drymedar on 2009-07-31
Thanks for the tip, GParted on the live-cd it is!

---

