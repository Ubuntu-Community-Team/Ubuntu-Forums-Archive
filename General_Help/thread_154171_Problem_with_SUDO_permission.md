---
title: "Problem with SUDO permission"
date: 2006-04-02
forum: General Help
---

### Post by Dropknee on 2006-04-02
I recently install Ubuntu in my external HDD, in expert mode. When I try to update with the update manager and write the root password, nothing happen. This happen with all root permission, simply  the program wont start. 

Need help with this. I install few month ago Ubuntu in the same way and not have this problem.


pls help

---

### Post by aysiu on 2006-04-02
I know you say you've installed this way before with no problems, but I've generally found non-experts who install in expert mode end up with sudo/root problems.

Stick with a regular install until you consider yourself expert enough to not need help with expert mode.

---

### Post by llamakc on 2006-04-02
SUDO doesn't want the root password, it wants the password of your user that YOU created during the installation. 

Make sure your USERNAME is in the file /etc/sudoers and try using that USER's password instead of root's.

---

### Post by Dropknee on 2006-04-02
[QUOTE=aysiu]I know you say you've installed this way before with no problems, but I've generally found non-experts who install in expert mode end up with sudo/root problems.

Stick with a regular install until you consider yourself expert enough to not need help with expert mode.[/QUOTE]


Im not a geek or something like that , but is you pay more attention, you notice one thing, Ubuntu is in a EXTERNAL HDD and this need to be in expert install because you need to modified some setting so ubuntu can boot, I just follow this [http://www.ubuntuforums.org/showthread.php?t=80811&highlight=external+hdd]("http://www.ubuntuforums.org/showthread.php?t=80811&highlight=external+hdd")

Like I write before I do this install before without any problem few month ago, no sudo problem, no nothing. Really dont undestand why this happen.

---

### Post by Dropknee on 2006-04-03
bump.

Any help!!?? pls

---

### Post by aysiu on 2006-04-03
[QUOTE=Dropknee]Im not a geek or something like that , but is you pay more attention, you notice one thing, Ubuntu is in a EXTERNAL HDD and this need to be in expert install because you need to modified some setting so ubuntu can boot[/QUOTE] According to [the first post in that thread](http://www.ubuntuforums.org/showthread.php?t=80811), it's not necessary to use expert mode:> ( STEP 1 ) **Instead of using "expert" mode** to install, I just hit enter to start the install process (using the install CD ... NOT the live CD).

So it's not a matter of "pay[ing] attention."

---

### Post by nanotube on 2006-04-03
regardless of who is paying attention where... :)
check your /etc/group file, to see if your username is in the admin group. if not, reboot into recovery mode, and edit that file to include yourself. that might solve your problem.
or even better, read the end of this thread for detailed instructions:
[http://ubuntuforums.org/showthread.php?t=146859&page=2](http://ubuntuforums.org/showthread.php?t=146859&page=2)

---

