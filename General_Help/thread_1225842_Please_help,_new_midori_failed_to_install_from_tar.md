---
title: "Please help, new midori failed to install from tar!"
date: 2009-07-29
forum: General Help
---

### Post by stozi on 2009-07-29
Is there anything I can do? I was following the directions that came in the Midori tar.bz2:
> Change to the Midori folder on your hard disk in a terminal.

Run './waf configure'

Run './waf build'
but this is what happened:
```
lee@lee-desktop:~/midori-0.1.8$ ./waf configure
Checking for program gcc                 : ok /usr/bin/gcc 
Checking for program cpp                 : ok /usr/bin/cpp 
Checking for program ar                  : ok /usr/bin/ar 
Checking for program ranlib              : ok /usr/bin/ranlib 
Checking for gcc                         : ok  
Checking for program glib-genmarshal     : not found 
Checking for program glib-mkenums        : not found 
Checking for program rst2html.py         : not found 
Checking for program rst2html            : not found 
Checking for program msgfmt              : not found 
/home/lee/midori-0.1.8/wscript:102: error: The program msgfmt (gettext) is mandatory!

```

There is no package called msgfmt.

---

### Post by spcwingo on 2009-07-29
I think what you need is gettext and possibly libgettext-ruby1.8/libgettext-ruby-utils.  Try gettext first.

---

