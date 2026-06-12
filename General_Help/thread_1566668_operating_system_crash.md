---
title: "operating system crash"
date: 2010-09-02
forum: General Help
---

### Post by Maradona on 2010-09-02
> 

[0.602862] Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)

After I press the start (power on) it should nothing more than the above.  Is there anyone can help for that?  Do I need reinstall everything?

---

### Post by Sctmon on 2010-09-04
I have just had exactly the same thing happen. When I tried to boot up (working fine last night when I powered down) I got the following:

[  0.607422] Kernel Panic - Not Syncing: VFS: Unable to mount root fs on unknown-block (0,0)

It is the PC running my mythtv frontend and I have 2 other drives in the system, one with Windows 7 and another drive with data and other stuff - no OS.

Coincidentally (or not) Windows 7 would not boot either just hanging on startup screen.

I have the BIOS set to boot from SATA 3 which is the drive containing Mythbuntu and use Grub to select the Windows drive if I need it.

I suspect that this is a hardware issue. I managed to get Mytbuntu to boot normally after a few attempts, one of which only got to the GRUB loader and said :
GRUB Loading
error: HD 0,1 out of disc

I am currently backing up my system in case it is a hard drive issue but I have run full diagnostic scans on all of them and they are all good.

Any thought on what normally causes this error?

---

