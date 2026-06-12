---
title: "Checking battery state ... &amp; Login timed out after 60 seconds"
date: 2010-07-14
forum: General Help
---

### Post by dara168 on 2010-07-14
Dear friends,

I just installed Ubuntu server 10.04 LTS on Dell Optiplex 380 with gnome desktop.
After setting up Samba, I disable gnome desktop from start up by eding GRUB config file.

Everything works just fine. 

But this evening, when I tried to boot my server it hanged for about 3 minute with

```
Checking battery state ...
```After that come the login. After I inputed my user and password it hanged again for 1 minute than it displayed a message saying

```
Login timed out after 60 seconds.
```I tried to login agian and again but end up with the same error message.

I was sure i typed the correct user and password.

Any idea what was going wrong?

Any reply would be appreciated.

---

### Post by dara168 on 2010-07-14
Any help please!

Anyone?

---

### Post by borth92 on 2010-07-14
Open a terminal and type:
sudo apt-get install -f

This will fix any broken packages in your installation that may be causing the problems. Not sure if this will work, but post the results...

---

### Post by e.m.fields on 2010-09-06
hey there. did you ever find a solution to your problem?
I just had the first issue with this today, running Maverick Alpha 3, don't know what's caused it.
I booted up into "recovery mode" from GRUB menu, and chose "failsafe mode".  It seemed to boot into my normal desktop fine, no problems, so I'll reboot and see what happens from normal boot now. 

Weirdness.

---

