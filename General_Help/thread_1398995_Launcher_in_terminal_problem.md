---
title: "Launcher in terminal problem"
date: 2010-02-05
forum: General Help
---

### Post by RogerD on 2010-02-05
Hi

I don't seem to be able to create a Launcher properly.

I use CrashPlan to backup my files, and in oder to get it to work properly with 9.10, I have to use a short script:

export GDK_NATIVE_WINDOWS=1;/usr/local/bin/CrashPlanDesktop

Currently, I open the terminal, paste a copy of the script into the command line, press enter, and away we go. I'm sure I should be able to create a Launcher to automate this process.

I right-click on the desktop, the Create Launcher window appears, under type, I select Application in Terminal, I put CrashPlan in the Name box and paste my script into the command window - seems straightforward, and when I click on OK, I get a CrashPlan Launcher icon on my desktop.

However, when I double click on the icon, I  get the message:

There was an error launching the application.
Details: Failed to execute child
process "export" (No such file or directory)

Anybody know what I'm doing wrong.

Roger D

---

### Post by audiomick on 2010-02-05
I set up one to start synergy.

I had to save the start command as a txt file.
Mark the file as executable (nautilus, right click>properties>permissions tab, check the box)

Do the right click on the desktop (I put mine in the panel) and create starter.
Choose "application" as type
use "search" to point to the file with the start command in it.

---

### Post by sisco311 on 2010-02-05
in the command field type:
```
sh -c "export GDK_NATIVE_WINDOWS=1;/usr/local/bin/CrashPlanDesktop"
```

---

### Post by RogerD on 2010-02-05
It works!

Many thhanks for your help

Roger D

---

