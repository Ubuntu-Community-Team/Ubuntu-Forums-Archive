---
title: "kubuntu 10.10 No logoff"
date: 2010-10-17
forum: General Help
---

### Post by OldAlgis on 2010-10-17
Last week installed kubuntu 10.10. Today it fails to log off - the system simply ignores the click on shut down and continues to happily buzz along. Mobo J&W 790 GX "Extreme", Phenom CPU, 1 Mb/sec broadband connection, 4 GB RAM, works fine in ubuntu 10.04, but kubuntu 10.10 just likes staying on  :)

In desperation I have tried the command:
```

sudo init 0

```
This works! It simply shutsdown the OS, whilst clicking on the "Quit" button does not seem to affect the operation of the OS in any shape or form - consistently! The last operation before the system developed this "feature" was a half hearted attempt to use the KDE micro blog.  I did not find it useful, so just deleted the icon for it from the desktop.

After loggingof via the above command, the GUI logoff procedure has recovered - I can now log off either by the CLI or by clicking the "shutdown" icon. So the problem disappeared and the reason for the hiccup is as mysterious as its disappearance.

SOLVED! (sort off  :)  )

---

### Post by ulriks on 2011-04-17
Marvellous! Works like a charm. Thanks!

In addition I found that the profile is not saved, and that the computer hangs briefly upon login. 

To clarify the logout problem: attempting to logout, using 'Shutdown' from the Application Launcher, does not result in the confirmation button.

```

sudo shutdown -h now
or
sudo shutdown -p now

```
did not solve the problem (though the computer shuts down and turns off power)

---

