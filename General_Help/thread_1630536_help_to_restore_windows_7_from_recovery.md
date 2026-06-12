---
title: "help to restore windows 7 from recovery"
date: 2010-11-25
forum: General Help
---

### Post by suoko on 2010-11-25
hi,

I have a sony vaio netbook and installed ubuntu on it some months ago
After some weeks windows 7 crashed and stopped booting
I tried to recover it but still no success.
When i bought it it had one partition only (plus the first one for windows recovery)
When I installed ubuntu I partitioned my hard drive at my pleasure as you can see in attached image
When I try to recover windows 7 it says it "can't find the windows partition or it's too small"
Since 80 gb is not too small, i bet it can't recognized the partition anymore.
Can anybody suggest a way to let it recognize my sda2 ?
Does it have to have the "C:" label or "Windows something"? (I can only name it C without colons)
Does it have to formatted FAT in a particular way ?

thanks for your help since sony didn't help much so far

---

### Post by RJ12 on 2010-11-25
Unfortunately it probably goes off the MBR and since it was over written by GRUB, it doesn't recognize it, at least my Toshiba Recovery doesn't work either I think because of this. I have never been able to get it working even with Ubuntu not being on it, and the partitions being original size

---

### Post by suoko on 2010-11-25
So dell's windows recovery is the only one that works on dual Boot pcs so far.
must call a technician soon then, to kick him

---

### Post by Quackers on 2010-11-25
suoko, did you create the recovery discs?
Also how are you trying to access the recovery partition?

---

### Post by suoko on 2010-11-25
No recovery disks since i had no time to buy a cdRom reader before windows committed suicide. what's for the recovery partition and its tool if i need recovery disks ?
i can Boot the recovery session through burg  which automatically detected the windows recovery partition.
the recovery tool is a minimized windows session which lets me choose between c: or entire system recover.
at the moment they are both failing and i don't wanna spend a cent for this matter

---

### Post by Jags_FL on 2010-11-25
@ suoko

do you have Windows 7 installation DVD? if yes, did you try to fix MBR? 

Here are some helpful links:

1, [http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html](http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html)

2, [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

3, [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Quackers on 2010-11-25
It is wise to make the recovery discs, as partitions can become corrupted.
In the Vaio Recovery environment it is common for one of the options to fail when non oem partitions are discovered, but not both options. This seems to me to be a symptom of something more serious, but I may be wrong.
Basically, if the recovery partition is not working and you don't have the recovery discs, you may need to contact Sony and ask them for a set of recovery discs, but they are likely to want to charge you for them.
The only other suggestion that I can make at this stage is to delete all partitions after sda2 and then resize sda2 so it takes up the rest of the disc.
Then see if the recovery works properly. (You may then need to access the recovery partition via the key sequence during boot (maybe F11 or similar - check the recovery manual, as burg may then not work!
Beware that this would delete your Ubuntu installation!!!

---

### Post by Quackers on 2010-11-25
When you say "Windows crashed" do you mean that you were using Windows and it crashed and wouldn't reboot, or do you mean that it wouldn't boot after you installed Ubuntu?
If it is the second one you should definitely try Jags_FL's advice first!

---

### Post by suoko on 2010-11-25
I asked Sony a Bootable pendrive or a downloadable iso to dd  to one the thousands pendrives i have, but they didn't know what i was talking about.
I'll trash the entire netbook asap due to nonsense And get a galaxy tab with slide keyboard for coming new years eve

thanks anyway

---

### Post by Quackers on 2010-11-25
You can download a Windows repair disc from the net and then try Jags_FL's advice from post #6

---

### Post by suoko on 2010-11-25
Don't think I'll loose my time behind this stuff anymore.
btw starting wayland from a xorg-less single mode session looks great

---

