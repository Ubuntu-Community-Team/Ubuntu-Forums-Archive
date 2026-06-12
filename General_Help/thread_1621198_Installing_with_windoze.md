---
title: "Installing with windoze"
date: 2010-11-14
forum: General Help
---

### Post by monsard on 2010-11-14
[SIZE=2]I have win XP and just got the bug to try Linux and ubuntu turned up because all the old crusts were complaining about it for taking too much away from the enthusiast. Well I have spent all my computer life in the windows shell so I thought it would be just the thing for me to start with.
The Problem:[/SIZE] [SIZE=2]I started with wubi after reading about it[/SIZE] [SIZE=2]so I downloaded ubuntu 10.10 and wubi and put them both in the same folder and then created a shortcut to wubi on my desktop.  I executed wubi and it immediately started downloading ubuntu 10.04 so I let it go.  At the first reboot my win loader showed up and I selected ubuntu which loaded and I got some screen where it was doing a lot of configuring and stuff and then the screen went black and some text appeared, but for a very short time.  It was tiny so I haven't been able to read it.  After that I got a cursor that just hung.  I rebooted and selected ubuntu and the cursor just hung again.  A few more times with the same result.  I ran wubi again and it removed the installation and reinstalled it.  The exact same thing happened.  I took the 10.10 iso and[/SIZE] [SIZE=2]burned it to a dvd,  I thought it might have its own installer but when I looked in it I saw that wubi was there on the dvd.  So I ran it and installed again and the result was identical.  I am flummoxed that I cannot install ubuntu on my machine.  It has its own 33 gb partition, I have 5 gb of ram so the installation dose not hang up.  The partition is NTFS as I have no other choice, if that makes a difference, I could find no information about formatting and there is certainly no formatting with the install app.  Any help will certainly be appreciated.  I am getting damn tired of microsoft.  
:confused:
[/SIZE]

---

### Post by wilee-nilee on 2010-11-14
Your thread title is going to get you less responses, the term is windows even on this forum. 

If you have extra space just do a full install, reloading the bootloader to the MBR for XP is one command fixmbr if you just decide Linux isn't your cup oh tea.

If you decide to dual boot make sure you resize the XP, defragg and clean beforehand reboot it make sure it works and then install Ubuntu in a open space it will be more stable and easier to fix in this configuration.

You can also post the bootscript in my signature or run it for yourself it is a handy tool. Post it in code tags if you decide to share it for help.

I assume to as well that since your a windows shell user that you know that XP has a pretty good full backup set up built in. Doesn't come installed on the home version, but it's actually on a XP home install disc.

---

