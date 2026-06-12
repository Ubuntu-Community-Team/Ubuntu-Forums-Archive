---
title: "Copying files from  one file without using command line"
date: 2010-12-09
forum: General Help
---

### Post by mr2v6 on 2010-12-09
Hello,
Is there a way to copy a file from the desktop to /usr/lib/ICAclient folder that I have, by using drag and drop.
For some reason, I thought I was able to do this in Mint.

Thanks in advance.
Mr2v6

---

### Post by nothingspecial on 2010-12-09
Press Alt F2
```
gksudo nautilus
```

---

### Post by mr2v6 on 2010-12-09
Thanks, I did it but the file that got copied has a small X on the upper right hand corner.  What does this mean?  Also the program for which relies on this file does not work. Perhaps because of the presence of X.

MR2v6

---

### Post by kanishkdudeja on 2010-12-09
that means you dont have the permission to access that file.

---

### Post by mr2v6 on 2010-12-09
Hi Kanishkdudeja

Thanks, that makes sense to me now.   How do I go around it?
The file is inside the usr/lib .
thanks,
Raymond

---

### Post by kanishkdudeja on 2010-12-09
gksudo nautilus

then navigate to /usr/lib

after that right click on the file..

click on permissions..

set permissions of your username, your groupname and others to read and write..

---

### Post by nothingspecial on 2010-12-09
> **kanishkdudeja said:**
> gksudo nautilus

then navigate to /usr/lib

after that right click on the file..

click on permissions..

set permissions of your username, your groupname and others to read and write..

No, libraries should be owned by root.

What are you actually trying to do?

---

### Post by mr2v6 on 2010-12-09
I am actually going to certificates, and make a file be root.  You are right that the certificates around that folder have root permissions with the exception of the one I have mentioned.  Because of this the citrix application I am trying to run won't work.

Thanks,
Mr2v6

---

### Post by mr2v6 on 2010-12-10
Thanks for all your help.
I was able to change the file to have root ownership.
Mr2v6

---

### Post by kanishkdudeja on 2010-12-10
great..please mark the thread as solved..:)

---

### Post by kanishkdudeja on 2010-12-10
btw u did it by which way ?

---

