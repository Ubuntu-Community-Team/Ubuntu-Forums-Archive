---
title: "Encrypted swap and suspend-to-disk"
date: 2010-02-15
forum: General Help
---

### Post by pagin on 2010-02-15
Hello,

I have installed ubuntu via the alternate installer, activating encrypted home directories, which in turn enabled to have encrypted swap partitions and disabled hibernation (suspend-to-disk).

I understand the arguments for having an encrypted swapspace in these cases. However, I'd like to be nevertheless able to hibernate. Now that the system is already set up, I cannot change and completely encrypt my harddisk via LUKS+LVM as it is suggested in numerous places.

Instead, I tried the following. I created two swap partitions (sda7 and sda8): one being encrypted via cryptsetup, to be used as a 'real' swap (sda7). Another without encryption, which is not listed in /etc/fstab, so that it is not normally used by the system.
I have then configured uswsusp in order to use sda8 as a resume partition:

```
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda8
splash = y
compress = y
early writeout = y
image size = 1911459594
RSA key file = /etc/uswsusp.key
shutdown method = platform

```

I have decided to encrypt the resume image - I don't care entering a password once every time I resume, it just shouldn't be at every boot. And this way, I can have hibernation without the uncomfortable solution of having my decrypted, open files on the disk as clear text.

However, as sda8 is not 'mounted' when I want to suspend, I get the following error:

```
pagin@saaba:~$ sudo /usr/sbin/s2disk
[sudo] password for pagin: 
s2disk: Could not use the resume device (try swapon -a). Reason: No such device

```

Consequently I have written a wrapper script mounting sda8 only for the purpose of suspend-to-disk. I have moved /usr/sbin/s2disk to /usr/sbin/s2disk.unwrapped and created the following script as /usr/sbin/s2disk:

```
#!/bin/sh

swapon /dev/sda8
exec /usr/sbin/s2disk.unwrapped $*

```

When I try to suspend now, it works. The image seems to get correctly written to sda8. However, on reboot, the image does not seem to be detected and the system is not resuming. I end up with a fresh login screen.

Does anyone have an idea on how I could still do what I want or am I on t completely wrong track?
The idea would be also to unmount sda8 upon resume, is this better done by entering a hook in /etc/pm/sleep.d or can I just continue in the wrapper script above by executing s2disk.unwrapped only by calling it (without 'exec'), and entering a swapoff line behind it?

---

### Post by P3t3r on 2010-05-02
I'm going to bump his topic. On **[this page]("https://help.ubuntu.com/community/EncryptedHome")** I read that "This is a known, wishlist issue that we hope to solve for Ubuntu 10.04", but does anyone know if this has been solved, or if there is any chance for a workaround?

---

