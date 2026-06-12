---
title: "Recent update errors"
date: 2010-09-20
forum: General Help
---

### Post by Quackers on 2010-09-20
The last 2 or 3 updates have reported errors with regard to the linux image headers (pics enclosed).
I thought they might be corrected by future updates, but I was wrong :)
Can I do anything to correct the issues? Thanking you all :P

---

### Post by philinux on 2010-09-20
Open a terminal Apps>Access>

And use this command. Report back any errors.

```
sudo dpkg --configure -a
```

---

### Post by Quackers on 2010-09-20
Thanks for the speedy response philinux, here is the outcome :(

```
mike64@mike64-laptop:~$ sudo dpkg --configure -a
[sudo] password for mike64: 
Setting up linux-image-2.6.32-24-generic (2.6.32-24.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.32-24-generic
mike64@mike64-laptop:~$ 


```

---

### Post by andrewthomas on 2010-09-20
> **Quackers said:**
> Thanks for the speedy response philinux, here is the outcome :sad:

```

**Could not find postinst hook script [update-grub]**.
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'


```

Try and reinstall grub2
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Quackers on 2010-09-20
Ah, I see what you mean.
I have a 32 bit Ubuntu installation and a 64 bit installation. This error happens only on the 64 bit installation, which probably shouldn't be a surprise when you consider that I removed grub2 from the 64 bit installation and use the 32 bit installation's grub2 to boot both systems.
Hmm, do I re-install grub2 on the 64 bit, or just leave it and ignore the error?

---

### Post by andrewthomas on 2010-09-20
I would just install it to the partition and ignore the warnings that it is a bad idea.  It is really up to you.  If it works ...

---

### Post by Quackers on 2010-09-20
Ok, and thanks for your help :-)

---

