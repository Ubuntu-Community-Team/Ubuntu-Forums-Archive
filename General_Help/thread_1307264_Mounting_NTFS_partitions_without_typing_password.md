---
title: "Mounting NTFS partitions without typing password"
date: 2009-10-31
forum: General Help
---

### Post by oblador on 2009-10-31
Hi,

In Ubuntu 9.10, everytime I want to mount a NTFS partition (by clicking on it) I'm asked to type password and confirm. What can I do to just click and mount without typing any password?

Thanks.

---

### Post by howefield on 2009-10-31
Have a look here..

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

ntfs-config should give you the ability to mount your drive automatically when you boot up.

You can manually add the drive to your fstab file if you prefer, ntfs-config gives you a simple gui for it though.

---

### Post by bashphoenux on 2009-10-31
download pysdm

```
 sudo apt-get install pysdm
```
and then 
type pysdm as root !!
a window will appear , select the ntf partition and to the right you will see 'Mount' button. click on it! 
and from the next you boot in you will find the partition mounted for rest of your life :)

---

### Post by oblador on 2009-10-31
but I don't want NTFS partitions to be automatically mounted. What I do want, however, is just being able to mount it as a common user without having to type my password.

---

### Post by WorLord on 2009-11-02
> **oblador said:**
> but I don't want NTFS partitions to be automatically mounted. What I do want, however, is just being able to mount it as a common user without having to type my password.

Or, at least, have Nautilus remember the password.  Why is it this dialog doesn't have the remember / for this session only checkboxes?  That looks like a regression to me.

---

### Post by oblador on 2009-11-03
Yes, I couldn't find an option for the password to be remembered, so I decided to mount my ntfs partitions automatically at system boot.

Thanks for helping.

---

### Post by przetyczce on 2009-11-16
Try this 
[http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic](http://www.shareconnector.com/howto-remember-authentication-mounted-drive-in-ubuntu-910-karmic)
It work for me ;)

---

