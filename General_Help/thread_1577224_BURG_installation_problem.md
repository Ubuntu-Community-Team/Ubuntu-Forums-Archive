---
title: "BURG installation problem"
date: 2010-09-18
forum: General Help
---

### Post by storm of mort on 2010-09-18
Hi, dis is my first thread and hope some1 can help me out. I been using Ubuntu faithfully and had loads of fun on 9.04. The first thing i wanted to do after upgrading to 9.10 was to install BURG and get an eyecandy boot-up screen

But on installation I'm getting dropped into a grub shell, and now hav to load the kernel manually to boot into linux. 

So is this a problem with legacy grub? And what should i do to solve this problem or restore the old grub menu back. I prefer to have burg running as it looks so kewl.

thnx a lot in advance, n i hope im posting in the right place.
------

**found out how on this forum... Thnx in advance.**
Boot from grub-shell to linux

[SIZE="5"]```
search -f vmlinuz
```[/SIZE]

u'l get something like (hd1,msdos1), mine was... urs might be (hd0,msdos1) mayb. Remember
hd = sd
0 is the indexing of disk from zero. hd0 is first disk and hd1, ur second disk. The msdos1 part of the result is your partition
0 = a
1 = b
2 = c where u hav your root folder. I dunno y it says msdos1 for me. The alternative way of marking this (hd1, msdos1) is (hd1,1) or sdb1. (remember, the partition is named starting from 1, unlike hard disk count which started at zero).


so the return u got last time (hd0,msdos1) can also b translated as sdb1. So u hav successfully found out where ur linux kernel is. Its time to load it up

[SIZE="5"]```
linux /vmlinuz root=/dev/sdb1
initrd /initrd.img
boot
```[/SIZE]

once you are in your ubuntu get remove burg, upgrade grub to grub2 as given here. Install burg back using synaptics (all the burg packages) and voila it works.
:guitar: Ubuntu rocks. Almost any screwups can be fixed. The reason i think i was being dropped into a grub shell is because i forgot to update burg. u must run dis command manually after install of burg in your terminal

[SIZE="5"]```
sudo update-burg
```[/SIZE]

Hope this helps someone :popcorn: 

BURG = really neat boot manager, bdw. Much better den text version. The only annoying thing is that it loads the background and u can see it loading.

---

### Post by jvacek996 on 2010-11-01
hey there, i am running ubuntu 10.10 - maverick, and i tried to install burg. it went horribly wrong. :(

i got myself a supergrubdisk2, and im trying to run the search command, but it reples "no such device: vmlinuz" anyone help please??

---

