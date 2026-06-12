---
title: "URL in buildroot not doing what I need it to do"
date: 2012-02-20
forum: General Help
---

### Post by david55 on 2012-02-20
Hi
I am working through a tutorial showing how to build linux for an embedded system using buildroot. I am using Ubuntu running in Vmware as the host system. The tutorial says I must do the following in the buildroot menconfig app: 
[*] U-Boot --->                 
(smdk6410)U-boot board name                  
U-boot version (Custom tarball) ---> 
                (u-boot1.1.6__TE6410_2636.tgz) URL of custom U-Boot tarball

the file "u-boot1.1.6__TE6410_2636.tgz" is in the dl directory of buildroot. The problem is that when I do "make all" it seems to be looking for this file on the internet not in the dl directory. 
Perhaps somebody could tell me how this should be configured that it looks in the dl folder instead?

The error is:

--2012-02-20 13:31:02--  [http://.//u-boot1.1.6__TE6410_2636.tgz](http://.//u-boot1.1.6__TE6410_2636.tgz)
Resolving .... failed: Name or service not known.
wget: unable to resolve host address `.'
--2012-02-20 13:31:02--  [http://sources.buildroot.net//u-boot1.1.6__TE6410_2636.tgz](http://sources.buildroot.net//u-boot1.1.6__TE6410_2636.tgz)
Resolving sources.buildroot.net... 176.9.16.109
Connecting to sources.buildroot.net|176.9.16.109|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-20 13:31:03 ERROR 404: Not Found.

all help will be appreciated

thanks

---

### Post by Khayyam on 2012-02-20
Its very hard to tell what the script is doing without seeing the code. However, when you are prompted for a URL for the "custom tarball" try the following:

file:///path/to/u-boot1.1.6__TE6410_2636.tgz

Note: three slashes after "file:"

HTH ... khay

---

### Post by david55 on 2012-02-20
Thanks for that. I in the meanwhile figured out that if I just gave it a shorter name then it worked (u-boot1.tgz). Seems to be a bit of a bug somewhere :)

Anyway thanks for your reply - it might still come in handy :D

---

