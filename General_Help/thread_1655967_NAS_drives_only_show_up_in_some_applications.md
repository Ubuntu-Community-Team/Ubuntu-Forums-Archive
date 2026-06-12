---
title: "NAS drives only show up in some applications"
date: 2010-12-30
forum: General Help
---

### Post by drawltx on 2010-12-30
My NAS drives can be accessed by some applications (Nautilus, GIMP - for example) but don't show up for others (calibre, audacity).  If I look at the properties for the drives using Nautilus, I get something like smb://myNAS/photos/.  So, I think this tells me that SAMBA is running and that the drive is mounted.  But where is the mount point and how do I make it show up in the file/directory structure for these other packages when I want to open a file or point to a directory?  

I'm new to ubuntu.  Downloaded and installed 10.10 but when I look at System>About Ubuntu it tells me I am running Ubuntu 11.04 (which hardly seems possible since that would be April, 2011).  Running on AMD Athlon X4.  Network includes WIN7 and OSX machines, plus this Ubuntu box.

Thanks,
drawltx

---

### Post by dcstar on 2010-12-31
> **drawltx said:**
> My NAS drives can be accessed by some applications (Nautilus, GIMP - for example) but don't show up for others (calibre, audacity).  If I look at the properties for the drives using Nautilus, I get something like smb://myNAS/photos/.  So, I think this tells me that SAMBA is running and that the drive is mounted.  But where is the mount point and how do I make it show up in the file/directory structure for these other packages when I want to open a file or point to a directory?  

I'm new to ubuntu.  Downloaded and installed 10.10 but when I look at System>About Ubuntu it tells me I am running Ubuntu 11.04 (which hardly seems possible since that would be April, 2011).  Running on AMD Athlon X4.  Network includes WIN7 and OSX machines, plus this Ubuntu box.

Thanks,
drawltx

[LIST=1]
[*]The 11.04 thing is a bug. It is 10.10.
[*]Nautilus is a Gnome app and other Gnome apps will be able to see the Nautilus mount, non-Gnome apps may not.
[*]You should be able to mount the NAS share directly so all apps can access, install the **pysdm** package and see if that will do the job for you.
[/LIST]

---

### Post by drawltx on 2011-01-03
> **dcstar said:**
> 
[LIST=1]
[*]The 11.04 thing is a bug. It is 10.10.
[*]Nautilus is a Gnome app and other Gnome apps will be able to see the Nautilus mount, non-Gnome apps may not.
[*]You should be able to mount the NAS share directly so all apps can access, install the **pysdm** package and see if that will do the job for you.
[/LIST]


dcstar - Thanks for the response (and explanation).  pysdm shows me my local drives but none of the NAS.  But it gives me a starting place - now that I know that I have to explicitly mount the NAS drives for non-gnome applications.  I appreciate the help!

drawltx

---

