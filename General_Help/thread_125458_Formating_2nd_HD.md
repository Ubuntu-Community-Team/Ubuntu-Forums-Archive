---
title: "Formating 2nd HD"
date: 2006-02-04
forum: General Help
---

### Post by Jedeye on 2006-02-04
Hi – here is my situation. I have 2 hard drives my primary is Extended 3 and my second is a NTFS and VFAT(2 partitions). I want to format the 2nd hard drive as one Extended 3 drive, are there any tools for doing this? I am not sure what the best way to go about doing it is/

Thanks

---

### Post by taurus on 2006-02-04
You need to remove those two partitions on your second HD first and then format it as ext3.  You can do that with 

fdisk /dev/hdb

---

### Post by gerbman on 2006-02-04
[QUOTE=Jedeye]Hi – here is my situation. I have 2 hard drives my primary is Extended 3 and my second is a NTFS and VFAT(2 partitions). I want to format the 2nd hard drive as one Extended 3 drive, are there any tools for doing this? I am not sure what the best way to go about doing it is/

Thanks[/QUOTE]

Check out the utility 'gparted'.  It's in the repository, and makes things like that very easy.

Cheers.

---

### Post by Jedeye on 2006-02-04
thanks guys :)

---

