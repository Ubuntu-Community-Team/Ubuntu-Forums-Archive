---
title: "How do I remove Grub?"
date: 2006-04-25
forum: General Help
---

### Post by s|k on 2006-04-25
I tried to upgrade to Dapper, but everything broke, so after about 4 months of using Ubuntu and having sworn not to go back to Windows, I'm going back to Windows. Now I would just like to remove grub so it just boots into Windows directly. Anyone know?

---

### Post by LucasLinard on 2006-04-25
I know!
i've just done that with another machine today
Use your windows install cd to enter the recovery mode
then type fixmbr or mbrfix, mbr-fix fix-mbr (I REALLY don't remember :) )
Hope it helps...
EDIT: thanks to Doytch: fixmbr is the command.

---

### Post by Doytch on 2006-04-25
FIXMBR

One thing to remember though, is that you NEED an admin password for WXP.  If you have a blank password, that won't work, because of some problem with how Windows treats blank passwords.  If you try to enter your blank password in the recovery console, it'll say it's wrong.  Now, there's a way to fix this, involving floppies and a bunch of other crap, but I think the following way is easier:  
You'll have to go into Administrative Tools>>Computer Management, open the Local Users and Groups section, select Users, and change the Administrator account password to something. 

Once you're done that, just reboot, and do what LucasLinard said(FIXMBR).

---

### Post by LucasLinard on 2006-04-25
Thanks Doytch for correcting me!
I didn't really remember the command. THanks a lot.
I had a machine using both windows XP and linux and my father now is the only one who uses that machine, so I removed Ubunt from it today, earlier.
THanks again

---

### Post by enopepsoo on 2006-04-25
I use Ubuntu on an old and busted 750 MHz system at home.  At work I use XP on a 3.2GHz system with 1.5GB ram.
Even given how fast the work computer is (before starting work there last week, I had no idea computers are that fast now) I still miss the functionality of my home system.
I am not trying to start a flame war, but I think p|k may miss Ubuntu and give it another go.  With that being said, I know Ubuntu is not for everyone.

---

### Post by tsrjzq on 2006-04-25
just insert your windows boot CD, and fix /mbr ,that's ok

---

### Post by s|k on 2006-04-26
[QUOTE=enopepsoo]I use Ubuntu on an old and busted 750 MHz system at home.  At work I use XP on a 3.2GHz system with 1.5GB ram.
Even given how fast the work computer is (before starting work there last week, I had no idea computers are that fast now) I still miss the functionality of my home system.
I am not trying to start a flame war, but I think p|k may miss Ubuntu and give it another go.  With that being said, I know Ubuntu is not for everyone.[/QUOTE]
Actually, I gave it another try already and managed to fix the problem in about 5 minutes. LOL

Thanks for the help anyways! :)

Dapper is nice!

---

