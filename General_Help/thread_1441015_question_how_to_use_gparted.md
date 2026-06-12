---
title: "question how to use gparted"
date: 2010-03-28
forum: General Help
---

### Post by reza.adinata on 2010-03-28
Hallo,

I have a question about using gparted. I am currently using windows 7 and ubuntu 9.10 in my computer. Before that, I used also windows vista and wubi-installed ubuntu inside the windows vista. After trying to reformatting everything, I ended up having windows 7 and ubuntu 9.10 (dual boot). However, on the first boot menus, I still have options of windows vista, and old ubuntu. I tried to use gparted, and tried to -with force- wipe out the windows vista and ubuntu which is also installed inside the vista, however I am getting very confused after looking at the partitons

To make it more clear, please see the image of the gparted software below

[http://i41.tinypic.com/2lxdvt5.png](http://i41.tinypic.com/2lxdvt5.png)

I want to keep my windows 7, ubuntu 9.10 (new one, not the one which is inside the vista), want to wipe vista+ubuntu9.10(old) . I also wanted to keep documents (/dev/sda5). I want to format the unecessary partition, and merge everyting so I have more space for new ubuntu 9.10. Can anyone point out how to do this? Please point out which partition I can delete, because as you can see in the image, I have some stuffs that are the same (like swap in /dev/sda7 and /dev/sda11). Sorry for my bad english, I hope it is clear enough..



Thank you for your helps.

---

### Post by drs305 on 2010-03-28
The first thing is to do all this from the LiveCD. Any partition you want to delete must be unmounted, and you will most likely need to unmount any partitions higher than the one you want to delete (inluding swap). Partitions that are mounted have the "key" icon next to them in the lower panel.

Even on the LiveCD, you will need to unmount swap. You do this by highlighting the swap partition and then from the gparted menu "Partition, swapoff".

Since / is currently mounted, your current Ubuntu install is on sda10 (assuming this is the one you want to keep).

You also have two swap partitions, sda7 and sda11. You only need one of them. sda11 is currently mounted, so that is the one I would keep.

---

### Post by NiGhtMarEs0nWax on 2010-03-28
if you are referring to old boot options in grub, grub has a configuration file stored in /boot in ubuntu.

first backup the config file:
```
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.bak
```

then use gedit to modify it:
```
sudo gedit /boot/grub/grub.cfg
```

**BE CAREFUL** if you mess up in here yo wont be able to boot your machine without restoring the backup file.

it looks complicated at first but its not, if you scroll down you will see the blocks of code for each operating system.

```
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 24420e75-5730-4529-8434-f047727be5cd
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=24420e75-5730-4529-8434-f047727be5cd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
```

is the block for the most recent kernel version, notice the very outer { }, they signify the block.




```
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 24420e75-5730-4529-8434-f047727be5cd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=24420e75-5730-4529-8434-f047727be5cd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
```

is an old kernel.



```

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 22a02f5da02f3727
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```


is windows xp.


GL.

---

### Post by reza.adinata on 2010-03-28
> **drs305 said:**
> 

You also have two swap partitions, sda7 and sda11. You only need one of them. sda11 is currently mounted, so that is the one I would keep.

Sometimes, when I am running gparted, both sda7 and sda11 (swap) both does not show any key next to it. It is kinda strange. Is it ok if i just delete one of them (maybe I'll remove sda11), do I have to configure anything afterwards, or the ubuntu can detect which partition of the swap he is going to use (incase that it is not a proper swap partition of the ubuntu that I am currently using).

---

### Post by drs305 on 2010-03-28
> **reza.adinata said:**
> Sometimes, when I am running gparted, both sda7 and sda11 (swap) both does not show any key next to it. It is kinda strange. Is it ok if i just delete one of them (maybe I'll remove sda11), do I have to configure anything afterwards, or the ubuntu can detect which partition of the swap he is going to use (incase that it is not a proper swap partition of the ubuntu that I am currently using).

You would have to reconfigure /etc/fstab as a minimum to point it to your new swap partition if it changes from the current sda11. It appears that sda11 is your working swap partition, so your files won't need to be edited if you are using UUIDs and you delete other partitions and continue to use sda11 as your swap file.

If you have any questions once you have the extra partitions deleted/moved, you can post the contents of your fstab and partitons with these commands and we can help you make sure it's correct:
```

sudo fdisk -l  # Lowercase L
cat /etc/fstab
mount

```

---

### Post by reza.adinata on 2010-03-28
> **drs305 said:**
> If you have any questions once you have the extra partitions deleted/moved, you can post the contents of your fstab and partitons with these commands and we can help you make sure it's correct:
```

sudo fdisk -l  # Lowercase L
cat /etc/fstab
mount

```

Hi,

I messed everything up. I tried to delete some partitions, and I ended loosing my boot loader. So again, I installed a new ubuntu, and it turned out that my partition is getting worse. The previous ubuntu was /dev/sda8, and I format it into ntfs ( hoping that I can merge it with drive DOCUMENT in windows 7). Is this a correct proceddure?  Can you please point out how to format unneceassry partitions, cause I am loosing so many capacities after reinstalling everyting, it is a total mess.

so for sudo fdisk -l # Lowercase L
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        5320    41189626+   7  HPFS/NTFS
/dev/sda3            5321       13846    68485095    f  W95 Ext'd (LBA)
/dev/sda4           13903       14594     5544960   17  Hidden HPFS/NTFS
/dev/sda5            9247       12724    27926186    7  HPFS/NTFS
/dev/sda6            7292        8833    12386083+  83  Linux
/dev/sda7            9160        9246      698796   82  Linux swap / Solaris
/dev/sda8           12725       13846     9012433+   7  HPFS/NTFS
/dev/sda9            5321        7202    15117102   83  Linux
/dev/sda10           7203        7291      714861   82  Linux swap / Solaris

```


cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=af378c76-f7f6-4350-9e32-65e5150db603 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=f37e897c-597b-42f2-bb92-5f6faae0622b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

mount

```
/dev/sda9 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dana/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dana)


```

Thank you

---

### Post by drs305 on 2010-03-28
The less complicated way by reinstalling Ubuntu:
1. Backup any important data in partitions you move/delete/resize.
2. Leave partitions 1-4 alone. (Note sda4 is at the far right end of the drive).
3. With gparted, delete sda 6,7,8,9,10.
4. From inside Windows, use a Windows defrag utility to defrag sda5 (DOCUMENT).
5. Move sda5 all the way to the left end of the extended partition (sda3). It should now appear to touch sda2. 
6. Expand sda5 to the right, making it as large as you want.
7. Reinstall Linux, using the unallocated space.


The complicated way without reinstalling:
We can sort this out although after you delete things and then expand/move partitions it might be just as fast to reinstall again. But here is what you can do to restore order to what you have.

First, make backups of any important data you have on any partitions you plan to move (or obviously, delete).

Second, I'm not going to recommend any actions for sda1-4. Leave them alone.

sda5 is your DOCUMENT partition? If not, don't go any further.

sda6 and sda7 were from your previous install, and sda8 is empty if I understand you correctly. 

You can delete sda6, sda7, and sda8 if you are sure you don't need any of the contents. This will leave a large section of unallocated space.

If sda5 is DOCUMENT, and you want to expand it, now would be the time. Since this is a Windows partition, it would be best to go into Windows and use it's utilities to defrag the partition and move it to the left - so it is at the right end of the extended partition (sda3) and appears to touch sda2. Then expand it to the right to add as much extra space as you want. You should use Windows utilities to defrag sda5 and move it, but except for the defrag the rest can be done with gparted from the LiveCD if you prefer.

This should leave you with sda partitions 1-5. Depending on whether you used all the empty space for sda5, you would then have sda9 as your Ubuntu partition, and sda10 as swap.

Let's stop there and see what you have done. Post the results of the following, and another screenshot would be helpful:
```
sudo blkid -c /dev/null
cat /etc/fstab
fdisk -l
mount

```

This can all be very confusing. Again, the first approach would probably be quicker and easier.

If you have questions, ask before doing!

---

### Post by reza.adinata on 2010-03-29
> **drs305 said:**
> The less complicated way by reinstalling Ubuntu:
1. Backup any important data in partitions you move/delete/resize.
2. Leave partitions 1-4 alone. (Note sda4 is at the far right end of the drive).
3. With gparted, delete sda 6,7,8,9,10.
4. From inside Windows, use a Windows defrag utility to defrag sda5 (DOCUMENT).
5. Move sda5 all the way to the left end of the extended partition (sda3). It should now appear to touch sda2. 
6. Expand sda5 to the right, making it as large as you want.
7. Reinstall Linux, using the unallocated space.


If you have questions, ask before doing!

Yes, my mistake.. I should have asked before doing.:(

Now I will ask. 
So according to what I understand from what you've written above, first, I have to use gparted (using live cd) to delete sda 6,7,8,9,10. I will try it, but doesn't that mean that if I do that, means I also delete the boot loader, and I can't go to windows?). Is this correct? I am sorry if I ask these basic questions.. I don't have any other harddisk, so I hope I won't do any mistakes.. :(

This is what I capture from the current partition while still using my ubuntu, I hope you get what I am worried about.

[http://picfront.de/d/7wRJ](http://picfront.de/d/7wRJ)

Thank you

---

### Post by drs305 on 2010-03-29
> **reza.adinata said:**
> Yes, my mistake.. I should have asked before doing.:(

Now I will ask. 
So according to what I understand from what you've written above, first, I have to use gparted (using live cd) to delete sda 6,7,8,9,10. I will try it, but doesn't that mean that if I do that, means I also delete the boot loader, and I can't go to windows?). Is this correct? I am sorry if I ask these basic questions.. I don't have any other harddisk, so I hope I won't do any mistakes.. :(

This is what I capture from the current partition while still using my ubuntu, I hope you get what I am worried about.

[http://picfront.de/d/7wRJ](http://picfront.de/d/7wRJ)

Thank you

After you delete those partitions you will not have the GRUB bootloader until you reinstall. During the reinstall, Grub 2 will be placed on the new partition and it will recognize the Windows partition. Sometimes it doesn't recognize it immediately and you have to run "sudo update-grub" once after the install for Grub 2 to find Windows. As long as you have a working Ubuntu installation CD you should be fine.

Should you still not be able to get into Windows following a reinstall, here is a link that can restore Windows as long as you have the Windows CD:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by reza.adinata on 2010-03-30
Yes, I managed to do everything, thank you for the assistance.:D

---

