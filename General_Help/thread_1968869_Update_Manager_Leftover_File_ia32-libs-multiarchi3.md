---
title: "Update Manager Leftover File ia32-libs-multiarch:i386"
date: 2012-04-29
forum: General Help
---

### Post by stevedude on 2012-04-29
I upgraded from Ubuntu 11.10 64-bit to 12.04 64-bit via the upgrade process (Ran update and used the Upgrade button that appeared). I use Gnome-Shell if that makes any difference. Since then I cannot seem to resolve a message I receive in Update Manager that states under "Distribution Updates" - "Multi-arch versions of former ia32-libraries (ia32-libs-multiarch:i386 [Size 5kb])"

I searched and found this post [http://ubuntuforums.org/showthread.php?t=1966091&highlight=ia32](http://ubuntuforums.org/showthread.php?t=1966091&highlight=ia32) and tried the recommended action there, but it did not work for me.

I installed and tried to use Synaptic Package Manager to find broken packages or some other issues and I noticed that there is an exclaimation symbol next to ia32-libs-multiarch:i386. If I select the package for removal it states it will also remove Skype which I need. 

Anyone know how to resolve this issue?

Thanks in advance!

---

### Post by stevedude on 2012-04-29
RESOLVED

I used Synaptic Package Manager anyway and removed the ia32-libs-multiarch:i386 file(s) and it also removed Skype. Instead of installing Skype through a download from their website, I installed Skype via the Ubuntu Software Center repositories and the issue is resolved. 

Skype works fine and I no longer have this orphan set of files sitting in Update Manager.

---

