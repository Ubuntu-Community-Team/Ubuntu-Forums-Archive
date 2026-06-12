---
title: "How to wipe ubuntu system volume clean / back to NTFS?"
date: 2009-07-30
forum: General Help
---

### Post by Blade_Jones on 2009-07-30
I created a dual boot (XP and Ubuntu) but somehow used up way more space on the drive for the Ubuntu volume. So I've been trying to figure out how to wipe the Ubuntu volume clean so that I can reformat it in NTFS. Partition Magic doesn't recognize the Ubuntu volume and neither does Windows or the Windows command prompt.  So how do you reformat an Ubuntu system volume in NTFS?  I read that you need to unmount the Ubuntu volume, then there's an option under "administration" that allows you to format in NTFS, but I didn't see either options. Perhaps these options who up if I attach this hard drive to a secondary computer as an external drive using a SATA to USB adapter?

---

### Post by Elfy on 2009-07-30
Do you still get grub when you boot you pc - the linux menu list. If you do then if you are removing ubuntu completely you need to use your xp install disc to fixboot.

Once you have the pc booting to windows - start the pc with the ubuntu livecd - in System > Admin menu there is a partition editor - you can do what you need to there.

[http://ubuntuforums.org/showthread.php?t=672328](http://ubuntuforums.org/showthread.php?t=672328)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by wojox on 2009-07-30
Boot your live cd and use gparted.

---

### Post by Blade_Jones on 2009-07-30
Yep. Booted up with my Ubuntu boot CD (instead of booting with the volume on the HD) and then Gparted partitioning tools because available. I deleted the Ubuntu partition, restarted the computer but got that grub loading error thing. So I booted with my Windows CD, selected "R" for repair and did a "fixboot c:" and "fixmbr". Everything's back to normal now. Thanks for the help!

---

