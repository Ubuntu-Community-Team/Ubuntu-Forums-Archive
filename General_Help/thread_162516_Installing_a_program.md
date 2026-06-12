---
title: "Installing a program"
date: 2006-04-19
forum: General Help
---

### Post by newbietolinux on 2006-04-19
I cannot install any programs that come in the form of tarballs on my Ubuntu 5.10. I get an error message but I can't make out anything from that. Please help me. The result I get is here:

vipin@ubuntu:~/Softwaretesting/gtksee-0.6.0b-1$ ./configure
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables

---

### Post by henryk69 on 2006-04-19
Do you have write permitions in this folder? Maybe try: ```
sudo ./configure
```

---

