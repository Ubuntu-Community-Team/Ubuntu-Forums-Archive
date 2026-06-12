---
title: "OpenOffice 3.1 won't start"
date: 2010-03-14
forum: General Help
---

### Post by EmyrB on 2010-03-14
Hi All,

Just noticed today that OpenOffice.org3 wont start in 64bit Karmic. All I get is the 3.1 splashscreen and that's it. Nothing opens, writer, calc, base or drawing.

Any ideas?

Cheers

EmyrB

---

### Post by jounihat on 2010-08-17
I have the same problem. Any ideas how to fix this? Running 64-bit 10.4.

Any idea how can I install 32-bit version of OpenOffice, just to check if it helps?

---

### Post by earthpigg on 2010-08-17
hi,

can you please start openoffice.org from a terminal and copy/paste any error messages you recieve? 

type this into a terminal:

> openoffice.org

---

### Post by jounihat on 2010-08-17
> **earthpigg said:**
> hi,

can you please start openoffice.org from a terminal and copy/paste any error messages you recieve? 

type this into a terminal:


No error messages. Nothing. I tried openoffice.org, oowriter and oocalc.

---

### Post by earthpigg on 2010-08-17
> **jounihat said:**
> No error messages. Nothing. I tried openoffice.org, oowriter and oocalc.

well, damn.

did this happen starting with a recent update?

if so, have you restarted since the update? usually not needed, but i've seen that resolve general "wonkyness" before.

if OO.o has worked since your most recent update, have any other changes been done that stick out in your mind?

---

### Post by jounihat on 2010-08-17
> **earthpigg said:**
> well, damn.

did this happen starting with a recent update?

if so, have you restarted since the update? usually not needed, but i've seen that resolve general "wonkyness" before.

if OO.o has worked since your most recent update, have any other changes been done that stick out in your mind?


This is a clean install, I have rebooted my computer a couple of times but it didn't change the situation. Could I try to install 32-bit version of OOo somehow?

---

### Post by earthpigg on 2010-08-17
this is a clean install of 10.04 or 9.10?

reason i ask is because a 10.04 install that has been updated ought to have openoffice 3.**_2_**.

---

### Post by jounihat on 2010-08-17
> **earthpigg said:**
> this is a clean install of 10.04 or 9.10?

reason i ask is because a 10.04 install that has been updated ought to have openoffice 3.**_2_**.


Oh yes, this is a clean install of 10.04 and the OOo version is 3.2.0-7ubuntu4.1. Sorry for not noticing that before.

---

### Post by jounihat on 2010-08-17
I tried to reinstall OpenOffice but now I cannot even see the splash screen when I try to start the program :-S

In other words, looks like some sort of a segfault...

---

### Post by earthpigg on 2010-08-17
hrm.

i suppose the next step is to try uninstalling openoffice with 'mark for complete removal' checked in synaptic, hitting apply, and then reinstalling it.

---

### Post by AlphaLexman on 2010-08-17
I know this is a shot in the dark, but try ->
```
ooffice -norestore
```
If you had a bad shutdown of OOo, it will try to restore the last session by default. Sometimes this helps.

---

### Post by jounihat on 2010-08-17
Hey! Thank you very much for your help! I tried the reinstall procedure already before, but something went wrong I guess. Now I tried again to remove every single package related to openoffice. I happened to notice that when synaptic was removing a package called openoffice-emailmerge, it gave a "Bus error" message. I remember that someone else also had this same message when encountering problems with OOo. Anyway, this time after reinstall everything worked fine :-)

Thank you again for your help! This was very puzzling problem because I had a clean install and OpenOffice didn't start even for the first time. So anyone having this same problem, look for the bus error message and reinstall everything (a couple of times if necessary).

---

### Post by jounihat on 2010-08-25
Ok, today I tried to start OpenOffice and SAME PROBLEM AGAIN! I didn't do anything with OOo before this, last time I only checked that it works. Can anyone tell me how can I install 32-bit version of OpenOffice? The 64-bit version SUCKS!

---

