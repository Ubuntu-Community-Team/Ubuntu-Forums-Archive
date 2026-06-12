---
title: "help adding boot option to grub 2"
date: 2009-10-27
forum: General Help
---

### Post by xdevnull on 2009-10-27
Okay - so grub just got a lot more complicated

I need to add:

```
libata.force=noncq
```

to my boot options (even when there is a kernel upgrade).  How do I do this in grub2 without hosing my system?

Thanks

---

### Post by XDevHald on 2009-10-27
For the best guide and no one to mess it up but YOURSELF and to save others from messing your computer up. Read this: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If someone jumps in to help on this then please do but the guide in the link above will help you even better.

---

### Post by oldfred on 2009-10-27
Another grub2 guide:

 look in #5 for entries in  /etc/default/grub

The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by XDevHald on 2009-10-27
> **oldfred said:**
> Another grub2 guide:

 look in #5 for entries in  /etc/default/grub

The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


Great thread, but it's already best to link to the official Canonical Wiki pages as these are updated daily for the best results in tutorial support.

---

### Post by xdevnull on 2009-10-28
Alright - thanks for the information.  I had already looked at the documentation mentioned above.  Does this mean I have to become a programer to add a boot option now?  I'm not a programmer, but I never had problems make small edits to menu.lst.  I don't see anything in /etc/default/grub that is a "boot option" ; the files in /etc/grub.d are frankly a mystery.  Does this mean I'm SOL?  

This reminds me - in an unhappy way - of what has happened in X.  First xorg.conf becomes almost meaningless; now it is simply absent.  Much of the help out there that people like me used to get involved editing a few files.  Now I can't seem to fix much of anything on my own.

---

