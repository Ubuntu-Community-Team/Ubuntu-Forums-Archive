---
title: "cannot boot USB after creating"
date: 2010-09-05
forum: General Help
---

### Post by ken poy on 2010-09-05
Hi,  i currently am running Ubuntu 9.10.  i once updated to 10.04 via the update manager but somehow it reverted to 9.10 (not sure what happened)??
i have now downloaded 10.04.1 and attempted to create a startup USB.
i created my 9.10 USB using Unetbootin in Windows and it worked fine and i installed from it.
i am now creating the USB via Admin USB startup disk creator.  i formated the USB pointed it to my 10.04 ISO image and the USB and hit create.  files were copied, persistent storage, and file system created. all went well to completion with no errors.  my USB is a 4 gig SanDisk.
when i attempt to boot the USB i get a screen with vertical colored lines only
i have tried twice with the same result.
Questions:
1.  will the Admin USB startup disk creator produce a bootable USB??
2.  it seems straight forward but are you aware of any problems??
3.  I tried Unetbootin for Linux and had problems recognizing my USB drive.
Maybe my USB stick is bad. i will get another.
Also i will pursue Unetbootin in Linux.
i prefer to avoid being Dependant on Windows and would like to generate a Linux only system with Virtualbox.
i guess i have rambled enough.  thanks for any help/ideas.     ken;)

---

### Post by wilee-nilee on 2010-09-05
Not sure if it is the problem but the Sandisk thumbs have (U3 built in firmware) that causes some problems. Take a look on Google it can be removed if you want to.

The disc creator works well, when you boot it hit the shift key immediatly several times to get to the choose to tryout..etc screen hit f6 and try nomodeset and any others to see if it boots.

---

### Post by C.S.Cameron on 2010-09-05
Have you checked the MD5SUM of the iso to insure the download was ok.

---

### Post by ken poy on 2010-09-09
hi thanks for the updates.
1.i will try another USB stick non sandisk.
2. that was a helpful exercise checking MD5SUM.  i did get through it and my sum compares exactly with the Ubuntu check sum file thanks......ken

---

