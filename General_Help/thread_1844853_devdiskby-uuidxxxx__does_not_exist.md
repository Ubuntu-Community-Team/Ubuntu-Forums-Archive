---
title: "/dev/disk/by-uuid/xxxx  does not exist"
date: 2011-09-15
forum: General Help
---

### Post by z61P on 2011-09-15
I'm running the LTS server package (10.04). The system has been running great for about a year. However, when I came into work yesterday, the following was on the monitor: 
 
>  
Gave up waiting on root device. Common problems: 
- Boot args (cat /proc/cmdline) 
...
- Missing modules (cat /proc/modules; ls /dev) 
 
ALERT! /dev/disk/by-uuid/xxxx does not exist. Dropping to a shell! 
 
Busy Box v1.13.3 ....
 
(initramfs)_ 
 
 
The system has two (2) HDDs; one for Ubuntu stuff, and the other is a "dedicated" drive that has files accessed by the Samba server we run. The Samba drive was (IIRC) formated as a Windows file system of some sort (but I'm not 100% on this). However, I assume since the system can't find the root device, it is the "Ubuntu HDD" that the system cannot locate; i.e. the disk it boots from, aka sda1. 
 
I booted from an installation CD, and ran fsck on sda1 with result: "clean". I was also able to mount sda1, and browse around the file system. 
 
I'm not sure what to do from here. Some have suggested editing config files, while others have found success doing a kernel upgrade. I hate to do anything without a clear understanding of what I'm doing. 
 
Could someone please point me in the right direction to get this resolved? 
 
Gracie!

---

### Post by RealityMaster on 2011-09-16
I would start by seeing if the drive uuid in fstab is the same as the system is actually reporting (when booting to cd...)

---

### Post by z61P on 2011-09-19
> **RealityMaster said:**
> I would start by seeing if the drive uuid in fstab is the same as the system is actually reporting (when booting to cd...)
 
This appears to be at least part of the problem. When I checked /etc/fstab, the contents were: 
 
```
 
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

```
 
That is the entire file - it would appear that it has been altered/corrupted, perhaps during a power outage? Point is that my root partition is not even listed in /etc/fstab... wonder how that happens?? 
 
/etc/fstab was apparently created during the install process (about a year ago), but I can find no backup file. 
 
More to the point, "How do I fix my /etc/fstab file?" 
 
Danke,
z61P

---

### Post by WorMzy on 2011-09-19
To fix your fstab file, we'll need some more info.

Post the output of the following command:

```
sudo blkid -c /dev/null
```

---

### Post by z61P on 2011-09-19
> **WorMzy said:**
> To fix your fstab file, we'll need some more info.
 
Post the output of the following command:
 
```
sudo blkid -c /dev/null
```
 
Apologies, but I botched my earlier post - I was looking at the wrong /etc/fstab file! I can mount the HDD partition /dev/sda1 from the Live CD, and when I looked in that /etc/fstab file, I found the following entry: 
 
```
 
# / was on /dev/sda1 during installation 
UUID=41225f87-c0f8-44a3-86a1-f3d2d9078633  /  ext4  errors=remount-r0  0  1

```
 
Sorry for the confusion, but now I am truly confused... if the /etc/fstab file has the correct UUID, why can the system not find it at boot time? 
 
Thanks!

---

### Post by WorMzy on 2011-09-19
Uh.. did you type that out by hand? Because "errors=remount-r[COLOR="Red"]0[/COLOR]" should be "errors=remount-r[COLOR="Red"]o[/COLOR]". If the file says "errors=remount-r0", then make sure to fix that.

That error itself wouldn't cause any problems (the kernel would, at most, just post an error message, then continue booting) but it's worth fixing in any case.

As for why it's not finding it at boot time, there could be a number of reasons. Are you certain that the UUID in fstab is exactly the same as the one listed by the blkid command I posted earlier? If the UUID has changed (for whatever reason), then the fstab file will need to be updated, as well as grub's grub.cfg (via update-grub).

If the UUID is definitely correct, then there may be a problem with the partition. Check it with e2fsck (make sure that it's not mounted before you do so)

```
sudo e2fsck -fp /dev/sd[COLOR="Red"]##[/COLOR]
```

If the file system checks out fine, then the only other thing I can think of is that the initial ram disk (initrd) is damaged; in that case, try booting into an earlier kernel.

---

### Post by z61P on 2011-09-19
Yes - I mis-typed -ro as -r0 (sorry about that). 

The UUID in fstab is exactly the same as the one provided by blkid:

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="41225f87-c0f8-44a3-86a1-f3d2d9078633" TYPE="ext4" 
/dev/sda5: UUID="c2a5e58a-8e0f-425a-984d-585c6adb33f2" TYPE="swap"
```  

# / was on /dev/sda1 during installation
UUID=41225f87-c0f8-44a3-86a1-f3d2d9078633 /               ext4    errors=remount-ro 0       1

After unmounting /dev/sda1 in "Disk Utility" app, I ran e2fsck: 

```
ubuntu@ubuntu:~$ sudo e2fsck -fp /dev/sda1
/dev/sda1: 391220/29786112 files (0.1% non-contiguous), 3030975/119124736 blocks
```

How do I boot into an "earlier kernel"? 

Thank You

---

### Post by WorMzy on 2011-09-19
Press and hold down shift immediately after your PC POSTs (when it first turns on), and you should be presented with the grub menu. From there, you should be able to select a different (older) kernel to the default, and boot into that instead.

[The wiki page]("https://help.ubuntu.com/community/Grub2") has more info about that.

---

### Post by drs305 on 2011-09-19
Another option to try to get it to boot from the grub menu is to edit the menuentry (press 'e') and:

1. Remove the 'search' line entirely by holding down the DEL key on the line. 
2. Cursor to the 'linux' line and change
> root=UUID=
to 
root=/dev/sda1 # or the applicable partition designation
Press CTRL-x and see if it boots.

---

### Post by z61P on 2011-09-19
> **WorMzy said:**
> Press and hold down shift immediately after your PC POSTs (when it first turns on), and you should be presented with the grub menu. From there, you should be able to select a different (older) kernel to the default, and boot into that instead.
 
[The wiki page]("https://help.ubuntu.com/community/Grub2") has more info about that.
 
This didn't seem to work: I selected the "Linux 2.6.32-32-server" option which was one down from "Linux 2.6.32-33-server", but the system still failed to boot (wound up in initramfs again). 
 
Should I try one of the "Recovery" kernels?

---

### Post by z61P on 2011-09-19
A new item of information: 
 
I selected one of the "recovery" kernels to boot from. This generated a lot of text on the screen that flew by, but things slowed, and then stopped when the following lines appeared: 
 
```
 
ata6: softreset failed (device not ready) 
 
...
 
ata6: reset failed, giving up

```
 
Does that shed any light?? 
 
Thanks

---

### Post by z61P on 2011-09-19
> **drs305 said:**
> Another option to try to get it to boot from the grub menu is to edit the menuentry (press 'e') and:
 
1. Remove the 'search' line entirely by holding down the DEL key on the line. 
2. Cursor to the 'linux' line and change
 
Press CTRL-x and see if it boots.
 
 
I tried this, but it also failed to boot the system... 
 
Am I totally screwed, or can I recover from this?

---

### Post by drs305 on 2011-09-19
> **z61P said:**
> I tried this, but it also failed to boot the system... 
 
Am I totally screwed, or can I recover from this?

Those were just the simple fixes. If you boot a LiveCD and download/extract/run the boot info script and post the contents of RESULTS.txt we may be able to see what is going on. Click the "BIS" link in my signature line to take you to the script page.

Alternatively, you could try the Boot Repair Tool. It's a GUI app that is often successful. It can also grab the BIS if it doesn't work.
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by WorMzy on 2011-09-19
This is an odd problem. There are quite a few posts regarding your "ata softreset failed" problem, and I can't find anything conclusive about it. It *may* be a sign of hardware failure, but I don't think that's the case here (as you can still use the PC in a Live environment, run fsck on the affected disk's partitions, and access the initrds that are actually on the partitions)

When you're booted into the initrds, what shows up when you run
```
ls /dev/disk/by-uuid
```

---

### Post by z61P on 2011-09-22
> **drs305 said:**
> Those were just the simple fixes. If you boot a LiveCD and download/extract/run the boot info script and post the contents of RESULTS.txt we may be able to see what is going on. Click the "BIS" link in my signature line to take you to the script page.

Alternatively, you could try the Boot Repair Tool. It's a GUI app that is often successful. It can also grab the BIS if it doesn't work.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Sorry for the delay - I tried Boot Repair Tool first, and the sequence was this: 
1. d/l and ran BRT from Live CD. It instructed me to run in a 64-bit environment (?!) 
2. d/l and booted from the Ubuntu Secure 64-bit CD; ran Boot Repair Tool; it ground away for a few minutes, and said it repaired something
3. Tried booting from HDD (sda1), but wound up in initramfs - just as before (i.e. no diffs as far as I can tell) 

So I rebooted using the Ubuntu Secure 64-bit CD again, and ran BIS. I've attached the RESULTS.txt file, but I don't see anything in in it that looks like a smoking gun. 

Thanks again for your help, and please let me know if there are other things to try. 

z

---

### Post by z61P on 2011-09-22
> **WorMzy said:**
> This is an odd problem. There are quite a few posts regarding your "ata softreset failed" problem, and I can't find anything conclusive about it. It *may* be a sign of hardware failure, but I don't think that's the case here (as you can still use the PC in a Live environment, run fsck on the affected disk's partitions, and access the initrds that are actually on the partitions)

When you're booted into the initrds, what shows up when you run
```
ls /dev/disk/by-uuid
``` 

Hmmm... not sure I'm doing what you asked, but from a terminal window while running from the Ubuntu Secure 64-bit LiveCD, here's what I get: 

```
ubuntu@ubuntu:~$ ls /dev/disk/by-uuid
41225f87-c0f8-44a3-86a1-f3d2d9078633  c2a5e58a-8e0f-425a-984d-585c6adb33f2
ubuntu@ubuntu:~$
```

---

### Post by drs305 on 2011-09-23
I can't see any problems in your RESULTS.txt output.

You have already done the things I would recommend:[LIST]
[*]fsck the partition to make sure there are no errors
[*]try other kernels
[*]the system is attempting to boot and no grub prompt, so it's finding the /boot/grub menu and files
[*]I don't think it's a bad initrd file since you have tried other kernels
[/LIST]

I am not familiar with the 'ata' error, but that is probably what I would try to learn more about.

We don't see this problem much any longer, but here is a similar problem and solution regarding the ALERT! message:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix")

---

### Post by z61P on 2011-09-23
I tried the minix boot problem fix, but it failed to yield any improvement. And, I've been unable to locate anything specific or useful wrt the ata error. 
 
This is so frustrating - the "visible" part of the file system appears to be completely intact, but it just won't boot. I tried running Boot Repair Tool again - this time I checked the "Restore MBR" option in the Advanced menu. Upon re-starting, I got the error message from the BIOS that the Opertaing System was missing (?!). I re-booted with the LiveCD, ran Boot Repair Tool again using the default option, but after trying to boot from HDD, I only got the initramfs prompt again. 
 
This may be insoluble - it certainly seems so now. Unless there are some other things to check, I need to move on, and try to restore this system. Along those lines, I am contemplating the following: 
 
1. Install a new HDD alongside the existing HDD, and install the same OS (10.04.3 Server 64) on the new HDD. If the system will boot from the new HDD, this would suggest that the problem is somewhere on the old HDD. 
 
2. Copy config files from the old HDD to the corresponding location on the new HDD. 
 
Q: is there a quick and clever way to do this without manually copying files from one drive to the other? 
 
Any other analysis or comments? 
 
Thanks Again! 
 
 
2.

---

