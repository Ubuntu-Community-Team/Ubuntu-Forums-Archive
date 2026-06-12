---
title: "Can't import Thunderbird profile"
date: 2009-09-22
forum: General Help
---

### Post by mibadt on 2009-09-22
Hi,
I recently moved to Kubuntu from another distribution where I've been using the Thunderbird mail client. (I've kept my former /home partition).
Although I've followed Mozilla's guidelines, I can't manage to configure my newly installed Thunderbird (ver 2.0.0.22) to open my **existing** profile(mail, news, address book atc.)hpi7do2r.default.

Please advise!

Thanks

Michael Badt

---------copy of ~/mozilla-thunderbird contents--------

bash-4.0$ ls -l
total 954860
drwx------ 5 miki miki      4096 2009-09-21 14:06 hpi7do2r.default
-rw-r--r-- 1 miki miki        95 2009-09-22 12:50 profiles.ini
-------------end-----------

---------copy of my profiles.ini (there)------------
[General]
#StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=hpi7do2r.default
-------------end-------------

---

### Post by scouser73 on 2009-09-22
The Thunderbird profile can be found by showing the hidden files, to do this please follow the steps.

**1** - Go to **/home/yourname**

**2** - Press **CTRL & H** to open the hidden files & folders

**3** - Now you can see the file **/home/yourname/.mozilla-thunderbird**

***Now say for instance that you wish to move your existing Thunderbird profile to a new hard drive.***

**1** - Install Thunderbird on your new drive.

**2** - Now open the newly installed Thunderbird & then close it immediately

**3** - Now go to the newly made Thunderbird folder: **/home/yourname/.mozilla-thunderbird** and delete all the contents inside the newly created folder but not the folder itself

**4** - Now paste your existing Thunderbird profile into **/home/yourname/.mozilla-thunderbird**

**5** - Start up Thunderbird, and now you will see all your email accounts, contacts & emails

---

### Post by malimrav on 2009-09-22
right click to icon and to command copy this:thunderbird %u -Profilemanager, now you can edit/delete/import profiles

---

### Post by mibadt on 2009-09-22
Thanks,
You've helped me solve the problem!
Michael Badt

---

### Post by kowsik on 2009-09-25
Thanks for the instructions. This worked without any problem.

---

