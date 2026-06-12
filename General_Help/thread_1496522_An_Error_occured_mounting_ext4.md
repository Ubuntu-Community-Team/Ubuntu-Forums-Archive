---
title: "An Error occured mounting ext4"
date: 2010-05-29
forum: General Help
---

### Post by randallsstevens on 2010-05-29
When booting up I get the error, "an error occurred mounting ext4, press S to skip or M for manual recovery" .

If I skip, ubuntu boots and functions perfectly. Pressing M takes me to a terminal which says: Filesystem moun or check failed. A maintenance shell will now be started. Press CTR-D to skip. Give root password, which I did. But after that nothing happens?

How do I get rid of this screen ?

Thanks, 

-Linux noob

---

### Post by randallsstevens on 2010-05-30
Nobody have any ideas ? :)

---

### Post by Hazbeen on 2010-06-01
I've got the same problem "an error occurred while mounting 0", ever since installing Lucid Lynx. No other problems so can't complain. Anyone else?

---

### Post by doas777 on 2010-06-01
and mine, when mounting my / partition, is 
"Error Mounting 'errors=remount-ro'".

so it seems clear what the issue is, but not the fix.
an fsck on / (when unmounted of course) yeilds no issues and a clean volume. if i add -f to fsck, it runs the scan but finds no errors.

as for the message, look at your /etc/fstab file.

it is defined as such:
```

UUID=c36420d9-2fc0-4012-bfeb-4fe23d78b430 /               ext4    errors=remount-ro 0       1

```where '/' is the mount point (the token that that message shoudl read), 'ext4' is the filesystem type, 
'errors=remount-ro' are the options, and '0 1' are the scanning options. 

it appears to be confusing the columns, in my case missing by 2 to the right, and in each of yours more than just 2.

perhaps replacing all the tabs with spaces in the fstab will correct the issue. not sure if the problem we are seeing is a bug in the error message, or a message that indicates the original problem though.

most infuriating to have a readonnly root though, as you have to boot from a live cd to save changes to fstab.

---

### Post by Hazbeen on 2010-06-06
I reinstalled from an iso file on disc this time, rather than update from the website, and it fixed my fstab file.

---

