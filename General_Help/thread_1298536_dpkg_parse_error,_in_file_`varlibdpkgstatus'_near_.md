---
title: "dpkg: parse error, in file `/var/lib/dpkg/status' near line 5 missing package name"
date: 2009-10-22
forum: General Help
---

### Post by marco77 on 2009-10-22
Hi,
after today Ubuntu downloaded the new upgrades, it was not able to install one and now I cannot start it.
After a few hours in the forum I realized my problem is dpkg. I did everything. After I 
dpkg --configure -ait says :
*dpkg*: parse error, in file `/*var*/*lib*/*dpkg*/*status*' *near line* *5 **package* *missing package name*
E:Encountered a section with no Package: header, 
 E:Problem with MergeList 

I did dpkg --clear-avail or apt-get update or aptitute or other things. Nothing.
Any help please? 
Thanks
[EMAIL="marco77au@yahoo.com.au"]marco77au@yahoo.com.au[/EMAIL]

---

### Post by seanlynch on 2009-11-06
> **marco77 said:**
> Hi,
after today Ubuntu downloaded the new upgrades, it was not able to install one and now I cannot start it.
After a few hours in the forum I realized my problem is dpkg. I did everything. After I 
dpkg --configure -ait says :
*dpkg*: parse error, in file `/*var*/*lib*/*dpkg*/*status*' *near line* *5 **package* *missing package name*
E:Encountered a section with no Package: header, 
 E:Problem with MergeList 

I did dpkg --clear-avail or apt-get update or aptitute or other things. Nothing.
Any help please? 
Thanks
[EMAIL="marco77au@yahoo.com.au"]marco77au@yahoo.com.au[/EMAIL]

You have an error in the file '/var/lib/dpkg/status'. It is near line 5.
This thread
[http://ubuntuforums.org/showthread.php?t=474587](http://ubuntuforums.org/showthread.php?t=474587)
shows how you can use the backup apt makes to restore a working copy.

If this does not work

post the lines from your file around line 5 and I'll see if I can spot the error causing the parse error.

Sean

---

