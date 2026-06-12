---
title: "rhythmbox starts at startup"
date: 2010-01-09
forum: General Help
---

### Post by libihero on 2010-01-09
rhythmbox isnt one of my startup programs, but for some reason it starts up every time i boot my computer.  i even downloaded bootup manager and its not on that list either...

---

### Post by happyhamster on 2010-01-09
Take a look at System-->Preferences-->Removable Drives and Media-->Multimedia if rhythmbox is listed there. If so, de-select. Or perhaps System-->Preferences-->Removable Drives and Media-->Storage and untick the Auto-run and/or Auto-open options.

Good luck.

---

### Post by michy99 on 2010-01-09
Go to System->Preferences->Startup Applications. Click on Options tab. Make sure that 'Automatically remember running applications when logging out' is selected. Close all application and log out. When you log in again, go back and UNSELECT 'Automatically remember running applications when logging out.'

---

### Post by ajgreeny on 2010-01-09
You may have shutdown at some time with Rhythmbox still running in the system tray, and for some reason saved the session at shutdown.

Try closing everything, so there are definitely no programs running, then going to System->Preferences->Startup Applications->Options tab, and in there, just for once, enable the "Automatically remember ...... loging out".  Now log out, and back in again.  Hopefully there will be no unwanted applications running.  If all is OK, go back to System->Preferences->Startup Applications->Options tab and disable the "Automatically ..................".

Now hopefully there will be no unwanted applications running when you startup the machine from that time on.

EDIT:
Too slow.  I hope we were right!

---

### Post by libihero on 2010-01-09
worked! thanks :)

---

