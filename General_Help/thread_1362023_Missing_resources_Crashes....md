---
title: "Missing resources? Crashes..."
date: 2009-12-22
forum: General Help
---

### Post by DarkSunrize on 2009-12-22
Hello I am fairly new to ubuntu... I have been using it for about 2 weeks now. Im running Ubuntu 9.04 Desktop Edition. I installed off of my live CD about 2 weeks ago and then i went ahead and did the updates so the update manager would stop bothering me and i have updated twice or so since then. But now i keep getting a pop up box that says "Missing Resources" and all of my icons disappear, and i literally cannot do a thing other than shut down. I will boot into recovery mode but i cannot find an error with anything. This Missing Resources error im getting happens randomly and sometimes instead of the error my laptop just freezes.

Somehow i got the recovery mode BIOS to tell me i need to run
 ```
apt-get autoremove
```

and then it also told me to run 
```
apt-get update
```

I ran both of these. The first one i ran in the recovery mode shell and it worked and removed what it told me it needed to. The update command i had to run in the terminal after i booted bc my recovery shell wouldnt connect to the internet...  But it still worked fine.

I did this just a couple minutes ago and my computer has run fine for the amount of time it has taken to type this but i was wondering if there was something else i should be doing or why this happened in the first place?

Thank you for your time!

---

### Post by DarkSunrize on 2009-12-23
Its been about 24 hours so i figured i could bump this... Now im having even more trouble. I havent the error i mentioned above happen but like 4 times in a row i booted up and i couldnt get my wireless to work (and i have the driver installed... i even checked) it is working okay at the moment but all last night i had horrible trouble. It kept freezing and sometimes just plain wouldnt boot.

What should i be checking and how should i fix this? Would it be more beneficial for me to completely wipe this partition of Ubuntu (i have another partition with GRUB on it bc i messed up on the one with GRUB) and install 9.10?

Any help is much appreciated... 

P.S. I know the wirless problem had nothing to do with my driver because i booted into windows and the internet was working fine. But i switched to Ubuntu from windows because i was having problems with windows working... I kept getting the BSOD so its not really an option for me to just switch back to windows.

---

### Post by john newbuntu on 2009-12-23
Start with a disk check and memory check and make sure your hardware is ok.  For disk check, go to system->admin->disk utility.  Then choose 'more information' and 'run self text'.  You have problems if you have too many bad sectors.  The memory test can be done from the GRUB menu.
You may later have to run a file system consistency check (e2fsck) to correct any other file related issues.  This needs to be done from a liveCD.

---

