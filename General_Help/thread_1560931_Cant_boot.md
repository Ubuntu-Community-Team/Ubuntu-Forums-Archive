---
title: "Cant boot"
date: 2010-08-25
forum: General Help
---

### Post by TyLLy_4 on 2010-08-25
Please help. Ubuntu 10.04 was working fine yesterday. (no significant changes. just normal usage) except maybe forced shutdown. 

(my computer started doing this thing where it would take forever to finish a system shutdown so i just pressed the power key for 5 seconds)

i get this error. 

```
   1.
      init: Failed to playmouth mountall main process: unable to execute: input / output error
   2.
      init: Failed to hwclock mountall main process: unable to execute: input / output error
   3.
      init: Failed to spawn mountall main process: unable to execute: input / output error
   4.
      init: Failed to spawn mountall post-stop process: unable to execute: input / output error
****
```

---

### Post by dabl on 2010-08-25
First, boot a Live CD and run memtest86 (multiple passes), to make sure the memory is good.

What filesystem?  Have you tried to fsck it, from a booted Live CD or USB stick?

Also, you should never need to use the power button.

Alt-SysRq R S E I U B will do a graceful shutdown/restart, and save a lot of destruction to your filesystem and running packages.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by TyLLy_4 on 2010-08-25
thank you very much for your reply. 

booting from live CD right now. 

file system is EXT3. 

Memory (ram) its OK (ran test from a live cd)

Hard drive also OK (Test from BIOS)


should i just reinstall? (Third reinstall in 2 months :( )

---

### Post by dabl on 2010-08-25
Can you post the file /etc/fstab?  It might be easy to fix.  If not, you can reinstall.

---

### Post by TyLLy_4 on 2010-08-25
here's my /etc/fstab

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

```

and here's my 
/lib/init/fstab/
```
# /lib/init/fstab: static file system information.
#
# These are the filesystems that are always mounted on boot, you can
# override any of these by copying the appropriate line from this file into
# /etc/fstab and tweaking it as you see fit.  See fstab(5).
#
# <file system> <mount point>             <type>          <options>                    <dump> <pass>
/dev/root       /                         rootfs          defaults                          0 1
none            /proc                     proc            nodev,noexec,nosuid               0 0
none            /proc/sys/fs/binfmt_misc  binfmt_misc     nodev,noexec,nosuid,optional      0 0
none            /sys                      sysfs           nodev,noexec,nosuid               0 0
none            /sys/fs/fuse/connections  fusectl         optional                          0 0
none            /sys/kernel/debug         debugfs         optional                          0 0
none            /sys/kernel/security      securityfs      optional                          0 0
none            /spu                      spufs           gid=spu,optional                  0 0
none            /dev                      devtmpfs,tmpfs  mode=0755                         0 0
none            /dev/pts                  devpts          noexec,nosuid,gid=tty,mode=0620   0 0
none            /dev/shm                  tmpfs           nosuid,nodev                      0 0
none            /tmp                      none            defaults                          0 0
none            /var/run                  tmpfs           mode=0755,nosuid,showthrough      0 0
none            /var/lock                 tmpfs           nodev,noexec,nosuid,showthrough   0 0
none            /lib/init/rw              tmpfs           mode=0755,nosuid,optional         0 0

```

I have 3 partitions. 
1 ext3 root partition (20GB)
1 ext3 home partition (130 GB)
1 swap swap partition (5GB)

your help is very much appreciated

---

### Post by dabl on 2010-08-25
Isn't AUFS for USB memory stick or flash drive/SSD installations?

[https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)

I assume we're talking about a hard drive here?

My googling on your error turned up a solution at post #6 here: [http://ohioloco.ubuntuforums.org/showthread.php?p=9072878](http://ohioloco.ubuntuforums.org/showthread.php?p=9072878)

But that was for a conventional ext3/4 installation on a hard disk drive.  If you want, you can try changing the boot options in your /lib/init/fstab file, but I really think your problem is related to the AUFS filesystem on a hard drive.

---

### Post by TyLLy_4 on 2010-08-25
my cd drive dosen't read right so im live booting from a USB. 

Did i post the wrong fstab? 
im sorry i used locate fstab and that was the first ressult that made sense.

---

### Post by dabl on 2010-08-25
OK, so you're mounting your hard drive from the Live USB, and then looking at it?  There's a file at /etc/fstab (on the hard drive) that should look similar to the ones in that link that I posted.  I need to see that file.

---

### Post by TyLLy_4 on 2010-08-25
now mu liveusb isn't booting anymore :( i think vista killed when i pluged it to the other computer to copy the fstab files :(

---

### Post by dabl on 2010-08-25
> **TyLLy_4 said:**
> now mu liveusb isn't booting anymore :( i think vista killed when i pluged it to the other computer to copy the fstab files :(

Bummer.

I think I see a new installation in your future .....

   :-({|=


Just remember the Alt-SysRq R S E I U B thing -- use that when you think your system is "hung" or "frozen".  Pushing the power button on a running ext3/4 filestem can wreck it (and or your data).

---

### Post by TyLLy_4 on 2010-08-25
ill remember alt+system req ... it might as wsell post the right fstab anyways since i have to create a new bootable usb either way. (cd rom dont work)

thx again.

---

