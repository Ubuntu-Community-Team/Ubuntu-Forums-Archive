---
title: "ESATA hot swap JMB362 broken"
date: 2010-12-28
forum: General Help
---

### Post by CPUUnlimited on 2010-12-28
Hello, I hope someone can assist me here.  I have been using UBUNTU 10.04 for months now and was very happy with it for the most part.  I am now trying the new 10.10 and just can not seem to figure out what happened to my ESATA hot swap ability.

when I run lspci I can see the Jmicron Tech JMB362 so I assume that means it should be working.

However when I put a drive in my ESATA bay I can not access it.  I have to have the drive already in the bay while booting UBUNTU in order to see the drive.  This will NOT work for me.. I must have the hot swap working and would appreciate any help any of you may have to offer.

Thank you

CPUUnlimited

---

### Post by McLogic on 2011-01-23
I am concerned about this **regression**. The Ubuntu developers should also be concerned. The current and upcoming desktop boards from the major manufactures are using this J-Micron chip for E-SATA. Thousands and thousands of new boards a day!

My only advice is to revert to a backup, or make a new install of 10.04.1 to get the JMB362 working again. The LTS versions are the best choice if you need to have a system for getting work done.

---

