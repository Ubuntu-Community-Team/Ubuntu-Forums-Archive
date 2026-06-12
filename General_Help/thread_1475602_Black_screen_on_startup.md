---
title: "Black screen on startup"
date: 2010-05-07
forum: General Help
---

### Post by satish_j on 2010-05-07
Iam facing a weird problem with ubuntu since last week...
Starting system-->selecting ubuntu from grub menu-->ubuntu splash screen comes and it loads fully-->black screen is displayed instead of login window..
Restarting the system and the prob is gone..able to login properly..

This problem is ocurring randomly..sometimes i can login in 1st attempt properly,other times i have to restart the system twice or even thrice to get to the login screen..
Any ideas what can be the possible reason to this...I have not done any updates also..

---

### Post by dino99 on 2010-05-07
have these issues myself, and its a weird random story since we have distro built with evdev/ext4/grub2 (karmic b1), then plymouth and/or compiz bring more mess too. Seems to be a timers race at boot time.

try:

- check hardware driver to see if its well activated
- sudo apt-get install -f
- sudo dpkg --configure -a
- sudo dpkg-reconfigure gdm
- sudo dpkg-reconfigure plymouth

- sudo shutdown -F -r now  (will force a fsck at next reboot)

---

### Post by iblazev on 2010-05-07
Hello!
I had a similar thing - my comp started to boot but then when it supposed to display login screen, it restarted, then it worked fine.

Then I tried what you said:

> **dino99 said:**
> 

- check hardware driver to see if its well activated
- sudo apt-get install -f
- sudo dpkg --configure -a
- sudo dpkg-reconfigure gdm
- sudo dpkg-reconfigure plymouth

- sudo shutdown -F -r now  (will force a fsck at next reboot)

and so far it works great. There aren't any proprietary drivers so reconfiguration of gdm and plymouth seems to do the trick.
Thanx! :popcorn:

---

