---
title: "Resize an existing linux partition, dual boot and more space"
date: 2009-08-10
forum: General Help
---

### Post by berlinbrown on 2009-08-10
I haven't done this in a while. And I have three questions.

I have used this Ubuntu Linux machine for a while. Pure Linux. I have the latest Ubuntu version.

It is a 120GIG drive, I setup 80gigs for Linux and let the 40 gigs free. Not touched.

Win32

I needed to do some work solely in win32 (terminal services and other work that will only work under windows). So, I installed windows on the 40gigs that were free.

Can't boot back into Ubuntu, problem 1

I installed windows xp and now I can't get back into Linux. I am assuming the install wrote over the MBR and now all I would need to do is get a live CD or something and install grub or something? I wish I had the exact details. I want to be able to dual boot, maybe with a prompt allowing me to select win32 or ubuntu.

How to resize the win32 system, add a new partition, problem 2

So I have this win32 install which only has a 40gigs. I ran through that pretty quickly over the last week. And now I only have 15gigs free. I need to install more stuff. So, how would I use some of the space from the Ubuntu linux install. I have 50gigs free on the Linux side.

What steps would I need to resize the linux and give to the win32 side?

I will use grub to reinstall what is on the mbr.

But what about resizing my linux partition/data for 
use on the Linux side?  Can I use gparted without losing
any data on the Linux or Windows side?

---

### Post by merlinus on 2009-08-10
Restoring grub:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use hd and numbers from the previous command
setup (hd0)  #use hd and its number from the previous command
quit 
```Remove the cd and restart.

You can use gparted on the live cd to resize linux and add the space to xp, but it and the xp partitions need to be adjacent.

---

### Post by ArmenianLeader4 on 2009-08-10
System > administration > partition editor

---

### Post by michy99 on 2009-08-10
An excellent guide to resizing partitions:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

This is actually the opposite of what you are trying to do. (It is how to shrink windows and expand Ubuntu) but it works the same the other way.

---

### Post by berlinbrown on 2009-08-10
[http://img43.imageshack.us/img43/2312/screenshotdevsdagparted.png](http://img43.imageshack.us/img43/2312/screenshotdevsdagparted.png)

OK, here is my configuration.  I tried to resize so that I can add more for the windows size.  Couldn't do it.

---

### Post by merlinus on 2009-08-11
First of all, you need to be using gparted on the ubuntu live cd or its own, as you cannot do anything if the partitions are mounted (the lock next to them shows this to be the case).

You will then need to delete sda5 and sda2, shrink sda1, and grow sda3 into the freed=up space.  You can then create a new swap partition.

---

