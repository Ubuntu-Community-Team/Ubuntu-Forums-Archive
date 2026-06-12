---
title: "File Permissions on PSP"
date: 2009-10-17
forum: General Help
---

### Post by ninjapirate89 on 2009-10-17
I know the answer to this will be obvious but I can't get it. My psp randomly decided to become read-only and I can't switch it back to read-write. My psp is mounted at /media/PSP.
I put this in the terminal 'sudo chmod 777 /media/PSP' and it is still saying read only. What am I missing?

By the way, this is the output from the terminal:
```

chmod: changing permissions of `/media/PSP': Read-only file system

```

If I put in 'sudo chmod -R 777 /media/PSP' instead it does the same thing except it lists every file on my psp and says they are read-only.

---

### Post by Dorrax on 2010-05-15
keep backups and reformat the memory stick using the PSP reformat option under system information when it stops reading correctly. It sucks, but that's the only I have found that works.

---

