---
title: "What version of Ubuntu?"
date: 2010-04-05
forum: General Help
---

### Post by aunderwood32 on 2010-04-05
Hello,
I have had my desktop in storage for about a year and was wondering how you know what version of Ubuntu you are running? I know that probably sounds like a really dumb question, but I have no idea and have been looking around on my desktop, but can't figure it out. I probably need to update it, but didn't know if you have to uninstall and then reinstall the newest. I am very confused.
Thanks!

---

### Post by whoop on 2010-04-05
```

cat /etc/issue

```

---

### Post by Naitsirhc Hsem on 2010-04-05
click on System>Administration>System Monitor and select the system tab.

You can upgrade using the update manager.  that will bring you up to the latest version of ubuntu.  it will show up on the top of the window like "Click here to upgrade to ubuntu 9.10"

---

### Post by Iowan on 2010-04-05
> **aunderwood32 said:**
> ...how you know what version of Ubuntu you are running?  Click System>About Ubuntu. If you update, you'll need to go release-to-release (ie. Intrepid>Jaunty>Karmic). LTS versions (Hardy was the last) can upgrade to the next (Lucid... when it releases).

---

### Post by gmargo on 2010-04-05
At the command line:
```

lsb_release -a

```

---

### Post by Sef on 2010-04-06
> I have had my desktop in storage for about a year and was wondering how  you know what version of Ubuntu you are running? I know that probably  sounds like a really dumb question, but I have no idea and have been  looking around on my desktop, but can't figure it out. I probably need  to update it, but didn't know if you have to uninstall and then  reinstall the newest. I am very confused.

1) The only dumb question is the one not asked.  You will not learn if you do not ask.

2) Depending on how old your version is, you may be able to update, but that is just to the next version.   I prefer doing a clean install, i.e., installing a new system over the old one.  I would wait till Lucid is stable (29 April) and install that.  Since it is  Long Term Release (LTS), the desktop will be updated for 3 years instead of 18 months.

---

