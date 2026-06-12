---
title: "Problem with GRUB"
date: 2011-12-20
forum: General Help
---

### Post by sjparida on 2011-12-20
Hi folks,         I have a problem with the grub boot menu,as i am installed wndows7ultimate and ubuntu 11.10,whenever i start the system there is no boot menu for choosing the OSes,by default ubuntu starts.  but after checking some post over the forum i found that someone said pressing SHIFT key on boot up will show the boot menu.but as i did so its is showing this message and i can't able to use my system.   --------------------------------------------------------------------  SYSLINUX 4.04 EDD 2011-04-18 copyright (c) 1994-2011 H.Peter Anvin et al ERROR : No configuration file found No DEFAULT or UI configuration directive found!   boot: ------------------------------------------------------------------   please help me folks so i can use my system.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by BC59 on 2011-12-20
Can you post the result of these commands?

```
sudo parted /dev/sda print 

sudo fdisk -l
```

---

### Post by emmomalick on 2011-12-20
Will you have reinstalled the GRUB after installing windows? 
See here

[http://www.tuxgarage.com/2011/01/re-installing-grub2.html](http://www.tuxgarage.com/2011/01/re-installing-grub2.html)

---

### Post by sjparida on 2011-12-20
I can't access the system as sson as i boot a black with these instruction are showing.   No DEFAULT or UI configuration directive found!. boot :

---

### Post by BC59 on 2011-12-20
In that case you don't have an operating system, try to reinstall Ubuntu. Then we will find a solution for Windows.

---

### Post by MartijnNL on 2011-12-20
> **BC59 said:**
> In that case you don't have an operating system, try to reinstall Ubuntu. Then we will find a solution for Windows.

He sayd at the beginning he could just boot into Ubuntu, so I asume he has an OS, there just seems to be a problem with GRUB.

---

### Post by BC59 on 2011-12-20
> **MartijnNL said:**
> He sayd at the beginning he could just boot into Ubuntu, so I asume he has an OS, there just seems to be a problem with GRUB.

Don't read only the first message

> #4 I can't access the system as sson as i boot a black with these instruction are showing. No DEFAULT or UI configuration directive found!. boot :

---

### Post by sjparida on 2011-12-20
thnx buddy,it is solved now tnx for the [http://www.tuxgarage.com/2011/01/re-installing-grub2.html](http://www.tuxgarage.com/2011/01/re-installing-grub2.html) link its vry helpful

---

### Post by MartijnNL on 2011-12-20
> **BC59 said:**
> Don't read only the first message

I didn't. But I got the impression the error just occurred after hitting shift. It's a bit weird when you get a syslinux warning warning when going to the grub menu.

But the fact that he was able to boot into Ubuntu before shows that there is an OS, that doesn't just disappear by pushing shift on boot. So re-installing Ubuntu seemed a bit premature to me. And as it turned out re-installing GRUB was enough.

---

### Post by emmomalick on 2011-12-20
> **sjparida said:**
> thnx buddy,it is solved now tnx for the [http://www.tuxgarage.com/2011/01/re-installing-grub2.html](http://www.tuxgarage.com/2011/01/re-installing-grub2.html) link its vry helpful
:) You're welcome.

---

