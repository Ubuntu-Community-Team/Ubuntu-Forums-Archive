---
title: "Getting error on make"
date: 2010-12-04
forum: General Help
---

### Post by karthick87 on 2010-12-04
```
karthick@Ubuntu-desktop:~/pidgin-nudge-read-only$ make
[CC] pidginnudge.o
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
Package purple was not found in the pkg-config search path.
Perhaps you should add the directory containing `purple.pc'
to the PKG_CONFIG_PATH environment variable
No package 'purple' found
Package gobject-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gobject-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gobject-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
pidginnudge.c:3:18: warning: glib.h: No such file or directory
pidginnudge.c:5:23: warning: gtkplugin.h: No such file or directory
pidginnudge.c:7:20: error: notify.h: No such file or directory
pidginnudge.c:8:20: error: plugin.h: No such file or directory
pidginnudge.c:9:21: error: version.h: No such file or directory
pidginnudge.c:10:21: error: gtkconv.h: No such file or directory
pidginnudge.c:11:19: error: debug.h: No such file or directory
pidginnudge.c:15: error: expected ‘)’ before ‘*’ token
pidginnudge.c:43: error: expected ‘)’ before ‘*’ token
pidginnudge.c:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_load’
pidginnudge.c:54: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_unload’
pidginnudge.c:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘info’
pidginnudge.c:94: error: expected ‘)’ before ‘*’ token
pidginnudge.c:98: warning: data definition has no type or storage class
pidginnudge.c:98: warning: type defaults to ‘int’ in declaration of ‘PURPLE_INIT_PLUGIN’
pidginnudge.c:98: warning: parameter names (without types) in function declaration
make: *** [pidginnudge.o] Error 1

```

Can anyone help??

---

### Post by karthick87 on 2010-12-04
Bump for a move...!

---

### Post by Spyderkid on 2010-12-04
do you need to "make clean"?

---

### Post by karthick87 on 2010-12-04
yes i did.

---

### Post by SeijiSensei on 2010-12-04
Did you try and fix these errors?

> Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable

1) Do you have pidgin installed?

2) Did you try running "sudo apt-get build-dep pidgin" to download any required libraries and headers?

3) It appears this program uses "pkg-config," an entirely different method of installation from Ubuntu's .deb.  You need to at least install pkg-config before trying to compile a program like this.

4) Is it really unavailable from the repositories?

---

### Post by karthick87 on 2010-12-04
Uh i am really not aware of that.Can you explain me step by step?

---

### Post by asmoore82 on 2010-12-05
Do you have the pidgin development files? ```
sudo apt-get install pidgin-dev
```

---

