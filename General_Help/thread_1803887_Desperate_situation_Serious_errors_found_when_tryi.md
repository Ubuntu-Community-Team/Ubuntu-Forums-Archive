---
title: "Desperate situation: Serious errors found when trying to mount system at startup"
date: 2011-07-14
forum: General Help
---

### Post by gluon90 on 2011-07-14
I had moved my home folder to a second hard drive recently, meaning that the os was on one disk and the home directory being on the other. I had few problems with the move save for one. At startup I was met with an error indicating that a serious problem had been found when trying to mount 'media/home/....' or something along those lines. I was offered three options, either ignore the error, skip mounting, or attempt to recover it manually. When I chose to ignore the error, the computer proceeded to boot up normally. At of curiosity, I tried to fix this seemingly benign error.

Looking around online I found a suggestion to regenerate my initramfs using the command 'sudo update-initramfs -u'. I entered the command and it regenerated whatever it did. I restarted my computer only to be met with the same error, but upon choosing to ignore the issue, I was led to a black screen indicating the loading of various things only to have it stop completely, and as such, the boot fails, leaving me unable to access my computer.

As you can probably tell, I'm a newbie when it comes to linux in most respects. The only way I'm able to post this is with the live cd. Any help is greatly appreciated. I need this computer and everything that's on it.

---

### Post by gluon90 on 2011-07-14
If any one can help in any way, please do.

---

### Post by CattyNebulart on 2011-07-14
can you post the content of '/etc/fstab' and the results of running the 'mount' command? Of course you need to pull the fstab file from the actual root drive, not the one that the liveCD is using.

To run the mount command from the kernel with issues you could try to boot and when you get the black screen try hitting ctrl+alt+F1, or ctrl+alt+F2. These should bring up a text console that you can log into and use.

Also some more details on the error would be helpful.

Explanations:
/etc/fstab is the file that controls how and where drives are mounted. This will let us see what your system is trying to do.

Running mount without any arguments lists the currently mounted drives and their state.

update-initramfs -u will update a mini-me version of linux whose job it is to start the main system. Wikipedia has a decent article on it. [http://en.wikipedia.org/wiki/Initrd](http://en.wikipedia.org/wiki/Initrd)
I have never had to update it before so I am not sure of all the details.

Ctrl+alt+F1; This will switch you to a different tty, usually tty 1 or 2 is used for displaying boot information and error messages and tty7 and up are where the graphical (xserver supported) interfaces exist with usually only tty7 existing, though if you choose to switch users and create a new session it will usually allocate the next tty (8 in this case). You accsess the tty by ctl+alt+and the F key for the numbered tty you want to use.

---

### Post by gluon90 on 2011-07-14
Here are the contents of /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d6747d51-6b68-414b-8f29-eef279347759 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ba228596-e5b3-4c9a-9355-e5fb33e3ce93 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0   
/dev/sdb1    /media/75c081ff-d71e-4465-bf01-b8c029c8216e   ext4    defaults     0        2
/dev/sdb1 /home ext4 nodev,nosuid 0 2

And here are the results of running mount:

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb1 on /home type ext4 (rw,nosuid,nodev,commit=0)
/dev/sdb1 on /media/75c081ff-d71e-4465-bf01-b8c029c8216e type ext4 (rw,commit=0)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)

As for the error, it simply states the serious errors were found when mounting /home. Despite this, failsafe mode works fine and all of my files in /home are completely intact.

---

### Post by gluon90 on 2011-07-14
-Bump-
Any tips on where to go from here would be greatly appreciated

---

### Post by psusi on 2011-07-14
You are trying to mount your home partition in two different places.  Don't do that.  Also you should use the UUID instead of /dev/sdb1.  You can look up the UUID with blkid.

---

