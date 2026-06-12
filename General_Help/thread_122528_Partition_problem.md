---
title: "Partition problem"
date: 2006-01-27
forum: General Help
---

### Post by samurai017 on 2006-01-27
I am installing ubuntu and I gave ubuntu 41G but when I procide it says that it will formate all my hard drive. I do not want to loss my stuff that i have in there. please help me ^^

---

### Post by byen on 2006-01-27
Hey samurai017...welcome to Ubuntu!
Now.. I need to understand your situation a little more..Are you dual booting with another OS and installing Ubuntu in an empty drive?

---

### Post by samurai017 on 2006-01-27
For the information you ask I want to duel boot with Windows XP. i have a cd and everything but when I got the the peartition option it selected Manually edit patition table then from there on i pretty much lost i got to a point where i gave 40G to Ubuntu and it said that i will formation both patitions. I am new to this so I stoped at that point to ask for help. Thank you for advance.

---

### Post by byen on 2006-01-27
Ok.. see if this link helps:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
It has all the necessary steps needed step by step pictures and might help you.

PS: So Windows is in the C: drive and you have a different drive where you want to install linux?

---

### Post by samurai017 on 2006-01-27
No i want to do both winwos and ubuntu in the c drive if posible.

---

### Post by byen on 2006-01-28
OK. Now we have a problem. You see.. Windows uses NTFS file system for XP and linux uses EXT3 (among others) file system. It is not possible to install both windows and linux in the same drive (file system) due to compatability issues and file-system restrictions. If you can, I suggest using a program like "Partition Magic" in windows which would help you create a new partition without having to format or remove existing data.

EDIT: I just found a thread that might help you..check it out.
[http://www.ubuntuforums.org/showthread.php?t=124587](http://www.ubuntuforums.org/showthread.php?t=124587)

---

### Post by samurai017 on 2006-01-28
Thanks for your help. I will use patition magic to see fi that does it.

---

### Post by psomas on 2006-01-28
i had windows xp,and installed ubuntu in same drive...
it made automatically the partition...
i just defined the space that ubuntu would have...
it said that it will format both partitions,but it didn't...
normally after the installation you will have 3 partitions...
1 ntfs,1 ext3,and 1 swap(or something like this)...
i did this twice,because i reinstalled ubuntu...
however if you're not sure,and don't want to risk losing your windows partition then don't do it... ;)

---

