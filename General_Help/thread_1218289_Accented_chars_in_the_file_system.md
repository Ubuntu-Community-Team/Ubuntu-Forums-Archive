---
title: "Accented chars in the file system?"
date: 2009-07-20
forum: General Help
---

### Post by ownaginatious on 2009-07-20
I actually use Debian, but I think Ubuntu suffers from the same problem I'm having.

Anyway, does anyone know how to enable using accented characters within the file system for names of folders and such? I don't mean anything Unicode, I just mean the full range of ASCII characters. For example, in some of my files names I would like to have the character "ü", but the system doesn't allow it, or replaces it with gibberish.

Any help would be appreciated.

Thanks!

---

### Post by CatKiller on 2009-07-20
I've not seen an Ubuntu system fail to support those characters in filenames. Are you using FAT or NTFS, or something?

---

### Post by ownaginatious on 2009-07-20
I'm using NTFS. I read somewhere it may have something to do with locale settings, but it was all quite complicated.

---

### Post by CatKiller on 2009-07-20
If you're using NTFS then I suspect you're going to have to mount it with the utf-8 option to support Unicode characters. I haven't mounted an NTFS partition in years, so I can't really remember much more than that.

---

### Post by ownaginatious on 2009-07-20
> **CatKiller said:**
> If you're using NTFS then I suspect you're going to have to mount it with the utf-8 option to support Unicode characters. I haven't mounted an NTFS partition in years, so I can't really remember much more than that.

Hmm... here's what the line in my fstab looks like now:
```
/dev/sdb1       /media/windows1 ntfs-3g defaults,locale=en_CA.utf8 0 0

```

It seems like that I already have that option enabled. Do you see anything wrong there?

I honestly would also like to try to break away from NTFS (and anything Windows altogether), but unfortunately, a lot of the software I need is only available in Windows. I'm sure Unix based systems will come to overshadow it some day. :p

---

### Post by CatKiller on 2009-07-20
As I said, it's a long time since I used NTFS in Linux, and I don't think *ntfs-3g* was available at the time.

Do you really need locale=en_CA in there? I believe that the *ntfs* driver would have something like **nls=utf8**, although the mount.ntfs-3g manpage suggests that just **utf8** is a valid option.

---

