---
title: "Libreoffice opens in wrong workspace"
date: 2011-05-09
forum: General Help
---

### Post by gregalynch on 2011-05-09
If libreoffice writer is already running in workspace 1 and you open a new document, that document opens in workspace 2.  And, interestingly, if you first open writer in workspace 2, it opens new documents into workspace 1.  

I tried to recreate the problem with the spreadsheet program and couldn't, it seems to be confined just to the word processor.

I don't know if this is a natty problem or a libreoffice problem - I got them both at once with the upgrade.

Also, I don't know if this is the right forum for reporting bugs.  If not, mods please move it where it goes.   Thanks

---

### Post by areteichi on 2011-05-13
Yeah I experience this issue as well. The only workaround I've been able to find is to create a blank document first and then open the document I wish to open.

---

### Post by Sicadastra on 2011-06-23
I also have the same problem which just popped recently (all documents open on workspace 1 when I clicked it open from workspace 2 or 3). I hope this can be fixed soon because it's a bit irritating.

---

### Post by the_chink_between on 2011-08-05
Hi, me too.  If I open Libre Office Writer from the Nautilus file manager in workspace 1 then the document opens into workspace 2.

Regards

---

### Post by duranl on 2011-08-22
Me five.  It get annoying since I sit there waiting for it to open and then realize that it's been open in another workspace.

---

### Post by linux4me on 2011-08-25
I have the same problem, but found it by right-clicking a Word document someone sent me and choosing "open with." 

There's [a related bug reported on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/778020").

You might want to add yourself to the people affected list.

---

### Post by amber21 on 2011-11-05
I have the same problem. Found a workaround - use unmaximized windows. Drag the frame of the unmaximized window to cover your screen if you find it difficult to work with smaller windows - but do not use maximized windows.

---

### Post by vasa1 on 2011-11-05
Would it be a good idea to merge [another thread]("http://ubuntuforums.org/showthread.php?p=11426815#post11426815") with this one since this one has an earlier first post?

Also, if people are still having problems, it would be worth knowing whether they are accepting updates or have stopped updating for whatever reason. Some of us seem to no longer have the problem.

---

### Post by Sigma1 on 2012-01-16
Hello,
I'm having this self-same problem, which appeared just a day or two ago. The system is up to date (on a machine running 11.04). The CCSM tweaks didn't sort anything out. Reducing the number of desktops to 1 of course removed the problem, but is hardly a solution, since, when you increase them back to 4, the problem reappears. Removing .libreoffice/ is an unsatisfactory and temporary solution, too. Unsatisfactory, because you lose your preferences in libreoffice, and temporary, because despite removing .libreoffice/, the problem is back.
The fact that removing the .libreoffice/ folder works, even temporarily, suggests that this has something to do with the libreoffice preferences, or libreoffice / ubuntu integration, but I can't for the life of see where.
The desktop config is standard: I only installed CCSM to see whether the fix would work, otherwise everything is as it was after the installation.
Any help much appreciated, as always.

---

### Post by Sigma1 on 2012-01-17
Here, for what it's worth, are two fixes.
The first involves not maximising windows as suggested elsewhere. Just a few pixels less than full-screen size is sufficient.
The second, which I find more satisfactory, involves activating the "Put" extension, in "Window Management" in Compiz.
For the time being, with the second fix in place, and windows maximised as normal, things seem to be behaving themselves.

---

