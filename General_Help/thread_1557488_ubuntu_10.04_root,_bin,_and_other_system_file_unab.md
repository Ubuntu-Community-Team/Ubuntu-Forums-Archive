---
title: "ubuntu 10.04 root, bin, and other system file unable to access under admin."
date: 2010-08-20
forum: General Help
---

### Post by mkn1620 on 2010-08-20
Hello, I'm very new to ubuntu10.04. I'm running window xp and unbuntu 10.04. I ran into a problem where I reinstalled unbuntu by erasing old one under CD boot. During installation, it asked me to place files and i placed it in /. Now when I log in as single user (only user or other at login screen) and try to change any system files, it said I don't have permission. I can't change anything or access root file. I try chmod function and it said i don't have permission as well. Please help, thank you.

---

### Post by quixote on 2010-08-21
The simple answer, if you haven't done much customizing, is to just reinstall.  Something obviously went wrong during installation.

If you really want to try to fix, it sounds like you may need to use the command line and a program called [visudo]("https://help.ubuntu.com/community/Sudoers") do get the permissions back.  I can go through that in simpler terms if you'd like, but first let's make sure I haven't misunderstood.

When you say "login as single user" do you mean login to the recovery console as root?

When you say "only user or other at login screen" what do you mean?  How many users have you set up on your system?  Are you trying to use sudo under the account of the first user set up during install?  Or a second user, perhaps?

---

### Post by mkn1620 on 2010-08-23
Yes, login to the recovery console as root.

At ubuntu 10.04 login screen, it has 2 options, admin and other(under x window? I was reading books and guessed it's x window). Under admin, it prompts with password. I never create any user other than my own. Therefore, I never create 'other' as a user. I thought it's created by default.

---

### Post by quixote on 2010-08-25
Is that literally the name of the non-root user: "other"?  It sounds like maybe you didn't set up an actual user during installation.  If you didn't give "other" a password when you installed, that's why nothing is working.

(You may know all this already, but just in case.... Ubuntu is set up so that there is no graphical login as root.  In the recovery, command-line console there is, but not once the graphical interface starts.  When you set up the first user and the password during install, that one is automatically given admin privileges. If there's no password, the system won't give those privileges.  If there is a password, when you login as that primary user, you can use "sudo" to execute root commands.)

If you have no user set up, then do this:

boot into recovery console, where you're root and see the # prompt```
adduser -aG admin *[COLOR="Blue"]the-user-name-you-want[/COLOR]* 
```the system will prompt for a password.  Type in the password you want to use. I'm not positive you need the -a switch.  That's what you use when you modify an existing user, but I think you also want it here.  -G means "add to this group also". It's important to add the primary user to the admin group because that's what'll allow sudo to work.

Make sure that your sudoers file has this line in it (usually toward the bottom):> # Members of the admin group may gain root privileges
**%admin ALL=(ALL) ALL**The way to check is to type```
visudo
```at the command prompt.  Use the down arrow key to move down the file. If the bolded line is not there, add it. Ctrl-x to start the process of saving the file, and then hit return to save it under the name it provides.  Once you're back at the command prompt, type reboot to see whether you can indeed log in as the new primary user and use sudo commands.  Hopefully, yes!

---

### Post by mkn1620 on 2010-08-26
Alright, I created password for admin already. I have to create one for other?

---

### Post by quixote on 2010-08-26
Yes.  From the operating system's point of view, you've done this a bit backwards.  You're not supposed to establish a password for root.  You just have a password for the primary user, who can then become root by using sudo.  I'm not sure whether having a separate root password will get you in trouble or not.  I'd suggest setting up the primary user, as outlined before, with password, and see how the system works when you're logged in as that user.  If you go to System > Administration > Synaptic will it let you run synaptic, for instance?  If you open a terminal and run "sudo nano", it should prompt for a password, and when you enter your primary user password it should open the command line text editor. (Ctrl-x will close it, or ctrl-x and hitting the enter key.)  If that works, then it doesn't matter that root has a separate password.

---

