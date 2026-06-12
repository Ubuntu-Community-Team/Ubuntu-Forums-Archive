---
title: "Need help, installing windows"
date: 2011-08-10
forum: General Help
---

### Post by blargityblarg on 2011-08-10
I currently have Ubuntu... I want windows for my laptop.  I just installed a new hard drive into that laptop, and I put Ubuntu on it, now I would like windows 7 on it.  I have a copy of windows 7, and when I try to boot off of the cd I always get cd error 5.  I found other ways to try installing and got another error message saying that windows setup cannot find a location to store temporary installation files.  It also said something about a boot disk partition... I'm wondering if I have to put a partition on my hard drive, but I'm not sure how to do that on Ubuntu... I am very confused, and really need help, any would be very much so appreciated, thanks!

---

### Post by zvacet on 2011-08-10
If free space is unallocated or partition as NTFS you should be able to install Windows.After installation you can restore grub.If someone can give other solutions,don´t hesitate!

---

### Post by blargityblarg on 2011-08-10
That's why I'm so confused, I don't understand what is wrong lol

---

### Post by sam1948 on 2011-08-10
can u boot other CDs?
if yes, then its a bad win7 cd.
in addition CDs are burned in different ways in different drives so if the supplier of the CD has some license to burn he might have done something wrong. but i think only MS allowed to burn CDs and local suppliers can only buy it and add their own signature on it. so that leaves as with a wreaked CD you can borrow other cd from a friend to verify it.

---

### Post by blargityblarg on 2011-08-10
So far, any time i try booting from cd i get cd boot error 5.  Keep in mind I installed ubuntu with no problem at all off of a cd, and this is all after i got a new hard drive.

---

### Post by Mark Phelps on 2011-08-11
You keep saying Win7 "CD", but it does not come on a "CD", it only comes on a "DVD".  If it really is a CD, then it's not an installation disk.

If it really is a DVD, have you confirmed that your optical drive can read DVDs by trying other DVDs.  If it can read others, check the Win7 DVD for scratches or marks on the surface that would prevent it from being read properly.

If your drive is already fully allocated with Linux filesystem partitions, you will NOT be able to install Win7 from the DVD because it doesn't understand Linux filesystems.  You will first have to boot into an Ubuntu LiveCD and use Gnome Partition Editor (GParted) to shrink the Linux filesystem partitions to make room for Win7.  

Also, do NOT use GParted to format a new NTFS partition; instead, let the Win7 installer do that.

---

### Post by sam1948 on 2011-08-11
> **blargityblarg said:**
> So far, any time i try booting from cd i get cd boot error 5.  Keep in mind I installed ubuntu with no problem at all off of a cd, and this is all after i got a new hard drive.

it's a long shot but,
is the hard drive connected using sata or other connection?
do you have additional hard-drive which is not sata?

---

### Post by Jerry N on 2011-08-11
> **Mark Phelps said:**
> Also, do NOT use GParted to format a new NTFS partition; instead, let the Win7 installer do that.

I have done this numerous times for Win2000, WinXP, and Win 7, without any difficulty whatsoever.

Jerry

---

### Post by blargityblarg on 2011-08-21
ok, I finally got it.  I did need the gnome partition editor, I think... anyways thanks for the help!

---

