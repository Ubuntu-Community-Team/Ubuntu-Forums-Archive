---
title: "bus error causes liuuxdcpp to close"
date: 2010-07-23
forum: General Help
---

### Post by rexxxlo on 2010-07-23
i couldnt figure why linuxdcpp was closing so i opened it up with the terminal and the sudo cammand this is what i get:


> acer@acer-laptop:~$ sudo linuxdcpp
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Bus error
acer@acer-laptop:~$ 



then after that after a bit of goggling i found dmesg

i got more of this than i can even scroll through to the last command

> 1265.454588] attempt to access beyond end of device
[ 1265.454591] sdc1: rw=0, want=27474149024, limit=623755692
[ 1265.454595] attempt to access beyond end of device
[ 1265.454597] sdc1: rw=0, want=18683376600, limit=623755692
[ 1265.454601] attempt to access beyond end of device
[ 1265.454604] sdc1: rw=0, want=20340468976, limit=623755692
[ 1265.454607] attempt to access beyond end of device
[ 1265.454609] sdc1: rw=0, want=15269629800, limit=623755692
[ 1265.454613] attempt to access beyond end of device
[ 1265.454615] sdc1: rw=0, want=3632268680, limit=623755692
[ 1265.454619] attempt to access beyond end of device
[ 1265.454621] sdc1: rw=0, want=17241396272, limit=623755692
[ 1265.454624] attempt to access beyond end of device
[ 1265.454627] sdc1: rw=0, want=25837360504, limit=623755692
[ 1265.467491] attempt to access beyond end of device
[ 1265.467499] sdc1: rw=0, want=10871528456, limit=623755692
acer@acer-laptop:~$ 



my disk drive is a usb drive and working correctly because i am watching a video now from that drive, it is not full, i have plenty of ram and it happened before any software updates.

what gives?

how do i find out what happened?

what causes this ?

---

### Post by rexxxlo on 2010-07-26
oh this is a laptop and a 2.5" usb drive that has a dual usb plug to provide power

---

### Post by rexxxlo on 2010-08-02
bump

---

