---
title: "Cannot open docs off of network share"
date: 2010-09-02
forum: General Help
---

### Post by OMRebel on 2010-09-02
I'm having a problem that is driving me nuts. I have mounted a share to a network folder on a Windows Server. I can read/write to that share just fine. I can open up .txt files just fine. But, for some reason, whenever I try to open up any .doc, .docx, .xls files that are located on that drive, I get the following error:

"Could not display "smb://192.168.1.105/z_drive/Information2.doc"
There is no application installed for Word document files"
(see attached screenshot)

Yes, Open Office is installed.  I can copy the file down locally, and Open Office will open the file up fine. If I use the "Select Application" button, it just opens up an instance of Open Office but the document appears blank (even though it's not).

I have tried reinstalling Open Office, but that hasn't solved the problem.  I'm confused as to where to do from here.  Help?  :)

---

### Post by OMRebel on 2010-09-03
Bump.  Sorry about bumping this thread, but I'm desperate to find a solution to this problem.

---

### Post by OMRebel on 2010-09-14
Anyone?

---

### Post by Morbius1 on 2010-09-14
nobrl ?

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=31490#p147091](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=31490#p147091)

---

### Post by capscrew on 2010-09-14
> **Morbius1 said:**
> nobrl ?

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=31490#p147091](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=31490#p147091)

Note that you have to mount the share yourself rather than allowing Nautilus to do it.  I believe that OO has problems when Nautilus provides that mount.

I mount one share of mine from a script (mount -t cifs etc,) just to accommodate this peculiarity.  I do not use **noblr **though.

---

