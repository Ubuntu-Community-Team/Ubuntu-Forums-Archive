---
title: "Is it possible to have USB port appear as drive?"
date: 2011-11-13
forum: General Help
---

### Post by jtgd on 2011-11-13
(I didn't see a storage subgroup so posting to general)

I just got a Toshiba Thrive tablet and am quite disappointed that the mini USB port is MTP only, and mtp-tools/qlix does not work. The only way I can transfer files now is with FTP over WiFi (or with my VirtualBox WinXP. UGH!). But the Thrive does have a USB-A port for thumb drives.

So I am wondering if software exists that will do what I want. (if not, I wish someone would write it :)

It would be nice if I could connect my USB port on Ubuntu to the USB port on Thrive and have my Ubuntu machine (mount point or directory tree) appear as a USB flash drive to it.  Is it possible?

(or any other Thrive/MTP advice is welcome as well)

Thanks everyone!

---

### Post by Cyclane on 2011-11-13
Googling for 'linux mtp mounting' gave me this: [http://www.anythingbutipod.com/forum/showthread.php?t=32817](http://www.anythingbutipod.com/forum/showthread.php?t=32817)

Is this what you where looking for?

---

### Post by jtgd on 2011-11-14
Thank you.

I followed those instructions (although naming it /media/Thrive) and this step failed:

sudo mtpfs -o allow_other /media/Thrive/
fuse: bad mount point `/media/Thrive/': Transport endpoint is not connected

Not sure if it is significant, but lsusb shows:

Bus 001 Device 033: ID 18d1:7102  

(blank, with no name)
for the Thrive device.

(if it matters I am running Lucid)

---

### Post by jtgd on 2011-11-14
I see here:
[http://alldroid.org/tabid/40/g/posts/t/1125/Mount-Internal-Storage-of-Xoom-inhttp://alldroid.org/tabid/40/g/posts/t/1125/Mount-Internal-Storage-of-Xoom-in-Ubuntu.aspx-Ubuntu.aspx]("http://alldroid.org/tabid/40/g/posts/t/1125/Mount-Internal-Storage-of-Xoom-inhttp://alldroid.org/tabid/40/g/posts/t/1125/Mount-Internal-Storage-of-Xoom-in-Ubuntu.aspx-Ubuntu.aspx")

"Others have gotten it to work on 10.04 but the mtpfs package is broken in Lucid and you will have to compile it from source yourself."

Well, maybe it's time to upgrade.... :(

---

