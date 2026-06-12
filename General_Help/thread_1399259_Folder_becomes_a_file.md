---
title: "Folder becomes a file"
date: 2010-02-05
forum: General Help
---

### Post by wrixis on 2010-02-05
Hi!

I have a folder that I don't know why becomes a file and now I can't open it. Can I do somthing to convert again into a folder. I thinking about commands like chmod somthing like that.

Thanks.

---

### Post by chewearn on 2010-02-05
Can you run "ls -l" command on the file and post the output here.
```
ls -l
```

Note:
That the letter "L", not number 1.

---

### Post by wrixis on 2010-02-05
I thought it can be the "ó", but I have other folders whit this kind of letter and works fine.

I did:
```
ls -la
```

and I got:
```

drwxrwxrwx 1 root root      4096 2010-02-05 19:17 .
drwxrwxrwx 1 root root      4096 2010-02-04 00:57 ..
-rwxrwxrwx 1 root root 312975360 2010-02-05 01:17 Sólo Vista y 7
drwxrwxrwx 1 root root      4096 2010-02-05 19:13 Varios SSOO
drwxrwxrwx 1 root root      4096 2010-02-04 04:51 Windows7
drwxrwxrwx 1 root root      4096 2010-02-04 04:05 Windows Vista
drwxrwxrwx 1 root root         0 2010-02-04 02:10 Windows XP

```

---

### Post by chewearn on 2010-02-05
Mmm, not sure what's going on; never seen one of these before.  Furthermore, the size is too large.  Is it a ext3 / ext4 filesystem?

I couldn't find any information on whether it is possible to simply flip the "d" bit. Could be corrupted?  How about running a "fsck"?

---

### Post by falconindy on 2010-02-05
what's the output of:
```
file "Sólo Vista y 7"
```

---

### Post by wrixis on 2010-02-05
Thanks so much! but I know part of what happened. I went here to tell you and doing file confirme me that. Yes too large, I was wondering why too. The folder was replaced by an ISO file. Don't ask me why because I was trying a soft for first time, maybe it doesn't work when I select a output folder (I remember that few years ago, a music cd ripper had a problem with the output directory, that is, some times created bad folder).

Thanks so much. The bad thing is I lost my files... :(

---

