---
title: "Secure delete help"
date: 2009-07-26
forum: General Help
---

### Post by Psycho.mario on 2009-07-26
Hi, I regularly secureley delete my partitions with:
```
dd if=/dev/zero of=/dev/sd*
```
Is there any way i can use the same technique to securely delete files instead? I would rather use this method than have to install some other program. Thanks

---

### Post by wojox on 2009-07-26
Totally delete a file:

```
shred -f -v -z -u file.txt
```

---

### Post by benny bronx on 2009-07-26
You can add wipe to the context menu with this:
[http://ubuntu-unleashed.com/2008/01/securely-wipeerase-files-in-ubuntu-via-right-click-menu-in-nautilus.html]("http://ubuntu-unleashed.com/2008/01/securely-wipeerase-files-in-ubuntu-via-right-click-menu-in-nautilus.html")

I added "q" (quick 4 pass wipe) and "s" (silent) to the parameters.  The one possible downside here is that there is no warning or confirmation dialogue, so if you accidentally click on it, your file will be in Ubuntu Heaven.

---

### Post by dlmarti on 2009-07-26
shred doesn't work on ext3, nfs, etc
[http://http://www.cyberciti.biz/tips/shred-tip-securely-remove-multiple-files-so-no-one-can-recover-file-again.html]("http://http//www.cyberciti.biz/tips/shred-tip-securely-remove-multiple-files-so-no-one-can-recover-file-again.html")

---

### Post by wojox on 2009-07-26
I have ext3 and it works just fine. Have you tried it? Your link is broken by the way. One to many http://

---

### Post by benny bronx on 2009-07-26
link does not work.  But possibly from the same article:

   >  In the case of ext3 file systems, the above disclaimer applies (and shred is thus of limited effectiveness) only in data=journal mode, which journals file data in addition to just metadata. In both the data=ordered (default) and data=writeback modes, shred works as usual. Ext3 journaling modes can be changed by adding the data=something option to the mount options for a particular file system in the /etc/fstab file, as documented in the mount man page (man mount).



---

### Post by t0p on 2009-07-26
> **dlmarti said:**
> shred doesn't work on ext3, nfs, etc
[http://http://www.cyberciti.biz/tips/shred-tip-securely-remove-multiple-files-so-no-one-can-recover-file-again.html]("http://http//www.cyberciti.biz/tips/shred-tip-securely-remove-multiple-files-so-no-one-can-recover-file-again.html")

From the shred manpage:

> In the case of ext3 file systems, the  above  disclaimer  applies  (and shred  is  thus  of  limited  effectiveness) only in data=journal mode, which journals file data in addition to just  metadata.   In  both  the data=ordered  (default) and data=writeback modes, shred works as usual. Ext3 journaling modes can  be  changed  by  adding  the  data=something option  to  the  mount  options  for  a  particular  file system in the /etc/fstab file, as documented in the mount man page (man mount).

The above means that shred *does* work with ext3 in its default mode (data=ordered).  So shred *does* work.

You know, I've posted this so many times, to correct so many users who claim shred won't work with ext3, it ain't funny.

There's another option for secure deletion in linux: [**srm**]("http://srm.sourceforge.net/").  It seems to work in the same way as shred - overwriting deleted files - so the same caveat as shred about filesystems in journalled mode may apply.

---

