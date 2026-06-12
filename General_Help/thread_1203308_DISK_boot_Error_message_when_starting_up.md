---
title: "DISK boot Error message when starting up"
date: 2009-07-03
forum: General Help
---

### Post by thirdeye420 on 2009-07-03
Hi everyone,

Fired up my PC yesterday and was met with a "Disk Boot Failure." message.  I'm guessing my hard drive crapped out, but could it be something else?

---

### Post by blueridgedog on 2009-07-03
Make certain you bios is set to boot from the correct hard drive and that you have have no media (usb flash drives, cdrom disks, floppy disks) in the system.  If it still won't boot, then you can boot on a liveCD and we can try and mount the drive.

---

### Post by thirdeye420 on 2009-07-03
I can get it to boot with the live cd.  how do I mount the drive once Im booted up?  Is there a setting I have to modify in order to get it to boot from the HD?

---

### Post by akakingess on 2009-07-03
> **thirdeye420 said:**
> I can get it to boot with the live cd.  how do I mount the drive once Im booted up?  Is there a setting I have to modify in order to get it to boot from the HD?


I believe it would be ```
mount /dev/sda
```

or whatever the drive is listed/named as within your live CD.

akakingess

---

### Post by blueridgedog on 2009-07-03
> **thirdeye420 said:**
> I can get it to boot with the live cd.  how do I mount the drive once Im booted up?  Is there a setting I have to modify in order to get it to boot from the HD?

If you post the output of:

```
sudo fdisk -l
```

and 

```
mount
```

We can give you more specific mounting instructions.

---

### Post by thirdeye420 on 2009-07-03
here it is:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc70ec70e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        9836    79007638+  83  Linux
/dev/hda3            9837        9964     1028160    f  W95 Ext'd (LBA)
/dev/hda5            9837        9964     1028128+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/hda2 on /media/disk type ext2 (rw,nosuid,nodev)
ubuntu@ubuntu:~$

---

### Post by blueridgedog on 2009-07-04
Based on your post, you have one hard drive that has a single linux partition and an extended partition that is used for swap:

/dev/hda2 1 9836 79007638+ 83 Linux
/dev/hda5 9837 9964 1028128+ 82 Linux swap / Solaris

I also note that the LiveCD did not mount your Linux partition, so it may have errors.  What happens when you try and run the following:
```

sudo mkdir /mnt/hda2
sudo mount /dev/hda2 /mnt/hda2
```

---

### Post by thirdeye420 on 2009-07-04
ubuntu@ubuntu:~$ sudo mkdir /mnt/hda2
ubuntu@ubuntu:~$ sudo mount /dev/hda2 /mnt/hda2
ubuntu@ubuntu:~$

---

### Post by blueridgedog on 2009-07-04
Sorry, can you also post:

```
ls /mnt/hda2
```

That should be your hard drive, if it is, we need to find out why it can't boot.

---

### Post by thirdeye420 on 2009-07-04
ubuntu@ubuntu:~$ ls /mnt/hda2
bin    dev   initrd          lib         mnt   sbin  tmp     var
boot   etc   initrd.img      lost+found  proc  srv   usr     vmlinuz
cdrom  home  initrd.img.old  media       root  sys   usrlib  vmlinuz.old
ubuntu@ubuntu:~$

---

### Post by blueridgedog on 2009-07-04
Lets see if we can install grub to the file system.  Open terminal and do the following.
```

sudo grub
root (hd0,1)
setup (hd0)
quit
```

Then try and boot off of your hard drive.

---

### Post by thirdeye420 on 2009-07-04
that worked for me.  I'm back in business now haha.  thanks for your help.  it's much appreciated!

---

### Post by akakingess on 2009-07-04
> **blueridgedog said:**
> Lets see if we can install grub to the file system.  Open terminal and do the following.
```

sudo grub
root (hd0,1)
setup (hd0)
quit
```Then try and boot off of your hard drive.


Actually I want to thank you as well blueridgedog, cuz I did not know how to resetup grub on the hd and now I do just in case that happens to me. I love it when I learn something that I am pretty sure I am going to need to use someday. Thanks for your time and persistence/patience with us.

akakingess

---

### Post by blueridgedog on 2009-07-04
In case you don't know which drive is the boot drive and which drive has the boot files on them, these are the steps to use (I did not need all of these steps as I was able to see where the boot files were from the earlier posts):

Bootup a live cd, open a terminal and do the following.
```

sudo grub
```

This will result in a "grub>" prompt. At grub>. enter these commands
```

find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to use as the source for the new mbr.

Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Note, if you want to put the new mbr in another hard drive, you will need to adjust it accordingly.

Finally exit the grub shell
```

quit
```

---

### Post by akakingess on 2009-07-04
Cool, thanx again.

akakingess

---

### Post by thirdeye420 on 2009-07-12
well here i am again ....  tried to fire u p the PC this morning and guess what?  disk boot error message again.  So i tried the following suggestions listed above and here is what im getting:

when i get into the grub prompt and type "root (hd0,1)" i get "Error 21:  Selected disk does not exist."  

When I type "find /boot/grub/stage1"  I get "Error 15:  file not found".

any idea on whats happening here this time?

---

### Post by blueridgedog on 2009-07-12
> **thirdeye420 said:**
> 
when i get into the grub prompt and type "root (hd0,1)" i get "Error 21:  Selected disk does not exist."  

When I type "find /boot/grub/stage1"  I get "Error 15:  file not found".

any idea on whats happening here this time?

It looks on the surface as if your internal hard drive is not present.  While booted on the live CD, can you post the output of:

```
sudo fdisk -l
```

Your drive or its controller may have stopped working, or the cable may be bad or loose.

---

### Post by thirdeye420 on 2009-07-12
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$

---

### Post by TeamJ on 2009-07-12
> **thirdeye420 said:**
> I'm guessing my hard drive crapped out

I agree. try and use the Live CD to retrieve files. If the HDD isn't broken, it may be the os has randomly died, just reinstall

---

### Post by blueridgedog on 2009-07-12
> **thirdeye420 said:**
> ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$

Your internal drive is no longer visible.  Either it stopped working or the controller stopped working.  I would check the cable to be certain and try and put it on another port.

---

### Post by thirdeye420 on 2009-07-12
ok, well i have 2 hard drives, so the 80gb one i had is the one that crashed.  so I took it out of my computer and took it apart and found that the spindle head thing broke.  SO i put my 20 gb one in, then run livecd to install on it.  when i get to the partition prompt, nothing shows up.  whats up now?

---

