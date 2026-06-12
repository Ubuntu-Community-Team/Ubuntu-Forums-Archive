---
title: "Cannot get Wine to work"
date: 2011-03-14
forum: General Help
---

### Post by ojahr on 2011-03-14
Hi,
I cannot get Wine to work on my ASUS 8400 with 312 meg ram. Picasa will not install and also not after I installed wine 1.3. Tried then Picasa 3.8, but it freeze when loading set-up page and the crash and back to desktop.

I have tried Picasa 2.7 - 3.0 and now 3.8 with separate Wine installation. No luck. My distro is Lubuntu 10.10.

Anyone who can give me a hand? - I have searched the web for days....

Kind rgds
Ola

---

### Post by kvarley on 2011-03-14
Picasa is available for Linux as a native application.

[http://picasa.google.com/linux/]("http://picasa.google.com/linux/")

---

### Post by ojahr on 2011-03-15
Thanks, I know. But this version also uses Wine (included) and I think that is the problem. Exactly the same happened when I tried to install 3.0 directly by the installer. The PC freeze at the first condition confirmation page and then it goes back to the desktop. I am quite confident that Wine is the problem as I cannot load anything like Notepad in Wine after installing 1.2 and 1.3 Beta. Same story - first page in Notepad freeze and then back to the desktop...

---

### Post by Script Warlock on 2011-03-15
> **ojahr said:**
> Thanks, I know. But this version also uses Wine (included) and I think that is the problem. Exactly the same happened when I tried to install 3.0 directly by the installer. The PC freeze at the first condition confirmation page and then it goes back to the desktop. I am quite confident that Wine is the problem as I cannot load anything like Notepad in Wine after installing 1.2 and 1.3 Beta. Same story - first page in Notepad freeze and then back to the desktop...

why not use the stable version of wine which is 1.2 and also as kvarley suggested use the picasa for linux. cleanup/reinstall your wine.

---

### Post by ojahr on 2011-03-15
Thanks, but I am still a bit puzzled. I started off downloading 3.0 for Linux (Debian) and installed and it froze on first running.
Then I installed Wine 1.2 and tried again - same result. I cleaned up and installed Wine 1.3 and tried 3.8 - same result.
Can it be that Wine will NOT work if you have less than 500 meg ram? I have in fact installed Picasa linux version on 2 PC's under Lubuntu 10.10 with 500 meg ram without problems and I have also installed same Picasa on my own 312 meg PC under WattOS 3 based on Ubuntu 10.10. However I find Lubuntu better, that's why I still try...

---

### Post by grahammechanical on 2011-03-15
I have found that that you get configuration conflicts from failed installation of programs in wine. I would suggest that 

1) you use the wine menu to uninstall the wine software.

2) use sysnaptic or update manger to uninstall wine.

3) delete  or rename the folder .wine. It is in the Home folder but you need to select View>Show hidden files.

4) Re-install wine and start again.

This worked for me when I had trouble getting a program to load. I fixed the loading problem but it still would not load because of conflicts in the .wine folder.

Regards.

---

### Post by ojahr on 2011-03-15
Thanks a lot, but unfortunately no luck. I did it all and also deleted .wine dir, and then I just reinstalled Wine from package mgr. Wine will simply not work - I tried to rund the configuration and I get the small wine window telling me that it configures the .wine folder, but it crashes as soon as I get the first config window on the screen. Exactly same way as Picasa would crash/freeze.
Kind rgds
Ola

---

### Post by ojahr on 2011-03-15
Sorry, does still not work. I simply cannot get Wine up and running. It cannot even be uninstalled from the wine menu - it freeze the same way as the others. I did all you mentioned - also deleted the .wine folder. 

Thanks anyway...
Ola

---

### Post by ojahr on 2011-03-19
Tried to get Wine and also Picasa 3.0 to work on Pentuium III with 312 meg ram - no luck. Got 10.04 and it works perfectly. Looks to me like 10.10 take too much memory as it freeze in the last session all the time.
Ola

---

