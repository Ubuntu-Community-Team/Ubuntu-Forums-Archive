---
title: "can I delete the folder: lost+found"
date: 2009-10-15
forum: General Help
---

### Post by huangjb on 2009-10-15
I add a new disk and mount it( for example, to the path /home/backup-storage ). After that, under the directory /home/backup-storage, I see a folder named lost+found. I googled and known that it's related to disk recover.

Is that really important?
Can I delete it?
What will happen after I delete it?
Or can I hide it from ls...

I really dislike to see it under my backup directories...

---

### Post by dominiquec on 2009-10-15
Don't. It's part of the ext file system.

---

### Post by lensman3 on 2009-10-15
No.  Originally damaged clusters on the hard drive were listed there.  The low level file system primitives used it for book keeping.  Every partition had a lost+found directory.

Do a "man mklost+found" from the command line.  You will see what it is used for.

---

### Post by huangjb on 2009-10-15
ok. I'll just keep it...

---

### Post by sirtrent on 2009-10-16
You could also use a different filesystem which doesn't use the lost+found directory. For example I use reiserfs, and I must admit there are times when it's nice to not have to see lost+found.

Though, changing file system on an already working drive may be a bit excessive for aesthetics; you'd have to reformat your drive.

---

