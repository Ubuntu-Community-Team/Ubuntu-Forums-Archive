---
title: "What is the dot at the end of ls permissions, and why does it prevent me from..."
date: 2009-11-04
forum: General Help
---

### Post by hwttdz on 2009-11-04
What is the dot at the end of ls permissions, and why does it prevent me from making a backup of a file

```
-rw-r--r--.   1 hwttdz hwttdz         15 2009-11-04 13:12 test.txt
          ^ that guy
```

It's attached to some of the files in my home directory, which I would rather not post the entire contents of.  And how can I fix it.  I'm connecting to the machine with ssh, but I don't figure that should matter.

Edit: I figured out what the dot is, it means the file has an access list with SELinux.  So I guess I need to know how to strip this access list off of all my files.  And I don't have selinux installed.

Edit: I tried to install selinux, which of course caused some error when attempting to login with ssh, functionally breaking the machine. And by error I don't mean the machine is trying to be more secure, I mean glibc invalid pointer.

---

### Post by hwttdz on 2009-11-05
Ok, back to where I was, now trying to strip the dot (really strip the selinux policy from files).  This will let me edit my files again.  Does anyone know how to remove the policy from a file (or remove the policy from my whole filesystem)?

---

### Post by Iowan on 2009-11-05
I presume you've tried to delete the file via **sudo rm test.txt**?

---

### Post by hwttdz on 2009-11-05
I believe I could have done so, however then I would be in the unfortunate situation of not having the file, which for test.txt would not be a big deal, but for a few other files in my home directory would have been much less convenient.  

So after figuring out what the dot meant I found out how to strip this from my files.  See here: [http://ubuntuforums.org/showthread.php?t=1315684](http://ubuntuforums.org/showthread.php?t=1315684)

---

