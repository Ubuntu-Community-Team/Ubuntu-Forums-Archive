---
title: "File Transfer Over Local Network"
date: 2011-05-22
forum: General Help
---

### Post by ericzmeh on 2011-05-22
I have just recently recovered my desktop from a HDD crash, and would like to transfer a good amount of backup files from my laptop back to the tower over the network.  I have apache2 http server installed as well as apache2-common.  I have network file sharing enabled under Ubuntu 11, updated to newest kernel and all packages.  I have read through a few threads and it seems i should be able to go to the Network in file explorer, and then to Workgroup from there, since Windows 7 is installed on my laptop.  Double clicking WORKGROUP fails to mount any Windows machines.  Other Windows machines on the network have no problem identifying and accessing the laptop.  I would very much like to get this done using network file transfer.  Am I missing something?  :-]

---

### Post by linuxinstalledfromhdd on 2011-05-22
[http://cinderbox.net/2011/05/12/use-ubuntu-live-cd-to-do-data-recovery-on-your-old-windows-pc/](http://cinderbox.net/2011/05/12/use-ubuntu-live-cd-to-do-data-recovery-on-your-old-windows-pc/)

---

### Post by ericzmeh on 2011-05-22
I'm sorry, seems as if I did not word my problem correctly.  I do not have an old PC, just a new HDD with nothing but Ubuntu installed on my tower now.  I am trying to access shared locations on my laptop which runs Windows 7.  I do not need help accessing a corrupt HDD on my tower.  The above tutorial does not address what I am trying to get done, although I do appreciate the response.

---

### Post by linuxinstalledfromhdd on 2011-05-22
Well if you read about half the way down it covers networking them together so you can do a data migration.  I think that is what you are asking for, but I could be wrong.

---

### Post by bootedguy on 2011-05-22
One option is to use the "Connect to Server" in Nautilus, and use the SSH protocol.  This will open up a folder for your Windows machine and you can copy and paste files back and forth.  I am fairly sure Windows supports SSH.  IMHO, this works much better than Samba.  Samba is slow and a bit flaky.  For Linux, the gold standard is NFS, but there is a bit of a learning curve, and Windows does not have native support.

---

### Post by linuxinstalledfromhdd on 2011-05-22
The fastest way I know to migrate data would be to physically hook the drive to the same bus as the unit you want to migrate your data to.  Ubuntu will detect the new drive and you will be good to go.

---

### Post by ericzmeh on 2011-05-22
Sorry linuxinstalledfromhdd, the tutorial was titled "How-to use Ubuntu Live CD to do Data Migration on your old Windows PC," and I am not on a LiveCD, nor did I notice the additional tutorial towards the bottom of the page.  It seems this tutorial is also non-compliant as it is for an earlier version of Ubuntu, and not the Natty release.  I do appreciate the information either way.

bootedguy, looking into using Nautilus now, thanks much for the tip.  Windows does support SSH, and this would be a great way to get done what I need if it proves to work :-]  Giving it a go now.

EDIT:  I am trying to transfer from a laptop drive that is not accessible unless I want to spend an hour ripping apart my new laptop, and another hour trying to put it back together, so transferring externally via USB or eSATA will not work, linuxinstalledfromhdd, but good idea nonetheless.

---

### Post by linuxinstalledfromhdd on 2011-05-22
Tested in Natty, works great for data migration.

---

### Post by ericzmeh on 2011-05-22
I cheated and used TeamViewer :-p  Will mark this as solved, thanks all for the responses.

---

