---
title: "Too Many Ubuntu Entries"
date: 2010-12-25
forum: General Help
---

### Post by YaPloNo1 on 2010-12-25
as the title says guys n gals...when grub loads i have: 

Ubuntu, with Linux 2.6.32-26-generic
Ubuntu, with Linux 2.6.32-26-generic (recovery mode)

Ubuntu, with Linux 2.6.32-25-generic
Ubuntu, with Linux 2.6.32-25-generic (recovery mode)

Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)

Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)

Ubuntu, with Linux 2.6.32-22-generic
Ubuntu, with Linux 2.6.32-22-generic (recovery mode)

Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)

are all these really necessary? i would like instructions on how to remove most of them and keep the most up to date one

---

### Post by Verbeck on 2010-12-25
its recommended to have the two most recent kernels, but since you have 6, do the following

open synaptic (system>administration)
and search for **linux-image-2.6.32-XX-generic** (replace xx with the kernel version)
then right click it > mark for removal and click apply

after that, run *sudo update-grub* from a terminal

---

### Post by spiky001 on 2010-12-25
You can open synaptic package manager select installed then in search type linux you can remove them from there keep the newest 1 and previous 1 just incase, remove linux headers +linux headers gerneric + linux images, make sure you remove the same 1,s i,e 21/22/23/24. keep 25/26

---

### Post by karthick87 on 2010-12-25
You can install ubuntu-tweak and you can remove unwanted kernel entries easily.
```
 sudo apt-get install ubuntu-tweak
```

[[COLOR=Red]**Removing kernels using ubuntu-tweak**[/COLOR]]("http://blog.ubuntu-tweak.com/2009/04/12/ubuntu-tweak-047-released.html")
[[COLOR=Red]**Here is a tutorial for removing unwanted kernels from grub.**[/COLOR]]("http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/")

---

### Post by Rubi1200 on 2010-12-25
> **karthick87 said:**
> You can install ubuntu-tweak and you can remove unwanted kernel entries easily.
```
 sudo apt-get install ubuntu-tweak
```[[COLOR=Red]**Removing kernels using ubuntu-tweak**[/COLOR]]("http://blog.ubuntu-tweak.com/2009/04/12/ubuntu-tweak-047-released.html")
[[COLOR=Red]**Here is a tutorial for removing unwanted kernels from grub.**[/COLOR]]("http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/")
Nice link karthick87 :) (I mean for the How-to Geek and not Ubuntu Tweak)

Clear and simple.

Bookmarked.

Thanks.

---

### Post by YaPloNo1 on 2011-01-22
> **Verbeck said:**
> its recommended to have the two most recent kernels, but since you have 6, do the following

open synaptic (system>administration)
and search for **linux-image-2.6.32-XX-generic** (replace xx with the kernel version)
then right click it > mark for removal and click apply

after that, run *sudo update-grub* from a terminal
do i select removal or complete removal?

---

### Post by yetiman64 on 2011-01-22
Complete removal takes out any configuration files for the package as well (should be safe to do with these, so either choice is ok).

---

### Post by oldos2er on 2011-01-22
'Removal' should work fine. Also you shouldn't need to run sudo update-grub afterward, since Synaptic will take care of that for you.

---

### Post by Quackers on 2011-01-22
Even selecting "complete removal", there are still 2 entries for each kernel in synaptic iirc.

---

### Post by YaPloNo1 on 2011-01-29
ok thanks everyone...just for reference i used the suggestion from verbeck and it worked and all is well...thanks everyone for your help

---

### Post by yetiman64 on 2011-01-29
> **YaPloNo1 said:**
> ok thanks everyone...just for reference i used the suggestion from verbeck and it worked and all is well...thanks everyone for your help

If all is fixed, could you mark the thread as solved please?. 

The thread tools drop down menu at the top of the browser window is how.

 Link #5 in my sig has detailed instructions if needed. Thanks. yetiman64

---

### Post by Krytarik on 2011-01-29
> **YaPloNo1 said:**
> ok thanks everyone...just for reference i used the suggestion from verbeck and it worked and all is well...thanks everyone for your help
You should remove the "linux-headers-*" and "linux-headers-*- gerneric" packages associated to the removed kernels as well, like *spiky001* suggested, it frees up additional disk space of 77 MB, per kernel!!

---

### Post by ssulaco on 2011-01-29
> **YaPloNo1 said:**
> as the title says guys n gals...when grub loads i have: 

Ubuntu, with Linux 2.6.32-26-generic
Ubuntu, with Linux 2.6.32-26-generic (recovery mode)

Ubuntu, with Linux 2.6.32-25-generic
Ubuntu, with Linux 2.6.32-25-generic (recovery mode)

Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)

Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)

Ubuntu, with Linux 2.6.32-22-generic
Ubuntu, with Linux 2.6.32-22-generic (recovery mode)

Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)

are all these really necessary? i would like instructions on how to remove most of them and keep the most up to date one
Always keep two entries,current and next to current....in your list you would keep 26 and 25,in the event you cant boot into 26 you can boot in with 25,
You can also use the terminal to remove the unwanted kernels
```
sudo apt-get remove --purge 2.6.32-XX-*
```
XX being the number you want to remove

---

### Post by ssulaco on 2011-01-29
> **ssulaco said:**
> Always keep two entries,current and next to current....in your list you would keep 26 and 25,in the event you cant boot into 26 you can boot in with 25,
You can also use the terminal to remove the unwanted kernels
```
sudo apt-get remove --purge 2.6.32-XX-*
```
XX being the number you want to remove
The asterisk (wildcard) will grab everything associated with that kernel,images and headers...

> **Krytarik said:**
> You should remove the "linux-headers-*" and "linux-headers-*- gerneric" packages associated to the removed kernels as well, like *spiky001* suggested, it frees up additional disk space of 77 MB, per kernel!!

---

