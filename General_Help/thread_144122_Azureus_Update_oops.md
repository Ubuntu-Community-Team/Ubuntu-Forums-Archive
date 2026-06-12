---
title: "Azureus Update oops"
date: 2006-03-13
forum: General Help
---

### Post by zorkerz on 2006-03-13
Hi
Opened up Azureus today and the updater poped up with an "SWT Library for gtk" update.  It updated fine and asked to restart Azureus, however each time i update Azureus they same "SWT Library for gtk" update version 3139, its 2.6 MB.

This is what the text window says wile downloading I assume theres nothing wrong here.
Downloading: [[http://torrents.aelitis.com:88/torrents/swt-3.1.2-gtk-linux-x86.zip.torrent:](http://torrents.aelitis.com:88/torrents/swt-3.1.2-gtk-linux-x86.zip.torrent:) torrent]
  Downloading: swt-3.1.2-gtk-linux-x86.zip
Torrent download complete

I have no idea where to begin with this problem, help much appreciated.

---

### Post by Xian on 2006-03-13
My experience with this is that if you installed Azureus from a binary package (such as a deb file from a repo via Synaptic or APT), then the updates that are listed will not have much chance of taking effect or working as might be expected. Generally, you will just need to wait until an updated binary package is made available. This is why I always install Azuerus directly from their website using the source package. It always takes any updates and implements them properly.

---

### Post by kverde on 2006-03-13
I have the same problem...  let us know if you figure out a solution.

---

### Post by zorkerz on 2006-03-14
Thanx for the replies you guys.  Xian, your theory makes much sence, I guess if i get bored some day i will reinstall azureus from the site, but besides the little annoyance it seams to be working fine so its not top on my list.

---

### Post by TylerH on 2006-03-14
I installed Azureus using Automatix and ran the Azureus updates that included the "SWT Library for gtk". Now Azureus just plainly will not open. If I click on it from the apps menu it does nothing. I expect this will require an uninstall/reinstall, annoying to say the least.

Anyone else with similar problems?

---

### Post by mlind on 2006-03-14
I didn't have any luck with swt update either, but I'm running Azureus locally
so I downloaded the swt update zip and updated swt manually.

---

### Post by Placid on 2006-03-14
I found that it didn't update the SWT library files. You can get a better idea of what is happening by opening a terminal session and running **azureus** from the prompt. After I manually copied the 3139 files to /usr/lib everything was fine.

Cheers

---

### Post by glycolized on 2006-03-15
[QUOTE=TylerH]I installed Azureus using Automatix and ran the Azureus updates that included the "SWT Library for gtk". Now Azureus just plainly will not open. If I click on it from the apps menu it does nothing. I expect this will require an uninstall/reinstall, annoying to say the least.

Anyone else with similar problems?[/QUOTE]

I have this exact problem.  I did install Azureus with Automatix.

I'd like to reinstall from the Azureus site.  Anyone know how I can safely remove my non-working install?

---

### Post by Xian on 2006-03-15
[QUOTE=glycolized]I'd like to reinstall from the Azureus site.  Anyone know how I can safely remove my non-working install?[/QUOTE]

I know nothing about using Automatix but surely there is a way to uninstall the applications that it provides. LOL, otherwise it would pretty much useless.

---

### Post by glycolized on 2006-03-15
Okay, I got it working again by copying the files as Placid noted above.

---

### Post by openmind on 2006-03-15
I went throught the same problems until I read several discussions here saying do not update Azureus, basically.

---

### Post by Sherlock Holmboy on 2006-03-16
[QUOTE=TylerH]I installed Azureus using Automatix and ran the Azureus updates that included the "SWT Library for gtk". Now Azureus just plainly will not open. If I click on it from the apps menu it does nothing. I expect this will require an uninstall/reinstall, annoying to say the least.

Anyone else with similar problems?[/QUOTE]
i had the same problem, i downloaded the latest build from the tarball from the azureus site, and ran it from my download directory

---

### Post by Chafnan on 2007-06-10
To fix this your need to run Azureus from the terminal as "sudo".  It will then ask for the update and install it.  Then exit Azureus and go into normally.

---

