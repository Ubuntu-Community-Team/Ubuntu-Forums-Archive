---
title: "Dell Mini 12 Rebooting on own accord"
date: 2009-07-09
forum: General Help
---

### Post by Fangman on 2009-07-09
I have a Dell Mini 12, and am running Hardy. I'm new to Ubuntu.... Today my laptop started randomly logging out to the main ubuntu screen where it asks you to put in the user name and password. it happens when i am touching the keyboard as well as when my fingers are off of it. I can't figure out why it is doing this, but it is causing me a major problem with my online class as it has happened when firefox is open each time, and i need to use firefox to access blackboard. Please help!

---

### Post by nikgare on 2009-07-09
It sounds like you xserver is crashing.
Have a look in the log files here:

/var/log/Xorg.0.log
/var/log/Xorg.0.log.old
/var/log/Xorg.1.log
/var/log/Xorg.1.log.old
etc...

to see if you can see any error messages - the'll probably be at the near the end of the files.

---

### Post by Fangman on 2009-07-09
ok- sorry newbie here- how do I go about doing that?

---

### Post by Fangman on 2009-07-09
Ok so i entered in the log files into the terminal.....  attached is a screenshot of the readout...


> **nikgare said:**
> It sounds like you xserver is crashing.
Have a look in the log files here:

/var/log/Xorg.0.log
/var/log/Xorg.0.log.old
/var/log/Xorg.1.log
/var/log/Xorg.1.log.old
etc...

to see if you can see any error messages - the'll probably be at the near the end of the files.

---

### Post by nikgare on 2009-07-10
You need to open them to read them.
Go to **Applications->Accessories->Text Editor** and then open the file up.
Scroll down to the bottom and look for error messages there.  You can copy and paste into here if you find any.

---

### Post by Fangman on 2009-07-10
Thanks!

Ok there were no errors under the first, the second was in some sort of symbol code but under xorg.20.log i found this

Fatal server error:
AddScreen/ScreenInit failed for driver 0

After further examination it seems to happen on flash driven sites through mozilla..... ie mafia wars on facebook. Every site i go to that uses flash says i need to upgrade to the latest version, but i thought I had done that.

---

