---
title: "Backup of BasKet notes"
date: 2011-12-01
forum: General Help
---

### Post by LorteMidget on 2011-12-01
I am thinking of reinstalling Ubuntu, because of some issues with updates that I cannot install. But I have a lot of important notes from BasKet Notepad, and I don't know how to save the files to an external hard drive. Is there a way to do it, or do I have to copy every single note to a Libre Office document, and then copy them back when I have reinstalled Ubuntu?

Hope you can help! :)

---

### Post by Habitual on 2011-12-01
To copy BasketNotes initially:
Terminal >
```
cp -pr ~/.kde/share/apps/basket [COLOR="Red"]**/media/External_Hard_Drive/**[/COLOR]Baskets_backup
```

To restore BasketNotes later:
Terminal > 
```
cp -pr [COLOR="Red"]**/media/External_Hard_Drive/Baskets_backup**[/COLOR] ~/.kde/share/apps/basket
```

Generally speaking you could then copy ~/Baskets_backup to a USB or other archive media and after you have (re)installed whatever, you copy it back to it's original location overwriting anything it may prompt for.

Fire up nautilus and press Control+H to see your hidden directories/profile.rc's etc... and use nautilus to copy to the external drive.

Unison works well too for this situation. and it's in the REPOs.
I use it to backup my entire /home/jj directories/*.
After the initial backup (takes awhile) then updates to the 3T USB drive are only a click away.

HTH.

NOTE: 
[COLOR="Red"]**/media/External_Hard_Drive/**[/COLOR]Baskets_backup may be /dev/sd*X* on your system.
the 
```
mount
``` command should show you this detail.

Change to suit your environment.
Subscribed with interest...

---

