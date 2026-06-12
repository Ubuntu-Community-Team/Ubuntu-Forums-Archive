---
title: "Cannot move files to trash"
date: 2011-06-14
forum: General Help
---

### Post by _Impact_ on 2011-06-14
I searched the forums and other sites, and tried a few things, but still doesn't work. 

I have a shared NTFS partition /dev/sda6 mounted on /media/sda6 

Tried adding uid=1000 and gid=46 in the 3rd line in fstab, but nothing changed.

Help appreciated.

---

### Post by sanderd17 on 2011-06-14
Are you sure the id is right? it should be your id, you can ask it with the command
```

id

```

the same for the gid (group id), it should be a group of which you are a member.

If that doesn't work, can you give your new fstab?

---

### Post by _Impact_ on 2011-06-14
Thanks for the reply, sanderd17!

```
id
```

Output:

```
uid=1000(valeriu) gid=1000(valeriu) groups=1000(valeriu),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),30(dip),44(video),46(plugdev),104(fuse),111(lpadmin),119(admin),122(sambashare)
```

What do you mean by the new fstab?
I'll attach the file -> sorry cannot attach.

I noticed that when I delete a file from my desktop, it goes to the bin, so the problem is only when I try to delete files from the mounted drive (/dev/sda6) 

Thanks again!

---

### Post by ajgreeny on 2011-06-14
Are you sure there can be a normal trash folder on an ntfs partition?  Don't forget trash is always on the partition where the files are situated, and will not go to your /home trash if on another partition.

---

### Post by _Impact_ on 2011-06-14
> **ajgreeny said:**
> Are you sure there can be a normal trash folder on an ntfs partition?  Don't forget trash is always on the partition where the files are situated, and will not go to your /home trash if on another partition.

I had the same issue in 10.10, but I somehow (don't remember how :D) fixed it. So I guess it is possible.

Btw, the ntfs partition has a .Trash-1000 folder.

---

### Post by _Impact_ on 2011-06-14
OK I got it. It appears that I left a space where I shouldn't have:

WRONG: /dev/sda6  /media/sda6  auto  defaults, uid=1000     0  0  
RIGHT: /dev/sda6  /media/sda6  auto  defaults,uid=1000     0  0  


Thanks a lot guys! Ubuntu rocks! ;)

---

