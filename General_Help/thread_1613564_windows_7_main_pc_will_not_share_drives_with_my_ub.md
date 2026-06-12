---
title: "windows 7 main pc will not share drives with my ubuntu pc"
date: 2010-11-04
forum: General Help
---

### Post by ab0ez on 2010-11-04
Greetings.

This is a new problem I have never encountered before.  I have two computers, both dual boot.  When both are running windows, drive sharing works fine.  When the PC in my workshop is running Ubuntu (preferred) I cannot access the drives on the computer in my house while it is running windows 7.  Ubuntu does see the computer, but when I try and access the drives on the W7 computer I get prompted for a password and I have tried all of the usernames and passwords for both computers, no joy.  The MS firewall on the W7 PC in the house is turned off.

I have never had this problem before with drive sharing between to the two platforms.  Does anybody have any idea what's up?

Thanks,

Jim, AB0EZ

---

### Post by dcstar on 2010-11-05
> **ab0ez said:**
> Greetings.

This is a new problem I have never encountered before.  I have two computers, both dual boot.  When both are running windows, drive sharing works fine.  When the PC in my workshop is running Ubuntu (preferred) I cannot access the drives on the computer in my house while it is running windows 7.  Ubuntu does see the computer, but when I try and access the drives on the W7 computer I get prompted for a password and I have tried all of the usernames and passwords for both computers, no joy.  The MS firewall on the W7 PC in the house is turned off.

I have never had this problem before with drive sharing between to the two platforms.  Does anybody have any idea what's up?

Thanks,

Jim, AB0EZ

Enable the W7 Guest account and make sure the Workgroup names are consistent.

---

### Post by luvshines on 2010-11-05
Also have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1607610](http://ubuntuforums.org/showthread.php?t=1607610)

We spent days debugging it and issue was resolved after uninstalling some of the softwares on Win7 :)

---

### Post by Mark Phelps on 2010-11-05
Be careful what you remove and turn off.  

Win7 is more secure than XP because of the presence of stuff like UAC, firewall, and AV software.  IF you end up turning off all of these to get access -- that is EXACTLY the environment that make the machine susceptible to infection with malware.

---

