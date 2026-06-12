---
title: "Changing Permissions of Files from LiveCD"
date: 2011-07-25
forum: General Help
---

### Post by blenderman345 on 2011-07-25
Hey everyone, it's me, that guy who comes every number of months every time he has a problem. :)
Anyhow, here's the problem. Long story short, my MacBook Pro's hard drive is all messed up, I'm trying to salvage files using an external HDD and an Ubuntu LiveCD, but the Users folder has 501 permission, and I am unable to change this using the shell (sudo chmod 777 -R [folder]). 

Thanks for any help!

---

### Post by Kira_Belka on 2011-07-25
> **blenderman345 said:**
> Hey everyone, it's me, that guy who comes every number of months every time he has a problem. :)
Anyhow, here's the problem. Long story short, my MacBook Pro's hard drive is all messed up, I'm trying to salvage files using an external HDD and an Ubuntu LiveCD, but the Users folder has 501 permission, and I am unable to change this using the shell (sudo chmod 777 -R [folder]). 

Thanks for any help!

:) what's problem?
mount your external HDD and change permissions.. really if your home aren't crypted..I don't see problem :)))

---

### Post by blenderman345 on 2011-07-25
Well, from the LiveCD, it's not executing a 'sudo chmod' properly, because after I do that it still won't change the permissions. It's OS X's main hard drive, the home folder might be encrypted. Is it possible to access the files with my OS X account's username and password?

---

### Post by Kira_Belka on 2011-07-25
> **blenderman345 said:**
> Well, from the LiveCD, it's not executing a 'sudo chmod' properly, because after I do that it still won't change the permissions. It's OS X's main hard drive, the home folder might be encrypted. Is it possible to access the files with my OS X account's username and password?

mmmm..if folder encrypted ((( .. 
about changing rights on folder.. try on change owner to root...mmmm..
 and when you use chmod .. try -v option.. so you can see what's happened exactly.

---

### Post by mcduck on 2011-07-26
If the drive is formated in Journaled HFS+ or the drive is larger than 2TB, Linux will at the moment only mount it as read-only. And that would explain why you can't chown files...

---

