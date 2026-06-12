---
title: "sda1 corrupted and unmountable"
date: 2010-10-20
forum: General Help
---

### Post by TRouBLe32 on 2010-10-20
After a restart yesterday, my computer doesn't boot correctly...
After GRUB, it prints
```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target Filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_
```
and falls to the busybox prompt...

I booted a 10.10 live cd.

Here is the output of fdisk -l for /dev/sda
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e45d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8924    71681998+  83  Linux
/dev/sda2            8925        9179     2048287+  82  Linux swap / Solaris
/dev/sda3   *        9180       46149   296961525    7  HPFS/NTFS
/dev/sda4           46150       60801   117692190    7  HPFS/NTFS

```
sda1 is the root filesystem (Ubuntu 10.04)
sda2 is the swap
sda3 is a Win7 NTFS partition
sda4 is an NTFS partition with media files.
I can normally access sda2-4.


The problem is when i try
```
sudo e2fsck /dev/sda1
```
with any switch it prints:
```
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```
When i try to mount the disk, the console just hangs.(it doesn't become unresponsive, the cursor just goes to the next line and doesn't do anything else) I tried leaving it for about 15 minutes in case it was checking the disk but nothing happened.

I don't care about restoring the system (i was gonna reformat anyway), all I want is access the data so i can backup (mainly my firefox profile:P).

---

### Post by CharlesA on 2010-10-20
If you are still booted up into the livecd, post the output of these commands:

```
sudo lsof /dev/sda1
```

```
mount
```

---

### Post by TRouBLe32 on 2010-10-20
```

ubuntu@ubuntu:~$ sudo lsof /dev/sda1
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
      Output information may be incomplete.

```

```
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

---

### Post by CharlesA on 2010-10-20
Well it's not mounted. Try this:

```
sudo fsck -fC /dev/sda1
```

---

### Post by TRouBLe32 on 2010-10-20
Exactly the same thing as before:

```
ubuntu@ubuntu:~$ sudo fsck -fC /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```

---

### Post by CharlesA on 2010-10-20
That's so strange. Try rebooting and then booting on the livecd again.

If that doesn't work can you see if you can boot into recovery mode from the grub menu (hold down shift) and drop to a root prompt to run fsck.

---

### Post by TRouBLe32 on 2010-10-20
> **CharlesA said:**
> That's so strange. Try rebooting and then booting on the livecd again.

If that doesn't work can you see if you can boot into recovery mode from the grub menu (hold down shift) and drop to a root prompt to run fsck.

Same thing.

Tried lsof/fsck/mount. the same thing

Tried the command promt of GRUB but there's no fsck.

---

### Post by CharlesA on 2010-10-20
you'd have to select recovery mode and then select "drop to a root shell" or something like that.

You should have been able to run fsck from there.

---

### Post by TRouBLe32 on 2010-10-25
GRUB already has an entry for grub-rescue (with the parameter single instead of quiet and splash) but it does the same thing..
All i get is a busybox prompt.

---

### Post by CharlesA on 2010-10-25
I'd say it's hosed. You could try putting the drive in another machine and trying to run fsck from that machine.

---

### Post by fmigpaulo on 2010-10-27
I got the same problem. What happen has that my Ubuntu 10.10 was updating and then the daemon died (maybe because i was running firefox at the same time and there was a firefox update??).

With the daemon killed there was nothing i could do: opening terminal just open a grey background window, could't mount devices saying that they were read-only files, and to shut-down i had to use the shortcut that shows when ctrl-alt-del is hit because the other shortcut only display an empty dialog box.

---

### Post by d-keig on 2010-10-27
Exactly the same has just happened to me today. Windows portion still works absolutely fine so I don't think it's to do with the hard drive? 

HELP!

Edit: the only difference is last time I shut down, I shut down with no problems. Don't think I installed any major updates

---

### Post by d-keig on 2010-10-27
is there a way to see what process is keeping the fsck from running  and then kill that process? I have sda1 which is windows, sda2 - ubuntu and sda 3 which is swap. Fsck runs on sda1 with no errors, just gives a message saying everything is fine. SDA2 no luck and cannot run on sda3 as a swap portion.

---

### Post by fmigpaulo on 2010-10-27
```
lsof | grep sda2

##SIGTERM
kill process_id_nr
## OR
##SIGKILL
kill -9 process_id_nr
```

---

### Post by d-keig on 2010-10-27
Thanks, and that will just kill the process that's making it impossible to run fsck whilst booted from a livecd? Just want to know what I'm doing when I'm doing it!

---

### Post by d-keig on 2010-10-28
Ok, I tried it anyway and got this output:

ubuntu@ubuntu:~$ sudo lsof | grep sda2
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
      Output information may be incomplete.
jbd2/sda2  504       root  cwd       DIR       0,17      280          2 /
jbd2/sda2  504       root  rtd       DIR       0,17      280          2 /
jbd2/sda2  504       root  txt   unknown                                /proc/504/exe

So would I now do a kill process_504?

edit:

So I killed it, and now when running lsof....sda2 i get:

ubuntu@ubuntu:~$ lsof | grep sda2
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
jbd2/sda2  504       root  cwd   unknown                                /proc/504/cwd (readlink: Permission denied)
jbd2/sda2  504       root  rtd   unknown                                /proc/504/root (readlink: Permission denied)
jbd2/sda2  504       root  txt   unknown                                /proc/504/exe (readlink: Permission denied)
jbd2/sda2  504       root NOFD                                          /proc/504/fd (opendir: Permission denied)
ubuntu@ubuntu:~$

---

### Post by d-keig on 2010-10-29
bug reported [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/668561](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/668561)

---

### Post by KainBox on 2010-10-30
> **TRouBLe32 said:**
> After a restart yesterday, my computer doesn't boot correctly...
After GRUB, it prints
```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target Filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_
```and falls to the busybox prompt...

The problem is when i try
```
sudo e2fsck /dev/sda1
```with any switch it prints:
```
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```When i try to mount the disk, the console just hangs.(it doesn't become unresponsive, the cursor just goes to the next line and doesn't do anything else) I tried leaving it for about 15 minutes in case it was checking the disk but nothing happened.

I don't care about restoring the system (i was gonna reformat anyway), all I want is access the data so i can backup (mainly my firefox profile:P).


Hi i had the same problem yesterday, the fsck command didnt worked too, in my case the problem was that ubuntu live cd was auto mounting the partinion, so it fsck didnt worked.

But it worked when i tryed fsck command in slax.

Thx to tensorpudding from #ubuntu channel for helping me out to solve the problem

---

### Post by d-keig on 2010-10-30
> **KainBox said:**
> Hi i had the same problem yesterday, the fsck command didnt worked too, in my case the problem was that ubuntu live cd was auto mounting the partinion, so it fsck didnt worked.

But it worked when i tryed fsck command in slax.

Thx to tensorpudding from #ubuntu channel for helping me out to solve the problem

That fixed it! Thanks so much, such a simple workaround when you know how!

---

### Post by bacardiandwatermelon on 2010-11-01
Slax did the trick. You guys rock!!

---

### Post by alexstz on 2010-11-04
> **KainBox said:**
> But it worked when i tryed fsck command in slax.
Wow! Everything in this topic was the same for me one-in-one. Slax worked for me too, I'so happy!

---

### Post by rcrath on 2010-11-10
kainbox's slax trick did it for me too, after hunting for a solution for 8 hrs.  Thnx!  Glad to have my sys back.

---

### Post by th3fa7kid on 2010-11-16
i have the same problem. tried everything everyone has suggested on any forum with no luck. slax did nothing for me. i have also tried re-installing ubuntu and it just sits on the initial screen for hours. can someone please help a n00b? im about to give up on ubuntu

---

### Post by d-keig on 2010-11-16
Are you sure the error messages are exactly the same? It's just when it happened to me, there were alot of posts about similer error messages but not exactly the same. Slightly different messages needed different methods of fixing the problem.

If it is exactly the same then:

Does booting into different kernel versions at boot (via the grub menu) give you the same result?

What does fsck tell you when running it with slax? Does it say there are any bad blocks?

edit: Just read your post with a bit more care. Are you able to boot into other OS's if you have any on the hard drive?

---

### Post by pylover on 2010-11-16
I have this problem also.

disk cheking is a reqular utility, it is verry bad if ubuntu cannot check a disk , & cannot stop automount .

---

### Post by manuganji on 2010-11-16
charlesA, I tried many of these solutions but they didn't work. Guess what, my hard drive failed! I think that's why none of them worked. That Dell guy is going to replace my hard disk today. Is there any information I need to retrieve from it so that some other person may not end up searching the solution in the wrong place?

---

### Post by Jetro on 2010-11-18
I'm having the same problem here, and am prepared to go to the "Slax" stage. But what is "Slax"? :( It seems to me a whole new Linux distro...

The case: Ubuntu wrongly shutting down, Windows working nicely, having the exact same error message (and outputs from suggested terminal commands) as original poster.

---

### Post by Jetro on 2010-11-21
BumpTM

To specify: sda1 is where Ubuntu is. The disk is not mounted or not even listed in "Places" when I boot from live USB.
```
fdisk -l /dev/sda
Cannot open /dev/sda
```

```
sudo e2fsck /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
```

```
sudo lsof /dev/sda1
lsof: WARNING: can't stat() tmpfs file system /cow
Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
Output information may be incomplete.

```

```
mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb2 on /media/CD75-D5CA type vfat (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
```

```
sudo fsck -fC /dev/sda1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1
```

```

```
```

```
```

```

I'll start another thread... [http://ubuntuforums.org/showthread.php?p=10145991#post10145991](http://ubuntuforums.org/showthread.php?p=10145991#post10145991)

---

### Post by bosozokujin on 2010-12-07
I was wondering how you used slax to solve this problem? as I dont know how to go about the process. Thanks

---

### Post by vmenkov on 2010-12-23
> **bosozokujin said:**
> I was wondering how you used slax to solve this problem? as I dont know how to go about the process. Thanks

The suggestion was to download another version of UNIX (called Slax) from [http://www.slax.org/](http://www.slax.org/) , burn a CD (or prepare a USB device), and boot from that, instead of Ubuntu live CD. Supposedly it won't have the problem that Ubuntu live CD has, namely, trying to auto-mount the now-unmountable partition (sda1), failing, and just sitting there, in the process keeping sda1 "busy" and not accessible to e2fsck.

I wanted to try that, but could not burn a good CD (i.e., one, booting from which would be fully successful without I/O errors), presumably because the CD writer I was using wasn't good enough for the "troubled" computer's CD drive to fully read.

I wondered if I could just change the startup options for Ubuntu live CD (this is how: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) ) to tell Ubuntu, "please, don't touch /sda1 for now!" But adding  options such as "sda=noprobe" (or should it have  been "sda1=noprobe"?) to the boot command line seemed to have no effect whatsoever.

So I ended up using the alternative solution described at [http://sanjayak71.blogspot.com/2010/10/recovering-unmountable-partition-from.html](http://sanjayak71.blogspot.com/2010/10/recovering-unmountable-partition-from.html)  : basically, copying the entire /dev/sda1 to a huge disk file on another hard drive using the "dd" command, then running e2fsck on that** file,** and finally copying the "fixed" file back /dev/sda1 with "dd":
```

  #-- mount my other (good) hard disk drive
  sudo mkdir /mnt/b
  sudo mount /dev/hdb1 /mnt/b
  #-- copy 
  sudo dd if=/dev/sda1 of=/mnt/b/sda1.img
  #-- fix
  sudo e2fsck -y /mnt/b/sda1.img
  #-- once e2fsck completes successfully, move the data back
  sudo dd if=/mnt/b/sda1.img of=/dev/sda1 

```Even before moving the data back (the second "dd") one could temporarily mount the "fixed" file as a "loop mount" filesystem:
```

  sudo mkdir /mnt/loopa
  sudo mount -o loop /mnt/b/sda1.img /mnt/loopa

```in order to verify that the "fixed" file system would indeed have your files as you know them. (I would, however, undo this temporary mounting (with "sudo umount /mnt/loopa")  before doing the second "dd", to ensure I am not trying to copy a file system in an inconsistent state.

In Sanjay's post referred to above, he was, I think, using an external USB device instead of a second hard drive. But that wasn't an option for me, since all my external USB devices happened to be formatted with vfat, and could not create a fiel bigger than 4 GB.

In any event, this was a rather inefficient way for solving the problem (as compared to running e2fsck directly on the affected drive, if you could make it run!), since the rate of data transfer between drives with "dd" was under 0.5 gigabyte per minute on my machine, and for an entire partition that totals up to quite a bit of wait. But at least it worked.

---

### Post by sanjayak on 2010-12-28
> **vmenkov said:**
> The suggestion was to download another version of UNIX (called Slax) from [http://www.slax.org/](http://www.slax.org/) , burn a CD (or prepare a USB device), and boot from that, instead of Ubuntu live CD. Supposedly it won't have the problem that Ubuntu live CD has, namely, trying to auto-mount the now-unmountable partition (sda1), failing, and just sitting there, in the process keeping sda1 "busy" and not accessible to e2fsck.

I wanted to try that, but could not burn a good CD (i.e., one, booting from which would be fully successful without I/O errors), presumably because the CD writer I was using wasn't good enough for the "troubled" computer's CD drive to fully read.

I wondered if I could just change the startup options for Ubuntu live CD (this is how: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) ) to tell Ubuntu, "please, don't touch /sda1 for now!" But adding  options such as "sda=noprobe" (or should it have  been "sda1=noprobe"?) to the boot command line seemed to have no effect whatsoever.

So I ended up using the alternative solution described at [http://sanjayak71.blogspot.com/2010/10/recovering-unmountable-partition-from.html](http://sanjayak71.blogspot.com/2010/10/recovering-unmountable-partition-from.html)  : basically, copying the entire /dev/sda1 to a huge disk file on another hard drive using the "dd" command, then running e2fsck on that** file,** and finally copying the "fixed" file back /dev/sda1 with "dd":
```

  #-- mount my other (good) hard disk drive
  sudo mkdir /mnt/b
  sudo mount /dev/hdb1 /mnt/b
  #-- copy 
  sudo dd if=/dev/sda1 of=/mnt/b/sda1.img
  #-- fix
  sudo e2fsck -y /mnt/b/sda1.img
  #-- once e2fsck completes successfully, move the data back
  sudo dd if=/mnt/b/sda1.img of=/dev/sda1 

```Even before moving the data back (the second "dd") one could temporarily mount the "fixed" file as a "loop mount" filesystem:
```

  sudo mkdir /mnt/loopa
  sudo mount -o loop /mnt/b/sda1.img /mnt/loopa

```in order to verify that the "fixed" file system would indeed have your files as you know them. (I would, however, undo this temporary mounting (with "sudo umount /mnt/loopa")  before doing the second "dd", to ensure I am not trying to copy a file system in an inconsistent state.

In Sanjay's post referred to above, he was, I think, using an external USB device instead of a second hard drive. But that wasn't an option for me, since all my external USB devices happened to be formatted with vfat, and could not create a fiel bigger than 4 GB.

In any event, this was a rather inefficient way for solving the problem (as compared to running e2fsck directly on the affected drive, if you could make it run!), since the rate of data transfer between drives with "dd" was under 0.5 gigabyte per minute on my machine, and for an entire partition that totals up to quite a bit of wait. But at least it worked.

Glad to see my solution has helped you. Of course this is when you don't have any other option.

---

### Post by nutsy.ben on 2010-12-30
Well. Got the same problem.

My workaround was to remove the hard drive and plug it as a slave into an external computer. then switch it off and replug the hard drive in the first computer.

Would be happy if there is a solution working faster.

---

### Post by Supergamesoftoday on 2011-01-04
I followed what you did, seeing as I have been having the same error messages as evryone else. I downloaded and successfully booted up Slax off of LiveUSB. However, I get this message:
```
e2fsck -y -f -v /dev/sda1
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
```

Per the request, I tried e2fsck -b 8193:
```

e2fsck -b 8193 /dev/sda1
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
```

I have also tried e2fsck -p /dev/sda1 and have received the same result. My Ubuntu install is 10.04LTS and so it has ext4. Not sure if I'm supposed to specify somewhere that it is. 

Help!!

---

### Post by Lrpbpb on 2011-01-05
Supergamesoftoday, you ran e2fsck in /dev/sda1, but are you sure that is the correct drive?

Only asking because in my case I had a similar error, but it was because slax recognized my drive as "hda" instead of "sda" (like in ubuntu).

To know what drive is the right one, run:
```
fdisk -l
```This will give you a list of your drives and partitions. Check and make sure you are using the correct partition on the correct drive.

If it is the right drive, it could be a bad superblock, as it says in your prompt. Try running (e2)fsck with _another_ alternate superblock.

To find the backup superblocks run:
```
dumpe2fs /dev/sda"X" | grep -i superblock
```Now you  can use the backup superblock to check the filesystem using superblock  #"X" (warning do not run the following on mounted live  file system):
```
e2fsck -f -b "#" /dev/sda"X"
```Replace "#" with the superblock numer, and sda"X" with correct partition.
Source: [http://www.cyberciti.biz/faq/linux-find-alternative-superblocks/](http://www.cyberciti.biz/faq/linux-find-alternative-superblocks/)

Tell me if that solves the problem.

---

### Post by Supergamesoftoday on 2011-01-06
I am a moron.

You, sir/(madam?), are a genius. How bitingly obvious it was! fdisk -l indeed revealed the true path of my hard drive (/dev/hda1....not sda1), and I am now up and running as miraculously as the other success stories here.

For those that are interested, the reason I was using sda was because I had looked it up using disk utility in an Ubuntu Live CD, and I was indeed looking at my 38GB Linux partition, but apparently the naming convention must be slightly different.

I've been on Ubuntu for almost 3 full years now, and today I remembered why I joined Ubuntu. I love the fact that I can go to a thread that's several days old and get a response in under 24 hours. The Ubuntu community is the best in the world. It really leaves no reason NOT to go Ubuntu. You just don't get this kind of support anywhere else.

Thank you, Lrpbpb, and God Bless.

---

### Post by xcorpion on 2011-01-06
hi
i just step in
i m having a problem with my hp compaq cq41-208au
i was using win7 and then i install ubuntu 10.10 via internet.
after installing ubuntu it asks me for update and i accept it buh after it also ask me smthng grub and didnt notice what it says and just click restart
after i got a screen which says 
error : no such device : bed4e5bc-7d2e-486e-a365-14e5de8d236c
grub rescue>

<Note: i have two partitions sda1 sda2 both are HPFS/NTFS
and my win7 is install in sda1 and ubuntu in sda2 and sda1 is boot*

help me out plz

---

### Post by skpacman on 2011-01-30
:D tried from slax, worked perfectly!  good thing i have several flash drives to just throw stuff on!

):P

---

### Post by aslam on 2011-02-05
I have same problem. My ubuntu 10.10 ext4 partition is broken while updating (kernel update)
sudo fsck /dev/sda6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda6
Filesystem mounted or opened exclusively by another program?

I tried Slax but not for me Slax does not support ext4 filesystem

Now downloading pmagic 5.9 i got it from another howto. It says supports ext4.  I will try that will reply later

---

### Post by aslam on 2011-02-05
Parted Magic did the trick for me.  Successfully recovered ubuntu 10.10 using gparted within parted magic
Here is the link for parted magic [http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

---

### Post by renderhead on 2011-03-05
Solved - had similar issues with my Ubuntu 10.10 install. After an update (which appeared to go just fine) and reboot, arrived at the desktop - then system froze. I did a hard reset after a minute or two, and then same story as above - dropped straight to busybox. Ubuntu system partition 'busy' thanks to over-zealous automounting of unclean fs, fsck a no-go. Same automount hassles with LiveCD, tried Slax Remix (Slax doesn't support EXT4) - no fsck joy (same 'busy' message, though partition was not mounted - I assume same automount issue).

Finally tried sanjayak's creative solution ([http://sanjayak71.blogspot.com/2010/10/recovering-unmountable-partition-from.html]("http://sanjayak71.blogspot.com/2010/10/recovering-unmountable-partition-from.html")) using Ubuntu LiveCD (thanks to vmenkov for the link) with an external SATA HDD, and now everything is back and working just fine.

Thank you sanjayak! A seemingly extreme solution, but the only one I could get working.

---

### Post by erudite on 2011-03-20
> **aslam said:**
> Parted Magic did the trick for me.  Successfully recovered ubuntu 10.10 using gparted within parted magic
Here is the link for parted magic [http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

That did the trick for me too.  Thank you very much.  This the second time I've had this problem.  The first time I couldn't find a decent answer so I just reinstalled the whole OS.  Not sure why it is reoccuring though.  Hopefully it doesn't happen with 11.04.

---

### Post by fhucho on 2011-03-29
I have MacBook Pro 7.1 and have this problem. Slax doesn't boot (SCSI not supported), copy slax folder workaround doesn't work. Any idea what can I do?

---

### Post by fhucho on 2011-03-30
Parted Magic live CD and "e2fsck -f -y- v /dev/sda3" worked!

---

### Post by grizzles on 2011-04-03
> **fhucho said:**
> Parted Magic live CD and "e2fsck -f -y- v /dev/sda3" worked!

Thanks everyone, this worked for me as well on my gf's Samsung N210 running 10.10 Netbook Remix. 

I had issues getting Parted Magic to boot off a thumb drive as well, found [this thread]("http://forums.partedmagic.com/viewtopic.php?f=2&t=1430&start=30") in case anyone has that same issue

---

### Post by onivan on 2011-06-11
Hello!

There is a more simple way to fix the issue without booting to Slax. Just boot to "Rescue a broken system" from your Ubuntu LiveCD and simply choose "Do not use a root filesystem" and "Execute a shell in the installer environment" on the "Enter rescue mode" screens and you will get "No filesystems were mounted".

I had the same issue in my Ubuntu 10.10 running inside VirtualBox and could do fsck in this rescue mode.
Here the screencast [http://www.youtube.com/watch?v=ReKMtNihNMU](http://www.youtube.com/watch?v=ReKMtNihNMU) (watch the HD version)

---

### Post by Ticatla on 2011-06-13
> **onivan said:**
> Hello!

There is a more simple way to fix the issue without booting to Slax. Just boot to "Rescue a broken system" from your Ubuntu LiveCD and simply choose "Do not use a root filesystem" and "Execute a shell in the installer environment" on the "Enter rescue mode" screens and you will get "No filesystems were mounted".

I had the same issue in my Ubuntu 10.10 running inside VirtualBox and could do fsck in this rescue mode.
Here the screencast [http://www.youtube.com/watch?v=ReKMtNihNMU](http://www.youtube.com/watch?v=ReKMtNihNMU) (watch the HD version)


Ohh, good to know. It's a little bit late since that, but will definitely keep that in mind.

---

### Post by amicable on 2011-08-30
> **onivan said:**
> There is a more simple way to fix the issue without booting to Slax. Just boot to "Rescue a broken system" from your Ubuntu LiveCD

The simpler way is to create a Slax CD, believe me. I wasted hours on this stupid issue today. :-x

1. Ubuntu 10.04 LTS live CD does not contain a recovery mode ](*,) You get a splash screen telling you to run the live cd because you can then search the web for your problem and most likely fix it from the live cd. :-x Did someone write that just to annoy users?

2. Slax 6.1.2 is super tiny and will burn/download/transfer in a few moments compared to the bloated Ubuntu disc. :guitar:

From there, I could run e2fsck and had a fixed system in 10 seconds.

Slax looks like an excellent fast rescue system, full of utils and nothing pointless.

---

### Post by DimaRoUk on 2011-10-27
> **aslam said:**
> Parted Magic did the trick for me.  Successfully recovered ubuntu 10.10 using gparted within parted magic
Here is the link for parted magic [http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

Parted Magic worked for me as well. For my self I had to make some adjustments.

1. Used Universal USB installer as opposed to UNetbootin
2. Could not properly start the Parted Magic as it failed to draw the screen, both graphic option. But booted up in console.

From there fsck here I come!

---

### Post by jsalelle on 2011-11-04
Same problem for me: after an update or an improper shutdown, /dev/sda3,the / ext4 partition of my Ubuntu Maverick install was unable to be mounted and the system went to de ram shell state. Moreover I was unable to fsck the partition from an Ubuntu live CD.

The solution that worked for me was to boot with a Clonezilla live-cd to the shell prompt and then "e2fsck -f -y- v /dev/sda3" IT WORKED!!!:popcorn:

---

### Post by Kleber on 2011-11-25
Same problem for me: after  an improper shutdown, /dev/sda1,the / ext4 partition of my Ubuntu 10.10 install was unable to be mounted and the system went to de ram shell state. Moreover I was unable to fsck the partition from an Ubuntu live CD.

The solution that worked for me was to boot with a Slax live-cd ([http://www.slax.org/](http://www.slax.org/)) to the shell prompt and then "e2fsck -f -y- v /dev/sda1".

Thank you so much!

---

### Post by snooffy on 2011-12-05
I love you guys, SLAX did it for me... THANKS!

---

### Post by tamerlaha on 2012-04-03
Usb stick with Trinity rescue kit (trinityhome.org):

fsck /dev/sda* fix the problem.

Before i'm try a systemrescuecd ([www.sysresccd.org](www.sysresccd.org)) and liveUSB Xubuntu it says that partition is busy.

---

### Post by alecz20 on 2012-11-18
> **onivan said:**
> Hello!

There is a more simple way to fix the issue without booting to Slax. Just boot to "Rescue a broken system" from your Ubuntu LiveCD and simply choose "Do not use a root filesystem" and "Execute a shell in the installer environment" on the "Enter rescue mode" screens and you will get "No filesystems were mounted".

I had the same issue in my Ubuntu 10.10 running inside VirtualBox and could do fsck in this rescue mode.
Here the screencast [http://www.youtube.com/watch?v=ReKMtNihNMU](http://www.youtube.com/watch?v=ReKMtNihNMU) (watch the HD version)

How do you access the hidden option in the newer versions of Ubuntu? the only options I see are: Try Ubuntu and Install Ubuntu. There is no more System Rescue, Memtest, check disk, or other useful tools.

Also, to everyone else:
Ubuntu Live CD will NOT work as Recovery CD (the way most Live Linux CD's do.)

The problem is that Ubuntu tries to mount all the disks. Since one of the disks is corrupted, it won't mount it, but it will lock it in the hope that it will eventually be mountable.

Because of this, fsck cannot fix the disk (because it is auto-mounted and locked).

Most other Linux Live CD's will not mount all your disks, so you can do fsck on them.

Conclusion is that Recent Ubuntu Live CD's are not the ulimate Linux Live CD's anymore. Now you also need a separate Live CD to fix the Ubuntu corrupted partitions. Slax, among many is a good choice mainly beucause it's easy to install on a USB, and takes about 200 MB (faster download)

Way to go SLAX!

Shame on Ubuntu for not being able to fix itself :mad:!

---

