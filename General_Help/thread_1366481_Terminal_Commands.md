---
title: "Terminal Commands"
date: 2009-12-28
forum: General Help
---

### Post by ColdLunch on 2009-12-28
How can I create custom commands like aliases?

For example, if I type "home" i want it to do "cd ~"

Thanks.

---

### Post by Fire_Chief on 2009-12-28
Have a look at this page [http://www.mediacollege.com/linux/command/alias.html]("http://www.mediacollege.com/linux/command/alias.html")

Then see this to make them permanent.
> Making Aliases Permanent

The main disadvantage with the alias command is that any alias set up with it remains in effect only during the current login session (i.e., until the user logs out or the computer is shut down). Although this might not be much of a problem for systems which are rebooted (i.e., restarted) only infrequently (such as corporate database servers), it can be a nuisance for systems that are frequently rebooted (e.g., home computers).
Fortunately, however, any alias can be made more enduring (i.e., until it is explicitly removed) by writing it to the appropriate configuration file with a text editor. The name and location of such file can vary according to the system. In the case of Red Hat Linux, an alias for any user can be added to the .bashrc file in that user's home directory. Because this file is read at login, the change will not take effect until the user has logged in again.
Aliases for the root user can be made permanent by entering them in the .bashrc file in the root's home directory, i.e., in /root/.bashrc. System-wide aliases can be put in the /etc/bashrc file. The system needs to be restarted before system-wide aliases can take effect.

Cheers!

---

### Post by Shrek01 on 2009-12-28
You need to edit your .bashrc 
```
gedit .bashrc
```
and add the line:  
```
alias home='cd ~'
```
Open a new terminal for the new changes to take effect.

---

### Post by blur xc on 2009-12-28
> **ColdLunch said:**
> How can I create custom commands like aliases?

For example, if I type "home" i want it to do "cd ~"

Thanks.
[http://crunchbanglinux.org/forums/topic/1093/post-your-bashrc/](http://crunchbanglinux.org/forums/topic/1093/post-your-bashrc/)

FYI- typing "cd" and hitting enter already is an alias in Ubuntu (dunno how many other distros) to take you back to your home directory.

~ isn't really in alias, but kind of like a shorthand environment variable for /home/username directory.  If I wanted to copy my music I could write cp ~/Music/*, etc...

BM

---

