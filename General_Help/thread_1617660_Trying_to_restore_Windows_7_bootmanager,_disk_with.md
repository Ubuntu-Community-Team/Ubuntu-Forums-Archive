---
title: "Trying to restore Windows 7 bootmanager, disk with ext4, ntfs and hfs+ partitions"
date: 2010-11-09
forum: General Help
---

### Post by themusicalduck on 2010-11-09
At one point I had WinXP, OSX, Win7 and Ubuntu installed on my computer. I kept XP around because I wanted to try Windows 7 out.

I then decided to delete XP and stick with Windows 7, so I deleted the XP partition. Of course it hadn't occurred to me that Windows 7 would have installed its bootmanager onto the XP partition rather than its own partition, so I can't boot into Windows 7 anymore.

I have a Win7 install disk and I tried to recover it from there. The automated recovery doesn't work, it doesn't detect the install at all. I tried selecting the Win7 partition with diskpart and using bootrec /rebuildbcd, but it comes up with an error about the partition being either an invalid filesystem or corrupted. If I remember right, Windows won't install onto a partition if there are other filesystems on the same drive, so could that be the same problem here?

I could reinstall if I have to, but if Windows won't install onto the disk when there are other filesystems, I really don't want to have to wipe my drive and reinstall Ubuntu and OS X just for the sake of making room for Windows.

Are there any other methods that might work?

---

### Post by wilee-nilee on 2010-11-09
Your on the right track. Post the bootscript in my signature in code tags. You can to get code tag wrapping just post the text from the generated file highlight it then click on the # in the reply panel.

---

### Post by themusicalduck on 2010-11-09
Thanks for the reply.

Actually on booting from the install disc for a second time, it recognised the installation and everything worked that time.

The difference was that I changed the boot order in the bios to use the drive with windows installed and not the drive with grub on, just to see what error I got. Not sure if that was the solution or if it just decided to work.

---

### Post by wilee-nilee on 2010-11-09
> **themusicalduck said:**
> Thanks for the reply.

Actually on booting from the install disc for a second time, it recognised the installation and everything worked that time.

The difference was that I changed the boot order in the bios to use the drive with windows installed and not the drive with grub on, just to see what error I got. Not sure if that was the solution or if it just decided to work.

Great, nothing like figuring it out yourself.;)

---

