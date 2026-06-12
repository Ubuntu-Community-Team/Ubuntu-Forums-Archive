---
title: "Connecting sony ericcson w595"
date: 2009-09-07
forum: General Help
---

### Post by Benzaa on 2009-09-07
Hi,

Does anybody have manage to transfer files from a sony ericsson to ubuntu with using the newest kernel??

I've been trying to do so but the computer does not recognize the memory card in the phone. Using lsusb, the kernel tells me that the phone is connected. 

With dmesg, there is a loop
```

[ 5407.343656] sd 7:0:0:1: [sdc] Sense Key : No Sense [current] 
[ 5407.343671] sd 7:0:0:1: [sdc] Add. Sense: No additional sense information
[ 5407.356084] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 5407.356099] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 5407.375555] sd 7:0:0:1: [sdc] Sense Key : No Sense [current] 
[ 5407.375570] sd 7:0:0:1: [sdc] Add. Sense: No additional sense information
[ 5407.388047] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 5407.388061] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information

```

Any ideas??

---

### Post by Benzaa on 2009-09-07
nobody??

---

### Post by Jerubaal on 2009-09-12
I'm planning on buying one - have you got anywhere with it?

---

### Post by Benzaa on 2009-09-14
Nop

I have no idea how to connect it.

I have to use my windows partition to transfer files

---

### Post by karpatt on 2009-10-30
See here :

[http://newyork.ubuntuforums.org/showthread.php?t=1140056](http://newyork.ubuntuforums.org/showthread.php?t=1140056)

---

### Post by Benzaa on 2010-01-17
In case that someone is having this problem, here is the solution

[http://www.ostalk.org/showthread.php?tid=635](http://www.ostalk.org/showthread.php?tid=635)

Hope it helps

---

