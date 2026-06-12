---
title: "Canon Pixma MP620 in Ubuntu 10.10, 64 bit."
date: 2010-11-15
forum: General Help
---

### Post by Mega_Mike on 2010-11-15
**EDIT**

I have better instructions on this thread:
[http://ubuntuforums.org/showthread.php?p=10575009#post10575009]("http://ubuntuforums.org/showthread.php?p=10575009#post10575009")

HOWTO:  Install Canon MP620 in Ubuntu 10.10 64bit via network connection.

I have packaged the PPD file and supporting Debian packages here (with corrected libcups2 dependencies).

[http://rapidshare.com/files/431005278/MP620.zip]("http://rapidshare.com/files/431005278/MP620.zip")

After installation of all the Debian packages 
  sudo dpkg -i *.deb

Add the printer, you should see a Canon series in the network browser (assumed powered on and on local network).  Let the driver search go, then manually select the PPD file and select the file from the package.  Thats it!

Both printing and simple scan work.

The instructions were originally/based from this extremely helpful blogpost:

[http://mp610.blogspot.com/](http://mp610.blogspot.com/)

---

### Post by Tagged on 2010-12-02
that link is at max, any other places hosting it? Thanks a ton!!!

---

### Post by MaDxCrEaM on 2010-12-02
would also like a working link, thanks!!

---

### Post by ErDty&amp;h on 2011-02-22
[http://bkintegration.com/2010/08/install-canon-mp620-on-ubuntu-linux-10-04/](http://bkintegration.com/2010/08/install-canon-mp620-on-ubuntu-linux-10-04/)

---

### Post by Mega_Mike on 2011-03-18
The rapidshare link is dead, these instructions are better
[http://ubuntuforums.org/showthread.php?p=10575009#post10575009](http://ubuntuforums.org/showthread.php?p=10575009#post10575009)

---

### Post by HaightsW on 2011-05-04
You are a star - thanks a lot!
PS: I used your file on Natty - works fine :)

---

