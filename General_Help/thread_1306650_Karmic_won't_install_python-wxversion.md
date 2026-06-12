---
title: "Karmic won't install python-wxversion"
date: 2009-10-30
forum: General Help
---

### Post by marcusesses on 2009-10-30
I recently upgraded to Karmic, and I am having troubles getting my wireless to work. 

I initially thought the problem was a failure to detect drivers or a change to a config file. 


However, the wireless managers I tried (currently using wicd) were able to detect networks, I was just unable to access them. When installing wicd, I received this error.

```

Setting up python-wxversion (2.8.10.1-0ubuntu1) ...
Compiling /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wxversion.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: error processing python-wxversion (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up wicd (1.6.1-3ubuntu1) ...
 * Starting Network connection manager wicd                              [ OK ] 

Processing triggers for menu ...
Errors were encountered while processing:
 python-wxversion
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

ANyone have any thoughts on this? Seems the problem is with a package called python-wxversion

---

### Post by Giblet5 on 2009-10-30
This might be an upgrade issue.

I installed wicd this morning and it went perfectly. That's a clean install for testing.

You can try reinstalling the python-wxversion package, but it may do the same thing.

---

### Post by marcusesses on 2009-10-30
> 
You can try reinstalling the python-wxversion package, but it may do the same thing.

```

XXX@home:~$ sudo apt-get install python-wxversion 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-wxversion is already the newest version.
python-wxversion set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-wxversion (2.8.10.1-0ubuntu1) ...
Compiling /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wxversion.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: error processing python-wxversion (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-wxversion
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Yup. Any ideas how to fix this?

And what's the difference between a clean install and an update?

---

### Post by papirosko on 2009-11-01
i have the same problem 
```
file does not exist: /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wxversion.py
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088; python-wxversion (--configure):
 &#1087;&#1086;&#1076;&#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1089;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1081; post-installation &#1074;&#1086;&#1079;&#1074;&#1088;&#1072;&#1090;&#1080;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; 1
&#1055;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1087;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1080; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080;:
 python-wxversion
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Hayjumper on 2009-11-02
I also had this problem on update from Jaunty to Karmic, also entangled with several other packages.  I was able to resolve the problem by locating a copy of the wxversion.py file in python-wx2.8 source code, and copying it to the following locations:

/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wxversion.py
/usr/lib/python2.5/dist-packages/wx-2.8-gtk2-unicode/wxversion.py

YMMV, good luck...

---

### Post by cumfy on 2010-07-26
I am having this problem on jaunty.

Was originally trying to get the wxpython demos to work; and the default wxpython doesn't recognise the "inpection module".Apparently the demos only work w the vey latest release.

So tried to uninstall and install latest version according to:
[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)


Now just get

   File "Grid.py", line 2, in <module>
    import  wx
ImportError: No module named wx


Great! So nothing works now.
Checked /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wxversion.py was there as per last post. Yes it was.

Glad I am not only one with this; but no solutions seem to be out there.
Any ideas ??

---

