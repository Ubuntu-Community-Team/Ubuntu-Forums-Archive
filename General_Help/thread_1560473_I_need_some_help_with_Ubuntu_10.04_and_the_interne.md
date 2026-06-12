---
title: "I need some help with Ubuntu 10.04 and the internet"
date: 2010-08-24
forum: General Help
---

### Post by MasterRyan on 2010-08-24
Okay, so i had the old ubuntu 9.10, and last night updated it to 10.04 (LTS) 
on ubuntu the internet was quick fast and nothing wrong with it.
when i finished upgrading to 10.04(LTS) i tried going onto mozilla firefox
and no matter what i do, i cant get it to go quickly, it either is really freaking slow
or it says connection timed out, or cannont find page, 404 error

i know its not my internet connection because i have 3 other computers in the house and they are all running super fast internet, and when i have 9.10 the internet was super fast, but only since i updated to 10.04(LTS) the internet has been going super slow.

Can someone help me please? im only new to Ubuntu, but im a quick learner and im getting through it super fast, so any other tips and information would be greatly appreciated :) Thanks

---

### Post by Iowan on 2010-08-24
Check your nameserver in */etc/resolv.conf*. IPv6 has also been blamed for slow internet access - as has MTU. Dunno how many (if any) have changed since 9.10.

---

### Post by lovinglinux on 2010-08-24
Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by MasterRyan on 2010-08-25
> **lovinglinux said:**
> Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").


Yes i have ipv6 disabled, It's really shockingly slow, i dont know where to go from here :S and i really cant be bothered re-installing 9.10 i like 10.04 to much. Hmm..:popcorn:

---

### Post by fresnofred on 2010-08-25
I had the same problem with kosmic karma on one of my pcs as the other with the same system was fast.  on the slow pc internet, i opened TOP in a terminal and noticed a program was running, not in root, called ICA.  I "killed" it 2 or 3 times as it kept popping up again.  When i got back on the internet, the connection was superfast and when I went back into the terminal and typed "top", the program was not running.  Perhaps this is what slowed my surfing down.  When i boot up again and try the net it will be interesting to run "top" again and see if ICA is once again running and if my surfing is slow and if it speeds up again if i kill "top" again.  To kill a program, open terminal, type "top", and find a non-root program and notice the number and type "k" followed by the program number and hit enter once and then again....ICA may have to be killed a few times.   See if this helps.

---

### Post by 7528620xs on 2010-08-25
i know its not my internet connection because i have 3 other computers  in the house and they are all running super fast internet, and when i  have 9.10 the internet was super fast, but only since i updated to  10.04(LTS) the internet has been going super slow.



   [ed hardy bags](http://www.edhardy-sale.net/)/[ed hardy clothing](http://www.edhardy-sale.net/)/[ed hardy shoes](http://www.edhardy-sale.net/)

---

### Post by afrowildo on 2010-08-25
You should check out this thread. The problem here wasn't restricted to 10.04, but may still be the same one.

[http://ubuntuforums.org/showthread.php?t=1395866](http://ubuntuforums.org/showthread.php?t=1395866)

If that doesn't work, then this next thread has a number of possible solutions, with post [#17]("http://ubuntuforums.org/showpost.php?p=9044672&postcount=17") being the solution to that particular problem.

[http://ubuntuforums.org/showthread.php?t=1434732](http://ubuntuforums.org/showthread.php?t=1434732)

---

