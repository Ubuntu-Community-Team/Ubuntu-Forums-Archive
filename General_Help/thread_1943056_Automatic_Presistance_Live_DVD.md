---
title: "Automatic Presistance Live DVD"
date: 2012-03-18
forum: General Help
---

### Post by CC Inc on 2012-03-18
Hi,

I just made a casper-rw disk with my usb drive. I would like to have my live DVD automatically enable presistance so I dont have to type in the kernal arguement every boot.

How can I do this?

---

### Post by CC Inc on 2012-03-19
Any help?

---

### Post by varunendra on 2012-03-21
Why don't you just create a persistent Live USB? It would just cost another 700MB (for base filesystem) on it, but then you won't have to carry the cd/dvd with it.

However, if you have any specific reason, [reconstructor]("http://linux.softpedia.com/get/Utilities/Reconstructor-16806.shtml") may hopefully be helpful as the wiki page suggests: [https://help.ubuntu.com/community/LiveCD/Persistence#Automatic_Persistence](https://help.ubuntu.com/community/LiveCD/Persistence#Automatic_Persistence)

---

### Post by Mark Phelps on 2012-03-21
I don't believe that you can make a Live DVD persistant -- because to do so, you would have to be able to write files to it, and a DVD is not formatted to have a changeable File System, in the way that a USB is formatted.

Have seem some Hybrid solutions that sort-of do this, but they boot from a DVD and use a companion USB stick to handle the persistance part -- because they can write to the USB stick.

---

### Post by varunendra on 2012-03-21
> **Mark Phelps said:**
> ....they boot from a DVD and use a companion USB stick to handle the persistance part -- because they can write to the USB stick.
By the original post, it seems this is indeed what the op is doing:
> **CC Inc said:**
> I would like to have my live DVD automatically enable presistance so I dont have to type in the kernal arguement every boot. -suggests that he/she is already able to achieve persistence by adding a kernel boot argument (probably F6 > add "persistent" at the end of boot command line).

Of course the persistent part is written on a flash drive, and that's why I don't get the point of carrying a cd/dvd along with the usb when the usb alone can serve the purpose. The only case when it makes some sense to me is using it on a computer which can't boot from a USB flash drive.

---

