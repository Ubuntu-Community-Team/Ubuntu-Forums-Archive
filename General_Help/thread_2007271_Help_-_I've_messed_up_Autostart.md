---
title: "Help - I've messed up Autostart"
date: 2012-06-20
forum: General Help
---

### Post by bill-lancaster on 2012-06-20
I thought (stupidly) I'd try a simple script to experiment with autostart.

I made a file startup.sh containing a simple "hello world" greeting.

I then included a reference to this file in autostart.

On re-booting the system practically hangs, 5 or 10 minutes just to get the application launcher to show.  Autostart doesn't run at all.

I have another drive on the system with Ubuntu installed so I have access to drive that has the problem.

Any ideas

---

### Post by drmrgd on 2012-06-20
It sounds strange that something so simple should hang the system like this.  Would you mind providing the script you wrote using the CODE tags please?  Also, did you remember to make the script executable after you wrote it (i.e. chmod +x yourscript.sh)?  Finally, did you remember to add a shebang to the first line of the script?  The first line should look like:

```
#! /bin/bash
```

I'm not sure if either of those things would hang the Autostart routine.  But, worth a look.  The other obvious thing along those lines is to remove the call to that script from Autostart and reboot.  It sounds like the system will eventually boot to the desktop and you can access the system settings.  If not, though, you can go to the Autostart folder from the commandline and delete the symbolic link it places to the script:

```
rm ~/.kde/Autostart/yourscript.sh
```

---

### Post by bill-lancaster on 2012-06-20
here is the simple code, not sure what you mean by "code tags",

#!/bin/bash         

echo "Hello, World"

---

### Post by bill-lancaster on 2012-06-20
Also, yes the 'shebang' is there but I didn't make the file executable

---

### Post by bill-lancaster on 2012-06-20
Thank you, I removed the file - ~/.kde/Autostart/yourscript.sh and booted fine.

---

### Post by bill-lancaster on 2012-06-21
Oh dear!

Next time the system was booted got this error.

Error launching /usr/share/applications/kde4/rekonq.desktop. Either KLauncher is not running anymore, or it failed to start the application.

But after a few minutes rekonq did launch and KLauncher IS running

---

