---
title: "chmod 000"
date: 2010-02-10
forum: General Help
---

### Post by conradin on 2010-02-10
Hi all, this is a general Linux question. What does chmod 000 do?
when i create a chmod'd file with the 000 permission what happens?

I tried creating a file with 000 permissions, and I was still able to read and write to it. So what what does chmod 000 actually do?

---

### Post by patchwork on 2010-02-10
After checking the man pages, it seems the leading 0 is applying the permissions to no one  (first digit 4 for user, 2 for group, 1 for sticky attributes, or add them together).  I think what you're trying to do would be chmod 700, which would make a file with no read-write-execute privileges for anyone anywhere...

---

### Post by gmargo on 2010-02-10
chmod 000 denies read, write, and execute permission to yourself, your group, and everyone else.  If you can still edit it, then you either had the file open before you changed permissions, or you're using some editor that's "helping" you by messing with the permissions (or removing/replacing the file).

```

$ cd /tmp
$ date > foo
$ ls -l foo
-rw-r--r-- 1 gmargo gmargo 29 Feb 10 07:43 foo
$ cat foo
Wed Feb 10 07:43:03 PST 2010
$ chmod 000 foo
$ ls -l foo
---------- 1 gmargo gmargo 29 Feb 10 07:43 foo
$ cat foo
cat: foo: Permission denied


```

---

### Post by conradin on 2010-02-10
Thanks! This was actually my mistake, I was logged in as root. lolz, thanks patchwork!

---

### Post by patchwork on 2010-02-10
Not sure I can take the credit for this.....seems gmargo had the right answer

---

### Post by lukutu on 2010-08-10
I still have the problem. When I try the method proposed here it works but the problem still when it is about a file not created by me or copied from another machine in GUI

---

### Post by Vaphell on 2010-08-10
if you are not an owner of the file, you need to login as the owner or root or grant yourself admin rights with sudo.

---

