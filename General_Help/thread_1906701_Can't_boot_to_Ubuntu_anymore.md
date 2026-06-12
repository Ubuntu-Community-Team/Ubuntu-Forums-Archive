---
title: "Can't boot to Ubuntu anymore?"
date: 2012-01-09
forum: General Help
---

### Post by Haisuke on 2012-01-09
I just got done installing Windows 7 on my computer, and now it will only boot to the windows 7, and doesn't even give any options before booting the windows to boot to anything else... I have all my other data on my Ubuntu partition (2 partitions, no swap space, both about 80GB), as I moved it over before the installation... Got anything for me to try? I'm going to mess around to see if I can fix it, but I don't think I can...

---

### Post by Basher101 on 2012-01-09
windows 7 overwrote your GRUB, this is why no GRUB bootloader gets loaded and you cannot access ubuntu. Here is an easy fix [http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html](http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html)

regards


note: you will have to do this every time you reinstall windows as every time GRUB gets overwritten.

---

### Post by Double.J on 2012-01-09
Hi there, boot up with the live cd, and use gparted if you wanted to rearange space - it'll be a good idea to create an ntfs partition for both windows and ubuntu to store common user files - that way you don't have ubuntu writing to the windows C drive and windows can't read ubuntu partitions!

I'd also create a swap patition - if you don't want one, be sure to have a swap file.


then, once it's set up as should be, use the terminal and these commands to get your boot sorted

```

mkdir /fix [COLOR="Green"]name doesnt matter[/COLOR]
mount /dev/sda[COLOR="Red"]X[/COLOR] /fix [COLOR="red"]X is the number of the ubuntu partition as shown in gparted[/COLOR]
mount -o bind /dev /fix/dev 
mount -o bind /proc /fix/proc 
chroot /fix bash 
sudo update-grub 

```
then reboot


All the best :)

---

### Post by Haisuke on 2012-01-09
> **Basher101 said:**
> windows 7 overwrote your GRUB, this is why no GRUB bootloader gets loaded and you cannot access ubuntu. Here is an easy fix [http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html](http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html)

regards


note: you will have to do this every time you reinstall windows as every time GRUB gets overwritten.
 
Thank you, Basher, you seem to have saved my *** a few times already... I had a feeling it had to do with GRUB, but I have no experience with anything that low...

---

### Post by Basher101 on 2012-01-09
> **Haisuke said:**
> Thank you, Basher, you seem to have saved my *** a few times already... I had a feeling it had to do with GRUB, but I have no experience with anything that low...

thanks appreciated. I was a noob with this stuff too you know... you will learn your way sooner or later.

regards

---

