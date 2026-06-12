---
title: "BOINC and a menu item"
date: 2009-11-09
forum: General Help
---

### Post by RichardUK on 2009-11-09
I've installed BOINC and set it up to run Seti stuff. But I want to start it from a menu item. currently I have to start a shell, cd into it's installation folder and then run boincmgr. 

I've tried to set up a menu item but it does not run when I select it in the menu. Any ideas???

---

### Post by RichardUK on 2009-11-11
I've now got it running fro the short cut but when it does it fails to find any of the config files. It's as if the current working directory is wrong but I can't find anywhere to set that.

Any ideas???

---

### Post by XCan on 2009-11-11
I think, for some unclear reason, that you have to start boinc from its home dir with the config files which is the "obvious" /var/lib/boinc-client. You probably should thus modify your launcher to run
```

sh -c "cd '/var/lib/boinc-client'; boinc-client"

```
if boinc-client is the command you run to start the client of course.

---

### Post by RichardUK on 2009-11-24
Thanks for the help, using your command with a little tweak it now works a treat. :)

```
sh -c "cd ~/BOINC ; ./boincmgr"
```

Many thanks.

---

