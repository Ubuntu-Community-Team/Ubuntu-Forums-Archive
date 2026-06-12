---
title: "System Restore back to Windows 7"
date: 2011-08-30
forum: General Help
---

### Post by Da_Bomb_Digity on 2011-08-30
Alright so I run a Gateway NV59C laptop and I put ubuntu 11.04. I have the system restore discs required and I wish to reinstall widnows 7. Its not that I dislike linux, it's just that I want to reinstall it side by side with windows so I can play games and such more easily. However when I pop in the restore discs and begin the process It pops up with an error message and the discs won't work...

Any solutions/similar problems?

---

### Post by searchfgold6789 on 2011-08-30
To assist you better, it would help if we had:

[LIST]
[*]More information about the CD's.
[*]More information about the error messages.
[/LIST]

---

### Post by Da_Bomb_Digity on 2011-08-30
Right I apologize I should've been more descriptive! 

> 
Restore Failed--Error code 0x3ed (The volume does not contain a recognized file system. Please make suretha tall required file system drivers are loaded and that the volume is not corrupted.) 

That is word for word what the error code message says. The discs I bought from the Gateway official website because I didn't make any when I bought my computer.

---

### Post by beew on 2011-08-31
AFAIK to use the restore disk your hard drive configuration has to be the same as it was out of the factory.  Since your hd has been partitioned for dual booting it is considered different hardware (computer) and the restore disk won't work. For the same reason you can't  use your restore disk to install Windows in a different computer, the license is for a specific machine and by partitioning the hard drive it technically becomes a different computer (Some propritary programs  in Windows will stop working too if you partition your hd, even though you haven't damaged anything, for exactly that reason)

---

### Post by Da_Bomb_Digity on 2011-08-31
> **beew said:**
> AFAIK to use the restor disk your hard drive configuration has to be the same as it was out of the factory.  Since your hd has been partitioned for dual booting it is considered different hardware (computer) and the restore disk won't work. For the same reason you can't  use your restore disk to install Windows in a different computer, the license is for a specific machine and by partitioning the hard drivbe it technically becomes a different computer.

I see, is there anything I could without purchasing widnows 7 again to install it? Or am I just out of luck?

---

### Post by madjr on 2011-08-31
> **beew said:**
> AFAIK to use the restore disk your hard drive configuration has to be the same as it was out of the factory.  Since your hd has been partitioned for dual booting it is considered different hardware (computer) and the restore disk won't work. For the same reason you can't  use your restore disk to install Windows in a different computer, the license is for a specific machine and by partitioning the hard drive it technically becomes a different computer (Some propritary programs  in Windows will stop working too if you partition your hd, even though you haven't damaged anything, for exactly that reason)

then he should just repartition his hard drive back?

anyway, i have had made different partitions and when i want to restore windows from the restore partition it would work, and deletes the old partition made.

---

### Post by madjr on 2011-08-31
> **Da_Bomb_Digity said:**
> I see, is there anything I could without purchasing widnows 7 again to install it? Or am I just out of luck?

can you load ubuntu from the live-cd and take a pic of your partitions using gparted?

---

### Post by Mark Phelps on 2011-08-31
If I understand what you said, you only have Ubuntu on your PC now, right?  Could be that the restore program is getting confused by the presence of a Linux filesystem on the drive.

Try booting with the Ubuntu CD and removing the Linux filesystem partition(s).  The restore disks should work then.

---

### Post by kesavachandran on 2011-08-31
It seems DA_BOMB_DIGITY is faced with his Win7 Loader not working.If he has a Win7 rescue disk he should boot from it, will show System Recovery Window.From this select Use Recovery Tools,click next for choose Recovery Tool.Should get a few options.Try System Recovery.If that solves the problem well and good.Windows 7 will boot and function without Linux.If System Recovery does not enable win 7 to function,repeat with Rescue Disk and continue till SystemRecovery.The new recovery tool is Command Prompt.Direct mouse pointer, click this title.A black window pops up on which please see X:\ Sources>(with a blinking --)Type against this line to look like X:\sources>bootrec /fixWDSUTIL.dll then press ENTER.
There will quite a number of message outputs.The last one is/Rebuild BCD.A command prompt will appear like this X:\sources>   type exit after sources>. Win7 should reboot and come back to life.Good Luck my friend
Kesava

---

### Post by Mark Phelps on 2011-08-31
> **kesavachandran said:**
> It seems DA_BOMB_DIGITY is faced with his Win7 Loader not working...

Not according to what I read -- where he says > I want to reinstall it side by side with windows so I can play games and such more easily.

He ONLY has Ubuntu on his PC at present.  He's trying to put Win7 BACK on his PC and he tried using the Restore disks -- but he gets an error message.

To the OP: If Ubuntu is still working OK, then open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out the partitions on the drive.  Post the results back here.

---

### Post by Da_Bomb_Digity on 2011-08-31
Yes you are right all I'm running is Ubuntu 11.04 on my laptop

And here is what I got when I did that in the terminal:  


> Disk /dev/sda: 500.1 GB, 500107862016 bytes
225 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
units = sectors of 1 * 512 = 512 bytes
sector size (logical/physical: 512 bytes / 512 bytes 
I/0 size (minimum/optimal: 512 bytes / 512 bytes

Device boot     Start     End                  Blocks        ID       System
/dev/sda 1 *     2048    969058303    484528128    83      Liniux 
/dev/sda2    96906350  976771071  3855361         5        Extended
/dev/sda5 969060352   976771071  3855360    82          Linux swap / solaris


Oh and here is the error code when I try to system restore in case nobody saw it. 
> 
Restore Failed--Error code 0x3ed (The volume does not contain a  recognized file system. Please make suretha tall required file system  drivers are loaded and that the volume is not corrupted.) That  is word for word what the error code message says. The discs I bought  from the Gateway official website because I didn't make any when I  bought my computer.

---

### Post by kesavachandran on 2011-08-31
His present priority seems to focus on getting his Win 7 back on track.Mentions use of Win7 rescue disk for a system rescue if my guess is right ,which went awry. That is what prompted me to try help him.Hope my intentions are not  misplaced,as i am a Linux lover :confused:

---

### Post by Slim Odds on 2011-08-31
I ran into this before...

The actual problem is the MBR, not the partitions. You can fix this by using the Live CD and wiping out the MBR.
```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```Note: of={device}, whatever it is for your system.

---

### Post by Da_Bomb_Digity on 2011-09-01
> **Slim Odds said:**
> I ran into this before...

The actual problem is the MBR, not the partitions. You can fix this by using the Live CD and wiping out the MBR.
```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```Note: of={device}, whatever it is for your system.

What exactly does this entail doing? And what are the risks?

---

### Post by Slim Odds on 2011-09-01
> **Da_Bomb_Digity said:**
> What exactly does this entail doing? And what are the risks?

I'm not sure what you mean....

You want to reinstall windows on that hard drive, right?

I'm assuming that you have everything off the drive already, right?

This operation would make a normal system unbootable. But you really don't care because you're trying to do a fresh install from DVDs.

It just wipes the MBR (Master Boot Record). Windows will put it's own boot record there during install, but it's too stupid to just overwrite what's there now.

When you installed Ubuntu before, it put it's own boot loader there (GRUB). That's what the Windows installer is upset about.

---

### Post by Da_Bomb_Digity on 2011-09-01
> **Slim Odds said:**
> I'm not sure what you mean....

You want to reinstall windows on that hard drive, right?

I'm assuming that you have everything off the drive already, right?

This operation would make a normal system unbootable. But you really don't care because you're trying to do a fresh install from DVDs.

It just wipes the MBR (Master Boot Record). Windows will put it's own boot record there during install, but it's too stupid to just overwrite what's there now.

When you installed Ubuntu before, it put it's own boot loader there (GRUB). That's what the Windows installer is upset about.

I see so by uninstalling Linux I'll be able to reinstall windows, essentially. If Windows still doesn't work for some strange reason, would I be able to put Ubuntu back on it with no issues?

---

### Post by madjr on 2011-09-01
> **Da_Bomb_Digity said:**
> I see so by uninstalling Linux I'll be able to reinstall windows, essentially. If Windows still doesn't work for some strange reason, would I be able to put Ubuntu back on it with no issues?

yes, exactly you can reinstall using the live-cd no problems

---

### Post by Slim Odds on 2011-09-01
> **Da_Bomb_Digity said:**
> I see so by uninstalling Linux I'll be able to reinstall windows, essentially. If Windows still doesn't work for some strange reason, would I be able to put Ubuntu back on it with no issues?

Like I mentioned, I had the exact problem. Also with a Gateway laptop and this is how I fixed it and reinstalled Windows 7.

Just do it.... :guitar:

P.S. As I mentioned, this is just stupid on the Windows installer side. It sees an MBR that is doesn't understand so it fails. Problem is, most people just want to wipe it out and get going with the install. They should at least have an option that says "Do you want to wipe it out anyway?" or something like that.

---

