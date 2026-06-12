---
title: "unicode support in ubuntu?"
date: 2011-08-13
forum: General Help
---

### Post by action9 on 2011-08-13
Hi...I have a folder of mp3s where some of the filenames and folder names are in unicode....Ubuntu cant see any of them....how do i get unicode support in ubuntu? so i can see my files and folders again.

Thanks

---

### Post by CatKiller on 2011-08-13
I'm pretty sure you set it as a mount option in /etc/fstab. I'm surprised it isn't UTF-8 by default, but it has been a while since I've played with mounting.

---

### Post by Frogs Hair on 2011-08-13
I have not used this , so you may want do some more searching before trying .
[http://techammer.blogspot.com/2011/01/enabling-unicode-support-for-linux.html](http://techammer.blogspot.com/2011/01/enabling-unicode-support-for-linux.html)

---

### Post by action9 on 2011-08-13
i tried with:

/dev/sdb2 /mnt/drive2 ntfs nls=iso8859-1 0 2

in my fstab but i still cant see the folders??

---

### Post by action9 on 2011-08-13
i get this error when i do a 'ls' in my music folder:

ls: reading directory .: Invalid or incomplete multibyte or wide character

---

### Post by CatKiller on 2011-08-13
I'm pretty sure that Unicode and ISO 8859-1 aren't the same thing. Try *utf8* instead of *nls=iso8859-1*.

---

### Post by action9 on 2011-08-13
i tried /dev/sdb2 /mnt/drive2 ntfs nls=utf8 0 2

still saying the same thing

---

### Post by CatKiller on 2011-08-13
You don't need the nls for utf8.

---

### Post by action9 on 2011-08-13
u mean like this? /dev/sdb2 /mnt/drive2 ntfs
cause that doesnt work

---

### Post by CatKiller on 2011-08-13
No.

Like this.

```
/dev/sdb2        /mnt/drive2        ntfs        utf8        0       2
```

EDIT:

I was just having a look at *man mount* for the NTFS options, and saw this:

```

       **uid**=_value_, **gid**=_value_ and **umask**=_value_
              Set the file permission on the filesystem.  The umask  value  is
              given in octal.  By default, the files are owned by root and not
              readable by somebody else.

```
Perhaps that's your problem rather than your encoding?

---

### Post by action9 on 2011-08-13
i tried:
/dev/sdb2        /mnt/drive2        ntfs        utf8        0       2
i am trying to access the files with sudo root access but still the same error:

ls: reading directory .: Invalid or incomplete multibyte or wide character

---

