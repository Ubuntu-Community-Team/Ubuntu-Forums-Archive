---
title: "Does Kubuntu 11.10 have restricted video drivers?"
date: 2011-12-10
forum: General Help
---

### Post by bark50 on 2011-12-10
My first dive with Kubuntu after 4 years of gnome Ubuntu.  The Ubuntu installs I've done have offered the option of installing restricted video drivers right after booting into the new system.  With this new Kubuntu install, I didn't receive any alert for video driver installation.  Should I have?  I can't find an option for it in System Settings.  Thanks.

---

### Post by oldtimer7777 on 2011-12-10
> **bark50 said:**
> My first dive with Kubuntu after 4 years of gnome Ubuntu.  The Ubuntu installs I've done have offered the option of installing restricted video drivers right after booting into the new system.  With this new Kubuntu install, I didn't receive any alert for video driver installation.  Should I have?  I can't find an option for it in System Settings.  Thanks.

Did you try running jockey from the command line yet?
gksu jockey-gtk

---

### Post by ExileAmongYou on 2011-12-10
> **oldtimer7777 said:**
> Did you try running jockey from the command line yet?
gksu jockey-gtk

This command won't work properly on Kubuntu because it uses KDE, not Gnome, so the command you use to run graphical apps as root is different and there's a slightly different version of jockey installed. I think it should be 
```
kdesu jockey-kde
```

You should also be able to run the driver utility by opening the main menu and searching for "additional drivers".

---

### Post by bark50 on 2011-12-10
Thanks for both replies.  Oldtimer's reply got me looking and I found jockey-kde in muon.  I found the drivers using Exile's search.  I'm set.  I've got a lot to learn about this operating system.

---

