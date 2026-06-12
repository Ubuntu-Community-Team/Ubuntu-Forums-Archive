---
title: "Need help installing windows"
date: 2011-03-04
forum: General Help
---

### Post by Korntoff on 2011-03-04
Tried every fathomable method to dual boot windows with my good install of Maverick (Mostly tried older versions, to play Age Of Empires ;D) after I lost it to an almost-brick. Ubuntu is my preferred OS, but now I need windows to flash ROMS onto the HTC HD2 and I've had no luck (I never get luck, with anything, ever.) Please help me? I lost my 2 vista cds, can't boot from usb, my blank cds are too small for seven, XP can't recognise my NTFS partition, blah blah, the list goes on

Damn microsoft! >:u

---

### Post by sesipdo on 2011-03-04
okay im here to help (: 

so u want to install windows xp ?

---

### Post by Korntoff on 2011-03-04
Any version, really. I just need something with good support for usb and stuff. What'd run the best on my HP mini with 1.66ghz atom cpu and 1gb RAM?

Edit: I put 166ghz lol

---

### Post by Ocxic on 2011-03-04
try CWM (clockwork mod) it allows you to flash roms right from the phone. you only need odin to flash and activate CWM (ie: 1 time deal)

---

### Post by sesipdo on 2011-03-04
i would go with xp on that and yes xp should have good usb support :P on sp3 service pack 3 


and do u have a external cd drive 

installing windows xp from usb is a long and super headache process trust me i have tryed so many times its hard .... 
:KS:KS

---

### Post by Timmer1240 on 2011-03-04
Do you have a licensed copy of xp?

---

### Post by sesipdo on 2011-03-04
yea that might be a good thing and a cd :P

---

### Post by Timmer1240 on 2011-03-04
Sometimes its best to run virtual box and install xp there thats how I run it.

---

### Post by TheDexter1111 on 2011-03-05
> **sesipdo said:**
> okay im here to help (: 

so u want to install windows xp ?

I also tried to install xp but had te same problem, booted from my licenced xp cd but it always fails due to it wont recognise the NTFS partition... I even tried booting from my Ubuntu cd, manually deleted all ext partitions and then tried again, yet same problem.

I love Ubuntu, but I do sorta need xp.. life would just be easier.
How do I go about doing this?

---

### Post by flyerbrooks on 2011-03-05
Are you booting from the Xp CD inside the Virtual machine? If you are, the formating should be taken care of by the guest machine at the time of making the new disk/VM as you run the cd for the install. I run Xp inside Lucid and its the dogs bolloxxs.

---

### Post by Mark Phelps on 2011-03-05
> **Korntoff said:**
> Please help me? I lost my 2 vista cds,
Vista does NOT come on CDs, it's too big.  It only comes on DVDs.

>  my blank cds are too small for seven,
See above ...
>  XP can't recognise my NTFS partition

Using Ubuntu, open a terminal and enter "sudo fdisk -lu" (that's a lowecase L, not a one).  That will list out your partitions.

I can understand Vista or Win7 not liking an existing NTFS partition, especially one you created with a Linux utility -- as Vista (and now Win7) use an enhanced version of NTFS that is different than the one used in the XP days.  But, XP (even SP3) shouldn't be that picky.

---

