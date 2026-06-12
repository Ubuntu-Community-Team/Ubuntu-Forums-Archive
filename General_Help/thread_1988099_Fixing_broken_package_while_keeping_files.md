---
title: "Fixing broken package while keeping files"
date: 2012-05-26
forum: General Help
---

### Post by hangfire on 2012-05-26
I used the procedure [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#80") to finally get an 11.10 system printing to an old Brother printer. However now the package system is broken. The real issue is probably that the printer is old, the package is old, the Linux is new, and Brother's Debian packages were always really shaky (csh anyone? Soft links in /etc/init.d?). But what I want to do is keep the printer driver but lose the package problem.

Here's the error:


sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc210clpr needs to be reinstalled, but I can't find an archive for it.

---

### Post by phaed on 2012-05-26
Have you tried removing / purging that package?

---

### Post by hangfire on 2012-05-26
> **phaed said:**
> Have you tried removing / purging that package?

Yeah, just found the uninstall magic that works:

dpkg --remove --force-remove-reinstreq <package>

First I copied the edited file aside, did the remove, did the re-install, copied the file back.

Then back to CUPS to change usb to socket.

Now I'm back to the false ink empty error I fixed earlier. But that's a different Brother problem.

Hmm. Update still broken.

---

### Post by plucky on 2012-05-27
> **hangfire said:**
> Yeah, just found the uninstall magic that works:

dpkg --remove --force-remove-reinstreq <package>

First I copied the edited file aside, did the remove, did the re-install, copied the file back.

Then back to CUPS to change usb to socket.

Now I'm back to the false ink empty error I fixed earlier. But that's a different Brother problem.

Hmm. Update still broken.


You are one of the lucky ones in that the package you require is already in the Ubuntu Repositories.Open **Synaptic Package Manager** and search for MFC-210C and install both the cupswrapper and lpr drivers that it finds.

p.s. Fix the package manager first.

Good Luck

---

