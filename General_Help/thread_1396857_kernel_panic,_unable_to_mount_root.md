---
title: "kernel panic, unable to mount root"
date: 2010-02-02
forum: General Help
---

### Post by Nightstalker2 on 2010-02-02
I recently (a couple weeks ago) installed Ubuntu on my desktop computer dual booting with Win XP (which I am using right now). I used Wubi to install it, and everything went fine. I used Ubuntu without a problem up until a few days ago. I am using an install of Ubuntu (I am not running it off a disc, USB drive or through the Wubi software). 

I restarted my computer after using Ubuntu constantly for the time I've had it installed. It booted into Win XP (because it was first on the list where you select which OS to load) so I restarted again and tried to boot into Ubuntu. Instead of working, it gave me the error "Kernel panic - not syncing: unable to mount root" or something like that. So, I restarted again, and it was the same thing. I restarted in recovery mode, and it was the same thing. What is wrong with it?

---

### Post by Nightstalker2 on 2010-02-03
bump...

---

### Post by dnvikram on 2010-02-03
1)It may be an issue with the /boot/grub/menu.lst entries.Check this in the recovery mode.
2)Grub may need to be re-installed (or) /boot restored.
3)Its possible that that RAM Disk image (initrd.img) somehow got corrupted.Recreating it may fix the issue,if all the above fails.

Try this and let me know.

---

### Post by Nightstalker2 on 2010-02-05
How do I do those things? I am not a super advanced computer user, so relatively basic instructions would be most helpful.

---

### Post by amsterdamharu on 2010-02-05
When you're in the boot menu goto the entry for ubuntu and press e.

There should be a line like:

linux    /boot/vmlinuz-2.6.32-12-generic **root=UUID=be36ec91-0c3f-416f-86d5-6dc34684c00a** ro   quiet splash

or

kernel    /boot/vmlinuz-2.6.32-12-generic **root=UUID=be36ec91-0c3f-416f-86d5-6dc34684c00a**  ro   quiet splash

the root part indicates your linux root filesystem. Can you post this?

I think wubi install creates a virtual drive on your Windows partition so Ubuntu doesn't get its own partition but a big file and uses that as it's partition. If that file is corrupt than you're out of luck. Make some space for Ubuntu and install it on it's own partition.

---

### Post by Nightstalker2 on 2010-02-05
The line is:

linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 loop=/ubuntu/disks\ /root.disk ro quiet splash

... which appears to be quite different from what you posted it seems

---

### Post by amsterdamharu on 2010-02-05
It's a wubi install, that means there is no partition for ubuntu. Instead Ubuntu uses a big file on the windows partition for it's partition.

There should be a file C:\ubuntu\disks \root.disk

Assuming C: is the first partition on the first harddisk.

Strange that there is a space in the disks directory name. You can check in windows if this is correct. If it's not then post the correct path to that file.

In the boot menu you can edit that line and take out the space so it will look something like this:

linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash

---

### Post by Nightstalker2 on 2010-02-05
Hmm....turns out the random back slash was just to indicate that that text was continuing on another line, so the line you told me to put in there is already in there.

---

### Post by amsterdamharu on 2010-02-06
Can you start the computer form the Ubuntu installation disk and run live mode? I think the menu entry is called try Ubuntu or something like that.

Then mount the big file on your windows drive and see if anyting goes wrong, copy and paste the following commands in a terminal in Ubuntu (running off the cd).```

sudo mkdir -p /media/WindowsXP
echo "Mounting NTFS Partition"
sudo mount -t ntfs /dev/sda1 /media/WindowsXP
sleep 1
sudo mkdir -p /media/root.disk
echo "Mounting Wubi Disk"
sudo mount -o loop /media/WindowsXP/ubuntu/disks/root.disk /media/root.disk
sleep 1
echo "Done :)"
gksu nautilus /media/root.disk

```

Post any errors or warnings you might get, the terminal allows you to copy and paste what's in there.

---

### Post by Nightstalker2 on 2010-02-08
```
ubuntu@ubuntu:~$ sudo mkdir -p /media/WindowsXP
ubuntu@ubuntu:~$ echo "Mounting NTFS Partition"
Mounting NTFS Partition
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/WindowsXP
ubuntu@ubuntu:~$ sleep 1
ubuntu@ubuntu:~$ sudo mkdir -p /media/root.disk
ubuntu@ubuntu:~$ echo "Mounting Wubi Disk"
Mounting Wubi Disk
ubuntu@ubuntu:~$ sudo mount -o loop /media/WindowsXP/ubuntu/disks/root.disk /media/root.disk
ubuntu@ubuntu:~$ sleep 1
ubuntu@ubuntu:~$ echo "Done :)"
Done :)
ubuntu@ubuntu:~$ gksu nautilus /media/root.disk
(nautilus:3698): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3698): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3698): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3698): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

That is what I got when I copy pasted what you posted.

Also, is there any way of installing Ubuntu directly on the hard drive (not a file in Windows) without losing all I have done in the Wubi installed version?

---

### Post by amsterdamharu on 2010-02-08
Strange you had no problem mounting the root.disk but at boot time it isn't working. Paths look ok too.

As for installing you could try creating partitions, mounting root.disk, copy all to the partition except /sys, /mnt and /media (you can create empty directories with those names. Tell grub where to find the partition and boot it.

Creating a partitions (swap and filesystem ext3):
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
swap size is about twice your memory
filesystem or root system minimal 8G

Mount root.disk, you've just done in previous post.

Copy all, you can use nautilus.

Telling grub you need to post the output of "sudo fdisk -l"

Edit fstab to tell ubuntu where the root system is and where the swap is.

---

### Post by Nightstalker2 on 2010-02-09
Errr, on second thought, I will hold off on installing Ubuntu to its own partition since I am likely to screw more things up if I try that.

What should I do next in terms of the kernel panic?

---

### Post by amsterdamharu on 2010-02-09
Well you can mount the root.disk file so that file doesn't seem to be corrupt and the entry in grub menu is correct.

Did you run an update recently? If so see if there are older kernels to boot (boot menu will show older kernels). Try booting the older kernel.

Did you change any hardware?

---

### Post by chuckheron on 2010-02-10
I'm having the same problem on my wife's laptop..  (a wubi installation)
I installed updates, and got a new kernel  ( -19 ) and I get the kernel panic when I start with that (regular and recovery mode)
I can boot to the previous kernel (-17).
I looked at the grub.cfg, and it didn't appear that there was anything different between the -19 menu and the -17 menu:

> 
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 88185c5d185c4bf6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 88185c5d185c4bf6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 88185c5d185c4bf6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}


Any help would be great..
Thanks
-chuck

---

### Post by amsterdamharu on 2010-02-10
Sometimes an update goes wrong, you can uninstall it and re-install it with synaptic package manager. If that doesn't fix it you can keep booting in the older kernel until a newer update fixes it.

---

