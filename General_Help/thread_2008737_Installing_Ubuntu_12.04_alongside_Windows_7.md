---
title: "Installing Ubuntu 12.04 alongside Windows 7"
date: 2012-06-23
forum: General Help
---

### Post by xango1986 on 2012-06-23
Hello everyone. I'm new to the world of Linux. Today I installed Ubuntu 12.04 on my laptop which already had Windows 7 on it. While installing I selected the install alongside Windows 7 option as I wasn't sure about using the "something else" option. After that, I didn't get any option to select which partition to use for the installation. After the installation was complete, I logged into windows and checked the partitions. The windows partition seems to be left untouched. But there is one new 1.91 GB primary partition. 

So seniors, how does it work? Is it alright? Will the 1.91 GB partition be extended when I install new programs? Sorry for the dumb question.:redface: I'd really appreciate it if you took the time to throw some light on it.

---

### Post by kc1di on 2012-06-23
welcome to linux and ubuntu xango1986,

Well first of all I'm not sure that the 1.91 gig partition is actually a linux partition as usually window 7 reserves some space for restore files.  
normally windows can't see the linux partitions on your drive. 

if you used the default install I'm assuming you will have a linux partion of about 12 to 20 gigs labeled / 

but to see it you'll have to boot to ubuntu. 

good luck 
Dave

---

### Post by xango1986 on 2012-06-23
> **kc1di said:**
> welcome to linux and ubuntu xango1986,

Well first of all I'm not sure that the 1.91 gig partition is actually a linux partition as usually window 7 reserves some space for restore files.  
normally windows can't see the linux partitions on your drive. 

if you used the default install I'm assuming you will have a linux partion of about 12 to 20 gigs labeled / 

but to see it you'll have to boot to ubuntu. 

good luck 
DaveI

Thanks Dave. This is a screenshot from disk utility. I'm assuming that the 50 GB ext4 partition is the primary partition for Ubuntu and the 2 GB partition is swap space. Is that right?

[ATTACH]220105[/ATTACH]

---

### Post by kc1di on 2012-06-23
> **xango1986 said:**
> I

Thanks Dave. This is a screenshot from disk utility. I'm assuming that the 50 GB ext4 partition is the primary partition for Ubuntu and the 2 GB partition is swap space. Is that right?

[ATTACH]220105[/ATTACH]

i believe your right :)

---

### Post by d.atanasov on 2012-06-23
Hello and welcome, 

I would suggest to you to have a look at how linux is managing the labels of the partitions as "/" or "/home". Then you will have a better look what you have when you use a program as "gparted" (use it carefully because it can make all things disappear). Here is a link maybe is too detailed but I hope it will give you better view 

[http://tldp.org/HOWTO/html_single/Partition/](http://tldp.org/HOWTO/html_single/Partition/)

There is also additional information inside. Enjoy

---

### Post by kc1di on 2012-06-23
Hi again,

I usually partition my drive if I have the space for linux the following way.  50g is ok but I like a little more room

/ (Root) Partition of 25 -30 gigs
/home (user home partition 100 gigs or more)
/swap if needed 2x ram installed. technically you don't even need a swap partition if your not using a laptop.  but I usuall put in 2 gigs just in case.

---

### Post by GreatDanton on 2012-06-23
That's right. I have 3Gb of swap and I never used it. Swap is useful if you don't have enough ram or when you hibernate.

---

### Post by xango1986 on 2012-06-23
Thank you all for your kind responses... Thanks a lot guys.

---

