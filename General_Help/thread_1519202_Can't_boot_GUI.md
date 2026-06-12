---
title: "Can't boot GUI"
date: 2010-06-27
forum: General Help
---

### Post by YaKillaCJ on 2010-06-27
For some reason Ubuntu isnt booting into the Graphical User Interface. I keep getting thrown into the the Terminal asking me to login. All functions there and working but I dont know whats the issue. Happened after a update. Its a fresh install on a Dual Boot (with Windows 7).

---

### Post by SecretLegend on 2010-06-27
Hey are you positive you didn't install Ubuntu Server or some other Distro? If not you should reinstall.

---

### Post by YaKillaCJ on 2010-06-27
Yea im sure. Im usin windows 7 right now. Thing is I did it twice and it gave me this issue.
Fresh Ubuntu.
Then all updates, then enabled all codecs, Flash, K3B, and basics ya kno. Could Ubunut Tweak cause the problem?

---

### Post by wilee-nilee on 2010-06-27
> **YaKillaCJ said:**
> For some reason Ubuntu isnt booting into the Graphical User Interface. I keep getting thrown into the the Terminal asking me to login. All functions there and working but I dont know whats the issue. Happened after a update. Its a fresh install on a Dual Boot (with Windows 7).

If you get the the command line log in then run startx then due a update and upgrade, and look for broken packages in synaptic from the custom filters tab.

You can also use the 2nd line in the grub kernel list recovery to get to a gui that has a fix broken packages, you have to be hard plugged in there to get update and a upgrade then if it fixes anything click on boot normally, and login and run startx there as well.

Also have you ever gotten to the regular desktop, and is this a dual boot or a wubi install.

---

### Post by laithk50 on 2010-06-27
hmmm...try logging in via terminal and issuing the following command to start the x graphical server:
```
startx
```

one question: what kind of graphics card do you have? (yes, it is very important) :confused:

---

### Post by YaKillaCJ on 2010-06-28
Thanx for your prompt responces, ill try out what yall suggested in a bit. I tried init 4 and 5, lol. Its been awhile since I had 2 do that and last time it was on Fedora bout 2 years ago. 

Its a Dual Boot. I manually had to make the partition form some reason. I did the 1 where it makes like a 2nd partition. Then ya put ext4 as / (partition 3) and a Swap (partition 4). I tried the other kernels.

---

### Post by YaKillaCJ on 2010-06-28
GeForce 6150SE nForce 430

I got in using startx, did updates. 1 of em included gnome manager which my guess was issue. As of right now, all is good, so problem solved and thanx alot ^_^

---

