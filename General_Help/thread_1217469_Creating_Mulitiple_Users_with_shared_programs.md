---
title: "Creating Mulitiple Users with shared programs"
date: 2009-07-19
forum: General Help
---

### Post by SirWeazel on 2009-07-19
Hello, I've switched to Ubuntu 9.04 32 Bit, and i think i have it close to completely set up and configured now.  So i want to create user account for one other person to use my computer.  I created the 2nd account, but it looks like none of the programs i installed carried over to this 2nd account.  I would like to just duplicate everything (installed printers, programs, and other configurations to a 2nd account with there own own profile)

Windows example: i could be logged in as administrator and install my programs often being asked to install to "all users" or i could edit the explorer file and copy over shortcuts for the programs.

I really don't want to have to reinstall printer drivers and options programs, again.  It took me awhile to get it set up the way it is now.

Thank you in advance for your help, I've tossed my Vista Ultimate in the desk drawer and i'm hoping to never see it again.

---

### Post by michy99 on 2009-07-19
What programs have you installed which are not available to the second user, and how did you install them? Anything installed through the repositories should be available to all users.

---

### Post by SirWeazel on 2009-07-19
Wow, thank you for the quick response.  And i feel kind of stupid, actually the other programs (Opera 10 beta and latest HP printer drivers both downloaded from eaches own website) are installed, i just didn't see them or needed to reboot or something but for the most part they are working and are available to other users except for one program i can't see in the second account. I'll explain:

I installed the latest version of Wine (1.1.26) from their website using the terminal and following the directions. This installed correctly and can be seen in both user accounts.  I then installed Office 2007 using Wine which appears under Applications/Wine/programs/ and office is only available under my account and not the other users. Do i need to install it again for each user, or is there away to carry over?

Before i get harrased about trying to use office with linux, i've only installed it for basically a couple reasons: so i can access some already created publisher files (which doesn't work anyways so a little frustrating), so i can slowly convert my girl over to openoffice but not hear her complaining that office isn't available, and sometimes original office files do not work completley or correctly with openoffice. Trying to completely get away from office, but it is everywhere and i do need to be familar with it and have access to it.  -- i will be setting up a virtual box for some windows only software that i need, but that will be awhile... another project another day.

Thank you for any help provided and thank you michy99 for your quick reply.

---

### Post by michy99 on 2009-07-19
Unfortunately, Windows programs installed with wine are installed in the user's home directory. I believe there is a way to share installations using symlinks, but that is not something I have ever done myself. A search of the forums for 'wine shared programs' or something like that might turn up something.

---

### Post by SirWeazel on 2009-07-20
Reply, thank you for your help. I've basically got everything set up now. I've had to do a lot of reading and learning, but i think i'm starting to get it down.  I've got everything working for both users except one or two things, but those questions should probably be started in a new thread. Given up on sharing Wine apps for now, and will probably just install things twice if its really needed, but i'm gonna stay away from Wine all together if i can, i've probably changed so many things to try and get publisher to work to no avail. Actully gonna have to hurry on virtubox setup with xp sooner than planned, gonna need some good scanning software for multiple scans and xsane isn't cutting it. Don't know if virtubox will be diffucult to share between users do u?

Also messed up home directeries trying to share files between users (fixed for now)... Starting to get permissions thing straitend out in my head. Now if i can only figure out how to get the second hard drive for storage to allow me access.....

Anyways, thank you for your help.  --- Also, when i switch users (fast user switch) sometimes video is messed up and i have to log out and back in to fix... where should i post this problem?

---

