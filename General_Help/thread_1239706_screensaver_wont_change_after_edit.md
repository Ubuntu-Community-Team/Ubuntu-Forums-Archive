---
title: "screensaver wont change after edit"
date: 2009-08-13
forum: General Help
---

### Post by Baneblade on 2009-08-13
I followed a guide on the forums to change my screensaver into a clock by editing gltext (which worked great)

Only trouble is, now that im bored of it (i change screensavers a lot) i cant seem to set it to anything else. Even blanking the screen no longer works?

It seems to me that editing 
```
/usr/share/applications/screensavers/gltext.desktop
```

may have caused this, but i dont know how to set it back now :p

---

### Post by BslBryan on 2009-08-13
I think there's a pretty good chance that if you revert gltext.desktop to its original contents, you should be good to go.  

I'm at my girlfriend's house ATM, so I'm away from my Ubuntu machine, but if you can wait until tonight, I'll provide you mine. :)

---

### Post by Baneblade on 2009-08-13
Thanks for the quick reply.

Iv tried reverting it back to the original by deleting the added text and had no joy.
When i tried to replace the file with the backup i made it refused as it was "being used by another process" or something to that effect. Even using nautilus with root permissions didnt help.
I think iv borked this nicely.. :p

---

### Post by BslBryan on 2009-08-13
Try using those same commands from a root terminal.  You can do that by selecting "recovery mode" from the GRUB menu, then resume normal boot and see if that helps.  

Or, you can open up the backup file in gedit and copy the contents, then open up the actual gltext.desktop and paste, save, and reboot.

Those should do, too.  I didn't know you'd backed up the file. :)

---

### Post by Baneblade on 2009-08-13
Problem solved.
In my quest for epic uptime, i may have overlooked the obvious "rebooting fixes everything" solution. Simple reboot fixed it.
Big thanks to you BslBryan for all the help! :)

For anyone else with this problem: 

I replaced the custom edit file with my backup 

Note - you will have to do this manually (ie: delete the one you customised and replace with the backup) as nautilus running from "gksu" will simply rename your file with a "~" on the end. Otherwise, use the terminal.

Then simply reboot and you should be good to go ;)

---

### Post by BslBryan on 2009-08-14
Haha, happens ALL of the time. :-)

I'm glad it's working now.

---

