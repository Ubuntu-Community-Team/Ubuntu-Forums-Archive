---
title: "Booting to Random Drives -&gt; Duplicate UUIDS -&gt; How do I change them"
date: 2011-01-19
forum: General Help
---

### Post by b0ot on 2011-01-19
I have been using dd (```
sudo dd if=/dev/drivetoduplicate of=/dev/backuplocation bs=1M
```) to create backups of my ubuntu system. My computer has 2 internal drives and 1 external drive.

I used ```
sudo blkid 
```to find out that all three drives have the exact same UUID which is probably why no matter what is selected in the BIOs it boots to a random drive.

My hope is someone can give a **beginner **friendly **step by step guide** to changing the UUID for the drives in a way that allows them to be uniquely specified in the BIOS.

Also if anyone forsees any other issues I may run into or anything else I might change from the dd backup process please share.

Thanks

**Update 1: **
I attempted to the change the UUID using 
```
 sudo tune2fs -U random /dev/sdc1 
```
which worked and I was able to see that it had changed using blkid
however
```
 sudo tune2fs -U random /dev/sdc5 
```
didn't work

and now when I select my external I'm unable to boot to it.

---

### Post by Aurabolt on 2012-05-19
I googled for the answer to this question, and it brought me here. I didn't see a reply, but I found the solution. 

This happened to me recently on my Debian server after I used the "dd" command.

Try this:

```
sudo ls -l /dev/disk/by-uuid/
```

I got a unique UUID (as I originally expected). Not sure why, but I'm not using "blkid" ever again.

---

### Post by oldfred on 2012-05-19
Your issue is using dd and leaving drives mounted. You can do that if removing drive or copying to a new drive and not using old drive on same system. Each drive is bootable because grub2 & fstab (plus a few more places) have UUIDs embedded.

Other backup methods would be better. I just back up my data with rsync, but if you want a bootable system there are other ways. 

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)


blkid is not an issue, it normally just shows UUIDs of drives.

---

### Post by Cheesemill on 2012-05-19
> **Aurabolt said:**
> I googled for the answer to this question, and it brought me here. I didn't see a reply, but I found the solution. 

This happened to me recently on my Debian server after I used the "dd" command.

Try this:

```
sudo ls -l /dev/disk/by-uuid/
```I got a unique UUID (as I originally expected). Not sure why, but I'm not using "blkid" ever again.

By default blkid reads it's data from a cache file not directly from the device. If the two aren't in sync then blkid can give incorrect readings. To read directly from the device you should use:
```
sudo blkid -c /dev/null
```
or
```
sudo blkid -p /dev/sda1
```
See 'man blkid' for more info.

---

