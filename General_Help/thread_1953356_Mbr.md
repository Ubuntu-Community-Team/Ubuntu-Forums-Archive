---
title: "Mbr"
date: 2012-04-06
forum: General Help
---

### Post by betterthanjordan79 on 2012-04-06
Hi guys,

I have a Samsung 2TB HDD which Windows managed to erase the MBR from(its an external and contains no operating system files etc). I have used Windows based recovery software to attempt to recover the files but to complete the process I would need a second 2TB HDD to recover the files on to which I don't have. Are there any tool or commands in Ubuntu(or Windows for that matter)that I could use to search for the files and rebuild the MBR on my original HDD?

Thanks for any help given,

Daniel

---

### Post by Cheesemill on 2012-04-06
I think you mean partition table, not MBR. If it doesn't have an OS on it then it doesn't need a MBR.

You could try using [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover the partition table.

[http://www.youtube.com/watch?v=EncqYP1ijFg](http://www.youtube.com/watch?v=EncqYP1ijFg)

If a simple partition recovery isn't possible and you have to use the deep scan option then yes, you will need another drive to copy the data to.

---

### Post by betterthanjordan79 on 2012-04-06
Thanks Cheesemill, I will try this out later!! It seems to be exactly what I'm looking for though!

---

