---
title: "Gnome Updates Causing Problems"
date: 2006-06-16
forum: General Help
---

### Post by driverkt on 2006-06-16
The latest gnome updates (I'm currently up to date with all ubuntu dapper updates at the time of posting) seem to be causing some weirdness in my environment.  

1) The Applications, Places, and System menus no longer show their icons.
2) If I try to start the theme manager, I get an error message saying: "The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly."  I haven't edited my gconf.
3) It switched back to spatial instead of ubuntu-spatial.

Any ideas on what to do to restore prior functionality? 

Thanks.

---

### Post by driverkt on 2006-06-16
[QUOTE=driverkt]The latest gnome updates (I'm currently up to date with all ubuntu dapper updates at the time of posting) seem to be causing some weirdness in my environment.  

1) The Applications, Places, and System menus no longer show their icons.
2) If I try to start the theme manager, I get an error message saying: "The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly."  I haven't edited my gconf.
3) It switched back to spatial instead of ubuntu-spatial.

Any ideas on what to do to restore prior functionality? 

Thanks.[/QUOTE]

BTW, I'm pretty sure the analogous update on FC5 called the same problem.  So, maybe it's a gnome issue?  Anyone else experiencing this?

---

### Post by homersbrain on 2006-06-17
I have exactly these problems, and in addition I have the mouse motion fised on slowest! Also when you minimise an app, it disappears, rather then goin to a taskbar. 
I don't know what to do. The trouble is that a reinstall would probably have the same effect once the updates are installed. If it isn't fixed soon looks like windows might have to go back on the pc. :(

---

### Post by homersbrain on 2006-06-17
Oh BTW, also I cannot get into synaptic or update manager. What is the terminal command for updating (if it gets fixed)?

---

### Post by shanepardue on 2006-06-18
i have something similar and i can't even access my file system through the gui, only command line.

i don't have the slow mouse and stuff, but everything the first post mentions, is what i'm experiencing!!

i hope there's a fix!

---

### Post by homersbrain on 2006-06-18
Describe your similar problems to the following bug report:

[https://launchpad.net/bugs/50133](https://launchpad.net/bugs/50133)

---

### Post by Perfect Storm on 2006-06-18
[QUOTE=homersbrain]Oh BTW, also I cannot get into synaptic or update manager. What is the terminal command for updating (if it gets fixed)?[/QUOTE]

```

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by homersbrain on 2006-06-18
Thanks AI

---

### Post by homersbrain on 2006-06-19
Bug reports now merged to here:

[https://launchpad.net/bugs/50150](https://launchpad.net/bugs/50150)

Please describe your problems there.

---

### Post by driverkt on 2006-06-20
*bump*

---

### Post by dcstar on 2006-06-21
[QUOTE=homersbrain]Bug reports now merged to here:

[https://launchpad.net/bugs/50150](https://launchpad.net/bugs/50150)

Please describe your problems there.[/QUOTE]
Biggest issue I have with the (fixed) Gnome updates is that the Debug compiler option seems to have been left on in the released version.

Just have a look at the Syslog/Messages log files on start up...........

---

### Post by driverkt on 2006-06-21
This post fixes the issue for me:  [http://ubuntuforums.org/showpost.php?p=1164346&postcount=11](http://ubuntuforums.org/showpost.php?p=1164346&postcount=11)

---

### Post by DREMA on 2006-06-21
I had the same problem, and here is the solution

[http://ubuntuforums.org/showpost.php?p=1164346&postcount=11]("http://ubuntuforums.org/showpost.php?p=1164346&postcount=11")

Hope this helps! :D

---

