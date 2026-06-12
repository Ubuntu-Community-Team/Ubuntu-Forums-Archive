---
title: "Need File location in /etc to correct &quot;TerminateServer=true&quot; for black screen bug"
date: 2011-12-13
forum: General Help
---

### Post by ozark_hillbilly on 2011-12-13
Kubuntu forum members have successfully corrected the "Black Screen" problem on logout by changing the TerminateServer = true parameter under the /etc subdirectory. Below is the info for Kubuntu. But I am running Lucid Lynx under Gnome. Where would this parameter be found under /etc for Gnome? It might correct my similar problem.   Thanks, Ed


Re: Black screen after logout
What videocard driver are you using?

In the past, some drivers (notably Intel's) made the X server crash when trying to regenerate the X session at logout. In essence, instead of shutting down X and starting it again, it tries to reuse the same process to save time and resources. If so, I think there will be a crash backtrace in /var/log/kdm.log.

You can disable this resetting behavior in /etc/kde4/kdm/kdmrc by finding the TerminateServer=true line and uncommenting it.

Code:
# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
TerminateServer=true
Use whichever text editor you're comfortable with.

To do it all from the terminal;
Code:
$ FILE=/etc/kde4/kdm/kdmrc
$ sudo cp $FILE ${FILE}.orig
$ sudo sed -ie 's/\#TerminateServer/TerminateServer/g' $FILE

---

### Post by ozark_hillbilly on 2011-12-23
Bump...

---

### Post by ozark_hillbilly on 2011-12-31
...bump

---

### Post by ozark_hillbilly on 2012-01-07
bump....any ideas please.

---

### Post by Toz on 2012-01-07
Found this link that talks about that setting: [http://wiki.cchtml.com/index.php/Troubleshooting#System_freezes_after_logout_with_GDM.2C_KDM_or_XDM.5B1.5D]("http://wiki.cchtml.com/index.php/Troubleshooting#System_freezes_after_logout_with_GDM.2C_KDM_or_XDM.5B1.5D")

Since Lucid Lynx uses gdm, I would go with the gdm option. According to that document, the file you need to edit is **/etc/gdm/gdm.conf** and the setting is:
```
AlwaysRestartServer=true
```

Make you sure you restart gdm (or just simply restart) for the setting to take effect.

---

