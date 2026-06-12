---
title: "OpenOffice highlighting-highlights whole paragraph, not selected text"
date: 2011-05-22
forum: General Help
---

### Post by jadu on 2011-05-22
Hello all,

I have Open Office 3.2 with Ubuntu 10.04.
When I select text-- a word, a few words-- and then click on highlight on the toolbar, it highlights the whole paragraph, rather than just the selected text. This is a new problem for me, before it seemed to be working fine. 
I searched online but haven't been able to find anything about this problem.
I had tried to install the sun version of Open Office a few months ago, but wasn't able to in the end:
[http://ubuntuforums.org/showthread.php?t=1599349](http://ubuntuforums.org/showthread.php?t=1599349)

I saw that OpenOffice 3.3 is out, but I would rather not upgrade until Ubuntu puts out the upgrade.

any ideas? 

thank you

---

### Post by SteveDee on 2011-05-22
> **jadu said:**
> ...I saw that OpenOffice 3.3 is out, but I would rather not upgrade until Ubuntu puts out the upgrade...

Unfortunately I don't think 3.3 will be added to the repository for 10.04.

I'm running OpenOffice 3.2.1 on 10.10 and don't seem to have the highlight problem you mention. If you believe this problem is due to OpenOffice 3.2 you might consider upgrading from 10.04 to 10.10.

As the future of OpenOffice is not clear (now that ownership rests with Oracle) you might like to try LibreOffice 3.3 on 10.04. Once again, I'm running this on 10.10 and it does not seem to have a highlight problem.

---

### Post by linuxinstalledfromhdd on 2011-05-22
I just tested it in LibreOffice and I didn't have that issue. 

You can upgrade your:P OpenOffice to LibreOffice here:

[http://cinderbox.net/2011/03/29/libreoffice-ubuntu-ppa-makes-installation-easy/](http://cinderbox.net/2011/03/29/libreoffice-ubuntu-ppa-makes-installation-easy/)

---

### Post by jadu on 2011-05-23
hi, thanks to both of you for your suggestions. I'm going to upgrade to Ubuntu 10.10 to get Openoffice 3.2.1 to see if that works. I think I won't install LibreOffice if I can help it, though in theory I think it's a great project; I'm just afraid it will be harder to handle and have less support, and I read this on the link you sent me:
> Installng LibreOffice probably will remove all of OpenOffice from your system and could possibly be irreversible. I tested it and found some breakage after I wanted to switch back to OpenOffice,

I haven't been able to upgrade to 10.10 because of problems with my internet connection, but when I do I'll post back here how it went for me.
thanks

---

### Post by jadu on 2011-05-24
hello all,

Not solved yet.
I upgraded to Ubuntu 10.10, but that didn't work.
I removed and then installed again Open Office Writer from the software manager. Still no.
Then I saw that the same thing happens in OpenOffice spreadsheet. So I went into the synaptic manager (the limits of my technical knowledge, I'm afraid), and searched for all installed openoffice software; then I "marked for reinstallation" basically everything but the dictionaries. Still didn't work.

Any ideas please? I work with openoffice writer for my job, on this computer, from home, and need the highlight function. Would much appreciate any hints...

---

### Post by linuxinstalledfromhdd on 2011-05-24
Test it with a live bootable "persistant" stick of Ubuntu on USB flash drive. And see if the issue still remains.

---

### Post by jadu on 2011-05-25
I tried something similar, thinking it would work the same as an experiment-- I booted with a live CD that I have of Linux Mint, and it worked fine. Also saved the correct highlighting to a document on my usb stick, and it opened showing the correct highlighting. But the problem remains when I try to highlight again, or to remove the highlighting that I had done in Linux Mint.
Should I still download the Ubuntu live cd and try that? or any other idea?

thanks

---

### Post by Hagar Delest on 2011-05-25
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, install the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Note that you can install both vanilla versions of OOo and LibO, they work fine in parallel. Better that than the PPA IMHO.

---

### Post by jadu on 2011-05-25
Changing my user profile worked!

I am very, very VERY grateful to all who took a moment of your time to help me.

---

### Post by jadu on 2011-05-25
I'm very embarrassed but I'm afraid the problem was much simpler than I had thought. Still, for the record I guess I should explain. I had always had just the font color and highlighting icons visible on the toolbar. For some reason the highlighting icon stopped being visible (though I assume it was still there, just not on the toolbar) and the "background" icon appeared. I had never seen the background icon before and didn't know what it was, and I didn't look very carefully, so I just assumed it was the same thing and that icon shape had changed. That was why it was highlighting the whole paragraph...
Sorry to take your time, thanks anyways, I'll try to be more careful next time before asking.

---

