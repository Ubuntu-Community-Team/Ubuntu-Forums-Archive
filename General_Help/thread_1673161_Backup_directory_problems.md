---
title: "Backup directory problems"
date: 2011-01-22
forum: General Help
---

### Post by Stefan_McFeeters on 2011-01-22
I am currently using terminal to backup my portable hard drive. I am backing it up to my external desktop hard drive using the command 

Cd /media/Backup
Tar -cvpzf PORTABLE_HD_Backup.tar.gz /media/PORTABLE_HD

However when I restore the backup it creates a totally new directory inside my Portable HD this is the media folder which contains my portable hd as a directory this folder has all of my backed up files in it. I do not want the media/PORTABLE_HD directory, I only want the files inside the PORTABLE_HD directory. Is there any way I can do this.

---

### Post by tredegar on 2011-01-22
Try this:
```
cd /media/PORTABLE_HD
tar -cvpzf /path/to/backup/PORTABLE_HD.tar.gz   * 
```

---

### Post by vanadium on 2011-01-22
And probably, this will also work:
```

Tar -cvpzf PORTABLE_HD_Backup.tar.gz /media/PORTABLE_HD/*

```

---

### Post by tredegar on 2011-01-22
> And probably, this will also work:

Tar -cvpzf PORTABLE_HD_Backup.tar.gz /media/PORTABLE_HD/* 
I don't think you can have tested this ;)

---

### Post by Stefan_McFeeters on 2011-01-22
Sorry, but none of the codes worked, the same problem still occured

---

### Post by vanadium on 2011-01-23
> **tredegar said:**
> I don't think you can have tested this ;)

No indeed, but I expected it would. But indeed, probably you are then also storing the pathnames /media/PORTABLE_HD/ into the tar archive, which is not the intention.

@Stefan: sure the code of tredegar did not work?

---

### Post by Stefan_McFeeters on 2011-01-23
> **tredegar said:**
> Try this:
```
cd /media/PORTABLE_HD
tar -cvpzf /path/to/backup/PORTABLE_HD.tar.gz   * 
```

Thankyou so much, your code worked a treat. Idont know what i did wrong the first time i tried it.

---

