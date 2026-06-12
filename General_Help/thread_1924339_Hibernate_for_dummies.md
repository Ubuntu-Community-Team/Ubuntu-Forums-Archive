---
title: "Hibernate for dummies"
date: 2012-02-12
forum: General Help
---

### Post by rajanm1 on 2012-02-12
Hi,

i have just installed ubuntu 12 onto me dell mini 9 netbook, but the hibernate option does not appear :(.

It only has an 8GB SSD but it was a fresh install so there is 3GB free and it only has 1GB ram.

As i only use this for surfing the net, checking emails etc. whilst on the move i really need to be able to have a hibernate option so could someone tell me how to do this please? :(

thanks!

---

### Post by Vishnu V on 2012-02-12
I read somewhere that gnome 3 automatically remove hibernate option if it not supported by the system
Command for hibernation is
```

sudo pm-hibernate

```

---

### Post by ajgreeny on 2012-02-12
And what size swap partition do you have?  I suspect that whatever size it happens to be, on an 8GB SSD it will not be big enough for hibernation.  If the 3GB free space is just that, ie free space on the main partition, I wonder if there is a swap at all.

Let's see the output of ```
sudo fdisk -l
```in terminal.

---

### Post by rajanm1 on 2012-02-12
> **Vishnu V said:**
> I read somewhere that gnome 3 automatically remove hibernate option if it not supported by the system
Command for hibernation is
```

sudo pm-hibernate

```


thanks! that did work, but is there a way to do this without having to go into the terminal and type that every time?

cheers

---

### Post by rajanm1 on 2012-02-12
> **ajgreeny said:**
> And what size swap partition do you have?  I suspect that whatever size it happens to be, on an 8GB SSD it will not be big enough for hibernation.  If the 3GB free space is just that, ie free space on the main partition, I wonder if there is a swap at all.

Let's see the output of ```
sudo fdisk -l
```in terminal.


to be honest i don't really know, but i thought that as i only have 1GB RAM and 3.3GB free then it should be able to hibernate ok.
here is the output though:

Disk /dev/sda: 7682 MB, 7682605056 bytes
255 heads, 63 sectors/track, 934 cylinders, total 15005088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00091b12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    12926975     6462464   83  Linux
/dev/sda2        12929022    15003647     1037313    5  Extended
/dev/sda5        12929024    15003647     1037312   82  Linux swap / Solaris

---

### Post by rajanm1 on 2012-02-12
bump

---

### Post by Vishnu V on 2012-02-12
This [link]("http://askubuntu.com/questions/94754/how-to-modify-policykit-to-allow-hibernation-in-upower") may hel you

---

