---
title: "Removing Linux (Not ALL Of It)"
date: 2010-12-15
forum: General Help
---

### Post by RobNJ on 2010-12-15
Hello!
I have a dual boot (tri boot?) computer at the moment. It has Windows, Ubuntu & a third Linux distro, that is giving me grief. Can I remove the third distro, without having to do ANOTHER clean install of Windows & Ubuntu?

---

### Post by Quackers on 2010-12-15
From within Ubuntu you can use Gparted (if it's not installed in your system it can be installed via Synaptic package manager).

Right-click on your swap partiton and select swapoff.
Then delete the partition(s) which refer to the other Linux distro.
Then right-click on swap partition and select swapon, then quit gparted.

Open up a terminal and run
```
sudo update-grub
```
and you should be good :-)

---

### Post by ninjaaron on 2010-12-15
Don't you have to run GParted from the live CD/USB... cause it can't work on mounted drives or something...

So has been my experience, at least.

---

### Post by Quackers on 2010-12-15
If the OP is booted into Ubuntu and turns swap off, the "other Linux distro" partitions are not mounted.

---

### Post by ninjaaron on 2010-12-15
Ah... must have been the swap that was my downfall.:p

... course, if he wanted to, say, resize his Ubuntu partition to fill that freed up space, would he then need the live media?

---

### Post by Quackers on 2010-12-15
> **ninjaaron said:**
> Ah... must have been the swap that was my downfall.:p

... course, if he wanted to, say, resize his Ubuntu partition to fill that freed up space, would he then need the live media?

Yes, definitely, in that case.

---

