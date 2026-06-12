---
title: "Drive Letter Change"
date: 2009-09-14
forum: General Help
---

### Post by samcal on 2009-09-14
Hello all, trying to get help with one minor issue.  

I have two Hard Drives installed, one is a 120gb(windows) and the other a 1tb(my docs).  
Installed ubuntu on my secondary hard drive which was previously assigned the letter H in windows.  I assigned ubuntu a 10gb partition just to play around.  Everything installed fine and it runs just fine. 

My problem is that now the Drive letter changed from H to E.  I tried to reassing letters, but can't select H because it is being used by buntu partitions, and if I try to select those it only gives me the option to reformat.  So my question is how can I change the drive letters back in windows so all my previous file paths and association work.  thanks.

---

### Post by sisco311 on 2009-09-14
Hi.

Linux can't change drive letters for Windows, that job is what Windows should do itself. 

Maybe a windows forum can better help you with this.

Anyway...

Try to install the ext2/ext3 driver in windows and then try to reassign the letters.

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by samcal on 2009-09-14
thanks that one didn't work for me, inode size error.

This one did help and successfully changed my drive letter back. 

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

thanks again.

---

