---
title: "Unable to open steam or any steam games"
date: 2011-12-10
forum: General Help
---

### Post by guyver_dio on 2011-12-10
A day ago I was able to run steam and run the games I downloaded but since installing system updates I've been unable to open steam or the games. When double clicked they will show in the apps panel of the left side and the mouse icon shows that it's thinking, then nothing apps, it'll disappear out of the apps panel and thats it. 

Not sure what's going on, anyone else experiencing the same problems?

Running ubuntu 11.10 oneiric

thanks

---

### Post by oldtimer7777 on 2011-12-10
> **guyver_dio said:**
> A day ago I was able to run steam and run the games I downloaded but since installing system updates I've been unable to open steam or the games. When double clicked they will show in the apps panel of the left side and the mouse icon shows that it's thinking, then nothing apps, it'll disappear out of the apps panel and thats it. 

Not sure what's going on, anyone else experiencing the same problems?

Running ubuntu 11.10 oneiric

thanks

What I did it get it to work was install PlayOnLinux. It is about 1/3rd the way down the following Ubuntu 11.10 checklist:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by guyver_dio on 2011-12-10
it seems to be wine related rather than steam itself. Just tried opening another program with the wine launcher and it did the same thing. May try reinstalling wine.

Thanks for the tip, I have PlayOnLinux installed but haven't messed with it yet, gonna take a look now.

---

### Post by oldtimer7777 on 2011-12-10
> **guyver_dio said:**
> it seems to be wine related rather than steam itself. Just tried opening another program with the wine launcher and it did the same thing. May try reinstalling wine.

Thanks for the tip, I have PlayOnLinux installed but haven't messed with it yet, gonna take a look now.

PlayOnLinux uses winetricks, which of course you can install separately to modify the Wine parameters for each installation you do with Wine, except PlayOnLinux does it automatically for you. It takes the headache out of using Wine in Ubuntu for everything I have needed to use it for.

---

### Post by guyver_dio on 2011-12-10
through playonlinux i was able to get some debugging output

[POL_Wine_SetVersionEnv] Message: Setting wine version path: 1.3.28, x86
[POL_Wine_SetVersionEnv] Message: "/home/guyver/.PlayOnLinux//wine/linux-x86/1.3.28" exists
[POL_Wine] Message: Running wine-1.3.28 Steam.exe
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  1376
  Current serial number in output stream:  1376
[POL_Wine] Message: Wine return: 1

---

### Post by oldtimer7777 on 2011-12-10
Have you checked the forums for it in WineHQ for a work-around yet?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444)

---

