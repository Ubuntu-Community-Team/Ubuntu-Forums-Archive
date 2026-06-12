---
title: "Compiz crashes, taking everything with it"
date: 2012-09-20
forum: General Help
---

### Post by JPR65 on 2012-09-20
I'm using Ubuntu 12.04, and I am running compiz and cairodock (I have nvidia 9800GT graphics card). Occasionally (between once and twice a day), compiz crashes. There is no error message, but all of my windows move to one workspace, then unity, cairo, and compiz all disappear, leaving me powerless to do anything. My mouse works, but I can't access anything, because all of the option screens are gone; keyboard shortcuts don't work other. I mean, the programs are still there, but there is not top on them, so I can't move them (alt-tab doesn't work, so I can only access the one on top). The only option to fix this is to reboot via the physical power button.  Can anyone help me fix this? Thanks!

---

### Post by daslinkard on 2012-09-20
You may need to remove the proprietary nvidia driver and should be able to use 12.04 with the standard "Ubuntu" log-in option.

System Settings --> Additional Drivers --> select driver to remove --> Remove

Hope this helps!

---

### Post by JPR65 on 2012-09-20
Ok, I took your advice...sorta. Before you posted I read some articles about bugs similar to mine. After you posted, I switched out my drivers; now I'm using the version-currentupdates nvidia driver. I haven't had any trouble with everything crashing, but now it seems compiz randomly(as in every 20-30 minutes)...how to describe this...refreshes, and all the windows move to one workspace. As you can imagine, this is quite annoying. Will removing my nvidia driver help this issue?

---

### Post by daslinkard on 2012-09-20
I do believe that removing the nvidia drivers will fix the issue.

---

### Post by JPR65 on 2012-09-20
Alright then, here goes...I'll give it a try, and see what happens :)

---

### Post by daslinkard on 2012-09-20
Let me know how it goes!

---

### Post by JPR65 on 2012-09-20
Ok, removed the driver and restarted. Unfortunately, I opened: firefox, thunderbird, pithos, and a libreoffice calc doc. I then positioned them in different workspaces via expo. Then compiz "refreshed", and all the tabs moved to one workspace. Anyway, although this bug is rather annoying, I can definitely live with it and be superhappy (linux still makes my day). It was just the manual reboots that were driving me nuts.

---

