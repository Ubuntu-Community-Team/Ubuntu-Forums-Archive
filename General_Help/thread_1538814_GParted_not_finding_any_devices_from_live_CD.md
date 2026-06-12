---
title: "GParted not finding any devices from live CD"
date: 2010-07-25
forum: General Help
---

### Post by Vaultx on 2010-07-25
Hello,
I'm trying to resize partitions using GParted on a 9.10 live CD. The problem is that no hard drives are detected in the disk utility or in GParted, so I am unable to make any changes. How do I get Ubuntu to recognize the hard drive?

---

### Post by wilee-nilee on 2010-07-25
> **Vaultx said:**
> Hello,
I'm trying to resize partitions using GParted on a 9.10 live CD. The problem is that no hard drives are detected in the disk utility or in GParted, so I am unable to make any changes. How do I get Ubuntu to recognize the hard drive?

What is on the HD now?

---

### Post by Vaultx on 2010-07-25
A Windows 7 partiton (which doesn't work, i'm trying to get rid of Windows all together) and an Ubuntu 10.04 64-bit partiton.

---

### Post by wilee-nilee on 2010-07-25
> **Vaultx said:**
> A Windows 7 partiton (which doesn't work, i'm trying to get rid of Windows all together) and an Ubuntu 10.04 64-bit partiton.

I would check that everything is plugged in inside your computer if you have access, it sounds like a HD failure if it's not showing anything in gparted from a live cd.

I would not really know about hardware in general myself, but this seems to be where the problems is. When you run a live Cd it doesn't use the hd, can you post the output in the Ubuntu terminal.
```
sudo fdisk -l
```
l=small case L

---

### Post by Vaultx on 2010-07-25
The HD is definitely working, I can boot from Ubuntu 10.04 off the HD and GParted/disk utility recognizes it from there. sudo fdisk -l doesn't do anything in terminal (on live CD)

---

### Post by Vaultx on 2010-07-25
It's suddenly working. Not sure why, but it is.

---

### Post by wilee-nilee on 2010-07-25
> **Vaultx said:**
> It's suddenly working. Not sure why, but it is.

I would be curious to see the bootscript in my signature posted, if you don't mind. Paste the output to a reply and highlight the txt and click on the # in the reply panel and post it.

---

