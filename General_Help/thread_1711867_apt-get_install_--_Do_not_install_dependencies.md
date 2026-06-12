---
title: "apt-get install -- Do not install dependencies"
date: 2011-03-21
forum: General Help
---

### Post by pransis on 2011-03-21
Hi all,

How do I make apt-get not install dependencies? For example, I wanted to install mailx but it also installs exim4 and others. I just want mailx and nothing else. How do I do this?

---

### Post by flipper T on 2011-03-21
the proper functionality of the app you require "depends" upon its dependencies.

if they are not installed your app will not function correctly.

---

### Post by pransis on 2011-03-21
I am aware of that but I just want to install this package via apt-get.

---

### Post by racie on 2011-03-21
I'm not sure you understand.  All of these dependencies are NEEDED for your program to run.  You program will have TONS of errors or will likely not run at all if you do not install the dependencies along with it.

---

### Post by matt_symes on 2011-03-21
Hi

Have a look at 

```
apt-get --no-install-recommends .....
```

Maybe what your after ?

Kind regards

---

### Post by pransis on 2011-03-21
I tried this but it still installs exim4 and others... :(

---

### Post by flipper T on 2011-03-21
just as a matter of interest, why would you want to install a app without its dependencies ?

---

### Post by pransis on 2011-03-21
First reason -- I already have an MTA installed (Postfix). Why am I forced to install exim4 if I only need mailx?

---

### Post by pransis on 2011-03-22
For example, installing the **mailutils** package would require the following:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  exim4 exim4-base exim4-daemon-light guile-1.8-libs libgsasl7 libltdl7
  libmailutils2 libmysqlclient16 libntlm0 mysql-common
Suggested packages:
  mail-reader eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl
  swaks mailutils-mh
Recommended packages:
  mailx
The following NEW packages will be installed:
  exim4 exim4-base exim4-daemon-light guile-1.8-libs libgsasl7 libltdl7
  libmailutils2 libmysqlclient16 libntlm0 mailutils mysql-common
0 upgraded, 11 newly installed, 0 to remove and 4 not upgraded.
Need to get 4,691kB/6,205kB of archives.
After this operation, 15.3MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by flipper T on 2011-03-22
...and this would adversely effect your system how ?

---

### Post by pransis on 2011-03-22
I'm not saying it would adversely affect my system. I'm just saying do I really need to have another MTA just to install mailx? Why can't it just look for a dependency based on function?

---

### Post by crk on 2012-12-29
> **pransis said:**
> Hi all,

How do I make apt-get not install dependencies? For example, I wanted to install mailx but it also installs exim4 and others. I just want mailx and nothing else. How do I do this?

If you "just" want to install mailx skipping any/all other packages, then you can do the following :

```

$ apt-get download mailx # downloads the .deb file
$ dpkg --force-all -i mailx*.deb # use the downloaded file to install
```

Done!

**Warning: This only ensures that what you asks is accomplished. It does not, however, warrant the proper functioning of mailx**

---

