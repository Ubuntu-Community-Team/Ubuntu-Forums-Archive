---
title: "New to Ubuntu"
date: 2009-07-12
forum: General Help
---

### Post by TimEnid on 2009-07-12
I have a dell Mini running ubuntu. No CD drive yet, but will get one next week.  When i go into my system monitor, i see that these two devices (/dev/sda2 and gvfs-fuse-daemon) are both full. I have no space left on them. So when i got to update apps, it tells me there is no space available. what can i do to free up space? Thanks.

also, when i click on the gvfs-fuse-daemon file, nothing is inside, or at least nothing is visible.

---

### Post by Revolutionary101 on 2009-07-12
/dev/sda2 is most likely a partition with all of the restore information that came with your computer so I wouldn't suggest trying to free up space on there. 

I don't know what gvfs-fuse-daemon is though.

---

### Post by davec64 on 2009-07-12
Which type of machine have you got, SD or HArd Disk?

Also go into Accessories and run the Disk Space analyser to see what's taking up the space. :)

---

### Post by TimEnid on 2009-07-12
> **davec64 said:**
> Which type of machine have you got, SD or HArd Disk?

Also go into Accessories and run the Disk Space analyser to see what's taking up the space. :)

how do i determind which machine? thanks for the help

---

### Post by wojox on 2009-07-12
gvfs = Gnome Virtual File System. If you mount network drives via nautilus, they are accessible from ~/.gvfs.

---

### Post by TimEnid on 2009-07-12
> **wojox said:**
> gvfs = Gnome Virtual File System. If you mount network drives via nautilus, they are accessible from ~/.gvfs.

mount a network drive? i dont think i do this. i only mount an external hd.

---

### Post by davec64 on 2009-07-12
When you bought the machine did you buy it with less than 8GB of storage or 60GB+. If it's a low figure you've got a machine that uses SSD rather than a traditional Hard Disk.

---

### Post by TimEnid on 2009-07-12
> **davec64 said:**
> When you bought the machine did you buy it with less than 8GB of storage or 60GB+. If it's a low figure you've got a machine that uses SSD rather than a traditional Hard Disk.

less than 8gb.

---

### Post by TimEnid on 2009-07-12
> **Revolutionary101 said:**
> /dev/sda2 is most likely a partition with all of the restore information that came with your computer so I wouldn't suggest trying to free up space on there. 

I don't know what gvfs-fuse-daemon is though.

these two folders are totalling 6.8gbs. if the first one should not be touched, what should i do with the second. thats 3.4gb im missing out on.

---

### Post by wojox on 2009-07-12
GnomeVFS is the core library used to access files and folders in GNOME applications. It provides a file system abstraction which allows applications to access local and remote files with a single consistent API.
I wouldn't screw with it.

---

