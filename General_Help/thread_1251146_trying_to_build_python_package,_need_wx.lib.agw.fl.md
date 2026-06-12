---
title: "trying to build python package, need wx.lib.agw.flatmenu?"
date: 2009-08-27
forum: General Help
---

### Post by uschxc on 2009-08-27
i'm trying to install this package i found on Lifehacker called Notalon

[http://bitbucket.org/saketh/notalon/overview/](http://bitbucket.org/saketh/notalon/overview/)

and i'm getting the following error on install:

```
Traceback (most recent call last):
  File "./setup.py", line 19, in <module>
    import notalonlib.widgets.dialogs.about as About
  File "/home/uschxc/Apps/Notalon-0.5.0/notalonlib/__init__.py", line 14, in <module>
    from window import NotalonWindow
  File "/home/uschxc/Apps/Notalon-0.5.0/notalonlib/window.py", line 21, in <module>
    import wx.lib.agw.flatmenu as FM
ImportError: No module named agw.flatmenu

```

i originally didn't have python-wxgtk2.8 installed but that doesn't seem to have the library this is looking for although it looks like one of the base libraries from wxpython.org

any ideas?

---

### Post by K6EF on 2009-08-27
This does not appear to be isolated to you. I am having exactly the same issue.

Not sure what packages I might be missing, I think I've installed most of the wx packages.

---

### Post by bchurchill on 2009-08-27
I think what's going on is that wx.lib.agw.flatmenu was introduced in version 2.8.9.2 of the wxpython library while the Ubuntu repository is based on 2.8.9.1 ([http://www.wxpython.org/docs/api/wx.lib.agw.flatmenu-module.html](http://www.wxpython.org/docs/api/wx.lib.agw.flatmenu-module.html) and [http://packages.ubuntu.com/jaunty/libwxbase2.8-0](http://packages.ubuntu.com/jaunty/libwxbase2.8-0))

So this probably won't be included until Ubuntu 9.10 (or perhaps later).  So it looks like you'll need to follow all the insructions on the [http://www.wxpython.org/](http://www.wxpython.org/) page to compile the library yourself (probably quite a bit of work).  Good luck!  Make sure you install all the dependencies ahead of time.

---

### Post by uschxc on 2009-08-28
> **bchurchill said:**
> I think what's going on is that wx.lib.agw.flatmenu was introduced in version 2.8.9.2 of the wxpython library while the Ubuntu repository is based on 2.8.9.1 ([http://www.wxpython.org/docs/api/wx.lib.agw.flatmenu-module.html](http://www.wxpython.org/docs/api/wx.lib.agw.flatmenu-module.html) and [http://packages.ubuntu.com/jaunty/libwxbase2.8-0](http://packages.ubuntu.com/jaunty/libwxbase2.8-0))

So this probably won't be included until Ubuntu 9.10 (or perhaps later).  So it looks like you'll need to follow all the insructions on the [http://www.wxpython.org/](http://www.wxpython.org/) page to compile the library yourself (probably quite a bit of work).  Good luck!  Make sure you install all the dependencies ahead of time.

i've already left a note with the developer informing him that there are _no_ documents referring to dependencies/prerequisites.  

its not an app that i desperately need.  i heart ubuntu and i only run into issues like this 3-4 times a year as far as their repositories not being up to date enough to run 0day apps.  i can wait a couple months... i'm sure they'll update python-wxgtk2.8 on the next iteration end of october.  thanks for the info... however can you tell me where/how you figured out that it a library in the newest version of python?  i didn't look for that but didn't come across anything listing version numbers and new libraries.

---

### Post by bchurchill on 2009-08-28
> **uschxc said:**
> i've already left a note with the developer informing him that there are _no_ documents referring to dependencies/prerequisites.  

its not an app that i desperately need.  i heart ubuntu and i only run into issues like this 3-4 times a year as far as their repositories not being up to date enough to run 0day apps.  i can wait a couple months... i'm sure they'll update python-wxgtk2.8 on the next iteration end of october.  thanks for the info... however can you tell me where/how you figured out that it a library in the newest version of python?  i didn't look for that but didn't come across anything listing version numbers and new libraries.

Check out [http://www.wxpython.org/download.php#prerequisites](http://www.wxpython.org/download.php#prerequisites) for the dependencies.

I by searching for agw.flatmenu, which I found is actually the wx.lib.agw.flatmenu.  Then I searched the ubuntu repositories for such a file, but came up blank.  It looked like something that should have been in python-wxgtk2.8.  And in fact, on the python api page (linked previously, found by googling), agw.flatmenu was included.  So then I looked at versions and found that the awg.flatmenu is listed as being introduced in this newer version.

---

