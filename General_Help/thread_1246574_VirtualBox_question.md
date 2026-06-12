---
title: "VirtualBox question"
date: 2009-08-21
forum: General Help
---

### Post by Phenom888 on 2009-08-21
I had installed and uninstalled Virtualbox twice before finally deciding to use it. I had deleted the ubuntu.vdi hard disk and machine before uninstalling. Now when I try to create another it says it already exists and can't create a new one with the same name. When I try selecting the old one that I deleted it says it is inaccessible, and when attempting to delete it says, "Note this hard disk is inaccessible right now and cannot be deleted". Does this mean it never really got deleted or should i just ignore this and create a new one with a different name?  Thanks.

---

### Post by Chronon on 2009-08-21
It seems like it's listed in some configuration for VirtualBox still.  Creating a new .vdi with a different name shouldn't be a problem.  Unfortunately, I'm not sure exactly how to clear the name of the deleted virtual disk from the list.

Check the .VirtualBox folder in your home directory.  You probably need to delete it from ~/.VirtualBox/Machines/.

---

### Post by Phenom888 on 2009-08-21
Oh, ok I will probably just continue to make a new one. I am just wondering if this means it is still taking up disk space somewhere (it is not shown in .VirtualBox folder). Just afraid it might happen again, if anyone else would like to help fell free to post :).

---

### Post by exploder on 2009-08-21
Start VirtualBox, go into, "File", Virtual Media Manager", and look through the tabs for what you want to delete.

---

### Post by rajcan on 2009-08-21
Are you running virtualbox on windows or linux? Cause all you should have to do is go into the director where the virtual hard drives (.vdi) are stored and delete them. I had to do this on windows and it worked perfectly fine.

---

### Post by Phenom888 on 2009-08-21
I am running Windows Vista and yes it shows up in Virtual Media Manager, and shows the .Virtualbox folder as its location but when I go to it it does not appear.
Also says inaccessible when trying to delete.

---

