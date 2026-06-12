---
title: "ASUS Laptop Freezing"
date: 2012-01-11
forum: General Help
---

### Post by timtaves on 2012-01-11
Hey there, I just got an ASUS G74S laptop.  I installed ubuntu 11.10 on  it and now it is crashing about once per day.  When it crashes the  screen just freezes and the caps lock button blinks.  I think this is  called a kernel panic.  When it happens I have to use the physical  on/off switch to turn it off and then back on.

From looking at forums it seems that other people have fixed this (on  different computers) by turning off their wireless connection and the  typing:  

sudo iwconfig wlan0 power off

into the terminal (I use wlan1).  This helps quite a bit but now I get  kernel panics about once or twice per week instead of once or twice per  day.  This is still a big problem for me as I need to run c++  simulations which take ~week to run.  

Any ideas?  Some of my specs are below.  Thanks in advance.

P.S. - I already posted this in the ASUS section but I realized that that may not have been the most appropriate place for it.  If this is not cool let me know and I won't do it again.

i7 - 2670QM - 2.2GHz
750GB HD+120GB SSHD (My OS is on the 120GB SSHD.  The system doesn't use RAID.)
I upgraded this from two 750GB HDs.
16GB of RAM - upgraded from 12GB.

---

