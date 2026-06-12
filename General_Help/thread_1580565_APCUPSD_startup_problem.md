---
title: "APCUPSD startup problem"
date: 2010-09-23
forum: General Help
---

### Post by scyntax on 2010-09-23
Hello All,

In order for the above to work, I have to first open Terminal and sudo /sbin/apcupsd. Otherwise, simply clicking on the program does not cause the program to run. Also, the tray icon functionality seems backward. Clicking on the radio button does not cause a notification area to become visible. Taking the checkmark off, also does not cause a visible icon either. However, after taking the checkmark off, I can randomly click in a small area by the date and a small box opens up saying "Jump to" and "quit". Also, there are two tray icon radio buttons, one is below the "Add/Remove" buttons and one alongside the "Enabled" radio button. Why are there two and what is the difference between them? 

Thank you.

---

### Post by tgalati4 on 2010-09-23
apcupsd is a daemon that is run in the background to watch for power outage events.  Normally you run it from a control script:

```
sudo /etc/init.d/apcupsd start
```

Once it is started in this fashion, it will automatically start at every boot until you issue the stop command.

You should find two files in /var/log/:  apcupsd.status and apcupsd.events

I'm running an old version of apcupsd.  I'm not aware of tray icon functionality.

---

