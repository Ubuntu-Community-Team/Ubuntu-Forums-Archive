---
title: "Help for mount option"
date: 2012-05-11
forum: General Help
---

### Post by jebaearnest on 2012-05-11
Hi,

I have created one directory say(/ubuntu). then inside that directory some contents(files) are there.
Then i have one drive(/dev/xvdb) is there. i mounted that drive
**sudo mount /dev/xvdb /ubuntu**.
then i did ls
only lost+found appearing. the contents which i had in the ubuntu directory not shown.
If i unmount again , then its showing.

But i want the files even after mounting.

Thanks.

---

### Post by bab1 on 2012-05-11
> **jebaearnest said:**
> Hi,

I have created one directory say(/ubuntu). then inside that directory some contents(files) are there.
Then i have one drive(/dev/xvdb) is there. i mounted that drive
**sudo mount /dev/xvdb /ubuntu**.
then i did ls
only lost+found appearing. the contents which i had in the ubuntu directory not shown.
If i unmount again , then its showing.

But i want the files even after mounting.

Thanks.

This is the correct behavior.  You should either mount the drive somewhere else (/ubuntu/drive) or move the files somewhere else (/files).

---

### Post by jebaearnest on 2012-05-11
But I want to have the old files in the directory to be in the drive.
Is there a way to do that

---

### Post by bab1 on 2012-05-11
> **jebaearnest said:**
> But I want to have the old files in the directory to be in the drive.
Is there a way to do that

If I follow what you are saying: just move the files to another directory temporarily, mount the drive and then move the files to that drive (it's really a partition).

---

