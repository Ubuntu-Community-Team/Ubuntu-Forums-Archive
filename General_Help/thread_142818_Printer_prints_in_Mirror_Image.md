---
title: "Printer prints in Mirror Image"
date: 2006-03-11
forum: General Help
---

### Post by pgunsul on 2006-03-11
I have a most aggravating problem with an HP printer.  Here's the situation.  I have a small network here at home consisting of 2 Ubuntu boxes and 1 XP box.  The HP deskjet is attached to one of the Ubuntu boxes, and it is shared with the other two computers.  Printing from the local ubuntu machine is fine, printing from the other Ubuntu machine is fine.  However, printing from the XP computer yields a mirror image of whatever I am printing.  There is communication to the printer, and there are no error messages, but everything I print from the XP box is mirrored.  I looked around at the settings on the Windows machine and discovered an option for mirror image.  It was not checked.  So I checked it just to see what would happen.  There was no change in the output.  Checking that box or unchecking that box does not change anything!  Anyone have any ideas??  Again printing from both Ubuntu machines is fine, and everything printed from Windows is mirrored (even windows test pages and printer test pages sent from XP).

---

### Post by pgunsul on 2006-03-13
Anyone have any ideas?  I would really appreciate some help!  ;)

---

### Post by learning curve on 2006-03-13
Try uninstalling and then re-installing the Printer on the XP machine and make sure you have the correct driver.

If you strike me down, I shall become more powerful than you can possibly imagine.

Learning Curve:)

---

### Post by pgunsul on 2006-03-17
Ok, I tried that.  I downloaded the newest driver from hp and the printer is still printing in mirror image.  I also tried it from another windows machine on the network and it has the same issue.  So to recap, I can print fine from the Ubuntu boxes, but mirrored on both XP boxes...  I've tried searching Google and other forums, but no luck...  I can't be the only person with this problem, can I?  :)

---

### Post by ramforth on 2006-09-30
You are not the only one.
I just got a HP Deskjet connected to my Ubuntu LAMP server.
And you know what? From one of the XP-boxes, the print is mirrored.
I have 1 Ubuntu Dapper and 1 XP Laptop connected in addition to the XP Box, and they print just fine.

](*,)

---

### Post by ramforth on 2006-09-30
I have sent a request for info to HP. If they can provide some usefull information, I will gladly share it.:)

---

### Post by janascii on 2007-03-06
I was also having this problem... first I was printing directly to CUPS and it was mirrored.  Then i switched it so that XP connected to the printer through samba and now it prints fine

---

