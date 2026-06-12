---
title: "Can't install or uninstall anything"
date: 2010-07-23
forum: General Help
---

### Post by rtz2rbbl on 2010-07-23
Ok, so I tried to run the .deb package to install the Facebook chat plugin for Pidgin, and something got all messed up with that, and now nothing will install or uninstall. Synaptics won't run, Update Manager tells me to try a termianl command that doesn't work, and the Software center doesn't work either. I've attached screenshots of the problems. I've tried to download and reinstall the .deb file, and it still doesn't work.

I wanted to upload one more picture, but it only allows five. The last picture was of the terminal window. Here's what it said.

"Sudo apt-get install f
reading package lists... done
building dependency tree
reading state information... done
E: The package pidgin-facebookchat needs to be reinstalled, but I can't find an archive for it"

Sooo...any help would just be spectacular

---

### Post by linux18 on 2010-07-23
Very strange error, I'm not experienced in this type of error but try ```
 sudo apt-get autoclean  && sudo apt-get clean && sudo apt get autoremove && sudo apt-get update && sudo apt-get purge pidgin-facebookchat || echo "POST THE PREVIOUS LINES OF CODE!!!!"   
``` then post all the output from the terminal.

---

### Post by rtz2rbbl on 2010-07-24
Sorry bout taking so long to reply, I worked 12 hours today, so it's been a loooong day. But here are the screen shots.

---

### Post by linux18 on 2010-07-25
> **rtz2rbbl said:**
> Sorry bout taking so long to reply, I worked 12 hours today, so it's been a loooong day. But here are the screen shots.
From the screenshots it appears that no errors occured, try to install something and post back if it still fails.

---

### Post by rtz2rbbl on 2010-07-25
I can't install other things. It always tells me that there's another installer running and that only one can tun at a time.

---

### Post by rtz2rbbl on 2010-07-25
Ok, well out of nowhere, update manager pops up, asks me if I want to remove the package because it's damaged. I click yes, Update Manager does it's thing and life is all good again. I don't know what happened to make that work, because I've tried to tun Update Manager a few times with no success. But I guess as long as it works then I'm happy.

---

