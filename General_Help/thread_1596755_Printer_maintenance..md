---
title: "Printer maintenance."
date: 2010-10-14
forum: General Help
---

### Post by Extreedoc on 2010-10-14
Well, I've had Ubuntu for two years come next March, it has been totally reliable and I won't be going back to Windows but one thing perplexes me and I haven't found the answer: How do you maintain your printer? Windows has printer status and maintenance software and Linux doesn't. How do you know when the cartridges are getting low, how do you clean the printer head or realign it? I have to boot in Windows, yes, I still have it on a second hard drive, in order to carry out these occasionally essential tasks. Seriously, how do you manage your printer maintenance?
I have an old Epson 680.

---

### Post by Schrute Farms on 2010-10-14
I don't have your printer, but I can tell you what mine does, if it's any help.

I have an old HP deskjet 932C.  I go to System/Administration/Printing.  Then I right click and select properties on my printer.  Toward the bottom of that window, there is a button for Clean Print Heads on my printer.  (I've never used it though).  There is also a selection on the left for Check ink/toner levels.  It does not report for my printer, although it will in Windows.

So check there.  Those things just might not be written into the Linux drivers.

---

### Post by todak on 2010-10-14
See [here]("http://ubuntuforums.org/showthread.php?t=1415955") for the answers you seek! :)
After doing some research I discovered that your printer is  supported with the *mtink* program, available in the repositories.

---

### Post by Extreedoc on 2010-10-14
Thanks guys, I'll check these out.

---

### Post by Extreedoc on 2010-10-15
> **todak said:**
> See [here]("http://ubuntuforums.org/showthread.php?t=1415955") for the answers you seek! :)
After doing some research I discovered that your printer is  supported with the *mtink* program, available in the repositories.

So if I install mtink... what will it do? My printer is working with the CUPS driver, will mtink be compatible with CUPS?

---

### Post by Extreedoc on 2010-10-16
Ok, I've installed mtink and associated files but it seems that mtink does not have enough right for accessing the device files. I have to be a member of the "lp group". I assume this is the lpadmin group? How do I proceed?

---

### Post by todak on 2010-10-18
> **Extreedoc said:**
> Ok, I've installed mtink and associated files but it seems that mtink does not have enough right for accessing the device files. I have to be a member of the "lp group". I assume this is the lpadmin group? How do I proceed?
Go to *System> Administration> Users and Groups*. Click on *Manage Groups* button. Scroll down to the *lpadmin* entry and double-click on that. It should show your user name with a check in the box beside your name. Click *OK> Close> Close*. It should work now, although I had an Epson printer and had to use the command *sudo mtink* (or *gksu mtink*, I don't recall if the GUI was gtk or not) for it to work. I even tried stylus-toolbox with the escputil backend with my Stylus C66 and still had to be root or sudo to read the ink levels or do any maintenance on the printer. Apparently it is peculiar only to Epson printers.

---

### Post by Extreedoc on 2010-10-20
> **todak said:**
> Go to *System> Administration> Users and Groups*. Click on *Manage Groups* button. Scroll down to the *lpadmin* entry and double-click on that. It should show your user name with a check in the box beside your name. Click *OK> Close> Close*. It should work now, although I had an Epson printer and had to use the command *sudo mtink* (or *gksu mtink*, I don't recall if the GUI was gtk or not) for it to work. I even tried stylus-toolbox with the escputil backend with my Stylus C66 and still had to be root or sudo to read the ink levels or do any maintenance on the printer. Apparently it is peculiar only to Epson printers.

Thanks todak, I did as you suggested and I can at last use mtink but as you said, I have to use sudo. I don't mind a bit though as it's a lot easier than booting into Windows to do the job.

---

