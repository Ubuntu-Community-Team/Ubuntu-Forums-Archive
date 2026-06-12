---
title: "Building Firefox from source"
date: 2006-02-14
forum: General Help
---

### Post by jofre on 2006-02-14
Hi lads, 

I am trying to build firefox from source:) . I downloaded the source and:
$ sudo tar -xjvf firefox-1.5-source.tar.bz2 -C /opt

I am following the step in:
[http://www.linux-sxs.org/internet_browsing/firefox_from_source.html](http://www.linux-sxs.org/internet_browsing/firefox_from_source.html)

The problem is that when i do:
 sudo make -f client.mk build

I get and error:
checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
*** Fix above errors and then restart with "make -f client.mk build"
make[1]: *** [configure] Error 1
make[1]: Leaving directory `/opt/mozilla'
make: *** [/opt/mozilla/../firefox-build/Makefile] Error 2


I check in synaptic and it look to me that was already installed.:neutral:  

Any ideas?:-k 
Thanks, Jofre

PD: I had post it previously in begginers talk, but I receive a reply wondering why in "begginers talk". So I decided to post it here. It is not my intention to cross-posts or whatever you call it to get a quicker answer.

---

### Post by Greg2 on 2006-02-14
You will need to install the libgtk2.0-dev package with synaptic or apt-get.

---

### Post by gremlin hunter on 2006-02-14
Okay.

Try adding /usr/lib/pkgconfig to PKG_CONFIG_PATH.
[I]
george@george:/usr/lib/pkgconfig$ ls gtk+-2.0.pc
gtk+-2.0.pc[/I]
```

george@george:/usr/lib/pkgconfig$ echo $PKG_CONFIG_PATH

george@george:/usr/lib/pkgconfig$ export PKG_CONFIG_PATH=/usr/lib/pkgconfig/
george@george:/usr/lib/pkgconfig$ echo $PKG_CONFIG_PATH
/usr/lib/pkgconfig/
```

---

### Post by jofre on 2006-02-14
I try to change the PKG_CONFIG_PATH , but it did not work. Then I apt-get libgtk2.0-dev, and it was fine. Until...:confused: :

checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
checking for libIDL-config... no
checking for libIDL - version >= 0.6.3... no
*** The libIDL-config script installed by libIDL could not be found
*** If libIDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the LIBIDL_CONFIG environment variable to the
*** full path to libIDL-config.
checking for libIDL-2.0 >= 0.8.0... Package libIDL-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libIDL-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libIDL-2.0' found
configure: error: Library requirements (libIDL-2.0 >= 0.8.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
*** Fix above errors and then restart with "make -f client.mk build"
make[1]: *** [configure] Error 1
make[1]: Leaving directory `/opt/mozilla'
make: *** [/opt/mozilla/../firefox-build/Makefile] Error 2
jofre@edoras:/opt/mozilla$ echo $PKG_CONFIG_PATH
/usr/

I am slightly lost:-k . I guess some day I would get it:-k . That day it will be a nice day:cool:

---

### Post by jofre on 2006-02-14
I just tried:

$ sudo apt-get build-dep firefox-1.5-source.tar.bz2
 Reading package lists... Done
 Building dependency tree... Done
$

So I don't think it work...

---

### Post by gremlin hunter on 2006-02-14
> I try to change the PKG_CONFIG_PATH , but it did not work.

Can you elaborate?
```

sudo apt-get install libgtk2.0-dev libidl-dev
export PKG_CONFIG_PATH=/usr/lib/pkgconfig/
```

^try these commands

---

### Post by jofre on 2006-02-14
hi again,

did not work=the same error still appear

the apt-get libidl-dev work fine. 

I think i pass the stage of 
"checkin for ..."

But i get a HELL of errors, that look like errors in the code itself, something strange when i think that i am using firefox1.5 to write this lines... Just some lines of the errors (there are far more!):

/opt/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:906: error: ‘treeroot’ undeclared (first use in this function)
/opt/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:909: warning: initialization makes pointer from integer without a cast
/opt/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:913: error: ‘user_data’ undeclared (first use in this function)
/opt/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:925: error: ‘Widget’ undeclared (first use in this function)
/opt/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:925: error: syntax error before ‘child’
/opt/mozilla/widget/src/gtkxtbin/gtk2xtbin.c:926: error: ‘child’ undeclared (first use in this function)
make[3]: *** [gtk2xtbin.o] Error 1
make[3]: Leaving directory `/opt/firefox-build/widget/src/gtkxtbin'
make[2]: *** [tier_9] Error 2
make[2]: Leaving directory `/opt/firefox-build'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/opt/firefox-build'
make: *** [build] Error 2


Don't worry. I think I will give up...

Just one question, this is my first attempt to build something from source. It is normally so complicated or it is just I am a new...

Anyway, thanks for all the help.
Jofre.

---

### Post by gremlin hunter on 2006-02-14
Providing you have all the dependencys it is usually alot easier. Although linux problem scills develop so that helps alot.

---

