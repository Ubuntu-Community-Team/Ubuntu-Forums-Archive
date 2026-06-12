---
title: "Installation MBR/GRUB Questions"
date: 2010-10-18
forum: General Help
---

### Post by dtkr on 2010-10-18
Hi All:

I've got a little question regarding GRUB and the MBR which I haven't wrapped my head around quite yet. 

Recently, my friend grabbed a copy of 10.10 from the net and while trying to install it, gave me some question which I am not too sure of. He has a Windows 7 dual boot with Mint (Linux) currently and he wants to install over Mint. 

So the Questions are:

1. Which Installation Option to Choose? The Basic or the one from GParted?

I originally recommended the basic, but then I was a bit worried about the second question... which is - 

2. When installing Ubuntu, does a new MBR get written? Or is GRUB written to the MBR? Will there be conflicting versions of GRUB? Will Mint be wiped properly, including GRUB and replaced?


Thanks for your help,
Darren 

P.S. I've attached a pic with his partition scheme. Hope that helps. Thanks!

---

### Post by zazuzimbo on 2010-10-18
If GRUB is already what manages his boot options, I am pretty sure the right thing should be done. I would not worry.

To guarantee that he is able to boot windows, whatever happens to the other partitions, copy the file /boot/grub/menu.lst to somewhere SAFE. If installation fails, he will know how to boot windows (this is a rext file that can be read with ease anywhere).

But be sure about installing over the right partitions, so the windows doesn't get lost. That is, choosing for the root partition the partition that Mint is installed, the swap partition, ...

Bye

---

### Post by ajgreeny on 2010-10-18
What version of Mint does he run at the moment, asMint now uses the same grub2 as ubuntu, so will probably not have a /boot/grub/menu.lst file to bother about.

I suggest you use the option to choose partitions manually, the third option on the disk preparation page of installing, and there you can choose the old Mint partitions as the new ubuntu partitions.  It may sound complicated but it really isn't.  Try it out and you'll see what I mean.

---

