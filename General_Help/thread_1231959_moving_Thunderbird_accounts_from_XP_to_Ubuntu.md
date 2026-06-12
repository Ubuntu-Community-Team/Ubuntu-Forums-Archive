---
title: "moving Thunderbird accounts from XP to Ubuntu"
date: 2009-08-05
forum: General Help
---

### Post by charonred on 2009-08-05
I'm migrating a friend from XP to Ubuntu 9.04; but I need to get all the emails from the XP install into Ubuntu.

I installed Thunderbird in XP and imported all the mail, settings and accounts from Outlook; now how do I get all that into Thunderbird in Ubuntu?

XP is on a separate drive to Ubuntu, but in the same PC; so it's easy to copy files across - just don't know quite how to import everything.

---

### Post by dmizer on 2009-08-05
Just copy the profile folder from Windows to Ubuntu.

[http://kb.mozillazine.org/Profile_folder_-_Thunderbird](http://kb.mozillazine.org/Profile_folder_-_Thunderbird)

That's it.

Edit:
In fact if you're planning to dual boot, you can point the Ubuntu profile to the folder on your Windows hard drive, and you won't have to import anything at all.

---

### Post by stinger30au on 2009-08-05
> **dmizer said:**
> 
Edit:
In fact if you're planning to dual boot, you can point the Ubuntu profile to the folder on your Windows hard drive, and you won't have to import anything at all.


just dont forget you have pointed it there in the first place when you decide to ditch xp and go full ubuntu and make sure you back up the directory

speaking from experience here ;-)

---

### Post by charonred on 2009-08-05
um .. how do I get it to use the ex XP profile - do I need to setup a account first in TBird ?

it won't be dual booting once TBird is functional; XP will get nuked and an 'XP appliance' will be imported to Virtualbox to take care of anything that 'needs' Windows, and only if it won't work in Wine (the XP drive will simply become a data storage drive)

---

### Post by charonred on 2009-08-05
ah ha, got it working

1st I created one user email account, then edited the 'profile.ini' file and inserted the name of old profile - bingo, all emails folders and addresses are there - only thing to set up are the other user email accounts (but that's easy enough)

thanks heaps people :D

---

