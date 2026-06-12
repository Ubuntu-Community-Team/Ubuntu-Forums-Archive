---
title: "Grub hangs with &quot;Starting Up&quot; during Windows Boot"
date: 2009-07-02
forum: General Help
---

### Post by exec_extreme on 2009-07-02
Hello all,
I'm relatively new to Linux, and I've fought through most of the adjustment process so far from Windows. I've searched high and low for an answer to my own question though, and I can't seem to find an answer.

I have ONE hard drive with the following partitions
(sudo fdisk -l)
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9190    73818643+   7  HPFS/NTFS 
/dev/sda2            9191       30515   171293062+   5  Extended
/dev/sda5            9191       29764   165260623+  83  Linux
/dev/sda6           29765       30515     6032376   82  Linux swap / Solaris

That first partition up there is my Windows XP partition. I'd like very much to boot into that partition, but after hours of searching and trying combination after combination of grub commands, grub hangs at "Starting Up" and will not boot into Windows.

Here is my most current menu.lst Windows section
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

I've seen a lot of similar issues with grub hanging at that "Starting Up" screen, but most, if not everyone with the problem has multiple hard drives, and the solutions has to do with remapping partitions back and forth. /shrug!

I really do appreciate any and all help I can get. I've browsed these forums so much lately and everyone is always very helpful and friendly here ;)

---

### Post by exec_extreme on 2009-07-02
bump...

Apologies for breaking the bump policy. I couldn't find it in any of the site documentation

---

### Post by merlinus on 2009-07-03
There may be a problem with xp, as from what you have posted, everything appears to be correct.

You might try supergrub to see if you can boot into xp, and if so, then things can probably be fixed.

[http://supergrubdisk.org](http://supergrubdisk.org)

Also, I assume the windows stanzas in menu.lst are at the very end of the file?

---

### Post by exec_extreme on 2009-07-03
Thanks for the reply! 
I'll look into Super Grub Disk for now and see if that can help.

---

### Post by exec_extreme on 2009-07-03
After trying to boot into my Windows partition with SGD, and having it hang after the boot command was given as well, the problem must lie within Windows having trouble booting itself. Earlier today I did two or three chkdsk's on it, and many fixmbr fixboot, but the problem still occurs. I'm going to try SGD's equivalent option of fixmbr and fixboot and see what comes of it.

EDIT: After trying SGD's fixmbr/fixboot commands, I get "Disk read error" when trying to load Windows after Grub has been wiped from the MBR. The issue seems to be wide spread... with no real remedy. I think I'm going to leave this issue alone then and either try to run the one program I needed to run in Windows on Wine, or in a Virtual Machine.

---

