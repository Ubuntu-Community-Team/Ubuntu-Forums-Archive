---
title: "Mounted Linux Partion not visible"
date: 2011-10-05
forum: General Help
---

### Post by fantab on 2011-10-05
I had an extra free partition formatted with ext4. I mounted it and gave the necessary permissions, I mounted it as **/storage**. I tried opening it from the terminal: *nautilus /storage* and nautilus opens it. So far so good.

I followed **[these instructions]("http://www.psychocats.net/ubuntu/mountlinux")** to mount the Linux partition.

However, when I open "Computer" the Device is not visible; it is neither shown in the unity panel nor can I access it without terminal. When I open the Home folder normally, the device is not listed in the sidebar-places.

**I want /storage to be visible and normally accessible as other partitions are... without the aid of the terminal.**

**What should I do?**

---

### Post by searchfgold6789 on 2011-10-05
Mount it under /media/storage instead of just /storage.

---

### Post by fantab on 2011-10-05
> **searchfgold6789 said:**
> Mount it under /media/storage instead of just /storage.

[B]Do I have to unmount it first ie undo what I did? If yes, then how do I do it.

or 
should just repeat the procedure with /media/storage?[/B]

---

### Post by Bucky Ball on 2011-10-05
Unmount. Delete /storage. Create new mount point /media/storage.

---

### Post by fantab on 2011-10-05
> **Bucky Ball said:**
> Unmount. Delete /storage. Create new mount point /media/storage.

How do I unmount it?

---

### Post by Bucky Ball on 2011-10-05
```
sudo umount /storage
```

---

### Post by Morbius1 on 2011-10-05
> However, when I open "Computer" the Device is not visible;
No mounted partition is visible when you open "Computer" - Well, except "File System"

---

### Post by typal on 2011-10-05
Make a new directory, /media/storage
```
sudo mkdir /media/storage
```

Then make sure you update the mount point in etc/fstab. 

Then, unmount, like BB said,
```
sudo umount /storage
```

Then, mount it again in the "right" spot
```
sudo mount -a
```

Then, delete your /storage folder.

Then, whenever you boot, it should auto mount that drive at /media/storage.

---

### Post by Morbius1 on 2011-10-05
And if you are keeping it mounted at /storage just use:
```
nautilus /storage
```And when it opens up bookmark it: Bookmarks > Add bookmark. It will show up on the left pannel of Nautilus.

---

### Post by fantab on 2011-10-05
**Thanks a lot**... I have it the way I wanted it.

By the way **what does 755 mean** in the following command

[HTML]sudo chmod -R 755 /storage[/HTML]

---

### Post by Morbius1 on 2011-10-05
You should never do a recursive chmod using octal mode on a directory:
> sudo chmod -R 755 /storageThat will make every folder and file 755 - read/write/executable to owner and read/executable to everyone else.

A better way is this:
```
sudo chmod -R a+rwX,go-w /storage
```Every folder will be executable ( which you must have to "open" the folder ) but every file will be left as non executable except those that were marked executable to begin with ( that's what the big "X" does ). The "go-w" will remove write for everyone other than the owner of the file.

---

### Post by Bucky Ball on 2011-10-05
Should be fine though as you have now deleted the mount point /storage and changed the fstab, yes?

---

