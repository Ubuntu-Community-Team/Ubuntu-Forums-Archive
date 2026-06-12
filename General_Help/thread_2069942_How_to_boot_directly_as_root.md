---
title: "How to boot directly as root"
date: 2012-10-11
forum: General Help
---

### Post by dinamex on 2012-10-11
Hi there,

I want to use OpenNI on a pandaboard. Unfortunately, I need root rights (some USB issues) to run the programms. Therefore I use ```
$sudo su 
```and run the programm. But I want to launch to programms with a script directly when I bootup and therefore it would be handy to boot (everytime/automaticaly) as root.

Would be great to get a hint where to look...

Regards,
Ronny

---

### Post by CCgirl6690 on 2012-10-11
Id install backtrack 5, its all root

---

### Post by MG&amp;TL on 2012-10-11
Logging as root is discouraged on these forums, for various reasons.

However, take a peek here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) - seek and ye shall find.

---

### Post by dinamex on 2012-10-11
thank you for your answer but I cant find a solution on this webpage. there is just the explanation how to add sudorights to a user or how to open a sudo shell. 
I need a bootup as root. (like linaro)

I know that this shouldn't be the normal way but my project is on a embedded board and to have sudo rights directly at startup would make some things alot easier for me.

---

### Post by lisati on 2012-10-11
As MG&TL has noted, "login as root" tutorials are discouraged here. 

Please take a look here:
[http://ubuntuforums.org/showthread.php?t=2021357](http://ubuntuforums.org/showthread.php?t=2021357)
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

