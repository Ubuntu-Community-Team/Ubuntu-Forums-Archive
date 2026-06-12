---
title: "Problem installing latest NVIDIA Forceware drivers!"
date: 2006-04-18
forum: General Help
---

### Post by Rakanishu on 2006-04-18
Hi.
I have been trying to install the latest NVIDIA Forceware drivers for my Geforce 6800 GS, with quite bad results.

First, when I entered:
```
sudo /etc/init.d/kdm stop
```
I got to the part where the computer checks the battery, and it says the batteries are okay, but then everything freezes and I never get to the command line. Pressing any buttons doesn't make any difference.

Then I decided to reboot and go into failsafe instead, and do the installation from there.

So I logged in to my user account using: 
```
login
```
and then entered:
```
sudo sh NVIDIA-Linux-x86-1.0-8756-pkg1.run
```

Everything seemed to run fine then, but then I got the message:
```
Skipping the runlevel check (the utility 'runlevel' failed to run)
```

I pressed ok, and was prompted with the license agreement, which I accepted.

Then I got another message:
```
No precompiled Kernel interface was found to match your kernel, do you want to download one from www.nvidia.com?
```

I have tried pressing both yes and no, but either of them leads to the message:
```
No precompiled Kernel was found to match your interface, this means the installer will ned to compile a new Kernel interface.
```

I pressed ok, and got this lengthy message:
```
gcc-version-check failed:
./usr/src/nv/conftest.sh: line 19: cc: c command was not found

Could not compile gcc-version-check.c.
Please be sure that you have your distribution's libc developer package installed and that 'cc' is a valid compiler name.

Press yes to abort installation, or press no to ignore gcc version check.
```

I pressed yes because I felt that things got a bit out of hand.

Now, do any of you guys have a clue of what's wrong?
Is it because I'm in failsafe mode that this happens?
If so, then I apparently have to fix the fact that I can't shutdown KDM properly. Or is a shutdown of KDM and running in failsafe mode the same thing?

Very thankful for any help!

---

### Post by Darkriser on 2006-04-18
sudo apt-get install build-essential gcc gcc-3.4
sudo CC=gcc-3.4
sudo export CC

and try again

---

### Post by Darkriser on 2006-04-18
in general, Method 2 of the following HowTo works great:

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

### Post by Rakanishu on 2006-04-18
[QUOTE=Darkriser]sudo apt-get install build-essential gcc gcc-3.4
sudo CC=gcc-3.4
sudo export CC

and try again[/QUOTE]

Thanks for the fast answer.
I have one problem with using 'sudo CC=gcc-3.4' though.
It says "command not found".
What should I do?

---

### Post by Darkriser on 2006-04-18
forget the 'sudo' part....](*,)

---

### Post by Rakanishu on 2006-04-18
Ahh, ok. ;) Anyway, to install the drivers I still need to close down X. And I can't do it with the regular stop-command, as written above. Can I as well boot in recovery mode and install the drivers?

EDIT: I booted in recovery mode and successfully installed the drivers. Thanks for the help both of you! That guide came in handy too.

---

