---
title: "Need to select safe mode when logging in"
date: 2010-11-19
forum: General Help
---

### Post by nnn= on 2010-11-19
I have to choose safe mode when logging in, otherwise (if I leave "Ubuntu desktop edition") after the desktop shows, the login prompt returns.

After I've logged in, if I go to switch users, then login back to the same user but with Ubuntu desktop selected (no safe mode) then it logs in fine.

I'm trying to understand what the problem is.

---

### Post by nnn= on 2010-11-24
No conjectures?

---

### Post by Rubi1200 on 2010-11-24
Hi,
could you please provide us with some more information to help us troubleshoot the issue.

1. what version of Ubuntu are you running?

2. are there other operating systems installed and what?

3. how did you install Ubuntu; to the drive or via Wubi?

4. did you recently update/upgrade the system?

5. what graphics card and how much RAM is installed?

6. has this always been a problem; if not, when did it start?

Thanks.

---

### Post by OldTech57 on 2010-11-24
Having same issue with Maverick 10.10 can't use desktop anytime.. safemode only works....I hope you get an answer...

---

### Post by nnn= on 2010-11-24
1. what version of Ubuntu are you running?
10.10

2. are there other operating systems installed and what?
No.

3. how did you install Ubuntu; to the drive or via Wubi?
To the drive.

4. did you recently update/upgrade the system?
Yes, I recently upgraded from 9.04 via recommended procedure.

5. what graphics card and how much RAM is installed?
Graphics Card: VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 11) (prog-if 00 [VGA controller])
RAM: 480.8 MiB

6. has this always been a problem; if not, when did it start?
In 9.04 I didn't have this problem. When I upgraded, I did not use any of the intermediate releases, so I only started to have this problem when I finished upgrading to 10.10.

By the way, I just logged in after a restart, and now I have a frozen X cursor in the centre of the screen, even though my regular cursor is also there and works fine.

---

### Post by Rubi1200 on 2010-11-25
When you say "safe mode," do you mean the GNOME-Failsafe session or from the Recovery Mode?

Try this, login using Failsafe and turn off desktop effects and see if it makes a difference.
System>Preferences>Appearance (visual effects, none)

Also, take a look here:
[http://ubuntuforums.org/showthread.php?t=830531](http://ubuntuforums.org/showthread.php?t=830531)

(my advice would be to ignore the second post and look perhaps at the last one).

---

### Post by nnn= on 2010-11-25
I suppose I mean GNOME-Failsafe session. But when I log in it's called, in the menu at the bottom of the screen, "Ubuntu desktop edition (safe mode)".

---

### Post by nnn= on 2010-11-26
If the solution you suggested consisted of renaming/deleting .profile, it didn't work. After I renamed the file, after restart it wasn't recreated and I still had to choose safe mode when logging in.

---

### Post by nnn= on 2010-11-26
I already have it set to no desktop effects.

---

### Post by nnn= on 2010-11-27
Is there something else I should try?

---

### Post by ctdesing on 2010-11-27
try ```
 sudo dpkg-reconfigure gdm
``` 

or ```
 sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by ctdesing on 2010-11-27
create another user and try login with your new user.

---

### Post by nnn= on 2010-11-27
```
sudo dpkg-reconfigure gdm
```Unsuccessful. Upon restart have a black X cursor frozen in the centre of the screen. Last time I had it, it seemed to go away after about a day.

```
sudo dpkg-reconfigure xserver-xorg
```Unsuccessful. Upon restart, again have a black X cursor frozen in the centre of the screen.

Creating another user was unhelpful as well.

---

### Post by Swagman on 2010-11-27
From grub screen, scroll down and select Recovery

---

### Post by nnn= on 2010-11-27
> **Swagman said:**
> From grub screen, scroll down and select Recovery

I didn't quite get that.

---

### Post by nnn= on 2010-11-27
Help.

---

### Post by nnn= on 2010-12-03
Help.

---

### Post by jmtd on 2010-12-05
I have the same problem on a freshly installed i386 ubuntu 10.10, which takes the whole HDD (no other OS).

safe mode login works, but normal login plays the login noise but does not draw the panel, or nautilus, etc.

Nothing is written to the user's .xsession-errors at all.

This happens for any user, including a newly created one for testing.

I can see via top that jockey and compiz are taking a lot of the CPU time whilst this is going on.

In safe mode, if I go to System -> Preferences -> Appearance, effects is already set to "None".

This is a Compaq Evo N1015v laptop, fairly old, athlon XP 1.6GHz CPU, 256M RAM (ouch! didn't realise it was that low); ATI Radeon mobility U1 video.

---

### Post by jmtd on 2010-12-05
I fixed this by uninstalling compiz.  A more brute-force solution than I would have liked, but it worked for this machine.

---

### Post by Cee# on 2011-05-05
You won't get any help on this. I have been trying to solve this issue for months. If you do get help the reponse will be so cryptic that you will have to research the response to see what it means. I am giving up and trying RedHat or one of the other versions because this community is a basket case... which is probably a result of the way the OS is developed and managed, not anyone in particular's fault.

---

