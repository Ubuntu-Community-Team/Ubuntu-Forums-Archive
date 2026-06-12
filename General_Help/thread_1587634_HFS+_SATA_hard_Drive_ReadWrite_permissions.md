---
title: "HFS+ SATA hard Drive Read/Write permissions"
date: 2010-10-03
forum: General Help
---

### Post by chesterlinux on 2010-10-03
So basically my Macbook Pro died about a month ago and I had no way of retrieving the files other than removing the SATA hard drive and placing it in an external case that can be read via USB.  This usb hard drive now mounts on UBUNTU, but folders such as My Documents, Videos, etc do not let me enter I get the following message when trying to enter them: "The Folder Could Not Be Displayed: You Do Not Have the Permissions Necessary to view contents of "Documents""  I was the administrator of my Macbook Pro and I have the password to enter my mac, but no clue how to get it to work via UBUNTU.  How to I change the permissions to enter these folders and get my really important data off of the hard drive?

---

### Post by dcstar on 2010-10-04
> **chesterlinux said:**
> So basically my Macbook Pro died about a month ago and I had no way of retrieving the files other than removing the SATA hard drive and placing it in an external case that can be read via USB.  This usb hard drive now mounts on UBUNTU, but folders such as My Documents, Videos, etc do not let me enter I get the following message when trying to enter them: "The Folder Could Not Be Displayed: You Do Not Have the Permissions Necessary to view contents of "Documents""  I was the administrator of my Macbook Pro and I have the password to enter my mac, but no clue how to get it to work via UBUNTU.  How to I change the permissions to enter these folders and get my really important data off of the hard drive?

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

---

### Post by srs5694 on 2010-10-04
Be aware that any files you copy to a Linux filesystem when using Nautilus as root (as dcstar suggests) will be owned by root. This could have negative consequences in the future. I recommend copying files to a single directory tree and then using the chown text-mode command, with its -R (--recursive) option to change ownership back to your normal user, as in:

```

sudo chown -R chester: /home/chester/copied-stuff

```

This changes the ownership of /home/chester/copied-stuff and all its files and subdirectories to chester. Change the username and directory name as necessary.

---

### Post by chesterlinux on 2010-10-04
Wow this is fantastic Thank you guys so much for all your help :)

---

