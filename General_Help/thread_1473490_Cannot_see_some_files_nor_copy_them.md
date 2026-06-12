---
title: "Cannot see some files nor copy them"
date: 2010-05-05
forum: General Help
---

### Post by enzominator on 2010-05-05
Hi - I am upgrading a QNAP NAS - the unit only had 1 drive to begin with. I have taken this original drive out and hooked it to my ubuntu system and when I boot my machine ubuntu sees the volume that was the volume the qnap shared. and it sees MOST of the files. but when I go to copy stuff it gives errors stating things like 'can't copy data2.cab' - when I go the directory where it claims it can't copy data2.cab there is no data2.cab. 

Thing is I am pretty sure there *IS* a data2.cab ... just that the rights or something are such that I cannot see / copy it.

is there a simple command I can run on the *entire* drive that will set the ownership of ALL files so that I can see and move them?  I just need to copy all these files over to the upgraded nas and then I can reformat this drive.

Thanks for all the help in advance!

---

### Post by dino99 on 2010-05-05
to find your file: install "locate" with synatic. Then into console: locate your-file

will return all "your-file" found over the system

[http://www.qnap.com/pro_application.asp?ap_id=135](http://www.qnap.com/pro_application.asp?ap_id=135)

[http://forum.qnap.com/viewtopic.php?f=35&t=28638](http://forum.qnap.com/viewtopic.php?f=35&t=28638)

---

### Post by MooPi on 2010-05-05
Locate the directory 
```
chown -R yourname /directory/location
```

---

### Post by enzominator on 2010-05-05
> **MooPi said:**
> Locate the directory 
```
chown -R yourname /directory/location
```

Edit- Yeah, the R is recursive ... Thank you!

---

