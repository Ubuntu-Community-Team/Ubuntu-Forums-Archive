---
title: "Remove or list orphaned *files*"
date: 2010-01-20
forum: General Help
---

### Post by artifex on 2010-01-20
I have installed some programs from source and found no trace where and what were installed and I would like to remove those installed files. So I am looking for any script or app to list all orphaned (I mean not related to any installed package) files.

I am using Ubuntu Server 9.10 without any fancy X11 stuff so console version is preferred. I have found bitbleach and computer janitor in this forum but they are X11 apps.

---

### Post by bigbrovar on 2010-01-20
If you installed source I am presuming you compiled? if that is the case. I would just get the source of the program I compiled and run the ./configure 
make 
but the last command would be
make uninstall 
that usually works for me. Btw what is the name of the program you installed from source?

---

### Post by artifex on 2010-01-20
> **bigbrovar said:**
> If you installed source I am presuming you compiled? if that is the case. I would just get the source of the program I compiled and run the ./configure 
make 
but the last command would be
make uninstall 
that usually works for me. Btw what is the name of the program you installed from source?

Thanks for your answer! It's asterisk-1.4.29 and asterisk-addons-1.4.10. Addons does not have any uninstall Makefile rule but asterisk have. It was so obvious... Shame on me. :)

---

