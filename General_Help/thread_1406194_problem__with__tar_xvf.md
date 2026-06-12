---
title: "problem  with  tar xvf"
date: 2010-02-13
forum: General Help
---

### Post by balki2005 on 2010-02-13
Hello,

I have a BIG problem,  I would like  untar a tar.gz file with  very important  data. but I allways  recieve  this  error:

gzip: leen.backup.tar.gz: invalid compressed data--format violated

or

when I try tar xvf file.tar.gz:

 gzip: stdin: invalid compressed data--format violated
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

what can  I do  to  recover these file? help !!! 

thanks in advance,

balki2005

---

### Post by giammy on 2010-02-13
are you sure the file is gzipped?
you can test it with the command "file myfile.tar.gz"

bye
giammy

---

### Post by tonywhelan on 2010-02-26
> **balki2005 said:**
> Hello,

I have a BIG problem,  I would like  untar a tar.gz file with  very important  data. but I allways  recieve  this  error:

gzip: leen.backup.tar.gz: invalid compressed data--format violated

or

when I try tar xvf file.tar.gz:

 gzip: stdin: invalid compressed data--format violated
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

what can  I do  to  recover these file? help !!! 

thanks in advance,

balki2005

Did you find a solution to this? I am getting an identical error trying to install DEB packages - but intermittently. I found one bug report [https://bugs.launchpad.net/ubuntu/+source/tar/+bug/453330](https://bugs.launchpad.net/ubuntu/+source/tar/+bug/453330) that suggested that tar has a fault in it but if that is so then why aren't there scores of similar reports from other people, I wonder.

---

