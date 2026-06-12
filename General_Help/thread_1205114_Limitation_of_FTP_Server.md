---
title: "Limitation of FTP Server"
date: 2009-07-05
forum: General Help
---

### Post by jcobban on 2009-07-05
There would appear to be an undocumented implementation limit in the ftp server.

I accidentally dumped a large number of files into my home directory on my ISP, and now I am trying to clean them up.  Because there are thousands of files using a GUI FTP client would be inconvenient, so I tried deleting them using the old line command utility"ftp -i"  and issuing "mdelete I@*".  The command responded with individual messages indicating that it had deleted the 40,000 or so files, but when I then issued an "ls" command, the files were still there, and if I reissued the same mdelete command, it AGAIN reports that it has deleted each of the files.  I cannot see this as a documented bug in the ftp server so I am quite puzzled.  I can delete the files, but only if there are fewer than 2000 files that match the pattern.  For example "mdelete I@I11*" works, because that matches less than 1000 files.

---

