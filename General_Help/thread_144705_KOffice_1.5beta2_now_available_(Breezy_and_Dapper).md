---
title: "KOffice 1.5beta2 now available (Breezy and Dapper)"
date: 2006-03-14
forum: General Help
---

### Post by Jucato on 2006-03-14
KOffice 1.5 beta 2 for Breezy and Dapper and amaroK 1.4 beta 2 for Dapper is now available for Kubuntu.

Here's the link :D
[http://kubuntu.org/announcements/koffice-amarok-beta2.php]("http://kubuntu.org/announcements/koffice-amarok-beta2.php")

---

### Post by bailout on 2006-03-14
the koffice links seems to be dead though :( I have been hoping koffice 1.5b2 would be released for dapper soon. Surprised the dapper packages weren't include in the main reps?

---

### Post by tikal26 on 2006-03-14
I just upgrade and I can't start krita I get the following error"
 
Krita could not start: no color space available

Anyone else getting error message?

---

### Post by Jucato on 2006-03-14
Is the link that I posted the one that you're saying is dead?
If it is, here's the list of sources for apt
NOTE: No need to add them all. Just choose one:
> KOffice
Packages are available for Kubuntu 5.10 (Breezy) and Dapper for AMD64, i386 and PowerPC
Mirrors may still syncing, try another mirror if you have problems.
Apt source:
For breezy:
deb [http://kubuntu.org/packages/koffice-15beta2](http://kubuntu.org/packages/koffice-15beta2) breezy main
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.5-beta2/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.5-beta2/kubuntu) breezy main
deb [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/koffice-1.5-beta2/kubuntu](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/koffice-1.5-beta2/kubuntu) breezy main
deb [http://mirror.cc.columbia.edu/pub/software/kde/stable/koffice-1.5-beta2/kubuntu](http://mirror.cc.columbia.edu/pub/software/kde/stable/koffice-1.5-beta2/kubuntu) breezy main
For dapper:
deb [http://kubuntu.org/packages/koffice15beta2](http://kubuntu.org/packages/koffice15beta2) dapper main
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.5-beta2/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.5-beta2/kubuntu) dapper main
deb [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/koffice-1.5-beta2/kubuntu](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/koffice-1.5-beta2/kubuntu) dapper main
deb [http://mirror.cc.columbia.edu/pub/software/kde/stable/koffice-1.5-beta2/kubuntu](http://mirror.cc.columbia.edu/pub/software/kde/stable/koffice-1.5-beta2/kubuntu) dapper main
Thanks to Isaac and the Debian KDE packagers for the KOffice packaging.


amaroK 1.4 beta 2 is not available for Breezy.

EDIT: @tikal: I'm still downloading the updates. I'll get back to you ASAP when I'm done

---

### Post by bailout on 2006-03-14
Problem solved. The kubuntu.org koffice dapper link in that announcement is wrong. It should be

deb [http://kubuntu.org/packages/koffice-15beta2](http://kubuntu.org/packages/koffice-15beta2) dapper main

instead of

deb [http://kubuntu.org/packages/koffice15beta2](http://kubuntu.org/packages/koffice15beta2) dapper main

Off to dl :D

---

### Post by Jucato on 2006-03-14
@bailout: oh, I see. so you were referring to the Dapper repository. I wonder if and how you could inform them about that typo?

@tikal: Krita works fine for me. I'm not really sure if it's  solution, but was the krita-data package installed together with the updates? Btw, I updated from KOffice 1.5 beta 1, if that matters...

---

### Post by tikal26 on 2006-03-14
Fenyx- For some reason the krita-data was not installed.Thanks for pointind me that direction. Where did you get amarok 1.4 for breezy

---

### Post by Jucato on 2006-03-14
I actually haven't gotten amaroK 1.4 beta 2 on breezy. They say because it depended on a newer version of taglib. I'm presuming it musn't be installed in Breezy. I was able to get amaroK 1.4beta1 only through klik. However it's no longer maintained.

Hope the krita-data solves the problem for you.

---

### Post by bailout on 2006-03-14
I got the same error msg with krita and koffice didn't show in the menu or open from the run command. One reboot later and it all works fine - who says you only need to do that with windows ;)

Fenyx - not sure, they don't have a webmaster contact on the kubuntu site just the emails of the main developers and I don't think I count as a press enquiry :)

---

### Post by Jucato on 2006-03-15
that's strange. the update worked perfectly fine on my end. maybe it was because I had KOffice already installed? Did you really have to reboot? sometimes all you need is to log out and back in again :D

---

### Post by bailout on 2006-03-15
I didn't have koffice already installed so maybe that was the difference. The beta2 version had been announced by kde when I installed dapper so I thought I would wait until dapper packages were available.

Perhaps a new sesion would have worked but it doesn't take much longer to reboot and I am in the habit now after so many adept crashes that don't seem to be fixed by just starting a new session ;)

If you think rebooting is bad, network connections froze my pc solid the other day and I had to do a hard reboot for the first time since moving from win98 :eek:

---

### Post by Jucato on 2006-03-15
Nah I don't think rebooting is bad. Just sometimes unnecessary. (It's one of Linux's pride, not rebooting after an install).

You still use Adept? God! How could you stand that pesky critter! :D

---

