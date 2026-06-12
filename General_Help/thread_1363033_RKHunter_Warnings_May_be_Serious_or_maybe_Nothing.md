---
title: "RKHunter Warnings: May be Serious or maybe Nothing?"
date: 2009-12-23
forum: General Help
---

### Post by ScottishGirl on 2009-12-23
[SIZE="4"]Hi Everyone :)

I am running Ubuntu 9.10 and when I ran 'RKHunter' I got a number of warnings.  I checked the log file and amongst other warnings I saw the following:
 [03:21:48] /usr/sbin/adduser                                 [ Warning ]

[03:21:48] Warning: The command '/usr/sbin/adduser' has been replaced by a scrip

t: /usr/sbin/adduser: a /usr/bin/perl script text executable


Checking /dev for suspicious file types         [ Warning ]

[03:23:14] Warning: Suspicious file types found in /dev:

[03:23:14]          /dev/shm/pulse-shm-2677351470: data

[03:23:14]          /dev/shm/pulse-shm-1576892285: data

[03:23:14]          /dev/shm/pulse-shm-3693035992: data

[03:23:14]          /dev/shm/pulse-shm-2618005978: data

[03:23:14]          /dev/shm/pulse-shm-2013227696: data

[03:23:14]   Checking for hidden files and directories       [ Warning ]

[03:23:14] Warning: Hidden directory found: /etc/.java

[03:23:14] Warning: Hidden directory found: /dev/.udev

[03:23:14] Warning: Hidden directory found: /dev/.initramfs
[/SIZE]

I am concerned about these warnings because they sound serious and I don't know what to do to check them out.  
 RKHUnter also detected two passwords in my passwd file that are completely unknown to me.  I am a single user so nobody else has direct access to my computer.
 I have read that RKHunter is giving false positives on the xzibit rootkit and I wonder if the program is also flagging up as warnings things that aren't that much of a security risk?
 
Any help in decoding the above will be much appreciated. :smile:

Stephanie

---

### Post by Krovas on 2009-12-23
Well, I've seen those hidden directories all the time, but I can't vouch for the rest of it.

---

### Post by dcstar on 2009-12-23
> **ScottishGirl said:**
> [SIZE="4"]Hi Everyone :)

I am running Ubuntu 9.10 and when I ran 'RKHunter' I got a number of warnings.  I checked the log file and amongst other warnings I saw the following:
.......

Distros evolve all of the time, things that are supposed to detect potential issues do not keep up at the same rate.

You can almost guarantee that these are all normal for a 9.10 system - given the absolute lack of posts about people's Linux systems being compromised by any "root kits".

People are at far more risk installing packages outside of the official repos, as they do on a constant basis (as the recent "screensaver" issue showed).

---

