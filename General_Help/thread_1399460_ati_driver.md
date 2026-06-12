---
title: "ati driver"
date: 2010-02-05
forum: General Help
---

### Post by dbowlin17 on 2010-02-05
I have the ATI Radeon 9550XL graphics card. I tried installing the driver, but don't think it did anything. Do I need to install it, or can I even install it? 

[http://wiki.cchtml.com/index.php/Frequently_Asked_Questions#Troubleshooting]("http://wiki.cchtml.com/index.php/Frequently_Asked_Questions#Troubleshooting") that is the wiki for it that I saw when I tried installing it.

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.25&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.25&lang=English") this is the link to download the driver and contains information about it.

I am running Ubuntu 9.10

---

### Post by howefield on 2010-02-06
Have you tried System > Administration > Hardware Drivers ?

Might also be worth reading this page.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by MelDJ on 2010-02-06
you should have installed it by:
```
sudo sh driverpackage
```
and the ati installer will come up

---

### Post by dbowlin17 on 2010-02-06
I am told it can not open the file. I don't know what to do. Is it even neccesary to load such drivers?

---

### Post by MelDJ on 2010-02-06
if you want to run things like compiz and 3d games, yes.
i am guessing you are typing something wrong...

---

### Post by dbowlin17 on 2010-02-06
well, i don't plan on doing any "compiz" and the only game im playing is sim city 4 on my xp partiton. so i think im good. thanks though.

---

### Post by c0mput3r_n3rD on 2010-02-06
Ubuntu has bad ATI support.  The fglrx driver isn't offered after 8.10, so I had a head ache for a long time until I got a GeFore 9500GT.  Nvidia cards work great.   You might want to think about downgrading if you can't find a solution, especially because I'm sure you wouldn't want to replace your video card.

---

