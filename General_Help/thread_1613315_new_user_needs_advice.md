---
title: "new user needs advice"
date: 2010-11-04
forum: General Help
---

### Post by reptile1 on 2010-11-04
Hi i have 3 questions
1.Have installed ubuntu 10.04 on 2 pc's both run xp 
on 1 pc boot up selects xp  the other selects ubuntu as the first choice. Why?
2.How do I uninstall ubuntu, and what effect will it have on xp ( both imported xp documents and settings ).
3.Do I need an antivirus or spam/malware filter?

Thanks
Rep

---

### Post by ibizatunes on 2010-11-04
A tip put this in absolute beginner area next time...

Hi i have 3 questions
> 1.Have installed ubuntu 10.04 on 2 pc's both run xp 
on 1 pc boot up selects xp the other selects ubuntu as the first choice. Why?
The reason the grub loader, that is what allow you to select xp or ubuntu (or other os's) this can be changed configure.... Take about 30 sec... Without looking at your grub.cfg file i couldnt tell you the reason!

> 2.How do I uninstall ubuntu, and what effect will it have on xp ( both imported xp documents and settings ).
Just boot to ubuntu, and the delete the ubuntu partition and then do xp recovery and restore the MBR, 
Your document have been migrate over to ubuntu so deleting ubuntu wont delete the xp file (as long as the files are still on XP)

> 3.Do I need an antivirus or spam/malware filter? No ubuntu doesnt really need a virus scanner, you can still get spam email, but there is blocker for that

---

### Post by Crazedpsyc on 2010-11-04
1. It depends on the way you installed ubuntu. the ubuntu installer makes ubuntu the first choice. Wubi makes windows the first choice.
2. I reccomend installing ubuntu by downloading wubi from [http://www.softpedia.com/get/System/Boot-Manager-Disk/Wubi.shtml](http://www.softpedia.com/get/System/Boot-Manager-Disk/Wubi.shtml)
2. It is not really necessary to have these for a normal home user, but if you want them, Clamav is a great antivirus and evolution mail (comes preinstalled) has a great spam filter called "Spamassassain" which I believe is preinstalled and configured. If you can't get evolution to work (I knwo I couldn't at first) Install Mozilla Thunderbird. It's setup process is so easy all you have to do is enter you email address and password and you're in!

---

### Post by Crazedpsyc on 2010-11-04
Oh *UN*install, sorry about that

---

### Post by mastablasta on 2010-11-04
> **reptile1 said:**
> Hi i have 3 questions
1.Have installed ubuntu 10.04 on 2 pc's both run xp 
on 1 pc boot up selects xp the other selects ubuntu as the first choice. Why?
2.How do I uninstall ubuntu, and what effect will it have on xp ( both imported xp documents and settings ).

 
how did you install it by using Wubi? if so then when you remove it everything you did in that disk area it will be removed. you can move it to windows area of the disk and that way data will stay on computer.
 
if you have it installed on separate disk or parittion then simply moving files from that partition to another before removing ubuntu will keep the files safe.
 
> 
3.Do I need an antivirus or spam/malware filter?
Thanks
Rep
 
if you plan to also use windows it might be a good idea to have some antivirus (ClamAV maybe?!) installed. though most likely it will search for windows viruses.

---

