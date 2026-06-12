---
title: "Cant see rest of the drive on which ubuntu is installed"
date: 2011-06-01
forum: General Help
---

### Post by manish23march on 2011-06-01
When I boot into Ubuntu, I can see my Windows partition, but I can't see  everything else that is on the second partition (where Ubuntu is  installed), all I see is the Ubuntu root. Can anyone shed some light on  how I can view the rest of my files?

Ubuntu is installed on D: drive and windows 7 is installed on c:

---

### Post by mcduck on 2011-06-01
I don't understand what you mean by not seeing the rest of the files on the Ubuntu partition. Can't you just open the file manager and browse around?

Do you have a proper Ubuntu install, or did you do a Wubi install (which would install Ubuntu into a file on a windows filesystem instead of using actual partition)?

If it's a normal Ubuntu install, then just open a file manager... Those *are* all the files on that partition. (if you did a normal install, and previously had some files on the partition where you installed Ubuntu, those files are gone by now.)

---

### Post by Mark Phelps on 2011-06-01
If this is a Wubi install, then you have to open a different item in Places, as it creates an icon for each partition -- and your "D" partition would be separate from your "C" partition.

And in Wubi, your NTFS partitions are available under /host

---

### Post by manish23march on 2011-06-02
> **Mark Phelps said:**
> If this is a Wubi install, then you have to open a different item in Places, as it creates an icon for each partition -- and your "D" partition would be separate from your "C" partition.

And in Wubi, your NTFS partitions are available under /host
[SIZE=4][B]

Thanks,It helped..... I got the [COLOR=DarkRed]/host[/COLOR] Folder[/B][/SIZE]

---

