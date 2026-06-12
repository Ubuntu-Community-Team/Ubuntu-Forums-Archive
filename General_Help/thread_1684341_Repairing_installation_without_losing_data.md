---
title: "Repairing installation without losing data?"
date: 2011-02-09
forum: General Help
---

### Post by methos3 on 2011-02-09
I have Ubuntu 10.10 installed on my computer (no other OS) and it wont boot up. I don't want to lose the files in my documents. I tried accessing them using a live CD and then copying them from the harddrive (home folder then 'richard' then documents then tried to open the folder but I dont have permission to and there seems to be no way of changing this.

The files are definitely on my harddrive but I dont seem to have a way of accessing them!

Is there anyway of either accessing them and copying them to a usb etc or repairing my installation of ubuntu without erasing the files in my documents? Opening in recovery mode etc wont work.

---

### Post by Primefalcon on 2011-02-09
alt+f2 to open a dialog box, type gksudo nautilus, this will open a file browser with root power, you should be able to copy them then

---

### Post by methos3 on 2011-02-09
Thanks,

Unfortunately this hasnt worked. I cant access the file system of the computer harddrive from the window that is created (it only brings up the file system for the live disk) if I open a new file browser for the harddrive it wont work.

Any ideas on how to repair the original installation?

---

### Post by dcstar on 2011-02-09
> **Primefalcon said:**
> alt+f2 to open a dialog box, type gksudo nautilus, this will open a file browser with root power, you should be able to copy them then

Or install the "Open as Administrator" Nautilus add-in package: **nautilus-gksu** in the Live session.

---

### Post by Primefalcon on 2011-02-09
in the nautilus windows that was opened, go to the go menu, your drive should be in there under something like 650gb (whatever the size of your hard drive or partition is) filesystem or something

---

### Post by Primefalcon on 2011-02-09
or once your mounted the drive with an ordinary (non root window), open up the root window and go to /media and your drive should be in there

---

