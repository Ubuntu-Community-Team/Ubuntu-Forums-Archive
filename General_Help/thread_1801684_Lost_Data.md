---
title: "Lost Data?"
date: 2011-07-10
forum: General Help
---

### Post by NormArchNo3 on 2011-07-10
Hey folks,

I'm rather new to Ubuntu, but decided that I'd like to get to know it. Please be gentle if I sound foolish, but it is my ambition to become much more knowledgeable. 

In any case, here's my problem:

I had a dual-boot Windows/Ubuntu desktop. I was trying to clear up disk space on Windows so I was uninstalling software via the control panel. I uninstalled something that I thought would only uninstall Wubi, but it seems that it uninstalled all of Ubuntu. I then reinstalled Ubuntu. My question is, is there any way I can get the data that was in my home folder on Ubuntu back?

Thanks!

---

### Post by 73ckn797 on 2011-07-10
> **NormArchNo3 said:**
> Hey folks,

I'm rather new to Ubuntu, but decided that I'd like to get to know it. Please be gentle if I sound foolish, but it is my ambition to become much more knowledgeable. 

In any case, here's my problem:

I had a dual-boot Windows/Ubuntu desktop. I was trying to clear up disk space on Windows so I was uninstalling software via the control panel. I uninstalled something that I thought would only uninstall Wubi, but it seems that it uninstalled all of Ubuntu. I then reinstalled Ubuntu. My question is, is there any way I can get the data that was in my home folder on Ubuntu back?

Thanks!
If you reformatted then it is likely that the data is lost. There are many posts that address data recovery so you will need to do a search. I recommend this link that is Ubuntu specific: [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

If you have to re-install again then create a separate partition for /home. Any future installs will allow you to keep personal data.

---

### Post by wildmanne39 on 2011-07-10
> **NormArchNo3 said:**
> Hey folks,

I'm rather new to Ubuntu, but decided that I'd like to get to know it. Please be gentle if I sound foolish, but it is my ambition to become much more knowledgeable. 

In any case, here's my problem:

I had a dual-boot Windows/Ubuntu desktop. I was trying to clear up disk space on Windows so I was uninstalling software via the control panel. I uninstalled something that I thought would only uninstall Wubi, but it seems that it uninstalled all of Ubuntu. I then reinstalled Ubuntu. My question is, is there any way I can get the data that was in my home folder on Ubuntu back?

Thanks!Hi, it was possible before you reinstalled over it, but if you reinstalled ubuntu in the same place then the data will have been over written. But it still would have been a major task.

---

### Post by NormArchNo3 on 2011-07-10
> **73ckn797 said:**
> If you reformatted then it is likely that the data is lost. There are many posts that address data recovery so you will need to do a search. I recommend this link that is Ubuntu specific: [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

If you have to re-install again then create a separate partition for /home. Any future installs will allow you to keep personal data.

Thanks for the fast reply!

I don't think I reformatted any partitions myself. And using the program in Windows Control Panel that lets me view the hard disk partitions it doesn't seem than any of the partitions are different from when I started.

---

### Post by NormArchNo3 on 2011-07-10
What confuses me is that whatever I deleted, it showed up as clearing up space in My Computer on Windows. Does this imply that Ubuntu and Windows shared a partition?

(Sorry for the noobish question.)

---

### Post by wildmanne39 on 2011-07-10
> **NormArchNo3 said:**
> Thanks for the fast reply!

I don't think I reformatted any partitions myself. And using the program in Windows Control Panel that lets me view the hard disk partitions it doesn't seem than any of the partitions are different from when I started.
Hi, the problem is that you are still using that system and you reinstalled ubuntu again which means you have written data to the drive, if you want to recover it, it could take days for the program to run and you would have to do it from a livecd and you can not use your system in the mean time, and it probably is to late since your have been writing data to that drive. Also I am not sure how it is affected by being a wubi install as far as using the livecd to recover the data, but I think you can do it, if you have not booted the computer since you lost your data.

---

### Post by wildmanne39 on 2011-07-10
> **NormArchNo3 said:**
> What confuses me is that whatever I deleted, it showed up as clearing up space in My Computer on Windows. Does this imply that Ubuntu and Windows shared a partition?

(Sorry for the noobish question.)Hi, yes ubuntu is just another application that you installed into windows when you install it through wubi, that is why you can delete it like any other program.

---

### Post by NormArchNo3 on 2011-07-10
> **wildmanne39 said:**
> Hi, yes ubuntu is just another application that you installed into windows when you install it through wubi, that is why you can delete it like any other program.

Thank you for clearing that up. That was the very misunderstanding that got me into this mess in the first place. >.>

Oh well. Live and learn, I guess.

---

### Post by wildmanne39 on 2011-07-10
> **NormArchNo3 said:**
> Thank you for clearing that up. That was the very misunderstanding that got me into this mess in the first place. >.>

Oh well. Live and learn, I guess.Hi, your welcome, I am sorry that you lost your data, I just to not think from this point that you can retrieve it, or if you can just parts of it, and it would be difficult.

---

### Post by NormArchNo3 on 2011-08-09
Thanks for your help all. I managed to do it using a different partitioning software for Windows. Everything seems to work now.

---

### Post by |{urse on 2011-08-09
just develop an algorithm for each filetype you believe you may have deleted, get an electron microscope. Carefully remove the platters from your hard disk and invent some sort of application that will progressively scan through images the electron microscope sends from the disks surface and use the algos you wrote to find your old files in the surface patterns on the hard disk.

In other words, sorry :(

---

