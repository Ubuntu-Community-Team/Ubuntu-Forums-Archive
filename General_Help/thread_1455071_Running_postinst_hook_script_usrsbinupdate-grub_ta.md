---
title: "Running postinst hook script /usr/sbin/update-grub taking a long time?"
date: 2010-04-15
forum: General Help
---

### Post by carn1x on 2010-04-15
Hi,

Running first upgrade after installing 9.10.

Currently on item "Configuring linux-image-2.6.31-20-generic" and the progress bar/terminal readout has not changed for an hour or so I'd say.

Don't want to cause issues by killing it halfway through, especially as it presents an opportunity to learn something!

Any advice please?

---

### Post by carn1x on 2010-04-15
Ok it's finally come up with:

error: cannot open '/dev/sdb' while attempting to get disk size

Which I've had before, and solved by removing the 

/dev/sdb 

entry from /boot/grub/device.map

All I need to do now is wait for the error message to hit again (could be a long night) and then hopefully it will read over device.map and get back on track. Atleast I think that's what happened last time I hit that error :S

This is twice I've had this problem now, and as far as I can tell it seems to be seeing the original LiveUSB that created the installation as /dev/sdb and shoving it into Grub. Is there a reason for this?

Thanks for any help!

---

### Post by carn1x on 2010-04-15
Yeh after making the change above, got up in the morning and it had successfully moved on.

---

