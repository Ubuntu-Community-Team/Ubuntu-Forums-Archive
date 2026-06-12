---
title: "OSX sees but wont access shared USB HDD on Ubuntu"
date: 2011-03-16
forum: General Help
---

### Post by 8dogsbarking on 2011-03-16
This is a strange issue.  I have three computers; Ubuntu desktop, Windows 7 laptop, and OSX laptop 10.5.8.  I have a shared usb hard drive on my Ubuntu desktop.  My Windows 7 machine sees and accesses it just fine.  My OSX computer sees it in the finder window, but says it can't access it because it can't find the original file.  I have tried to "repair the alias" but it doesn't work.  I have shared another folder on the Ubuntu desktop, but the new share is on the desktop internal hard drive.  OSX can access that share with no problems.  What in the world is going on?  If Windows 7 can see and access, is this an OSX problem or is there a terminal command that I am missing?  I am networking using Samba on the Ubuntu computer and the explorer/finder windows on the Windows7/OSX computers.  Please, any help would be appreciated so I don't have to abandon my Ubuntu!

---

### Post by 8dogsbarking on 2011-03-24
Got it fixed.  It seems that OSX will only read computer names that are less than 15 characters long.  But NOW, I can't get my Windows 7 machine to see the shared USB hard drive.  O well

---

