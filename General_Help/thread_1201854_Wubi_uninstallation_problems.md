---
title: "Wubi uninstallation problems"
date: 2009-07-01
forum: General Help
---

### Post by turgidtoupee on 2009-07-01
Okay, so I installed ubuntu gutsy a while back using wubi, and all was well. I installed it from my vista partition but on my xp partition. When I came to uninstall it from programs and features so I could install Jaunty, also by wubi, it gave me an error message saying some .dll could not be found then didn't uninstall. I also tried going into D:/ubuntu where it was installed and runnine uninstall-ubuntu.exe from there, but that gave the same error. Eventually I got frustrated and deleted the folder it was installed in, and removed the entry in the boot list using a program called easybcd. All references to there ever being an installation of ubuntu on my system are gone, yet it is still there when I start up the computer in the same place it always was, only it gives me an error if I try to start into it. Does anyone have any idea how I could get rid of it?

---

### Post by ajgreeny on 2009-07-01
I don't know for sure, but I think you may need tyo remove the reference to ubuntu from the boot.ini file in the root of windows, which windows I will have to leave you to find out, and I suggest you backup that file first, just in case, you can then restore it if everything goes wrong, by using the ubuntu live CD.

---

