---
title: "two general questions"
date: 2009-12-11
forum: General Help
---

### Post by Running Wild on 2009-12-11
i downloaded ubuntu and it runs very well

but im using a HP Pavilion zv6000 pretty old i know xD

and my wireless router is disabled theres no way to gain internet access ive searched different methods on youtube and none worked


another thing is there a way to transfer your old files because im running windows xp and i wanna transfer my files over to ubuntu 

anyhelp would be fantastic!!! ;)

*waits*:popcorn:

---

### Post by Matt__ on 2009-12-11
install from terminal
```
sudo apt-get ntfs-config
```and access all your xp partition files form ubuntu (choose partitions to view and allow write support when prompted) which will now mount on your ubuntu desktop.

also do ```
lspci
``` in the terminal and show the output here..Im sure someone can get your wireless working

---

### Post by themusicalduck on 2009-12-11
Have you gone to System > Adminstration > Hardware Drivers to see if you can install your wireless drivers from there?

---

### Post by Running Wild on 2009-12-11
> **themusicalduck said:**
> Have you gone to System > Adminstration > Hardware Drivers to see if you can install your wireless drivers from there?

the drivers are allready installed im pretty sure it works when i switch over from ubuntu to windows no problem

big ups matt thanx alot <3

> **Matt__ said:**
> install from terminal
```
sudo apt-get ntfs-config
```and access all your xp partition files form ubuntu (choose partitions to view and allow write support when prompted) which will now mount on your ubuntu desktop.

also do ```
lspci
``` in the terminal and show the output here..Im sure someone can get your wireless working

---

