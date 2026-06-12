---
title: "Unable to install draftSight.deb"
date: 2012-06-21
forum: General Help
---

### Post by vmalep on 2012-06-21
Hi,

Few months ago, I installed draftSight on Ubuntu 11.10 without problem. I upgraded to Ubuntu 12.04 and it kept running.

Today, I am trying to install it on a fresh 12.04 installation, but I got the following error:
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyxhost:  unable to open display ":0.0"
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 key
(ShowLicence:7781): Gtk-WARNING **: cannot open display: :0.0
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyxhost:  unable to open display ":0.0"
dpkg: error processing draftSight-1.2.229.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 draftSight-1.2.229.deb

(To be noted that I renamed the deb file with the version number, but I tried with the deb file I had downloaded for Ubuntu 11.10 to no avail).

Any suggestion?

Thanks in advance!
Pierre

---

### Post by gordintoronto on 2012-06-21
Did you get the file from here:
[http://www.3ds.com/products/draftsight/download-draftsight/draftsight.deb](http://www.3ds.com/products/draftsight/download-draftsight/draftsight.deb)

It appears to be a 32-bit program. When you download files from the Internet, it's up to you to make sure all dependencies are installed, such as libdirectfb-extra

---

### Post by vmalep on 2012-06-22
Hi gordintoronto,

Thanks for your reply and the suggestion. I did get the file from there, but it was not a problem of dependencies or either 32 vs 64bits architecture. It appeare that the error came from the installation script that was unable to open the licence "accept/reject" window.

I extracted the deb file, opened the DEBIAN/preinst file and commented the line:
export DISPLAY=:0.0

Then I run "dpkg-deb --build draftSight-1.2.229" (from the folder where the deb file was extracted) and "sudo dpkg -i draftSight-1.2.229.deb". This time, everything went fine.

Best regards,
Pierre

---

### Post by SilverLoz on 2012-06-27
A big thankyou to vmalep; followed your instructions and it fixed my install problem.

---

