---
title: "pygtk error."
date: 2006-02-13
forum: General Help
---

### Post by alavaliant on 2006-02-13
I've just installed Ubuntu 5.10 on one of my pcs but I'm running into an error with any python applications I run that I've never seen before.

Using the helloworld.py file from the pygtk tutorials as an example.  It errors out with;

File "./helloworld.py", line 7, in ?
    import gtk
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?
    from _gtk import *
ImportError: /usr/lib/libpangocairo-1.0.so.0: undefined symbol: pango_font_get_font_map

The same error results from any other pygtk app I run.

Here are the packages and their versions I have installed that might be of help to know;
python-gtk2                            2.8.1-0ubuntu2
python2.4-gtk2                         2.8.1-0ubuntu2
libpango1.0-0                          1.10.1-0ubuntu1
libpango1.0-common                     1.10.1-0ubuntu1
libpango1.0-dbg                        1.10.1-0ubuntu1
libpango1.0-dev                        1.10.1-0ubuntu1
libcairo2                              1.0.2-0ubuntu1
libcairo2-dev                          1.0.2-0ubuntu1

No other gtk apps seem to be having issues, just py ones.   Any ideas?   There  were no errors reported installing any of them and I'm quite stumped.   I've got a debian unstable install on another pc with about the same package set installed (but different versions of course) and it runs pygtk apps fine.

I also can't find any mention of this error in any bug tracking system either for ubuntu or debian.  Any ideas?  I'm completely lost.

Thanks

---

### Post by alavaliant on 2006-02-16
Ok progress has been made but now I'm even more stumped.. It seems to be an issue with my personal settings in my home directory.   As any other userid/environment it works but not using my settings.  So far not a clue what one is causing it.. I may have to rebuild them from scratch :cry:

---

