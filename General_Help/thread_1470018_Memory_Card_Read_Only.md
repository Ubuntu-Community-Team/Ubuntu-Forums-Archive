---
title: "Memory Card Read Only"
date: 2010-05-02
forum: General Help
---

### Post by leeds_shrew on 2010-05-02
Time to start a new thread on this one - no previous threads here seem to solve my problem.

I bought a new SD card which I intend to put some MP3s on - except that I can't write to it because it tells me the destination is Read Only.

No-probs thinks I: I'll just reformat it.

"Error creating file system: helper exited with exit code 1: cannot open /dev/mmcblk0p1: Read-only file system"

Very useful.

Various chmod commands all result in Read-only file system. I tried umount then mount commands, but it couldn't find it to mount once I'd unmounted it using the same /media/ file path (I assume it's the only one).

Any bright ideas?

Thanks!

---

### Post by gordintoronto on 2010-05-02
Many SD cards have a tiny "write protect" switch. Any chance yours is one of them?

---

### Post by leeds_shrew on 2010-05-03
Yes, but no - it didn't change anything! Thanks for the idea.

---

### Post by leeds_shrew on 2010-05-05
Does it change anything that I've now tried it with another SD card and it too came up as read only. USB sticks, however, are no problem.

It's an inbuilt 5 in 1 card reader on a Dell Inspiron.

---

### Post by dino99 on 2010-05-05
have you tried with gparted or partedmagic ?

the problem seem to be a chipset dealing with this reader, dont think about the card itself IMO

what give into console: lshw about that hardware ?

as i understand its not an external reader ?

---

### Post by efflandt on 2010-05-05
Have you tried those SD cards in a USB memory card reader?

Often the built-in slot in a laptop is some other type of block device (instead of sdXY serial drive).  Check **dmesg** after inserting an SD card in that slot.  Maybe there is some issue with that device in the /dev directory, either permissions or Linux support for it.

For example USB Startup Disk Creator does not work in the SD slot in my Toshiba laptop, but I can make a bootable USB iso by putting that same SD card in a USB card reader.  Even if I do that I cannot boot from the SD if it is in my laptop's own card slot, only if it is in a USB card reader.

On the other hand, the built-in memory card reader in my desktop is internally connected through USB, so I can boot from an SD card in that.

---

### Post by techunit on 2010-05-05
Um I know what the problem is but it very much depends on what your computer is. you need to edit the fstab to fix the issue but I don't remember what it is, but messing with this can cause problems. Are you using a netbook.

---

### Post by techunit on 2010-05-05
I kow that it has something to do with the fstab.. I am sorry but I won't be able to help you further because of the lack of knowledge on the subject. I hope someone will be able to help you with this baed on what I have contributed.

---

### Post by leeds_shrew on 2010-05-08
I'm still pretty new to all this stuff. Could someone give me a step by step to diagnosing the problem using a couple of the suggestions above? I've now tried it with a 3rd SD card, so I'm pretty sure it's an issue with how Ubuntu is treating SD cards inserted into this slot. [Incidentally, I can't seem to get it to recognise XD cards put into the slot at all at the moment - even when restarting with the card in]

Could it be a driver issue? Dell Inspiron 1721 running 64-bit Ubuntu 10.04.

Cheers, G.

---

### Post by leeds_shrew on 2010-05-30
I've sort of ignored this issue for a while, but it's come back to bite me...

Does anyone know anything more about the fstab issue? What might that be? It means frankly nothing to me at the moment!

---

### Post by wu-lee on 2010-08-04
So, this may solve your problem.  It did for me, on Kubuntu Lucid 10.4 with a ThinkPad T510.

Firstly, make sure the memory card hasn't got the "lock" tab engaged!  This is a plastic sliding thing on the side of the card.  Sometimes it is loose enough that pushing the card into the slot engages it.  To allow writing, the tab should be pushed into the forward position, nearest the contacts.

Now make sure you have write permissions for the device.  The memory card device is /dev/mmcblk0 (other devices will be different), so try this:

```

$ ls -l /dev/mmcblk0
brw-rw---- 1 root disk 179, 0 2010-08-04 10:35 /dev/mmcblk0

```

This shows it's readable and writable (rw) by the root user, and the disk group. I'm not root, so am I in the disk group?

```

$ groups
nick adm dialout cdrom plugdev lpadmin admin sambashare 

```

Nope. So how do I become a member?  You can set your user's group membership in  Applications->settings->sytem settings->advanced->user management (KDE) or in System->Admin->Users and Groups (Gnome).  Or you can do it with the command:

```

sudo usermod -a -G disk $USER

```
Where $USER is your user name.

Now check it worked - "disk" should be listed in your group membership, like this:
```

$ groups
nick adm disk dialout cdrom plugdev lpadmin admin sambashare 

```

Typically group membership won't get updated until you open a new log-in shell or start a new session.  So you may need to log off and on again, or open a login shell like this:
```

$ su - $USER -c bash

```

Now, as a member of the "disk" group, you should have write access to the memory card.

---

