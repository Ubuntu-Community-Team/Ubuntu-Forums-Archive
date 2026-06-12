---
title: "OpenOffice.org Base Reports"
date: 2010-01-27
forum: General Help
---

### Post by nathanhammontree on 2010-01-27
I am using OpenOffice.org Base version 3.1.1.  
I am using Ubuntu 9.10
I am using JRE: Sun Java 1.6.0_15

These are all the most current from what I have found.  Everything is working and I was able to build my database, forms, add data, create queries, etc.  I thought I would be able to run a report wizard, get kinda close, then modify the report design to make it what I really wanted....  NOPE.  If I make even a tiny change the whole report is ruined and has no data.  Furthermore, I don't see any way to create a blank report and/or add or remove fields.

So I installed the Sun Report Builder 1.1.0.  

The report builder will not launch.  It added the Create Report in Design View option all right, but it does nothing.  My DB crashses if I even try to modify a report.

Is there a better tool for building reports?  All the data in the world is  useless if we can't organize and evaluate it.  This DB ap has been around for quite some time, so it must be useful to someone.  I have a lot of Access experience, but this is not working for me at all.

---

### Post by Hagar Delest on 2010-01-30
For an extensive use of Base, better use the Sun version IMHO: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by nathanhammontree on 2010-01-30
Through some trial and error, and some help from other UBUNTU users I found the following for any of you who have similar problems.
 
The install instructions for OOo extensions won't work for the UBUNTU OOo install. If you followed the instructions and downloaded and installed an extention from the extension manager, do the reverse and remove it/them.
 
open Terminal
swithch to super user: su 
and enter the password
then use aptitude to get the extention: aptitude install openoffice.org-report-builder
then type exit two times to close terminal
 
Then you can open Base and it should be working. You can find extensions using aptitude: aptitude search openoffice.org will give you a list. 
 
Thanks to everyone for their help.

---

