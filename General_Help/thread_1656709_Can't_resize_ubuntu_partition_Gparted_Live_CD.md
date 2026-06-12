---
title: "Can't resize ubuntu partition Gparted Live CD"
date: 2010-12-31
forum: General Help
---

### Post by BigCityCat on 2010-12-31
I have tried to with the live cd. Here are a few screenshots.

[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-2.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-2.png)

[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-1.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-1.png)

---

### Post by mr.farenheit on 2010-12-31
try moving the location of the linux partition.

---

### Post by BigCityCat on 2010-12-31
do you mean copy and paste?

---

### Post by Quackers on 2010-12-31
Are you trying to extend sda5?
If you are, sda5 is a logical partition inside sda2, which is an extended partition. As they both start in the same place, and there is no free space within  sda2, you need to extend sda2 into the unallocated space first. When sda2 is extended, sda5 will then extend.

---

### Post by BigCityCat on 2010-12-31
> **Quackers said:**
> Are you trying to extend sda5?
If you are, sda5 is a logical partition inside sda2, which is an extended partition. As they both start in the same place, and there is no free space within  sda2, you need to extend sda2 into the unallocated space first. When sda2 is extended, sda5 will then extend.

Does gparted give me that option? I don't see a way to do that. Is there a command that I can use?

How do I extend sda2?

---

### Post by BigCityCat on 2010-12-31
I think I understand. Let me give it a try.

---

### Post by QLee on 2010-12-31
You aren't going to be able to do it with the partitions mounted. Try it from the live CD. But backup any important files first, just in case.

---

### Post by QLee on 2010-12-31
[Edit] Duplicate due to my slow connection. Sorry for the noise.

---

### Post by BigCityCat on 2010-12-31
Okay thanks. I booted into the Gparted live CD and I had to right click on the swap partition and unmount it or what ever. Then that automatically unmounted the extended partition. At that point I was able to extend the extended partition (SDA2). Then I still had to extend sda5, it's in that process now, but your explanation helped me understand what I needed to do.

Thanks

---

### Post by QLee on 2010-12-31
> **BigCityCat said:**
> I think I understand. Let me give it a try.
You aren't going to be able to do it with the partitions mounted. Try it  from the live CD. But backup any important files first, just in case.

[Edit] Oops, first two quick replies didn't show so I tried this with Quoted and when it went through all showed up. Once again, sorry for the noise.

I wanted to make sure to caution you to backup anything important but it usually works to slide partitions with no problem although it can take some time to complete. Does your extended partition now show as sda1?

---

### Post by Quackers on 2010-12-31
Swap should indeed be turned off first.
It can take a while to move your data about. A couple of hours seems to be about normal when I do it.
As Qlee has said already, it is good practise to backup data first. Partition adjusting carries risks!
It's not something to be scared of, but it should be done carefully :-)

---

### Post by BigCityCat on 2010-12-31
> **QLee said:**
> You aren't going to be able to do it with the partitions mounted. Try it  from the live CD. But backup any important files first, just in case.

[Edit] Oops, first two quick replies didn't show so I tried this with Quoted and when it went through all showed up. Once again, sorry for the noise.

I wanted to make sure to caution you to backup anything important but it usually works to slide partitions with no problem although it can take some time to complete. Does your extended partition now show as sda1?

Well Gparted is still working so i don't know if it has changed the partition to SDA1. I was wondering if I can delete th extended partition SDA2 after it finishes? Also I was reading that I may need to re install grub2?

I have backed up.

---

### Post by Quackers on 2010-12-31
On one of my systems I thought it would rename it to sda1 (as I had deleted sda1 previously), but it didn't. It's still called sda2 on mine, even though there is no sda1.
There should be no reason to have to re-install grub, unless it wasn't working before the change.
Grub (or the first part of it) is written to the mbr of disc sda, which is before sda1.

---

### Post by BigCityCat on 2010-12-31
Okay thanks. I will report my progress in about 50 minutes.

---

### Post by QLee on 2010-12-31
[QUOTE=BigCityCat]...I was wondering if I can delete th extended partition SDA2 after it finishes? ...[/QUOTE]

No, you need the extended volume as a container for the logical volumes sda5 and sda6.

Changing those designations at this point would mess up both grub and the fstab entry for swap in your install. Not advised. It would be possible to move everything to primary partition if that is what you are thinking but it would take considerable effort and magic.

---

### Post by BigCityCat on 2010-12-31
Okay it finished. i did not delete the extended partition.

Grub is not working. I am getting a blinking courser and that is it. I guess I should have mentioned that I had deleted the windows partition before i started. Not sure if that is why grub isn't working now.

How can I fix grub2.

---

### Post by BigCityCat on 2010-12-31
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

---

### Post by QLee on 2011-01-01
[QUOTE=BigCityCat]... I guess I should have mentioned that I had deleted the windows partition before i started. Not sure if that is why grub isn't working now.
...[/QUOTE]

If GRUB was working at the start, nothing you did should have changed that as long as you told us all you did. Exception to this would be if you were using Windows bootloader to load your Ubuntu, in that case deleting Windows would have eliminated the boot menu. Most people don't even know how to use the Windows bootloader for that, I would have expected you to mention it if you had configured that way.


[QUOTE=BigCityCat]ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly. 	[/QUOTE]

Since you can't boot to your Ubuntu install you must have done this from the live cd and that couldn't work for what you want to do.

The procedure would be what drs305 details in this link:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If you're still having trouble then it might be a good time to use the boot info script which will show what condition your system is currently in.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Happy New Year to you and good luck!

---

