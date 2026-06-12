---
title: "No init found"
date: 2011-04-03
forum: General Help
---

### Post by pyrial on 2011-04-03
I tried the different measures to fix this, so I started a new thread to hopefully help present the fix I found.
 
First I installed ubuntu on a seperate hard drive and ran that as primary hard drive. then I opened terminal and entered:
 
*sudo fdisk -l*
 
The errored hard drive was sdb1. I then entered:
 
*sudo fsck /dev/sdb1*
 
There were questions i answered yes to then, after swapping drives, I booted normally. Everything was normal exccept I have to choose a different version of ubuntu at startup. I havent had any problems so far but this was just an hour ago. Good luck and hope this helps.

---

### Post by pyrial on 2011-04-05
Well that didnt work.
 
After hours of my puter running and constant reboots my system finally crashed with the same error again. Patterns suggest that ubuntu doesnt work well with quad core processors. I think its actually the amount of memory in combination with quads that causes this error, but there are no memory or processor spikes when the error occurs. All I feel now is :confused:

---

### Post by pyrial on 2011-04-14
Since my last post I've not had any problems with my machine.

All I've done is kept the errored drive as secondary hard drive. Ubuntu now constantly accesses the primary hard drive for information, but I havent had any freezes or problems so far and its been running non stop. Hope this helps

---

