---
title: "Installing programs on a password-free system?"
date: 2011-09-18
forum: General Help
---

### Post by tdp2010 on 2011-09-18
Greetings all, 

I have a laptop (HP Pavilion ZT3000 for what it's worth) that I did an installation of Xubuntu 10.10 on a while back.  I've been using it lately and I need to update one or two things.  However, whenever I try to install a new program, either through the command line or the Ubuntu Software Center, it will not complete the installation unless I enter an administrator password.  When I installed the system, I set it up as a single user with no administrator password, so I don't have anything to enter and can't complete the installations.  Is there a workaround for this?  Or a master admin password that I can use?  Any help would be greatly appreciated.  Thanks.

---

### Post by mörgæs on 2011-09-18
Hi, welcome to the fora.

You did choose a password while installing (else it was not possible to install). Xubuntu is not asking for a reserved administrator password, just your normal password.

---

### Post by haqking on 2011-09-18
> **tdp2010 said:**
> Greetings all, 

I have a laptop (HP Pavilion ZT3000 for what it's worth) that I did an installation of Xubuntu 10.10 on a while back.  I've been using it lately and I need to update one or two things.  However, whenever I try to install a new program, either through the command line or the Ubuntu Software Center, it will not complete the installation unless I enter an administrator password.  When I installed the system, I set it up as a single user with no administrator password, so I don't have anything to enter and can't complete the installations.  Is there a workaround for this?  Or a master admin password that I can use?  Any help would be greatly appreciated.  Thanks.

It requires your own user password.

Please read here for a thorough explanation [RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by tdp2010 on 2011-09-18
Thanks for the replies, but I'm afraid I didn't explain myself correctly.  I did not choose a username or password on installing, so I don't have any password to put in.  That is why I'm having the problem.  The system boots up without requiring a login and works fine, but anything requiring root access I can't do for some reason, even though without having had a password set it should be automatic.

---

### Post by mörgæs on 2011-09-18
Sorry to repeat myself, but there must be a user name and password available at install time. You can ask Buntu to generate a random password, but mostly people select one that is easier to remember. 

This password can be easily forgotten, for example if people select the automatic logon. 

If you open **/home**, you will see a directory with your user name. From that user name, do you get an idea of which password might be used?

---

