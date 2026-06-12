---
title: "dpkg : .deb package not showing reinstall on trying to reinstall an application"
date: 2010-05-26
forum: General Help
---

### Post by vaibhavkhandu on 2010-05-26
Hi

I created a deb package using dpkg of a binary/executable file and installed it on other ubuntu desktop. But when I double click on the deb package, after installing once, I still get "install" button instead of "reinstall" button now.
[COLOR="DarkRed"]Do I need to set some extra extra parameters for it somewhere?[/COLOR] 
I have written the following, which I guess was all that was needed for the purpose, in the control file:

Conflicts: myAppName
Replaces: myAppName
Provides: myAppName


I get following warning message while trying to build the package(In case this has something to do with reinstall issue above):
[COLOR="Magenta"]myAppName-1.0.0.0//DEBIAN/control' contains user-defined field `Build-Depends'
warning, `myAppName-1.0.0.0//DEBIAN/control' contains user-defined field `Standards-Version'[/COLOR]

[COLOR="DarkRed"]What does this warning mean btw ?[/COLOR]

Thanks in advance for any help :)

---

### Post by vaibhavkhandu on 2010-05-28
still waiting for some reply...


Regards,
vaibhav

---

### Post by jerrrys on 2010-05-29
have you tried this?

[ATTACH]158625[/ATTACH]

---

### Post by vaibhavkhandu on 2010-05-31
Hi

I have not tried dpkg-repack and it is not installed on my system.
But i am not able to figure out how is it related to what i want to achieve?
[COLOR="Olive"]In case i could not make my problem clear in my previous post:
I just want to have "reinstall" option instead of "install" option (in GDebi package installer) if I double click on my .deb package which i have already installed.[/COLOR]
As far as i could figure out from googling on "dpkg-repack", it is used to create a package for some application which is installed on my system in case  i have lost its deb package.

[COLOR="DarkOrange"]I tried similar thing (trying to reinstall after installing from the same deb package) for google-chrome from its .deb package and it(GDebi package installer) is showing "reinstall" (instead of "install") from second install onwards. Also given that I dont have dpkg-repack installed on my system for this case too.[/COLOR]

---

