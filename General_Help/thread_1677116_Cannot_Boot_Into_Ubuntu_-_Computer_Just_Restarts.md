---
title: "Cannot Boot Into Ubuntu - Computer Just Restarts"
date: 2011-01-28
forum: General Help
---

### Post by witchking87 on 2011-01-28
Hi All,

I have a Wubi based Ubuntu installation on a Dell Studio Laptop (Intel Core2 Duo), which is running Windows Vista as the main OS. I have had this for quite a while now, started off with Ubuntu 9.10. Recently, I used the automatic upgrade version to upgrade to 10.04 and this worked without any problems. 

However, I was working yesterday and during the course of my work, the normal "Updates" window came up with the list of "Recommended Updates", I don't remember exactly what the updates were, but I do remember that there were some kernel related updates. I went ahead and was asked to 'restart' the computer, but since I was working, I chose the restart later option. Leaving my work unattended for hours (read: falling asleep), I came back to be greeted by a blank screen, where as normally I would be greeted by the login screen because the computer would lock itself after a certain period of inactivity. 

Now when I try to log in to Ubuntu (from the screen where I get to choose between Windows Vista and Ubuntu), I am brought back to this screen again after a re-boot. 

I don't know whether this is relevant or not, but long back (Dec 2009), when I was on the 9.10 version, I had a slightly different problem after a kernel upgrade. I would be directed back to a command prompt after selecting Ubuntu and then the latest Kernel version that I wanted to boot. I solved this, first temporarily by punching in some commands at the command prompt and then permanently by downloading a "wubildr" file from the links provided in one of the forums. The link below is the description of the problem that I had back then

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10&oldid=214](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10&oldid=214)

I would really appreciate if someone could help me solve this problem, without having to do a re-install. Thank you.

---

### Post by sikander3786 on 2011-01-28
Please see problem # 2 here.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

After you fix your current problem, don't forget to apply Permanent Fix from that page to avoid problems like these in future.

---

### Post by Rubi1200 on 2011-01-28
Hi and welcome to the forums :-)

See here for Wubi issues and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If Windows is still booting normally, then see below:

Problem #2, solution #1

Don't forget to apply the Permanent Fix back in Ubuntu, including locking the grub packages.

If you need more help, please ask.

---

