---
title: "Problem upgrading to OpenOffice.org 3.2rc1"
date: 2010-01-16
forum: General Help
---

### Post by LukeLinux on 2010-01-16
Hey guys!

Earlier today I came across a .docx file made with MS Office 2007. Since I was in Ubuntu already, I just thought "ok, well, instead of booting into Windows, I'll just install OpenOffice 3.2rc1 on linux!" It sounded simple.

First I uninstalled OOo 3.1...or at least I thought I did. I went into Ubuntu 9.10's (64-bit, if that makes any difference)** Ubuntu Software Center** and removed all OpenOffice.org components. I checked in the menu and saw that the links were gone, so I thought all was successful.

But then I downloaded 3.2 in the .deb format and installed all of them via terminal with **sudo dpkg -i *.deb**, which seemed to work. Only there were no menu shortcuts. So I tried launching it by typing **openoffice **in a terminal. I was surprised to find it launching OOo 3.1's quickstart menu, and simply not finding any of its components installed!

So now I can't use OpenOffice at all. I'm pretty sure I could get 3.1 back via the software center, but I would really like to be able to use 3.2. I've removed the rest of openoffice 3.1 with an apt command, but reinstalling 3.2 does no good. And I'm not confident that 3.1 is really uninstalled even still...Synaptic Package Manager shows a few packages left behind from several versions of OOo (even though 3.1 and 3.2 are the only files that should possibly be able to be on there).

Any help? I just want to get 3.1 removed and 3.2 installed, but so far no other forum posts (here or on the openoffice forums) have solved my problem...

thanks

---

### Post by ajgreeny on 2010-01-16
The pathway is probably /opt as it was if you upgraded to 3 when it first appeared, but before packages were available from ubuntu.

Have a look in there and make launchers manually for the executables if you want to add it to your menu.  If you have really uninstalled all your old version, see if there is another deb in the downloaded archive in a path like
/DEBS/desktop-integration/openoffice.org-3.2-debian-menus-x#x#x.deb.
as that may well do the job for you.  You must ensure all older versions are gone forst or the system will develop a big headache and not know what you want.

---

### Post by Hagar Delest on 2010-01-16
Before installing any version from the OOo web site, you have to make sure first that there is no Ubuntu package of OOo (packages with the 'ubuntu' string in their version number).

Note that there is no desktop-integration folder in the beta (but not sure about the RC). So not seeing the menus can be standard behavior (at least for betas).

---

### Post by Cheesemill on 2010-01-16
You do realise that 3.1 opens .docx files don't you?

---

### Post by gradinaruvasile on 2010-01-16
Yes it is. Install it and you will see the menus.

---

### Post by LukeLinux on 2010-01-18
> **ajgreeny said:**
> The pathway is probably /opt as it was if you upgraded to 3 when it first appeared, but before packages were available from ubuntu.

Now that's just weird, I looked all through the /opt folder before and tried to run the executables in the openoffice.org3 folder, but they wouldn't start. But I just tried it again and suddenly they work!

> **ajgreeny said:**
> Have a look in there and make launchers manually for the executables if you want to add it to your menu.  If you have really uninstalled all your old version, see if there is another deb in the downloaded archive in a path like
/DEBS/desktop-integration/openoffice.org-3.2-debian-menus-x#x#x.deb.
as that may well do the job for you.  You must ensure all older versions are gone forst or the system will develop a big headache and not know what you want.

I also tried installing that package before (in a terminal), but it always said there was a conflict with another package. This time I tried opening it in GDebi and found it to say this:
[COLOR=Red]
Error: Breaks exisiting package 'openoffice.org-common' conflict: openoffice.org-debian-menus ( )[/COLOR]

Last time I broke a package with GDebi I had to reinstall the whole operating system...do I need openoffice.org-common around with 3.2? Or will removing that break OpenOffice?

> **Cheesemill said:**
> You do realise that 3.1 opens .docx files don't you?

No, I didn't...I've tried to in the past (on Windows) without success...3.2rc1 was the first version that did it for me in Windows, so I assumed it would be the same in Ubuntu. :(

---

### Post by Hagar Delest on 2010-01-18
A conflict between packages for OOo usually means that you've mixed ubuntu packages and Sun packages of OOo. They are not compatible.

---

### Post by LukeLinux on 2010-01-19
> **Hagar de l'Est said:**
> A conflict between packages for OOo usually means that you've mixed ubuntu packages and Sun packages of OOo. They are not compatible.

Understandable...but I really just wanted to know if it would mess up my system to remove it, since I've had to reinstall the OS from stuff like this before.

Well, I just went ahead and tried removing openoffice.org-common with Synaptic and then installing the debian-menus package, and that seems to have cleared things up! OOo 3.2rc1 is now fully functional! =D>

Thanks, guys!

...and I just found out that OOo 3.2rc2 is available now :lol:

THREAD SOLVED

---

