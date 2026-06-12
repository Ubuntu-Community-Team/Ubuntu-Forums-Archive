---
title: "Error occurred while mounting /mnt/hgfs"
date: 2010-05-30
forum: General Help
---

### Post by kevinarth on 2010-05-30
I hope someone can help me. I'm running 10.04 in VMWare Fusion and every time I boot, I get this error. Options are:

S to skip mounting
M for manual recovery

If I press S, it seems to boot OK and I'm not noticing any ill effect. If I press M, I don't know what to do from there. I tried "mount /mnt/hgfs" but that didn't work. I saw something onscreen about "mountall." When I entered that, it seemed to behave as if i had pressed S.

This is how the error looks. 
[IMG]http://dl.dropbox.com/u/2727687/Ubuntu%20mount%20error.jpg[/IMG]

Any thoughts how I can resolve this issue? I'm pretty new to Linux and am not sure how to resolve this.

I later discovered the following:
I don't know if this is related, but I noticed yesterday that I'm having trouble accessing my Mac file system from the Ubuntu Virtual Machine.

I have my OS X Home folder shared with the VM in the VMWare settings and yet, I'm unable to 'see' that folder or its contents from the Ubuntu Desktop.

I tried once again to manually mount the folders through terminal with "mount /mnt/hgfs," but this didn't help. It seems that, with sudo, I can see the first level of folders under hgfs, but trying to drill any deeper in the herarchy yields permissions errors.

---

### Post by Ozymandias_117 on 2010-05-30
Can you post the output of ```
sudo fdisk -l
``` ```
sudo blkid
``` and ```
sudo cat /etc/fstab
```

---

### Post by kevinarth on 2010-05-30
Thanks so much for helping me work through this. Here's the information you requested:

==============================================================
sudo fdisk -l 
Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007d42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2497    20051968   83  Linux
/dev/sda2            2497        2611      916481    5  Extended
/dev/sda5            2497        2611      916480   82  Linux swap / Solaris

==============================================================
sudo blkid
/dev/sda1: UUID="293de9d5-2917-43cd-84ae-744c3a516dfa" TYPE="ext4" 
/dev/sda5: UUID="b2e9007f-3fb6-4cfe-867b-7dab368a381a" TYPE="swap" 

==============================================================
sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=293de9d5-2917-43cd-84ae-744c3a516dfa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b2e9007f-3fb6-4cfe-867b-7dab368a381a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# Beginning of the block added by the VMware software
.host:/                 /mnt/hgfs               vmhgfs  defaults,ttl=5     0 0
# End of the block added by the VMware software

---

### Post by Ozymandias_117 on 2010-05-30
Sorry, I thought I could help you. Apparently VMWare does it in a way that I know nothing about. :(

Just to tell you a little better what it's saying...

The error is simply that it can't find (or can't mount for some reason) your shared Mac drive. It won't hurt or make anything in Linux run incorrectly, only stop you from accessing your Mac's stuff.

Edit: One thing I just thought about... Do you have the Guest Additions installed in Ubuntu? Also, are you sure the folder you have it linked to is still there, and the shared folder is still in the VBox settings?

---

### Post by kevinarth on 2010-05-30
Well, understanding the nature of the problem is one step closer to a solution, so even though the problem's not solved yet, it gives me some direction. Thank you for the information you were able to provide. Perhaps if I approach it from the VMWare angle, I might be able to figure it out.

Again, Thank you! Your help is much appreciated.

---

### Post by kevinarth on 2010-05-30
> **Ozymandias_117 said:**
> Do you have the Guest Additions installed in Ubuntu? Also, are you sure the folder you have it linked to is still there, and the shared folder is still in the VBox settings?

I don't know what "Guest Additions" is, so unless it's installed as a default option with the OS, it's likely not there. Is there a way to check? 

The folder I have it linked to is still there. If, by VBox settings, you mean the settings in VMWare, it is. I even tried removing and re-adding the share without success.

---

### Post by Ozymandias_117 on 2010-05-30
Boot into Linux, then along the top of VMWare, just check inside those tabs, one of them should have something about Guest Additions... or something like that (Sorry, I've switched to VirtualBox so I can't open it and give you the exact name)

When you select it, it should mount a CD into Ubuntu and install something - This may fix your shared folder problem.

---

### Post by kevinarth on 2010-06-02
> **Ozymandias_117 said:**
> Boot into Linux, then along the top of VMWare, just check inside those tabs, one of them should have something about Guest Additions... or something like that (Sorry, I've switched to VirtualBox so I can't open it and give you the exact name)

When you select it, it should mount a CD into Ubuntu and install something - This may fix your shared folder problem.
Yes, you may be referring to VMWare Tools. I think I already have that installed, but I'll check it again to be sure. Thanks for all your help.

---

### Post by msodrew on 2010-08-11
For those of you running the latest VMWare + Ubuntu 9.10 and can't get that jackass of a shared folder feature working totally right (and by totally right I mean that the files, as browsed from your linux box to appear as owned by you:you vs like 1091:dialout), then listen to this.

After some googling, apparently Ubuntu 9.10 doesn't play nice with the vmhgfs mount and it takes a long time for VMWare to play catch up with their software. You basically have to build the modules into the kernel from source.

1. Install VMWare tools like normal (just cause this is what I did first, though it didn't work)
2. Change your VM settings to share the folder you want
3. Follow these instructions up to step #6 - [http://langui.sh/2009/10/05/ubuntu-9-10-in-vmware/](http://langui.sh/2009/10/05/ubuntu-9-10-in-vmware/)
4. In the VM, add the following line to your /etc/fstab file:

```

.host:/ /mnt/hgfs vmhgfs defaults,ttl=5,uid=1000,gid=1000,nobootwait 0 0
```

5. Also, add this to your /etc/init.d/vmware-tools (replace the vmware_mount_vmhgfs() function too. You'll have to force a write)

```

is_vmhgfs_in_fstab() {
    if grep -q " $vmhgfs_mnt " /etc/fstab; then
        echo "yes"
    else
        echo "no"
    fi
}
# Mount all hgfs filesystems
vmware_mount_vmhgfs() {
  if [ "`is_vmhgfs_mounted`" = "no" ]; then
    if [ "`is_vmhgfs_in_fstab`" = "yes" ]; then
        vmware_exec_selinux "mount $vmhgfs_mnt"
    else
        vmware_exec_selinux "mount -t vmhgfs .host:/ $vmhgfs_mnt"
    fi
  fi
}
```

6. Reboot.

The boot screen may bitch that it failed to mount, but low and behold it works gloriously.

---

### Post by QIII on 2013-03-18
Old thread closed.

---

