---
title: "Ubuntu Mounting Question"
date: 2012-03-18
forum: General Help
---

### Post by nato85 on 2012-03-18
Hey Guys

Quick question

I plugged in a USB Hard Drive to the computer and its come up as /dev/sdd1

How can I get this to be shown as /dev/sdc1

I am running a backup script that needs it to be sdc1 instead of sdd1

Please help

---

### Post by nato85 on 2012-03-18
was not too sure if this is in right area?

---

### Post by Rodney9 on 2012-03-18
I think it would be easier to change the script.

---

### Post by mikewhatever on 2012-03-18
> **Rodney9 said:**
> I think it would be easier to change the script.

Indeed, and while at it, you should change it to use the UUID, in other words, /dev/UUID.

---

### Post by redmk2 on 2012-03-18
> **nato85 said:**
> Hey Guys

Quick question

I plugged in a USB Hard Drive to the computer and its come up as /dev/sdd1

How can I get this to be shown as /dev/sdc1

I am running a backup script that needs it to be sdc1 instead of sdd1

Please help

When you refer to the partition in a script you should use the UUID (Unique Universal I.D.).  See [**_[COLOR="Blue"]here[/COLOR]_**]("https://help.ubuntu.com/community/UsingUUID") and [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/") for more info.

---

### Post by nato85 on 2012-03-19
normally i would agree with you, but when there is a USB hard drive rotation every night for backup, when i plug in the next drive, it will go back to SDC1, it only seems to be 1 drive thats SDD1

---

### Post by redmk2 on 2012-03-19
> **nato85 said:**
> normally i would agree with you, but when there is a USB hard drive rotation every night for backup, when i plug in the next drive, it will go back to SDC1, it only seems to be 1 drive thats SDD1

If you have multiple drives and one script then I would use volume labels to name the drives (i.e. *backup*)  The only caveat is that you can't have 2 of them plugged in at the same time.  A second method would be to have the script query for the UUID or volume label and mount by that ID.

Here is come info on drive labels:
[_[COLOR="Blue"]https://help.ubuntu.com/community/RenameUSBDrive[/COLOR]_]("https://help.ubuntu.com/community/RenameUSBDrive")

---

