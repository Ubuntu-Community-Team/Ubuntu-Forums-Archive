---
title: "Grub after update ubuntu 12.04 in MacBook Pro"
date: 2012-08-15
forum: General Help
---

### Post by josemanuel on 2012-08-15
Hello All, although I am an enthusiast ubuntu user after several years, I don't know whether I should be categorized as absolute beginner being stuck at this point, maybe te answer is yes. Also, I do  not know if this is the right forum for my very naïf question,  in such case my apologies. Anyway, my question is very simple: I run now ubuntu 12.04 amd64 in  a MacBook Pro with reFit, of course. Yesterday I ran a routine (I guessed ...) update (which entailed a kernel upgrade unfortunately, but I did not paid much attention to that..). It finished normally :) and asked me to reboot the system. I had no time for waiting for the reboot and posponed it until normal boot today. Now I get a flashing prompt :confused:!!!!!!! How can I repair/restore grub ???  Any help would be extremely appreciated.

 Thanks in advance 

                           Jose Manuel

---

### Post by mkstallings1 on 2012-08-15
I keep a copy of Boot Repair on CD just for these occasions.  Download it, burn to CD, boot it, and let it fix everything for you.

---

### Post by josemanuel on 2012-08-16
Thanks a lot !!!. I got it and fixed the problem (in fact I already had a copy of Boot Repair but I had forgotten that easy solution !!). Cheers

---

### Post by YannBuntu on 2012-08-16
Hello/hola
I am the dev of Boot-Repair tool. I am interested by your case because I have few feedback from Mac users.
For my information, please could you indicate the URL that was indicated by Boot-Repair when you used it? (if you don't remember, please follow [this tutorial]("https://help.ubuntu.com/community/Boot-Info"))
gracias :)

---

### Post by josemanuel on 2012-08-17
Hello,

      sorry, but the problem solved misteriously without the need of running Boot-Repair. I mean: when I tried to start from  a bootable usb with Ubuntu live (planning to apt-get Boot Repair from the network and running it afterwards, according to the standard procedure), by clicking its icon in reFit, instead the system booted normally from HD and everything looked OK. I'm working normally since yesterday with it. I really don't understand what happened.. 

 Therefore I cannot provide to you any details. If the problem arises again (I cross my fingers) I'll report it. Thanks for your help developing Boot Repair. 

 Cheers

---

### Post by YannBuntu on 2012-08-17
> **josemanuel said:**
> when I tried to start from  a bootable usb with Ubuntu live (planning to apt-get Boot Repair from the network and running it afterwards, according to the standard procedure), by clicking its icon in reFit, instead the system booted normally from HD

You mean the USB icon in Refit launched the Ubuntu on the HDD?

Anyway, please indicate your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL just for reference. This won't change your boot.

---

### Post by josemanuel on 2012-08-17
Hello, this is what I get (previously it says that EFI has been detected, what is correct):

[http://paste.ubuntu.com/1153007/](http://paste.ubuntu.com/1153007/)

 I hope it helps. 

 Cheers

---

### Post by josemanuel on 2012-08-17
Hola again, I forgot to answer to your previous question: yes, the USB icon in Refit launched the Ubuntu on the HDD. At least I am pretty sure that it was what I did, in fact I was expecting the ubuntu session from live CD when I discovered the personalized login screen of my  ubuntu installation in HDD. All's well that ends well :P (translation to spanish: "Bien está lo que bien acaba")

 Hasta la vista

---

### Post by YannBuntu on 2012-08-20
We have the same proverb in French ("Tout est bien qui finit bien") ;)

The icon mistake may be a bug of Refit. Maybe Refind (which is based on Refit) could solve it.

For your reference, your Ubuntu uses grub-pc (don't delete the sda4 partition, it is used by GRUB).

---

### Post by josemanuel on 2012-08-20
Merci beaucoup I see it (I just used gparted). I fact, several months ago a mismatch in the the partitioning (cylinders, indexing, etc..) was discovered and naïvely I deleted an unknown  tiny partition of about the same size in the same position (i.e. between  Mac partitions and Linuz partitions). I deleted it ...and it forced me to make a new installation (now I realize that by using boot-repair I probably would had fixed it ..). Now, as you write, I have  /dev/sda4 (Filsystem: unknown , Size: 977 KiB, Flags: bios_grub)   clearly indicated .  Thanks a lot for the information. 

 À la prochain

---

