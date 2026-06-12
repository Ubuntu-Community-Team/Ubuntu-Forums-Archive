---
title: "Login Authentication Failed and Cannot Enter Recovery Mode"
date: 2010-08-31
forum: General Help
---

### Post by drewboud on 2010-08-31
Hello Everyone.  Earlier today I was setting up ssh on a new computer.  I modified permissions on the Passwd folder to complete the setup.  I few hours later when I went to sudo something in the terminal I received the notice of an incorrect password (after using sudo prior to this), even though it was typed correctly.  

I tried to restart the computer to solve the issue, but was met with an Authentication Failed message, regardless of the user I tried to log in with.  I was hoping I could log in with recovery mode but was unable to do that as well.  I have searched a substantial amount and have not found a solution.  Could this be an issue with permissions on either the Passwd or Shadow folder?  If so, could these be changed if I ran a Live CD?  Thank you for the advice.

---

### Post by David Andersson on 2010-08-31
> **drewboud said:**
> 
Could this be an issue with permissions on either the Passwd or Shadow folder?


It depends, if you chmod o-r passwd, no user programs can read it. I guess some want to.

> **drewboud said:**
>  If so, could these be changed if I ran a Live CD?

**Yes**. From the live-cd, mount the partition with the system on it. Then sudo chmod XXX /media/YYY/etc/passwd or sudo chown ZZZ /media/YYY/etc/passwd.

For reference, on my system ls -l /etc/passwd /etc/shadow
```
-rw-r--r-- 1 root root   1800 2010-08-19 18:09 /etc/passwd
-rw-r----- 1 root shadow 1313 2010-08-19 18:11 /etc/shadow
```

**If** shadow need chown: User root always has id 0. In my system group shadow has id 42, but I don't know if that always is the case on all ubuntus. Compare live-cd's /etc/group and /media/YYY/etc/group if shadow is the same. Then you can sudo chown root:shadow /media/YYY/etc/shadow, otherwise sudo chown 0:NUMBER /media/YYY/etc/shadow, with shadow's group number in that system.

> **drewboud said:**
> Earlier today I was setting up ssh on a new computer.  I modified permissions on the Passwd folder to complete the setup.  


Why? (The only thing i did was install the package in Synaptic, or was it apt-get).

---

