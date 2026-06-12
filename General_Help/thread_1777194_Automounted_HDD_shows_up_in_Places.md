---
title: "Automounted HDD shows up in Places"
date: 2011-06-07
forum: General Help
---

### Post by Ender985 on 2011-06-07
Hello all,

This is kind of a silly question, but I'm curious to know the answer.
 
I recently added a new hard drive to my ubuntu box, and configured fstab to automount it to /home/ender/data, basically copying the settings from my previously automounted /home partiton. The /home/ender/data folder exists and it is not owned by root. 

Fstab now looks like this:
```
# ROOT: / was on /dev/sda5 during installation
UUID=6fc6cc56-80b4-449e-8f5e-333f125d9fe4	/               ext4    errors=remount-ro 0 1
# /home was on /dev/sda1 before
UUID=21ce46b8-f5d0-4b18-869b-c279667f419c	/home           ext4    defaults        0 2
# This is the new HDD
UUID=5dc01c9d-aaf4-4260-87f0-72031cbdc33d	/home/ender/data/	ext4	defaults	0 3
# swap was on /dev/sda6 during installation
UUID=469190bf-719e-4f60-87e6-b09d9c5a6c9c none            swap    sw              0 0
```

and blkid:
```

/dev/sda1: LABEL="new_space" UUID="5dc01c9d-aaf4-4260-87f0-72031cbdc33d" TYPE="ext4" 
/dev/sdb1: UUID="21ce46b8-f5d0-4b18-869b-c279667f419c" TYPE="ext4" 
/dev/sdb5: UUID="6fc6cc56-80b4-449e-8f5e-333f125d9fe4" TYPE="ext4" 
/dev/sdb6: UUID="469190bf-719e-4f60-87e6-b09d9c5a6c9c" TYPE="swap" 

```

My question then is: why does the newly added HDD show up in places (and in nautilus top left menu) as "new_space", while my other automounted partition, /home, doesn't? 

It is not a life-or-death scenario, but I would like it to disappear at least from the nautilus menus, just in case I mistakenly unmount it while trying to unmount a USB or a CD or something.

Thanks!

---

### Post by seawolf167 on 2011-06-07
The reason it shows up as "new_space" is because that was the volume label you gave the drive when you first formatted it.

Your /home partition *does* show up in the Places menu, just in a little different way. All those other folders like Desktop, Downloads, Pictures, Videos, Documents, etc. *are* parts of your /home folder. You can see them by opening a folder and browsing to /home/*your_username *where you will see that they are a part of that folder.

---

### Post by Ender985 on 2011-06-07
Hmm I see... Of course /home does show up in the Places menu and in the nautilus, but under my username, silly me. 

So /home does not have the unmount option in nautilus because it is a 'special folder'. But I take it that if I mount a HDD anywhere else in the file system it will show up regardless? Is there any (easy) way to disable that behavior?

---

### Post by seawolf167 on 2011-06-07
/home doesn't have an unmount option because unless you set up /home on its own partition you cannot separate and unmount it. Either way, you don't want to unmount it :P it contains all your user settings, preferences and files.

As far as I'm aware, any mounted devices (whether automounted or not; usb, PCIe, etc.) will show up under the Places menu.

---

### Post by Ender985 on 2011-06-07
Ok, thanks a lot for the fast answers. I guess I'll have to learn to live with it then xD

Edit: I was trying to mark the OP as [solved] but I do not see a way to do it..
Edit2: Got it!

---

### Post by seawolf167 on 2011-06-07
Glad I could help! Hopefully any other issues you have are this easy to explain/fix :P

---

