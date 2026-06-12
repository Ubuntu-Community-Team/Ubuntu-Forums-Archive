---
title: "Secure computer?"
date: 2009-08-28
forum: General Help
---

### Post by aceplayer97 on 2009-08-28
How can I make sure that no one besides me is able to access my computer or its files? Is there any program that I could use or something?

---

### Post by mike555 on 2009-08-28
You could set a bios password (but don't forget it)

---

### Post by aceplayer97 on 2009-08-28
Do you think, if you have the time to, help me setup a BIOS password?:guitar:

---

### Post by bchurchill on 2009-08-28
Rule #1: If someone has physical access to your computer they can obtain root access regardless of what you do.  

BIOS passwords do *a lot* to slow this down, but it's not a fail-proof solution.  If you want to do this, reboot your computer and find the BIOS setup menu (not the boot menu).  There will be some F- key to press to get to it.  Then setup a good password.

There are many, many security related articles that adress this question.  Ubuntu is a rather secure operating system from the get-go, but there are things you can do to help.  Try the following:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

There is an article with lots or resources and links.

---

### Post by credobyte on 2009-08-28
LVM ( alternate cd ).

---

### Post by XCan on 2009-08-29
As credobyte stated, encrypt your partitions.

---

### Post by DFlame on 2009-08-29
> **bchurchill said:**
> BIOS passwords do *a lot* to slow this down, but it's not a fail-proof solution.

BIOS passwords are practically useless. They can be bypassed with a screwdriver and a jumper. You sometimes don't even need the jumper (just short it with the screwdriver :-$) And why pass the BIOS when you can simply remove the hard disk?

As said, encryption is the way to go. A very simplistic way of doing this is to use Truecrypt to make an encrypted file container, where you would place anything you'd rather nobody but yourself have access to. They offer a linux version of the program [here](http://www.truecrypt.org/downloads). There is also documentation on that site.

Encryption ensures that even if the computer or hard drive is stolen, or accessed without your knowledge - only you retain access to what has been encrypted.

---

### Post by aceplayer97 on 2009-08-30
Thanks for all the help!:guitar:

---

### Post by grashdur on 2009-08-30
Hi Aceplayer: I can recommend two things: 

1. An encrypted Private folder that opens up whenever you log in. (There are instructions for setting this up in the forums but I don't have the link handy.) This is a great option for a laptop that you want to bring with you.

2. Install Truecrypt (available at truecrypt.org). It will let you create encrypted vaults / folders, which you can then select and open with Truecrypt whenever you want. This is a great option if you want to be able to copy files to back them up and you don't want your backup copies to be accessible to anyone who might take your backups. There's also a Windows version of Truecrypt so you can open your encrypted files in Windows too.

As far as hackers and all that, Linux is less vulnerable to hacking and isn't susceptible to any of the viruses that are out there. But no OS can guarantee absolute total privacy from a determined hacker.

---

