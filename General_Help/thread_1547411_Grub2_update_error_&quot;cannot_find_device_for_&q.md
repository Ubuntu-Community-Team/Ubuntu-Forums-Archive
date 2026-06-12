---
title: "Grub2 update error &quot;cannot find device for /&quot;"
date: 2010-08-06
forum: General Help
---

### Post by Kreme191 on 2010-08-06
I have installed ubuntu 10.04 and windows on two separate partitions and I am trying to get grub2 working. Currently my computer just goes straight to windows. I'm now on a live cd trying to access grub.cfg with terminal. However, when I mount the partition it's in and run "sudo update-grub" it returns "cannot find a device for / (is /dev mounted?)." The same thing happens when I'm in the containing file.

Any help would be great, I miss my ubuntu :(

Thanks in advance

---

### Post by asuastrophysics on 2011-02-01
Same exact problem. I followed the "official ubuntu documentation" to fix grub and now nothing will boot at all.

---

### Post by ksprasad on 2011-02-01
> **Kreme191 said:**
> I have installed ubuntu 10.04 and windows on two separate partitions and I am trying to get grub2 working. Currently my computer just goes straight to windows. I'm now on a live cd trying to access grub.cfg with terminal. However, when I mount the partition it's in and run "sudo update-grub" it returns "cannot find a device for / (is /dev mounted?)." The same thing happens when I'm in the containing file.
 
Any help would be great, I miss my ubuntu :(
 
Thanks in advance
 
 
Instead of "sudo update-grub" try 
"sudo grub-install --root-directory  /<MountPoint>  /dev/sda"
 
sda is the device on which Ubuntu installed. It may be sda,sdb.. etc.
mount point is where you mounted ubuntu partition. usually /mnt
 
reboot.
 
Regards,
ksprasad

---

### Post by Moloch85 on 2011-02-01
I suggest you to carefully read the "Reinstalling GRUB 2" section  (approximately at the bottom of this page):

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Try to follow the simplest method, then try the others. I hope you'll be able to have your ubuntu back as soon as possible. :)

---

### Post by ksprasad on 2011-02-01
Sorry.. didn't see the date of posting :)
 
But I hope it will help Asuastrophysics.
 
Regards,
ksprasad

---

### Post by asuastrophysics on 2011-02-02
I fixed it. I was uninstalling and then reinstalling grub-pc over and over again and couldn't figure out why it wasn't working. 

Turns out that in order for that documentation guide to work, you must first CHROOT into your partition from the livecd, and then run the commands. Simply running the commands won't do anything.

---

