---
title: "Burg on a triple boot system"
date: 2011-11-17
forum: General Help
---

### Post by superrupe on 2011-11-17
Good evening,

I recently installed Backtrack 5R1. Previously, I was dual booting Windows 7 and Ubuntu 11.10, booting with Burg. After installing Backtrack, upon boot-up, it boots to the Grub menu. Is there anyway I can configure Burg? 

So far, I have updated grub and burg on the Ubuntu partition and installed burg on the Backtrack partition.

Thanks guys!

---

### Post by elliotn on 2011-11-17
reinstall BURG it worked for me before. 
did u try 
sudo burg-update

---

### Post by dcstar on 2011-11-18
> **superrupe said:**
> Good evening,

I recently installed Backtrack 5R1. Previously, I was dual booting Windows 7 and Ubuntu 11.10, booting with Burg. After installing Backtrack, upon boot-up, it boots to the Grub menu. Is there anyway I can configure Burg? 
.......

Boot Ubuntu and then:

```
sudo dpkg-reconfigure burg-pc
```

---

### Post by superrupe on 2011-11-18
> **dcstar said:**
> Boot Ubuntu and then:

```
sudo dpkg-reconfigure burg-pc
```

This worked. Thanks everyone for their help!

Neil

---

