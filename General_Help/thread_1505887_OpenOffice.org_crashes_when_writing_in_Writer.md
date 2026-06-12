---
title: "OpenOffice.org crashes when writing in Writer"
date: 2010-06-09
forum: General Help
---

### Post by Eax.exe on 2010-06-09
Hi there.

I have the problem that whenever I write something it freezes up the window, my processor use rise to 100% and then it crash showing the OpenOffice.org crash-screen.
This only happens in Writer and not Spreadsheets, Presentation refuses to start.

Info about the system:
**OpenOffice:**
OpenOffice.org 3.2.0
OOO320m12 (Build:9483)
Debian 1:3.2.0-7ubuntu4.1, Thu Jun 3 02:15:29 UTC 20.

**Ubuntu:**2.6.32-22-generic
Ubuntu 10.04.
2.6.32-22-generic

Can anyone help me with this issue please?

**Edit:**
Reinstalling the entire package and rebooting did not fix this issue.

---

### Post by scouser73 on 2010-06-10
You've mentioned about reinstalling OpenOffice but have you tried deleting the OpenOffice profile, which can be found in your home folder.

Go to your home folder & press CTRL & H, which makes the hidden files visible.

Go into the folder named **.openoffice.org** & delete everything in that folder.

Now restart Openoffice Writer, and in theory it should work as normal.

---

### Post by Eax.exe on 2010-06-10
> **scouser73 said:**
> You've mentioned about reinstalling OpenOffice but have you tried deleting the OpenOffice profile, which can be found in your home folder.

Go to your home folder & press CTRL & H, which makes the hidden files visible.

Go into the folder named **.openoffice.org** & delete everything in that folder.

Now restart Openoffice Writer, and in theory it should work as normal.
Thanks for your answer, I have already tried this to no avail :(

---

### Post by Hagar Delest on 2010-06-10
Try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Eax.exe on 2010-06-11
> **Hagar de l'Est said:**
> Try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Will do, thanks! :)

---

### Post by Eax.exe on 2010-06-25
Installing the **Sun** version did **NOT** help :(
Can someone help please? :)

---

### Post by Eax.exe on 2010-06-27
Anyone? :)

---

### Post by AlphaLexman on 2010-06-27
Post the output of ```
oowriter
``` from a terminal.

---

