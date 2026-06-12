---
title: "OpenOffice 3 problems"
date: 2009-12-28
forum: General Help
---

### Post by Weballergy on 2009-12-28
Hey !

I've installed OpenOffice 3.1.0 from the DEB packages in 32bits.
My problem is: Ok, I've installed all DEB packages through Terminal using the dpkg -i *.deb and the desktop integration but...

When I restart my cpu, and I try to open the SWriter, the program shows me a window saying for document recovery, when I didn't opened nothing. So, I click ACCEPT, and follow the process, but all time is a loop, all time brings me to the same. So I've discovered that if I open an Openbase, and I save an openbase document, I'll can open SWriter normally during the entire user session, but if I restart again, I have to follow the same process again. Any idea? Is that a program bug ? I've followed one to one the steps to install from openoffice.org

Thanks !

And the last thing. How can I do to create a direct access in my desktop of "SOFFICE" ?
You know, that screen:
[IMG]http://www.fayerwayer.com/up/2008/10/openoffice_3_beta_1_start_540x427.jpg[/IMG]

---

### Post by jmszr on 2009-12-28
Weballergy,

This thread may help you with your first problem: [http://ubuntuforums.org/showthread.php?t=1343182](http://ubuntuforums.org/showthread.php?t=1343182) .

Hope that helps.

---

### Post by gradinaruvasile on 2009-12-28
Did the desktop-integration package install correctly? There is a package i dont remember right now how its called that is preinstalled and it has to be removed before installing the desktop-integration package.

---

### Post by Weballergy on 2009-12-28
> **gradinaruvasile said:**
> Did the desktop-integration package install correctly? There is a package i dont remember right now how its called that is preinstalled and it has to be removed before installing the desktop-integration package.

I think I did. I removed OpenOffice with aptitude remove in Terminal, and moved some packages by synaptic, but I don't remember if I removed the preinstalled desktop integration, but I did with the preinstalled openoffice.

jmszr, thanks, I'll check it now :D !

---

### Post by Weballergy on 2009-12-28
Hey, thanks for the info, but I didn't got clear what I have to do.

I tried to remove the Recovery.xcu, but when I restart, it gives the same error. ~~

---

### Post by Weballergy on 2009-12-29
No one knows ?

---

### Post by Weballergy on 2009-12-29
SOLVED !

Finally I've solved my problem. Well, after the installation, this thing makes the loop as I said, with the recovery panel.
The only thing you have to do is:

1. Go to: /home/username
2. Push Cntrl+H
3. Look for the .openoffice.org folder
4. Delete the folder.

After the restart, this works !

---

