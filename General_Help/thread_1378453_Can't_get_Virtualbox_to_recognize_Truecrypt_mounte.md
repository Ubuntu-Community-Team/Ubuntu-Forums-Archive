---
title: "Can't get Virtualbox to recognize Truecrypt mounted block device"
date: 2010-01-11
forum: General Help
---

### Post by bpont on 2010-01-11
I am trying to access my external hard drive through Ubuntu which is running as a guest OS using Virtualbox running on Windows XP as host.

Windows XP only recognizes this external drive as an unformatted block device because I used Truecrypt to encrypt and format the entire block device with the Ext3 filesystem.

I use Truecrypt (from within XP host) to mount the block device to drive letter L:\  Obviously, I can't browse the device because XP thinks it's unformatted and can't see the Ext3 filesystem.

In the Virtualbox Options for Shared Folders, I set up the machine name and the path to this Truecrypt mounted volume.  I also set up a USB device filter, which it recognizes and lists as Western Digital External HDD [0107].  However, when I boot into the Ubuntu guest, it's not listed as a mounted block device, with or without Truecrypt mounting it from within XP.

When I run the command:

```
sudo mount -t vboxsf -o uid=[username] [share name] [mount point]
```

I get this error:

```
/sbin/mount.vboxsf: mounting failed with the error: Protocol error
```

I should note that I am not using the default share name and the name of the share name and mountpoint are not identical either.  I realize people get this error message because of those reasons.  I should also note that I can successfully mount an XP folder using the same commands, so I know the correct procedures for setting up and mounting a shared folder residing on the host OS.

Lastly, I should note that I can successfully mount this block device on Ubuntu as host system (not running Virtualbox) after decrypting it with Truecrypt and mounting it to a mount point, so I know it's not going to be an issue with the block device itself, which is healthy and uncorrupted.

I'm really at a loss for what to do next.

---

### Post by bpont on 2010-02-04
I'm going to make one more request for help with this thread.  I suspect there is no way to do what I'm trying to do, but I'm going to try anyway.

Essentially, I'm running VirtualBox on an XP host.  I have a truecrypt encrypted block device (a USB external hard drive) which XP recognizes as an unformatted disk which it assigns drive letter L:\

I boot into Ubuntu as guest OS.  I want some way to get Ubuntu to recognize the block device, so I can mount it from within guest OS using truecrypt.  I've tried a virtualbox device filter to capture the device, but since it has no filesystem until mounted with truecrypt, it doesn't get assigned a /dev address.  If I mount it with truecrypt from host OS and then try to access it through virtualbox's shared folders tool, I get errors because only the host OS can see the device in an unencrypted state.

This exercise is mostly academic for me, since I can access what I need on a host Ubuntu system easily enough.

Anyone have any thoughts on this?  I'm pretty sure I've hit a brick wall, but I thought I'd ask one last time.

Thanks.

---

### Post by yateendra on 2012-05-12
Dear bpont:

Stumbled on your message looking for other truecrypt help.

I've no experience with Virtualbox, but suspect you are in a position where Windows is serving the filesystem to Ubuntu, however, no filesystem is recognized by Win.

I have successfully run a dual-booting Win/Linux system with encrypted block devices using "ext" filesystems with the help of Matt Wu's ext2fsd Windows driver. A file container on an "ext" drive, which in turn has an "ext" filesystem when mounted, can be automatically accessed using this driver (ext3 is especially easy; ext4 a bit more cumbersome with write permissions). In my experience, the interaction between truecrypt Win and ext2fsd is seamless, so you can mount the compound-ext device just as in linux.

If my premises at the beginning of this message are correct, Win should then be able to serve the filesystem to Ubuntu.

Best Regards,
Cam McIntosh

---

