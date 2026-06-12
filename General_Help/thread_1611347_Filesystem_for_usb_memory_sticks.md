---
title: "Filesystem for usb memory sticks"
date: 2010-11-01
forum: General Help
---

### Post by foxmulder881 on 2010-11-01
I'm trying to get away from FAT and FAT32 for my memory sticks. Is ext2 really a suitable option for usb memory sticks?

I don't want to use ext4 because of journaling, as it's simply not required for usb sticks.

---

### Post by Jahid65 on 2010-11-01
This is not a problem for linux-based os. But if you consider other OS like windows then problem will occur. FAT32 is recognized by all operating system(at least main 3). But ext2 may recognize only by linux default. Windows or Mac may not recognize it. However some 3rd-party tool can be used to recognize ext2 in windows or Mac.

---

### Post by foxmulder881 on 2010-11-01
> **Jahid65 said:**
> This is not a problem for linux-based os. But if you consider other OS like windows then problem will occur. FAT32 is recognized by all operating system(at least main 3). But ext2 may recognize only by linux default. Windows or Mac may not recognize it. However some 3rd-party tool can be used to recognize ext2 in windows or Mac.

Yeah I know that. But considering the aforementioned stick will never see Windows systems, I don't consider this to be a problem.

And there's no sign of MS Windows in my house! Only Linux and BSD! :)

---

### Post by t0p on 2010-11-01
It depends on what you are going to use the sticks for.  If they will be used only in a Linux environment, ext2 is fine.  But if you are likely to ever want to use a stick with a Windows computer, a FAT file system is best.  Windows won't be able to read an ext2 file system.

**EDIT:** I see you've already addressed this question.  So, ext2 will be fine.  As long as you don't ever remove the stick without properly unmounting it first.  As ext2 is not a journalling file system, an unclean removal can cause damage to your file system and potential corruption or loss of data.

---

### Post by coffeecat on 2010-11-01
> **foxmulder881 said:**
> Is ext2 really a suitable option for usb memory sticks?

Yes. Works just fine.

After you format it and after it has been automounted, chown the mountpoint to your ownership. This has the interesting effect of changing the ownership of the root of the filesystem rather than the mountpoint itself. Plug the stick into another Ubuntu/Linux system and you'll see what I mean.

Or you can use Disk Utility which has a 'take ownership' option if you choose a Linux filesystem and which has the same effect.

---

### Post by foxmulder881 on 2010-11-01
> **coffeecat said:**
> Yes. Works just fine.

After you format it and after it has been automounted, chown the mountpoint to your ownership. This has the interesting effect of changing the ownership of the root of the filesystem rather than the mountpoint itself. Plug the stick into another Ubuntu/Linux system and you'll see what I mean.

Or you can use Disk Utility which has a 'take ownership' option if you choose a Linux filesystem and which has the same effect.

Thanks for the tip. I would never have known this otherwise.

---

### Post by coffeecat on 2010-11-02
> **foxmulder881 said:**
> Thanks for the tip. I would never have known this otherwise.

It seems to be little known or understood. I've had a couple of posters flatly disbelieve me.

To extend the tip, you can chmod the mountpoint with the same effect on the root of the filesystem. Which in theory should be useful if you have different systems with different UIDs - which seeing as you are using both Linux and BSD might be the case. Does BSD have drivers for ext filesystems? I've never used BSD.

However, I discovered one quirk the other day. I was running a 10.10 live CD live session on my main desktop and it wouldn't mount from the Places menu my internal ext4 partitions which I had previously chowned and chmodded for regular use with my various multiboot systems. I had to mount from the terminal and then it couldn't display or read the contents correctly. Quite why I don't know. If this was because the live session ubuntu user has a different UID (99 - I think) then that bodes ill for what I just said about chmodding for different user UIDs. Or perhaps it is some other problem peculiar to the live session. I will investigate further.

**Edit:** Indeed - the penny only dropped as I posted. It was obvious. I've done some investigation by creating another user account which is in a different group. The partition(s) that was causing trouble in the live session I had 'sudo chmod 774' and, of course, now I can see the problem. Chmodding it 777 solved it. That is very permissive, but that suits me.

---

