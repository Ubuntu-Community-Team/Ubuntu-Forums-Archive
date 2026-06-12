---
title: "How to uninstall Ubuntu 12.04 from Vista?"
date: 2012-04-28
forum: General Help
---

### Post by iriscoder on 2012-04-28
First of all, I love Ubuntu, and run it dual boot to Vista, but I did a fresh install via disk of 12.04 and did not set the partition large enough so it couldn't fully install. How do I uninstall it, and then reinstall it? I don't have a Windows recovery disk FYI.

---

### Post by iriscoder on 2012-04-28
Please, help.

---

### Post by D.Dadsgé on 2012-04-28
just install it all over again and set your partition large enough? that should just work as you will need to format your disk while you are partitioning your hard drive

---

### Post by iriscoder on 2012-04-28
Well, I don't know how. And I want to cleanly uninstall it.

---

### Post by D.Dadsgé on 2012-04-28
you said you were installing ubuntu 12.04 from a disk, but it didn't have enough space on the disk. you dont need to remove your ubuntu partition before you restart the installation. run the disk and select the option to manually configure your partitions. it's all documented by ubuntu [HERE]("https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning").
when you are forming your new partitions pay close attention not to overwrite your vista partition! as you dont have a recovery disk for vista that would be a big problem! read all the info before you decide to create the partition.

---

### Post by iriscoder on 2012-04-28
I don't care about that... it is really complicated. I just need to get it uninstalled.

---

### Post by D.Dadsgé on 2012-04-28
you can always just cancel the installation after you formatted the ubuntu partition. or you can format the partition form your vista os or from the tryout version of ubuntu. 
i dont think you can just uninstall an os. i think formatting the drive is as close as it gets :)

---

### Post by iriscoder on 2012-04-28
I did it before with 11.04, but 12.04 is different. So yes, you can just uninstall an OS.

---

### Post by Zukaro on 2012-04-28
I've never heard of just uninstalling an OS.  Maybe the Windows installer has an uninstall feature?

Regardless, just format the drive.  It's simple.
Boot into Windows and find the partition which you've installed Ubuntu on.

If you can't do that, boot up the LiveCD and select "Try Ubuntu".  Then look for "Gparted" and use that to format the partition Ubuntu is installed on.  If you don't know which one has Ubuntu it's likely the one that's in the extended partition.  Make sure you've unmounted all the partitions (likely the only partition which will be mounted is swap; right click it and choose "swapoff" and that should unmount it).  If the partitions are still mounted it's not a big deal, all that's gonna happen is you'll get an error message when trying to format informing you that the partition is still mounted.

As for grub I'm not sure how to uninstall that.  Before you start deleting partitions make a Windows recovery disk (I'm pretty sure Windows has this feature).  However, if you plan on reinstalling Ubuntu grub removal isn't an issue as it will be overwritten upon reinstall and everything will work fine.

---

### Post by iriscoder on 2012-04-29
Well the drives are mounted, so that doesn't work.

---

### Post by DeadMansLife on 2012-05-22
Question, did you install Ubuntu through Wubi?

---

