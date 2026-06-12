---
title: "Force repair of external hfsplus HD"
date: 2010-11-28
forum: General Help
---

### Post by faal on 2010-11-28
I have an external hfsplus HD that quite frequently gets unmounted uncleanly because of various reasons. Thus I get the following message:

hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.

and every time I have to run fsck.hfsplus to repair. 

Is there some way to force a repair when mounting so i don't manually have to repair? I looked at modifying /etc/mtab but couldn't find anything that would achieve this.

---

### Post by Penguin=) on 2010-11-28
Yeh i had kinda the same problem, but i got it fixed eventually! 

Go to terminal and type:
Code:  **gconf-editor**

Browse to **/apps/nautilus/preferences/media_automount**. 

The **media_automount** key controls  whether to automatically mount media. If set to true, then Nautilus will  automatically mount media such as user-visible hard disks and removable  media on start-up and media insertion. 
There is another key **/apps/nautilus/preferences/media_automount_open**.  This controls whether to automatically open a folder for automounted  media. This key can also be set in the Nautilus (file manager) window.  From the **Edit** menu in Nautilus select **Preferences** and then select the **Media** tab.  
If  set to true, then Nautilus will automatically open a folder when media  is automounted. This only applies to media where no known x-content/*  type was detected; for media where a known x-content type is detected,  the user configurable action will be taken instead. This can be  configured as shown below. :p

Hope this helps =)

---

### Post by faal on 2010-11-28
>  This can be  configured as shown below.

Hm is there supposed to be a picture or something? Unfortunately, I don't see anything.

---

### Post by faal on 2010-12-01
Finally took the time to find a solution to this problem. Recording it here if someone else ever wants to do something similar.

1. Run udevadm info --attribute-walk --name /dev/sdb2

Note: you need to replace /dev/sdb2 with your device.

2. Look at the top under: **looking at device** NOT **looking at parent device**. Store the information somewhere.

3. As root create the following file: /etc/udev/rules.d/10-local.rules. 
E.g. sudo gedit /etc/udev/rules.d/10-local.rules

Paste the following into the file:
ACTION=="add", SUBSYSTEM=="block", SYSFS{model}=="Ext HDD 1021    ", SYSFS{vendor}=="WD      ", RUN+="/usr/local/bin/repair-hfsplus.sh %k", ATTR{partition}=="2"

But replace the information with what you saw in step 2.

4. Create /usr/local/bin/repair-hfsplus.sh.

E.g. sudo gedit /usr/local/bin/repair-hfsplus.sh

5. Paste the following into the file.

#!/bin/sh
echo "Running $1" >> /var/log/repair-hfsplus.log
fsck.hfsplus -r /dev/$1 >> /var/log/repair-hfsplus.log
mount -t hfsplus /dev/$1 /media/External >> /var/log/repair-hfsplus.log

Note: This will mount the device under /media/External if you want to mount somewhere else you need to change this.

6. Add execute to /usr/local/bin/repair-hfsplus.sh.
E.g. sudo chmod +x /usr/local/bin/repair-hfsplus.sh

6. sudo service udev restart

7. Remove the USB cable and plug it back in.

8. cat /var/log/repair-hfsplus.log

You should see something like this:
Running sdb2
** /dev/sdb2
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Rebuilding Catalog B-tree.
** Rechecking volume.
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking Catalog hierarchy.
** Checking Extended Attributes file.
** Checking volume bitmap.
** Checking volume information.
** The volume External was repaired successfully.

The volume should be mounted under /media/External/

---

### Post by Penguin=) on 2010-12-04
> **faal said:**
> Hm is there supposed to be a picture or something? Unfortunately, I don't see anything.

Oh yeah sorry i forgot about that, but it seems you have fixed it now so...

---

