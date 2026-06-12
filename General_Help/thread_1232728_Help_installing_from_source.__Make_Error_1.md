---
title: "Help installing from source.  Make Error 1"
date: 2009-08-05
forum: General Help
---

### Post by gldearman on 2009-08-05
Hello, all,

I am getting an error when I run the command "make" to install an application developed with Qt4.  I think the error message is telling me that I am missing some Qt plugins, but I'm not sure.

I am attempting to install an application called Wally.  (It's homepage is [here]("http://www.becrux.com/index.php?page=projects&name=wally").)

Wally requires Qt4, so I installed two packages from the repositories:

```

libqt4-dev
qt4-qmake
```

After unpacking, I followed the installation instructions, which were:

```

$ qmake
$ make
$ sudo make install
```

The qmake command created a makefile as expected.  When I ran make, though, it ran for some time, then gave me an error message and terminated.  This is the last few lines of the output (the part with the error message):
```

build.main/o: In function 'global constructors keyed to main':
main.cpp:(text+0x20d): undefined reference to 'qt_plugin_instance_qgif()'
main.cpp:(text+0x219): undefined reference to 'qt_plugin_instance_qico()'
main.cpp:(text+0x225): undefined reference to 'qt_plugin_instance_qjpeg()'
main.cpp:(text+0x231): undefined reference to 'qt_plugin_instance_qmng()'
main.cpp:(text+0x23d): undefined reference to 'qt_plugin_instance_qsvg()'
main.cpp:(text+0x249): undefined reference to 'qt_plugin_instance_qtiff()'
collect2: ld returned 1 exit status
make: *** [wally] Error 1
```

OK, so what does this mean?  Am I right in assuming that I am missing some Qt4 plugins, and installing them will make this error go away?  Where do I get these plugins?  (And why didn't this show up as a missing dependency when I created the makefile?)

Can anyone help me out and tell me what to do next?  I appreciate it!'

Thanks!

---

### Post by gldearman on 2009-08-06
Hi, all,

I figured this out.  Will post the solution here, in the unlikely event that anyone in the future is searching this forum because of this same problem.

I installed the package qt4-dev-tools.   It appears to contain the missing plugins, and now make works fine.  Gotta love missing dependencies that aren't identified when creating the makefile (grrrr).

Thanks to everyone who read my post, even if none of you know the answer!

---

