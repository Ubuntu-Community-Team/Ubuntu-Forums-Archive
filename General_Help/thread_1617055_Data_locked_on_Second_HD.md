---
title: "Data locked on Second HD"
date: 2010-11-08
forum: General Help
---

### Post by tbcomputerguy on 2010-11-08
Hello there, this is my first post.  I recently had CentOS installed, but felt that I didn't need the whole server thing, so I picked ubuntu as my OS as I have used it in the past and quite liked it.  I formated my first hard drive and installed Ubuntu 10.10.  My second drive is a ext3 data drive only.  After installing Ubuntu, I can see the drive on the desktop, telling me that it is mounted...i think?  But when I goto the drive all the folders are protected.  I tried to chown with root to see the stuff but to no avail.  I can't seem to change permissions on the drive either or the files.

How and what have I done?  I need this data.

Dave

---

### Post by dcstar on 2010-11-09
> **tbcomputerguy said:**
> Hello there, this is my first post.  I recently had CentOS installed, but felt that I didn't need the whole server thing, so I picked ubuntu as my OS as I have used it in the past and quite liked it.  I formated my first hard drive and installed Ubuntu 10.10.  My second drive is a ext3 data drive only.  After installing Ubuntu, I can see the drive on the desktop, telling me that it is mounted...i think?  But when I goto the drive all the folders are protected.  I tried to chown with root to see the stuff but to no avail.  I can't seem to change permissions on the drive either or the files.

How and what have I done?  I need this data.

Dave

You need to find out the UID of the files/folders on this drive and then create an account in Ubuntu that has a UID to match:
```

ls -n
```

---

### Post by tbcomputerguy on 2010-11-10
I fixed it.  I created a new user and made sure its uid was the same as the one indicated by the file(s) in question.  I logged in as that user, then opened a termainal.  Sudo'd to root.  Then I went to the directory in question, I ran chmod -R 777 on that directory and it worked.  I was able to see the files and copy move etc.  The first time I used chmod -r  (small r) and it think that may have bee the problem.

Thanks for the help.

---

### Post by dcstar on 2010-11-10
> **tbcomputerguy said:**
> I fixed it.


Then MARK THE THREAD.

---

