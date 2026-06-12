---
title: "Can't print to printer attached to Ubuntu from Windows"
date: 2006-02-26
forum: General Help
---

### Post by chapterthree on 2006-02-26
Hey All,

I sucessfully was able to get my Lexmark Z611 working under Ubuntu, which functions as my file server in my home LAN.  I can print from within Ubuntu without any issues.  What I'd like to do is be able to print from my Windows machines to that printer.  I have followed the instructions at:

[https://wiki.ubuntu.com/NetworkPrintingFromWinXP?action=show&redirect=NetworkPrintingFromWindows](https://wiki.ubuntu.com/NetworkPrintingFromWinXP?action=show&redirect=NetworkPrintingFromWindows)

Everything seemed to go fine, but when I try to send a job to the printer from Windows, it does not seem to get to the spool.  Also when I go into the properties for the networked printer from Windows and try to print a test page, I get an immediate error:

"Test page failed to print.  Would you like to view the print troubleshooter for assistance?  Unable to create a print job."

That would almost seem like a permissions issue, but I'm not quite sure how to troubleshoot this further.  Does anybody have any ideas?

---

### Post by WelterPelter on 2006-02-26
There are zillions of other threads in this forum and also in the ubuntu wiki that deal with this thorny issue. Hang in there, you'll make it work.

---

### Post by akniss on 2006-02-26
[QUOTE=WelterPelter]There are zillions of other threads in this forum and also in the ubuntu wiki that deal with this thorny issue. Hang in there, you'll make it work.[/QUOTE]

If that's the case I'd love it if you could point a couple good ones out.  I've given up, because all of them I've looked at say something like "use samba to share the printer, read samba documentation."  Well I'm no programmer, and after about 25 different attempts at samba configuration, i still cannot print from a windows laptop to my ubuntu printer on the same network.  Almost every search for relevant terms on this forum bring up a bunch of dead end threads of other users who i assume have given up as well, or not posted their "lucky" guess that finally got things working.

---

### Post by WelterPelter on 2006-02-26
Funny, I pull up some successful ones right away. For example [this thread]("http://www.ubuntuforums.org/showthread.php?t=119486&highlight=samba+printing") ends with several people making it work. Just keep digging. It's a pain in the butt, but it works.

---

### Post by chapterthree on 2006-02-26
Wow, after working on this for a few hours, I finally got it working.  I followed the exact steps in post 39 and it worked:

[http://www.ubuntuforums.org/showpost.php?p=742487&postcount=39](http://www.ubuntuforums.org/showpost.php?p=742487&postcount=39)

I guess the key is you have to have Adobe install the printer, rather than just installing the printer using the Windows installer.

---

