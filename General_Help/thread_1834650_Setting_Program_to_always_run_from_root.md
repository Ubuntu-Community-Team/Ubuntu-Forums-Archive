---
title: "Setting Program to always run from root"
date: 2011-08-27
forum: General Help
---

### Post by rajohns08 on 2011-08-27
when i click the icon i want it to automatically run from root (wireshark is the program). how do i set the icon to always run from root?

---

### Post by Enigmapond on 2011-08-27
It's not advisable to have anything run as root automatically however you can create a launcher with the command "sudo wireshark" and it will ask you for your pass prior to opening.

---

### Post by dniMretsaM on 2011-08-27
Right-click on the icon of the program and click on "Icon Settings." Then under the "Application" tab change the command from "wireshark" to "kdesudo wireshark" and it should work just fine. Note that these instructions are for the KDE desktop environment not GNOME (which is what you're probably on). I'm sure you can figure it out though. Also, the GNOME command would be "gksudo wireshark" (I believe, someone correct me if I'm wrong).

---

### Post by sbraz on 2011-08-27
> **dnimretsam said:**
> gksudo wireshark
this is correct. :)

---

### Post by rajohns08 on 2011-08-28
> **dniMretsaM said:**
> Right-click on the icon of the program and click on "Icon Settings." Then under the "Application" tab change the command from "wireshark" to "kdesudo wireshark" and it should work just fine. Note that these instructions are for the KDE desktop environment not GNOME (which is what you're probably on). I'm sure you can figure it out though. Also, the GNOME command would be "gksudo wireshark" (I believe, someone correct me if I'm wrong).

thank you this worked

---

