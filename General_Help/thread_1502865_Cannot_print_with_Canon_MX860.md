---
title: "Cannot print with Canon MX860"
date: 2010-06-06
forum: General Help
---

### Post by rdunnion on 2010-06-06
Hi. I cannot print with my Canon MX860. I have downloaded the proper drivers from the Canon Europe website and forced the arch to x64 as described on many sites. When I try to print a test page I get the error that "Idle - /usr/lib/cups/filter/pstocanonij failed". I have checked in lib64 and pstocanonij was there as well. If I change the URI from USB to CNIJUSB then I get the error that "cnijusb has failed". It may be possible to get this working as in another forum someone claims to be successful. I am able to use the scanner with the sane-backends package, so that is not a problem. I would appreciate any help with this, thank you. - Ryan

---

### Post by rdunnion on 2010-06-06
Sorry I forgot to mention that I'm running a fresh install of Lucid x64.

---

### Post by davidmohammed on 2010-06-06
in this [weblog]("http://www.lbsharp.com/wordpress/index.php/2009/11/21/setting-up-a-canon-mx860-printer-on-a-64-bit-linux-system/") the guy copied files from the default location to /usr/lib64/... etc

did you do this?

---

### Post by rdunnion on 2010-06-06
David - Thanks for the post. I did not have to copy those files because they were already in both lib and lib64. However, one comment on that page told of a user trying the Canon IP4600 ppd. I tried this and was able to print a test page, a document and a picture.
The test page and doc printed fine, but the picture was of poor quality despite settings. So it's partially working and I thank you for that. If anyone knows how to improve on this please post.

---

### Post by davidmohammed on 2010-06-06
hi there,
  try this [link]("http://febuntoo.com/mairin-duffy-how-to-set-up-the-canon-pixma-mx860-with-fedora.html") - somewhere in the middle of the page is instructions to set up on 64 bit with a link to the ppd.

hop this helps.

---

### Post by rdunnion on 2010-06-06
Yes I extracted that ppd file from the source code but still get the failed filter message after using it.

---

### Post by rdunnion on 2010-06-06
This issue was resolved by installing ia32-libs. This library allows the use of 32-bit executables on a 64-bit system.

---

