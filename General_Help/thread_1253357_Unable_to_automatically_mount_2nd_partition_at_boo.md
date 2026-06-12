---
title: "Unable to automatically mount 2nd partition at boot"
date: 2009-08-30
forum: General Help
---

### Post by aeternitas on 2009-08-30
Hello,

         I'm having trouble with getting the 2nd partition of my hard drive to mount on boot; as far as I can tell, I've gotten it added to fstab correctly (after quite a bit of trial, error, and restarts):

```
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=290760b8-6221-4ba6-b1bf-a45c4ac4f100 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5c958b42-c0dc-4a36-a073-5c034357e590 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**/dev/sda3        /media/storage  ext3   auto,rw,user 0       0**
```It's more of a convenience thing, not wanting to go through the hassle of re-mounting every boot, but I'm not sure what I'm missing/not doing right.  Any suggestions?

---

### Post by Megamanic on 2009-08-30
My guess is that the line should read:-

/dev/sda3        /media/storage  ext3   rw,user 0       0

You put in two file systems ext3 & auto then a comma that you don´t need

Try that & if you get no joy swap auto for ext3 & see if that works.

Don´t forget to backup your fstab file too :)

good luck

---

### Post by hal10000 on 2009-08-30
Hi,
you should use UUID=your_sda3_UUID instead of /dev/sda3 in the first column of your fstab-entry.
the correct entry to mount sda3 at boottime is then:
> 
UUID=XXXXXXXXXXXXXXXX    /media/storage    ext3    relatime    0    2

The UUID for /dev/sda3 can be found with the command [COLOR="Red"]blkid[/COLOR].

If you want to make the partition writeable (for a normal user), just use [COLOR="Red"][COLOR="Red"]sudo chmod o+w /media/storage[/COLOR][/COLOR] to give you write-permissions.

---

