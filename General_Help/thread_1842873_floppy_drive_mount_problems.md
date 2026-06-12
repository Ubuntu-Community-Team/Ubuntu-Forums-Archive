---
title: "floppy drive mount problems"
date: 2011-09-12
forum: General Help
---

### Post by johnalexrob on 2011-09-12
A friend of mine is having a problem with an install of Natty I did for him. He is trying to mount some old floppies to copy their contents to a flash drive. The GUI disk utility detected the drive but refused to read it, saying that there was no media in the drive. I read another post about a similar problem that said it may have appeared as something other than /dev/fd0. I checked /dev/sdc, and fdisk said the partition table did not look like one, and when I tried to mount it, it went through with no errors and told me that the mount point was empty and the device was not mounted. The system does not need additional drivers. They do not want to have to reinstall Windows just to read the disks, but I have already gone through everything I can think to do. Any ideas?

---

### Post by coffeecat on 2011-09-12
Yes. The GUI mounting of floppies has been broken for some time unfortunately. But this usually works.

Put a floppy in the drive, open a terminal and:

```
udisks --mount /dev/fd0
```

The floppy will spin up and an icon will appear on the desktop. Double-click on that and you *should* see the contents of the floppy.

If you have only one floppy drive, then it should be /dev/fd0. If the command fails it would an idea to see what the system lists with:

```
ls /dev/fd*
```

Tell your friend that writing to floppies and unmounting them is handled differently in Linux from what he is used to. Sometimes writes are delayed and you must always right-click on the floppy icon and choose unmount/remove/eject or whatever it says (can't remember exactly which) before you physically remove the floppy. You will hear it spin up again, so wait until the noise stops (writes have been committed) and it's then safe to remove the disk.

---

### Post by johnalexrob on 2011-09-13
OK, thanks. I will tell him to try this. I haven't had a chance to use a floppy drive with Linux since the only computer I have with a floppy drive is my server. Any idea why a mount command would go through without any error and then tell me the mount point wasn't mounted afterward?

---

### Post by coffeecat on 2011-09-13
> **johnalexrob said:**
> Any idea why a mount command would go through without any error and then tell me the mount point wasn't mounted afterward?

To be honest, no. The last time I used the mount command for a floppy was in about 2007 with a Gentoo system without a working GUI. I was needing to create an xorg.conf and I had the choice of typing it all out in nano or copying a working one from another system (probably Ubuntu!). I chose the latter. :-s

When your friend has tried the udisks command, can I trouble you to post again with an update? Although it seems to work for most people, I came across a post today from someone for whom it hadn't worked. It would be interesting to know whether it works for your friend. Thanks.

Good luck!

---

### Post by bab1 on 2011-09-13
I believe this has to do with the version of udisks.  I use version *1.0.1-1build1* and have pined it so as to NOT update.

See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1511446&page=4") for more information.

---

### Post by johnalexrob on 2011-09-16
Still trying to get back to him, he forgot to call me last night(this is where ssh would realy help) but I will get him to do it tonight and should have an answer by tonight or tomorrow.

---

### Post by johnalexrob on 2011-09-18
Thanks for the help. udisks did the trick for him. The disks mounted fine and he did not have to switch back to the other OS just to read them. I still wonder why a regular mount command couldn't mount them, but it doesn't really matter now since everything has been copied from them.

---

### Post by coffeecat on 2011-09-18
Thanks for the update and I'm glad udisks worked.

---

