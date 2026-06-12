---
title: "Broken login !"
date: 2006-04-08
forum: General Help
---

### Post by philip13 on 2006-04-08
Help !

I appear to have broken the loging system in 5.10 in a weird way, can any one help please.:( 

What happened :
After test compiling the application avidemux2 (to make only, not installed), I then did a make clean.
I then obtained checkinstall (via synaptic) and proceeded to repeat my steps to generate a deb package. However I aborted the generation (needed a configure option specifying).

That is when things went strange, wallpaper disappeared, panel bars disappeared and Gnome started behaving weird.
I switched to a text console and tried to log in, on doing so I got the message "cannot cd to /home/<my home dir>" .
I logged on as root and rebooted, the graphical interface failed to materialize and I was dropped out to a text login.

I have found that I am unable to su or login as me, I have found that my group has gone (missing from ./etc/passwd). In an attempt to fix I deleted myself, recreated myself and my group and chown'ed /home/<me> to my username and group. No avail, I retired with a test user name creating the group test and executing useradd -d /home/test -s /bin/bash -g test test.
When su'ing to test the system report "No shell", /bin/bash is ok and other readable and /etc/passwd and /etc/shadow appear correct.

Any ideas ?


Thanks.

---

### Post by philip13 on 2006-04-08
Fixed it !!

Did some more digging but this time concentrated on su. Found that the reason was due to the 'other' mode for /. and /.. being unset. So I checked /. and /.. on my system and what do you know ?! it was set to 700 ! Reset to 755 and now I can log in again, why the mode got set to 700 is unknown but I will keep a close eye on this, and report back if it has something to do with checkinstall.

---

