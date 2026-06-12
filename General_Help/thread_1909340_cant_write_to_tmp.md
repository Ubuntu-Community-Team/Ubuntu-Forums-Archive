---
title: "cant write to /tmp?"
date: 2012-01-15
forum: General Help
---

### Post by geoffree on 2012-01-15
I am running dual boot system with Linux Mint Debian and Kubuntu 11.04.
After inserting USB flash drive, the system crashed and when I tried to invoke Kubuntu I got the message in a white box:  
"xsession: warning: unable to wrte to /tmp; x.session may exit with an error"  plus a box with the text "okay". 
click on that box and get a log-in request. But after logging in I still can't get to a display screen.  I can boot the Linux Mint side but I want my Kubuntu.  Help?
Thanks.

---

### Post by Lars Noodén on 2012-01-15
Have you accidentally changed the settings for /tmp?  Is it a directory or is it mounted as its own partition?

You can check both this way:
```

ls -l / | grep tmp
grep tmp /etc/fstab

```

---

