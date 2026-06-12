---
title: "Can i mount two drives in my /home folder?"
date: 2011-04-15
forum: General Help
---

### Post by Meow27 on 2011-04-15
can i mount my home folder in the following way?

/dev/sda5 /
/dev/sdb3 /home/Folder1
/dev/sdb3 /home/Folder2


i think this is a simple question, and some confirmation would be much appreciated

im asking this because I'm using both an HDD and an SSD in my laptop. I want the Hd spinning at a minimum, this i'm trying to allocate all of my "data" folders to the HD.

if the above is not possible, can someone tell me an alternative solution?

thanks in advance.

---

### Post by WorMzy on 2011-04-15
No, but yes. A block device can only have one mount point, but there's nothing stopping you mounting the mount point somewhere else with the bind option.

Here's an fstab example: 

```
/dev/sdb3     /home/Folder1 ext4 defaults 0 2
/home/Folder1 /home/Folder2 none bind     0 0
```

You could use a symlink instead. Once /dev/sdb3 is mounted, run
```
sudo ln /home/Folder1 /home/Folder2
```

I don't understand your thought process however, so I don't know what you expect to accomplish by having two ways to the same folder.

---

### Post by sanderd17 on 2011-04-15
is your example right? mounting sdb3 to two different directories?

Because that's not what the title says.

Normally, you can only mount one partition to one directory. So if you want to map one drive to multiple directories, you need to make multiple partitions on that drive.

There is no way to map multiple drives to one directory since then Ubuntu would not know where to place the file you just put in that directory. 

An alternative to multiple partitions is working with soft links, type
```

ln --help

```
for more info.

---

### Post by Meow27 on 2011-04-15
I know that the thought process is crummy, thats part of the reason i was asking. 

I don't want to treat my home folder like separate drives (even though thats what ill be doing), nor do I want the symbolically linked. (seems what ill end up having to do.)

I suppose this was a silly question after all. 

unless someone has something to say, consider the thread as SOLVED

---

