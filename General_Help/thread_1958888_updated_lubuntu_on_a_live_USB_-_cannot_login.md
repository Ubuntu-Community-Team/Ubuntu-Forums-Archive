---
title: "updated lubuntu on a live USB - cannot login"
date: 2012-04-15
forum: General Help
---

### Post by Linux_junkie on 2012-04-15
I have Lubuntu 11.10 installed on a 2GB USB memory stick and up until yesterday when I foolishly decided to see if I can update it I have have a few problems the first was that it ran out of disk space.

After shutting it down for the night I wanted to load it back up and remove all unnecessary files to free up disk space, however, upon booting up I now get the login screen asking for a user id and password.  As far as I know I did not set up a user ID and password for this live USB system.

Before the update it logged in automatically using ubuntu as the user.  Have tried this and will not log in.

For further info, before I updated the live USB I installed clamAV and Magicfiles because I wanted to use it as a recovery disk. Now I need a recovery disk to recover this disk! lol

---

### Post by Strojar on 2012-04-15
live usb has a "problem". you canot actualy remove programs that are preinstalled in the distro, and anny bigger upgrade will take out all of your free space on such small drives. to reclaime your space you just need to make a new casper-rw, but you will lose everything that you changed ond the live usb:
[http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)
[http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/)

about the login part, i encounter the same problem when reusing an old casper-rw file on the same distro, after booting from live usb it asks me username and password.

---

### Post by Linux_junkie on 2012-04-15
> **Strojar said:**
> live usb has a "problem". you canot actualy remove programs that are preinstalled in the distro, and anny bigger upgrade will take out all of your free space on such small drives. to reclaime your space you just need to make a new casper-rw, but you will lose everything that you changed ond the live usb:
[http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)
[http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/)

about the login part, i encounter the same problem when reusing an old casper-rw file on the same distro, after booting from live usb it asks me username and password.

Thanks for the reply.  I had a feeling I had to re-install from the LiveCD on to the USB.  This I now have down, and have installed some extra packages to make the liveUSB in to a recovery disk.

I won't attempt to update on a liveUSB again. Lesson learnt.

---

