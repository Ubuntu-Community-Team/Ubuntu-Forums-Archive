---
title: "In a problem.... BIG problem"
date: 2010-10-23
forum: General Help
---

### Post by WinterAce on 2010-10-23
Hi,

I apologise if this is in the wrong forum. Please read the whole post and help me out.

I got my VAIO with Vista a few years ago. When 7 came out, I upgraded my Vista to 7. But the OS had some problems, so I decided to install Win7 on another partition without erasing my current one, as I had important data on it. So I have Win7 on my C drive and the upgraded Win7 on my D drive.

I recently backed up all my important data on the D drive and decided to format it, as it was taking up too much space. I used GParted to format it. Now, when I start up my computer, it says "BootMGR is missing, press Ctrl+Alt+Del to restart". I thought install GRUB would fix this, as my DVD drive does not read DVDs properly. So I installed Ubuntu so that I could even manage my files and do important stuff.

After installing Ubuntu, only Ubuntu, Memory Check and "Windows Vista (loader)" show up in the list. I start up the 3rd and it gives me all system recovery options.
Another thing, when I mount my old D drive in Ubuntu, it says:
```
Error mounting: mount exited with exit code 12: Failed to read last sector (307213448): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```So is there any way I can fix my Win7 and my D drive using Ubuntu? I have a 2 4GB USB drives, and a 150GB external hard disk (that has all my important data), if it can in any way replace the use of the DVD drive.

Thank you very much.

---

### Post by LiamWilson on 2010-10-23
Hmmm, looks like a borked NTFS file system. You might have to format it and then re-install, unless someone posts an alternative...

If you install gparted via the software centre (It's removed after installation of Ubuntu), you should be able to format it then, and then put all your data back on it. Very lucky that you backed it all up, eh?

If you need any help formatting your drive, Give me a shout, I've done it countless times :P

---

### Post by utilitytrack on 2010-10-23
> **LiamWilson said:**
> looks like a borked NTFS file system. You might have to format it and then re-install

No. First need to check NTFS partition by **chkdsk**.

See this resource: [http://support.microsoft.com/kb/315688]("http://support.microsoft.com/kb/315688")

As once all errors will be fixed, you can to mount it in Linux.

> **WinterAce said:**
> I used GParted to format it. 

Well, it seems that you were careless.
[SIZE="1"]
PS
Oh my god, I published link to Mi¢fQ$Qff site. I'm sorry, Linus. Simply I wish to help this man.[/SIZE]

---

### Post by WinterAce on 2010-10-23
Thanks for the replies.
I'll get the partition fixed later, that isn't a problem. The problem is that I cannot boot into Win7 because the BootMGR is missing.
Is there any way I can fix that through Ubuntu itself?

---

### Post by ivarn on 2010-10-23
Here's the thing. When you formated D:, you also deleted the boot file.
Your win7 depended on the partition you formated in order to run.
If you have any programs or files on your pc, take a backup and format the whole damn hard drive. Why? because your c: partition got destroyed after you made a new partition for win7. So what you got now is 1 formated MTFS partition and 1 currupted MTFS partition. Right?
Well, if you have ubuntu installed on your pc you also have a ext4 partition and you can simply move everything useful from the broken partition over to your linux.
Then, delete the ntfs partition from ubuntu or by using your win7 cd.
Now from your win7 cd, delete both the broken ntfs partitions and create a new one.
Then you'll have 2 partitions on your pc (ext4 and ntfs).
Install win7 and reinstall grub from your ubuntu cd or from windows.
You can use a windows app called Auto Super Grub which is the easiest way I think.
You can download it from download.com.
Good Luck :)

---

### Post by WinterAce on 2010-10-23
Umm, its actually the formatted hard disk that is corrupted, i.e., my D: drive. The D: drive had my previous problematic Win7, and that's why I formatted it. My current working Win7 is on my C: drive, which is working perfectly, except that it won't boot. And I don't want to format my C: drive as it has my installed software and games that I don't want to lose (I don't have their installers).

Also, my DVD drive isn't working so everything that I'm gonna do will have to be through my 2 4GB USB pen drives.

---

### Post by LiamWilson on 2010-10-23
could it just be a matter of updating grub? Try running:
```
sudo update-grub
```
And then when you reboot, you may or may not see win7. If it still doesn't work, you can always see this post, which looks like it is a problem caused by Windows, not Ubuntu.

[http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/](http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/)

---

### Post by Quackers on 2010-10-23
Is there a Windows Recovery (loader) option in the grub menu? If yes, then try booting that option. It will probably boot into your Windows installation. Grub sometimes labels them wrongly (particularly Vista on Vaio's)

---

### Post by Sef on 2010-10-23
FYI: Windows needs to on the first primary partition.

---

### Post by WinterAce on 2010-10-23
Thank you very much fellas! Windows 7 is back on my GRUB list! Thanks again!

---

### Post by Quackers on 2010-10-23
Excellent :-)
What fixed it exactly? 
Please mark the thread as solved using the thread tools so that others can benefit.

---

### Post by WinterAce on 2010-10-23
I have already marked the thread as solved.

So this is how I fixed it.
I got hold of Windows 7 recovery ISO which is available for free (I don't have the link now, but I got it through Google). I then used Unetbootin to copy it onto a USB and make it bootable. On booting the USB, I used the system repair and it automatically fixed the problems. But on restarting, Grub did not show Windows 7. So I did what LiamWilson wrote and updated Grub. Terminal said, to my joy, that it had found Windows 7 and I restarted to find it there.

Thanks again fellas, now I can happily dual-boot.

---

