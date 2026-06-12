---
title: "could not find python header"
date: 2006-04-23
forum: General Help
---

### Post by ivorobotnik on 2006-04-23
hi. i'm trying to install pygtk-2.8.0 but when i run ./configure i get this:

checking whether /usr/bin/python version >= 2.3.5... yes
checking for /usr/bin/python version... 2.4
checking for /usr/bin/python platform... linux2
checking for /usr/bin/python script directory... ${prefix}/lib/python2.4/site-packages
checking for /usr/bin/python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

could anyone help me and tell me what i have to do??

---

### Post by GeneralZod on 2006-04-23
python-gtk2.4 is in the repositories already; will that not do?

If it definitely won't do, then 

```

sudo apt-get install python-dev 

```

will get rid of that particular error message.  There may be more, though! :)

---

