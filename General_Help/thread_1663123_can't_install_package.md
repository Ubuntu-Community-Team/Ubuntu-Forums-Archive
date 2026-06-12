---
title: "can't install package"
date: 2011-01-09
forum: General Help
---

### Post by robotz421 on 2011-01-09
Hi.  I am trying to install my first package on a machine without an internet connection.  The package I want to install is gForth.  I downloaded the deb package and put it onto a cd.  Then I double clicked on the deb package and installed the software but when I type gforth at the command line I get the message &quot;'gforth' is not currently installed.  You can install it by typing: sudo apt-get install gforth&quot;  Any help would be greatly appreciated.

---

### Post by James_Lochhead on 2011-01-09
Open System > Administration > Synaptic Package Manager

Use the search on the right to search for your package. If it is installed it should have a green box next to it. There might be multiple occurrences so be thorough.

If it is installed properly then it might simply be that that version of the software doesn't use that particular command or you are not using the right command full stop.

---

### Post by QLee on 2011-01-09
[QUOTE=robotz421]Hi.  I am trying to install my first package on a machine without an internet connection.  The package I want to install is gForth.  I downloaded the deb package and put it onto a cd....[/QUOTE]

Well, gforth is not just a single package, at the very least you'd need both gforth and gforth-common and those two would only be enough if the other dependencies are already satisfied on your system. Is it your intention to always have the system not connected to the Internet and not install much and not do security updates?

---

### Post by robotz421 on 2011-01-09
QLee, yes it is.

---

### Post by Frogs Hair on 2011-01-09
If you intend to use the computer off line , the link may help . you will need internet access to get what is needed for your repository. 

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by QLee on 2011-01-09
OK.

Then you are going to have to satisfy all the dependencies for the package.

The GUI package manager that        James_Lochhead mentioned can show you what those are on your system from the menu Package-->Properties, Dependencies tab, when you have gforth selected.

---

### Post by robotz421 on 2011-01-10
Thank you QLee, that looks very helpful.

---

