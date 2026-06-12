---
title: "aticonfig: command not found Please Help"
date: 2010-05-13
forum: General Help
---

### Post by Tapas Bose, India on 2010-05-13
Hello everybody. I have installed ati driver in my desktop as described in [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) using ati-driver-installer-10-4-x86.x86_64.run file. But I am stuck on initialize aticonfig step. Whenever I am trying to execute  [FONT=monospace][/FONT]```
sudo aticonfig --initial
``` I am getting error message ```
aticonfig: command not found
```. Please help.

---

### Post by Globestern on 2010-05-13
hi

I've the same issue.

the problem is, that the links for aticonfig, fglrx etc doesnt exist.

they're located at /usr/lib/fglrx/bin

greets

---

### Post by kontiky on 2010-05-18
I've tried
```
kontiky@Dolphin:~$ cd /usr/lib/fglrx/bin
kontiky@Dolphin:/usr/lib/fglrx/bin$ sudo ./aticonfig --initial
```and got
```
Unable to open /etc/ati/control, please reinstall the driver.
./aticonfig: No supported adapters detected
```
How should I init fglrx driver?

---

### Post by Tapas Bose, India on 2010-05-18
Hello. I solved the problem. A stated here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) first time i followed the first instruction but I saw the "UBUNTU" in the boot screen is too big, i thought there may be some problem with my installation procedure, so I again try the second method and I got aticonfig : command not found. I was disappointed, and then I saw we should follow any one of these procedure. So I reinstalled Ubuntu (Thanks to god that I not installed any other softwares). And try the second one that is under the heading "**[FONT=Times New Roman][SIZE=2]Install the fglrx Driver from ATI Catalyst 10.3 For Ubuntu 9.10  Karmic[/SIZE][/FONT]**". And the problem is solved but the "**Plymouth**" logo was still ugly, after little googling I found it [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml) this solved the problem. I think this will help you. :P

---

