---
title: "Can't boot to Ubuntu 9.10"
date: 2009-12-21
forum: General Help
---

### Post by adaggerthrough on 2009-12-21
Hi, I've not been using Ubuntu 9.10 long and thus aren't exactly good at this... Anyway, my normal GNU GRUB boot menu has been replaced with:

> GNU GRUB version 1.97~beta4

[ minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>

I've pressed tab and gone through its list of commands and nothing seems to be doing anything (first one I tried, "boot", gives me back "error: no loaded kernel") and I'm not sure what to do. I'm running 9.10 on my laptop right now and haven't run into this on there either.

---

### Post by Leppie on 2009-12-21
if you only have ubuntu installed on this laptop, try the following at the grub prompt:
```
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro		
initrd /initrd.img		
boot
```

otherwise, if you have a live cd at hand, please post the output of the following command:
```
$sudo fdisk -l
```

---

### Post by 73ckn797 on 2009-12-21
9.10 uses grubs and is very different.

What are the results of the following commands in a terminal?
```
sudo fdisk -l
```

```
sudo blkid
```

Copy the info and post the result in a reply.

---

### Post by adaggerthrough on 2009-12-21
I don't know how to get to the terminal I'm afraid, because I'm stuck on that GNU GRUB menu where I can only input certain commands.

Also, I don't have a live CD handy either.

---

### Post by Leppie on 2009-12-21
then try this at the grub prompt (sh:grub>):
```
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro		
initrd /initrd.img		
boot
```

---

### Post by adaggerthrough on 2009-12-21
Just tried, it didn't do anything. :S

---

### Post by 73ckn797 on 2009-12-21
> **adaggerthrough said:**
> I don't know how to get to the terminal I'm afraid, because I'm stuck on that GNU GRUB menu where I can only input certain commands.

Also, I don't have a live CD handy either.

How did you install Ubuntu without the CD?

---

### Post by adaggerthrough on 2009-12-21
> **73ckn797 said:**
> How did you install Ubuntu without the CD?

I mounted the image and installed it within Windows 7 on my desktop (one with problems), and installed it via USB to my laptop.

---

### Post by Leppie on 2009-12-21
> **adaggerthrough said:**
> Just tried, it didn't do anything. :S

because you didn't mention it's a wubi install.

try the following:
```
insmod ntfs
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk
initrd /boot/initrd.img
boot
```

if it doesn't work, could you please post the output the grub shell gives you?

---

### Post by adaggerthrough on 2009-12-21
> **Leppie said:**
> because you didn't mention it's a wubi install.

try the following:
```
insmod ntfs
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk
initrd /boot/initrd.img
boot
```

if it doesn't work, could you please post the output the grub shell gives you?

Ah, sorry about that.

I get "error: no such partition" when I get to the third line.

---

### Post by Leppie on 2009-12-21
how are you accessing this forum at this moment? from another pc?

---

### Post by adaggerthrough on 2009-12-21
> **Leppie said:**
> how are you accessing this forum at this moment? from another pc?
Yes, from a different PC.

---

### Post by Leppie on 2009-12-21
I suppose it would be best for you to download a livecd image, burn it (and keep it for future use ;)).
with a livecd at hand, you have many more tools you can use to restore grub and it's especially handy if you do not know the exact partition layout of your disk(s).

---

