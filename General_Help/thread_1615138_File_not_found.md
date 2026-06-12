---
title: "File not found?"
date: 2010-11-06
forum: General Help
---

### Post by CharlesWelsh on 2010-11-06
For some strange reason when I try to access my Pictures, Videos etc. I get an error message "File not found" *screenshot* I can access the entire system via Nautilus. Granted I can still access my files; I want my system to run the right way. 

I believe the issue may be tied to WINE; due to the fact that, when I try to install Windows games it says something about "Executable Bits". Not to mention when I attempt to browse the C: Drive I get the same error as I first mentioned. (File not found)

Any help would be appreciated..

Ubuntu 10.10 Maverick
Toshiba Satellite A15 S1292

---

### Post by DirtyPC on 2010-11-06
> **CharlesWelsh said:**
> For some strange reason when I try to access my Pictures, Videos etc. I get an error message "File not found" *screenshot* I can access the entire system via Nautilus. Granted I can still access my files; I want my system to run the right way. 

I believe the issue may be tied to WINE; due to the fact that, when I try to install Windows games it says something about "Executable Bits". Not to mention when I attempt to browse the C: Drive I get the same error as I first mentioned. (File not found)

Any help would be appreciated..

Ubuntu 10.10 Maverick
Toshiba Satellite A15 S1292
That windows problem is solved this way:
right click exectuable (.exe) click properties>permissions, mark as executable.

if it wont let you, enter this at terminal

**gksu nautilus**

As with the other, try updating to the latest files and see if you're telling your OS to search in the wrong places.

harry,

---

### Post by CharlesWelsh on 2010-11-06
I'm sorry can you elaborate a little more? I'm not the most intelligent of Ubuntu users.

---

### Post by CharlesWelsh on 2010-11-06
and the command produced this output: (see screenshot)

---

### Post by CharlesWelsh on 2010-11-06
Bump^^

---

### Post by evilsoup on 2010-11-06
From the screenshot, it seems you are trying to open nautilus with 'gksu' (ie, to run it as root).
1) Why are you trying to run a window as root? Have you tried just using 'nautilus'?
2) The correct command is 'gksudo nautilus'

That said, I am not sure this is the root of the problem. Are you trying to access files on the same computer, or over a network?

---

### Post by CharlesWelsh on 2010-11-06
Same computer.. I go to PLACES-> PICTURES for example. I get that error. its the same for music... all of my places come back as not found. however if i use nautilus, it works fine. I just want my laptop to function properly.

---

### Post by Verbeck on 2010-11-06
create a new folder in your desktop, right click it>open with other application>select file browser

---

### Post by CharlesWelsh on 2010-11-06
okay. i feel stupid. thank you :] Now for the WINE issues? if i put a game disk in such as "Herods Lost Tomb".. and i double click it, its set to open with wine. however it says that message about executable bits. any ideas?

---

### Post by Verbeck on 2010-11-06
> **CharlesWelsh said:**
> okay. i feel stupid. thank you :] Now for the WINE issues? if i put a game disk in such as "Herods Lost Tomb".. and i double click it, its set to open with wine. however it says that message about executable bits. any ideas?

insert the game disk, then open a terminal window. type **wine** in it(put a space after it) then click and drag the executable from the file manager to the terminal window. hit enter

so the command should look some thing like

wine '/media/cd-name/xxx.exe'

---

