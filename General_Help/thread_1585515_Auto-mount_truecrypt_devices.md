---
title: "Auto-mount truecrypt devices"
date: 2010-09-30
forum: General Help
---

### Post by Klaue on 2010-09-30
I just encrypted a whole external HD with truecrypt 7.0a.
Is there a way to auto-mount it, so that the password dialog appears as soon as you plug it in, like the way it is with LUKS?
It's kinda unnerving to have to start truecrypt and manually mount the device all the time..

PS: I diddn't use LUKS/cryptsetup because the last time I did, I was unable to mount it on windows despite installing all the stuff it needs (decrypter, linux filesystem driver etc). I usually only need it on Ubuntu (so the auto-mount only has to work there), but a way to get to the data on other OSes would be great, thereore, truecrypt.

---

### Post by searchfgold6789 on 2010-09-30
You could try this.
Make a file that has this in it:
```
#!/bin/bash
gksu truecrypt (location of your truecrypt device)
```
Save it as mount.sh in your home folder.
Then open up a terminal and type ```
chmod +x mount.sh
```
Go to System > Preferences > Startup Applications
Follow the instructions [here]("https://help.ubuntu.com/community/AddingProgramToSessionStartup") to add the file to things that are run on startup.
Hope that helps

---

### Post by Klaue on 2010-10-01
Thank you, but what I meant is to have it mounted when I plug the external HD in, not having it mounted at startup ;)

---

