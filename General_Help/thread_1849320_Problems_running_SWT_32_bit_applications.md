---
title: "Problems running SWT 32 bit applications"
date: 2011-09-24
forum: General Help
---

### Post by rodrigogp on 2011-09-24
Hi,

I'm running eclipse 3.5 32 bit with java 32 and I'm trying to run an SWT 32bit application I'm working on. I was using windows but I want to be able to do it from ubuntu, so I added the SWT jar for linux

I'm running Ubuntu 11.04 64bit

I've tried the workarounds suggested here

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/781870?comments=all](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/781870?comments=all)

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=345477](https://bugs.eclipse.org/bugs/show_bug.cgi?id=345477)

But not working. 

I'm using the following script to run eclipse:

```
export UBUNTU_MENUPROXY=0
export GDK_PIXBUF_MODULE_FILE=/usr/lib32/gdk-pixbuf-2.0/2.10.0/loaders.cache
/home/rodrigo/Apps/eclipse_jee_galileo_lvs/eclipse
```

Then, when I try to run my app I get the following errors:

```
(SWT:3242): Gtk-WARNING **: Loading IM context type 'ibus' failed

(SWT:3242): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong
ELF class: ELFCLASS64

(SWT:3242): Gtk-WARNING **: Loading IM context type 'ibus' failed
Exception in thread "main" java.lang.RuntimeException:
java.lang.NullPointerException
 at
com.lvsint.abp.admin.AbpApplicationLauncher.launch(AbpApplicationLauncher.java:61)
 at
com.lvsint.abp.richclient.eventcreator.EventCreatorShell.main(EventCreatorShell.java:2237)
Caused by: java.lang.NullPointerException
 at org.eclipse.swt.accessibility.Accessible.isValidThread(Unknown Source)

```

I also tried with the snippet:

[http://dev.eclipse.org/viewcvs/viewvc.cgi/org.eclipse.swt.snippets/src/org/eclipse/swt/snippets/Snippet166.java?view=co](http://dev.eclipse.org/viewcvs/viewvc.cgi/org.eclipse.swt.snippets/src/org/eclipse/swt/snippets/Snippet166.java?view=co)

And when I run it I get this in the error log:

```
/usr/lib/gio/modules/libgiobamf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiobamf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
```

And when I close it I get the same logs as when running my app:

```
(SWT:3593): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong
ELF class: ELFCLASS64

(SWT:3593): Gtk-WARNING **: Loading IM context type 'ibus' failed

(SWT:3593): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong
ELF class: ELFCLASS64

(SWT:3593): Gtk-WARNING **: Loading IM context type 'ibus' failed

(SWT:3593): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong
ELF class: ELFCLASS64

(SWT:3593): Gtk-WARNING **: Loading IM context type 'ibus' failed
```


Any idea on how to workaround this?
Thanks!

---

### Post by .... on 2011-09-24
The easiest way is to set up a 32-bit chroot. Otherwise, you're going to have to get 32-bit versions of the libs it keeps asking for and put them in /usr/lib32

---

### Post by rodrigogp on 2011-09-25
Hi,

I've never tried to set up a chroot so maybe it's a good moment to learn about that :) Anyway, I'll wait a bit more to see if somebody else propose other solutions

The libraries are already under /user/lib32/gtk-2.0 but the other approaches suggested in the links above didn't work for me

Thanks and regards

---

### Post by rodrigogp on 2011-09-30
Hi, I realized that I could try to run the app using SWT for 64 bit, so I changed java, swt and eclipse to the 64bit version

Now I don't get the error logs, but still getting NPE

Here you can find my post explaining the problems

[http://stackoverflow.com/questions/7602067/swt-gtk-64-bit-and-ubuntu-11-04-npe](http://stackoverflow.com/questions/7602067/swt-gtk-64-bit-and-ubuntu-11-04-npe)

or here

[http://www.eclipse.org/forums/index.php/m/731212/#msg_731212](http://www.eclipse.org/forums/index.php/m/731212/#msg_731212)

Any ideas? Don't know if it's a problem with the SWT version, with this Ubuntu version or what

Thanks

---

