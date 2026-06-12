---
title: "Grub-rescue"
date: 2012-05-13
forum: General Help
---

### Post by Jaxke on 2012-05-13
Greetings, fellas,

I had two Ubuntu partitions and one Windows 7 partition on my hard drive(640GB). I deleted the second Ubuntu partition because it was corrupt, and on every boot, I get this
```
>Grub-rescue
```
Looks like Linux terminal to me. 
I believe it happens, because I just(stupid me) deleted the partition, and the 'boot file' got deleted. I still have one Ubuntu partition and W7 partition. How do I recover the bootloader?

Right now, I must boot my computer with a GRUB2 CD. It's not too handy...

Thanks for help, guys!

---

### Post by Easy Limits on 2012-05-13
Try this:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2012-05-13
Boot-Repair will work.

But if you are able to manually boot into your install you can just reinstall grub2's boot loader from that install to the MBR with this:

sudo grub-install /dev/sda

If you have more than one drive you can replace sda with any device or install to other devices the same way. 

Another way also updates some internals like which drive grub reinstalls on major updates.
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by Jaxke on 2012-05-13
> **Easy Limits said:**
> Try this:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thank you, sir. It worked :P

Oldfred, thanks, I'll keep it in mind :)

---

