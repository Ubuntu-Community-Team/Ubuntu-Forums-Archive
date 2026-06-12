---
title: "tar.bz2 skipping file???"
date: 2011-05-24
forum: General Help
---

### Post by WhyCali on 2011-05-24
I'm creating a directory backup using "tar -cjvf backup.tar.bz2 dirname" all has been working perfectly, but lately one particular file is not making it into the archive.  I noticed the file permissions were slightly different, but I changed them to 0644.  Still tar is skipping the file and I'm not sure why.  

One more thing.  I made a copy of the file, in the same directory but used a ".old" extension rather than ".php".  The .old file IS making it into the archive, but the .php file is not.   I've even deleted the .php file entirely and created a new one... didn't help.

Any ideas on what could be preventing tar from including this file?  

thanks!

Mike

---

### Post by hwttdz on 2011-05-25
What if you try /bin/tar both with the whole directory and again with only the file which is being passed over.

---

