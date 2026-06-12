---
title: "Installing the Widget Factory"
date: 2006-04-15
forum: General Help
---

### Post by mztriz on 2006-04-15
I'm a little confused with this program. I have downloaded it from here [http://www.stellingwerff.com/TheWidgetFactory/TheWidgetFactory-0.2.tar.bz2](http://www.stellingwerff.com/TheWidgetFactory/TheWidgetFactory-0.2.tar.bz2)

I'm not really sure what's going on I typed in ./configure and i get this ```
mztriz@ubuntu2:~/Desktop/TheWidgetFactory-0.2$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
mztriz@ubuntu2:~/Desktop/TheWidgetFactory-0.2$

``` 

The weird thing is, it does have the those files that it claims are missing? I'm probably just doing something wrong. Anyway if anyone knows...


Thanks,
Ava. :D

---

### Post by oscar on 2006-04-15
I think you have to run autogen.sh instead.
I get an error though:
```
checking for GTK... configure: error: GTK+-2.4 is required to compile gtk-engines
```

[edit]
I found a way you can run it without having to compile it. Debian unstable provides a package that works (for me at least) in ubuntu:
[http://packages.debian.org/unstable/gnome/thewidgetfactory](http://packages.debian.org/unstable/gnome/thewidgetfactory)

download the package that is right for your architecture (for me i386) and install it. Then run it using the twf command.

---

### Post by mztriz on 2006-04-15
[QUOTE=oscar]I think you have to run autogen.sh instead.
I get an error though:
```
checking for GTK... configure: error: GTK+-2.4 is required to compile gtk-engines
```

[edit]
I found a way you can run it without having to compile it. Debian unstable provides a package that works (for me at least) in ubuntu:
[http://packages.debian.org/unstable/gnome/thewidgetfactory](http://packages.debian.org/unstable/gnome/thewidgetfactory)

download the package that is right for your architecture (for me i386) and install it. Then run it using the twf command.[/QUOTE]

Oh nice, I'll give that a try. Thank you! :)

---

### Post by mztriz on 2006-04-15
ahh, it seems to want older versions of things that I already have.

```
Selecting previously deselected package thewidgetfactory.
(Reading database ... 114382 files and directories currently installed.)
Unpacking thewidgetfactory (from .../thewidgetfactory_0.2.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of thewidgetfactory:
 thewidgetfactory depends on libcairo2 (>= 1.0.2-2); however:
  Version of libcairo2 on system is 1.0.2-0ubuntu1.1.
 thewidgetfactory depends on libfreetype6 (>= 2.1.10-1); however:
  Version of libfreetype6 on system is 2.1.7-2.4ubuntu1.
 thewidgetfactory depends on libglib2.0-0 (>= 2.10.0); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 thewidgetfactory depends on libpango1.0-0 (>= 1.12.0); however:
  Version of libpango1.0-0 on system is 1.10.1-0ubuntu1.
 thewidgetfactory depends on libxrender1 (>= 1:0.9.0.2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing thewidgetfactory (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 thewidgetfactory

```

EDIT: It works anyway thanks oscar ;D

---

