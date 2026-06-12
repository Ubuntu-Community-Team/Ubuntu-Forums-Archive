---
title: "Maverick to Natty upgrade messed up..."
date: 2011-05-07
forum: General Help
---

### Post by DrCoolSanta on 2011-05-07
So I upgraded to Natty as soon as Update Manager showed me the option.
I think everything worked fine initially, but recently Nautilus stopped showing all the partitions (except the ones that are mounted). It used to give me an option to mount my other partitions when I needed them, it doesn't anymore. My USB disks stopped auto mounting. The desktop effects disappeared, when I got compiz to run, they started acting up.
Unity also had a lot of glitches and I found it annoying.

I tried installing Natty from scratch... Even the live cd gave me all those problems.

I haven't been able to find a fix... I'm planning to move to fedora or suse now :(

---

### Post by DrCoolSanta on 2011-05-08
I solved it myself... Anybody still wondering how to fix this might find this helpful.

So when I tried installing Fedora, it kept on complaining about my drives no being initialized properly... 

So I fired up fdisk, that gave me an error message "Omitting empty partition (5)." All my partitions were still there, i don't know which partition it was talking about. Anyway, so I rewrote the partition table and the error went away (I was still getting the reinitialise error.)

Then I opened the Partition Tool that comes with Fedora, and it wouldn't delete or add new partitions because I had overlapping partitions. I am pretty sure nothing touched my partitions, and I suspect that there is a bug in the update procedure that does this.

Since I couldn't use to tool, I used fdisk to remove my Ubuntu partitions and loaded the Ubuntu boot USB drive. Now everything was working fine, it let me mount all my partitions, the card reader started working and my thumb drives could auto mount. I started installing Ubuntu, but the installation tool did not show any partitions on my HD. I wanted to get rid of my other partitions anyway, so I backed up my data and installed.

Now everything works properly, Unity does not glitch, compiz works... Everything's perfect.

---

