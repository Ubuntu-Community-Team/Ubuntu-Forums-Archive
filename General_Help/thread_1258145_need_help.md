---
title: "need help"
date: 2009-09-04
forum: General Help
---

### Post by Darks_bane on 2009-09-04
Hey everyone,
So i'm fairly new to ubuntu.  I've been trying to install MS word fonts onto openoffice and found that the command for this is:

 sudo apt-get install msttcorefonts

but when i run this i get an error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

so i ran the command 

sudo dpkg --configure -a

however i'm completely lost as to what to do after... so if anyone could help me that'd be great

---

### Post by Whiffle on 2009-09-04
Try running your original command again, looks like there was some sort of foul up with apt, but "sudo dpkg --configure -a" should have cleared it.

---

### Post by Darks_bane on 2009-09-04
Hi okay so i did that and i got this: 

rajesh@ubuntu:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  msttcorefonts: Depends: ttf-mscorefonts-installer but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Whiffle on 2009-09-04
Ah I see.  Apt is complaining because something you're trying to install doesn't have all of its dependencies met, and then probably won't run.  Try doing "apt-get -f install"

---

### Post by Darks_bane on 2009-09-04
[LEFT] okayyy


E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?



um... does this mean it doesn't think im admin? how'd i change that?
[/LEFT]

---

### Post by NoaHall on 2009-09-04
Stop using it in other terminals/gui's

---

### Post by Darks_bane on 2009-09-04
sorry what does that mean...?

---

### Post by Whiffle on 2009-09-04
> **Darks_bane said:**
> [LEFT] okayyy


E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?



um... does this mean it doesn't think im admin? how'd i change that?
[/LEFT]

I'm guessing you didn't put sudo (which gives you root privileges) in front of that last command (i should have put it there, but I tend to forget...).  Sudo is what allows certain users in ubuntu to make system changes.  If you run a program, such as apt-get, which requires you to have root privileges to run, it will give you an error much like that one.

EDIT: the correct command should have been "sudo apt-get -f install"

---

### Post by Darks_bane on 2009-09-04
=D yay! thanks a lot guys!

---

