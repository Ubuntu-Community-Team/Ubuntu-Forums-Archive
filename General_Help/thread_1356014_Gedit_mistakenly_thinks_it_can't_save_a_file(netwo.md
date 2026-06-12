---
title: "Gedit mistakenly thinks it can't save a file(networked drive)"
date: 2009-12-15
forum: General Help
---

### Post by schwim on 2009-12-15
Hi there everyone,

I'm having a bit of an issue.  I use Gedit to work on my files that reside in a Win XP share.  I mount the share via the following in fstab:

```

//192.168.1.199/Websites /mnt/websites cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0

```

Here's my problem.  Gedit states that it's unable to save the file any time I choose to save. **It is, however, properly saving the file, as well as creating a backup**.  To clarify, there is no problem with the file being saved.  The only problem that exists is the fact that Gedit pops up a notice every single time I save a file telling me that it can't save a file when in fact it could.

I use Scite and other editors, ftp apps, etc, and they save the same files with no error.  Gedit is the only one that is doing this.

The only thing I can think of adding is that early on, Gedit didn't have this issue.  A couple weeks into the Ubu install, it started happening, so at one time, Gedit didn't have an issue with saving to my Win share.

I would greatly appreciate any help in getting Gedit working properly, as I miss it.

thanks,
json

---

### Post by Snow986 on 2009-12-15
If it was me, I would first start by uninstalling the gedit package and then reinstalling. Might fix the problem and its simple and harmless.

---

