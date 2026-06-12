---
title: "issue booting"
date: 2010-02-06
forum: General Help
---

### Post by dbowlin17 on 2010-02-06
when I boot into ubuntu i am told:

cannot yet be mounted swap:waiting for UUID:edc49d1a-e68d-4e08-b7a6-a550F4c0b

I then press escape to boot into recovery. This has happened since making the machine tri-boot windows xp and 7. I read things off of the linux partiton on windows. What could be causing this, or what should I do?

---

### Post by bill olsen on 2010-02-06
I've got a temporary fix that allows me to boot, but has not really gotten to the root of the problem. There is a thread about this somewhere on the forum, but I've lost it just now.  The jist is that "blkid" can't get the UUID information from some file because something is duplicated in it.  Yeah, I really know what I'm talking about!

Here is the temporary fix (I will be a little vague because I'm not sure if this is a great idea, and I don't want to enable other novices to do something wrong.)
- Note the problem UUID number in the error message.
- Launch Ubuntu from live CD.
- Manually mount the problem partition from a terminal, and cd to /etc
- Backed up /etc/fstab  
- Edited /etc/fstab (sudo gedit fstab)
- . Replaced the problem line "UUID = ###  stuff" with "/dev/sda5 stuff" 
      - . . (where "stuff" is everything that comes after the uuid value.)
- Save fstab, and reboot

---

### Post by oldfred on 2010-02-06
bill has it right, but if you have duplicate UUIDs it is a different problem. Should not get duplicate UUIDs but you can if you copy a partition. 

You probably deleted swap and recreated it or other partition changes that changed the UUID of swap

To see UUID's
sudo blkid
or
ls -l /dev/disk/by-uuid/

To edit fstab

gksudo gedit /etc/fstab

---

### Post by dbowlin17 on 2010-02-13
somehow i didn't do anything but it has been working. thanks...

---

