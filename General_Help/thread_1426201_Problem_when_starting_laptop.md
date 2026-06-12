---
title: "Problem when starting laptop"
date: 2010-03-10
forum: General Help
---

### Post by xJoshR on 2010-03-10
I'm running ubuntu 9.10 Karmic Koala
I had originally messed something up by accidentally changing permissions on /usr/bin to 777, which disabled me from using sudo.
fixing the permissions by root shell, and now when i try and start up my laptop it gets to the
 
"
Ubuntu
<progress bar thing here>
"
 
and then flashes between that screen and a black screen which says "*nmpd is running" or something.
 
Do i have to completely reinstall ubuntu or is there a way i can save myself? Please help!

---

### Post by xJoshR on 2010-03-10
Does nobody have any suggestions?

Also, when i try and use a command in root shell now, i get flooded with "parse error in /etc/sudoers".

---

### Post by iponeverything on 2010-03-10
what was the command that you ran.

If it was a recursive chmod, you might be better off reinstalling.

777 is never appropriate in my option. There are number of very easy to understand tutorials available for unix style permissions available via a google search. Spend an hour learning them and it could save you time in the future.

---

### Post by pastalavista on 2010-03-10
When you reinstall, use the same user name and when you get to the partition setup screen, select MANUAL install and UNCHECK ALL the 'format' boxes from previous setups. No chance of erasing anything that way except system files which will be replaced. You'll need to do updates again.

---

### Post by iponeverything on 2010-03-10
> **pastalavista said:**
> When you reinstall, use the same user name and when you get to the partition setup screen, select MANUAL install and UNCHECK ALL the 'format' boxes from previous setups. No chance of erasing anything that way except system files which will be replaced. You'll need to do updates again.

very good tip.

---

