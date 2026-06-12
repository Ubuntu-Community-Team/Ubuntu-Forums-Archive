---
title: "Ibus and Skype"
date: 2011-03-02
forum: General Help
---

### Post by Falc7 on 2011-03-02
I type Chinese using ibus, but it dosen't seem to work at all with skype, is there anything I can do to get it working?

Ibus isen't working for me in libre office either.

---

### Post by Falc7 on 2011-03-09
Tried this but it still dosent work
[http://code.google.com/p/ibus/issues/detail?id=613](http://code.google.com/p/ibus/issues/detail?id=613)

---

### Post by Zorael on 2011-03-10
Which of those suggestions did you try? Kubuntu has **im-switch**, so there's no need for modifying **~/.bashrc**.

You want to:
[list=1][*]remove any such interfering stuff from **~/.bashrc**
[*]make sure you have all the ibus libraries installed ([**ibus-gtk**](apt://ibus-gtk), [**ibus-qt4**](apt://ibus-qt4))
[*]run **im-switch** and pick ibus
[*]logout and back in[/list]
If it still doesn't work, please paste the terminal output of the following;
```
echo -e "GTK:\t$GTK_IM_MODULE\nQt:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS\n\n$(im-switch -l)\n\n$(dpkg -l \*ibus* | grep ^ii | grep -v usb)\n\n$(ps ux | grep uim | grep -v "grep --color=auto")"
```
All in one line for easy copy/pasting. The command is safe.

---

### Post by Falc7 on 2011-03-16
okay i edited out those lines, im-switch didn't help me type chinese in skype though

```
jamie@jamie-Inspiron-N5010:~$ echo -e "GTK:\t$GTK_IM_MODULE\nQt:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS\n\n$(im-switch -l)\n\n$(dpkg -l \*ibus* | grep ^ii | grep -v usb)\n\n$(ps ux | grep uim | grep -v "grep --color=auto")"
GTK:    ibus
Qt:     ibus
XMOD:   @im=ibus

Your input method setup under en_GB locale as below.
=======================================================
The configuration "/home/jamie/.xinput.d/en_GB" is defined as a link pointing to
ibus
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - manual mode
  link currently points to none
default - priority 10
default-xim - priority 0
none - priority 0
Current 'best' version is 'default'.
=======================================================
The available input method configuration files are:
default default~ default-xim ibus ibus-kde lo-gtk none th-gtk th-xim 
=======================================================

ii  ibus                                 1.3.7-1ubuntu4                                    New input method framework using dbus
ii  ibus-gtk                             1.3.7-1ubuntu4                                    New input method framework using dbus
ii  ibus-pinyin                          1.3.10-1                                          pinyin engine for ibus
ii  ibus-pinyin-db-open-phrase           1.3.10-1                                          pinyin engine for ibus, open-phrase database
ii  ibus-qt4                             1.3.0-1                                           qt-immodule for ibus (QT4)
ii  ibus-table                           1.3.0.20100621-1                                  table engine for IBus
ii  ibus-table-wubi                      1.2.0.20090715-1ubuntu1                           Wubi input method based on table engine of ibus
ii  libibus-qt1                          1.3.0-1                                           qt-immodule for ibus (QT4)
ii  libibus2                             1.3.7-1ubuntu4                                    New input method framework using dbus
ii  plasma-widget-kimpanel-backend-ibus  4:4.5.5-0ubuntu1ppa1                              addons for KDE 4 Plasma - universal input method widget
ii  python-ibus                          1.3.7-1ubuntu4                                    New input method framework using dbus



```

---

### Post by Falc7 on 2011-03-24
bump

---

### Post by Zorael on 2011-03-24
I think I know what's causing this. Have you upgraded to KDE 4.6 yet?

---

### Post by Falc7 on 2011-03-26
No not yet, i'm on 4.5.5

---

### Post by Zorael on 2011-03-27
Right. I wrote a long post about the bug in question, but after downloading and looking at the contents of the 4.5.5 kdm .deb file I'm not so sure anymore.

Try this in a terminal and see if it's just not merely ibus crashing (ignore the dollar sign but you need the dot and the space before the path);
```
$ . /etc/X11/Xsession.d/80im-switch
```
It might not miraculously fix everything (since it's being run so late in the startup process), but we mostly want to look at the terminal output anyway.

That's the script that is supposed to get run on session start, that loads your input method settings and starts the needed daemon. Looking at your output from 'ps ux | grep ibus', it either hasn't been started or it crashed.

In the 4.6 betas (4.5.85 and onwards), there was a regression that caused the scripts in **/etc/X11/Xsession.d/** to not get run at all, and so im-switch functionality broke completely. That's what I suspected was causing this at first, but now I have doubts.

---

### Post by Falc7 on 2011-03-28
I'm having several other problems with ibus, which are as follows. No character candidates appear (if i type 'ni' a whole list of possible characters that come from 'ni' should appear), and no language bar appears either, this makes it very difficult to type anything. Both of these things are kinda essential. I have checked the settings, and I have ticked the box marked 'show icon on system tray' and 'show language bar when active' but neither of them seem to work

Also as mentioned ibus dosen't work in Libreoffice or skype

```
jamie@jamie-Inspiron-N5010:~$ . /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_GB.
Start IM through /home/jamie/.xinput.d/en_GB linked to /etc/X11/xinit/xinput.d/ibus.
jamie@jamie-Inspiron-N5010:~$ current session already has an ibus-daemon.

```

Edit: I reinstalled ibus, and the language bar came back, but then i lost the ability to type anything (including English) into Libreoffice

---

### Post by Zorael on 2011-04-04
Not being able to input into certain applications is usually indicative that your input method can't (or hasn't) loaded the plugins needed for the window framework that your application uses. 

The '**echo -e "GTK:\t$GTK_IM_MODULE\nQt:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS\n**' part of the oneliner checks to see that you have the needed environmental variables set up, which you seemed to have. You then both have **[ibus-qt4](apt://ibus-qt4)** and **[ibus-gtk](apt://ibus-gtk)** installed, so the needed plugins themselves should exist on your system.

Hmm, I notice now that I made a typo in the oneliner; the last part that is to check if you have the ibus daemon running in the background. The results you posted from running '**. /etc/X11/Xsession.d/80im-switch**' suggests that it is running, but nevertheless, this bit should make it obvious.
```
$ ps ux | grep **ibus** | grep -v "grep --color=auto"
```

If...
[list][*]the plugins are installed
[*]the environment variables point to them properly
[*]and the daemon itself is running[/list]
...everything *should* work.

---

### Post by Falc7 on 2011-04-07
After an update, now both skype and libre office work fine :D

But QQ for linux still dosen't work, how can i get the input method to load the plugins for the window framework that QQ for linux uses?


```
ps ux | grep ibus | grep -v "grep --color=auto"jamie@jamie-Inspiron-N5010:~$ ps ux | grep ibus | grep -v "grep --color=auto"
jamie     4347  0.0  0.0  67436  3012 ?        Sl   12:59   0:00 /usr/bin/ibus-daemon --xim
jamie     4363  0.0  0.0 137424  3904 ?        Sl   12:59   0:00 /usr/lib/ibus/ibus-gconf
jamie     4365  0.1  0.7 298988 28208 ?        S    12:59   0:01 python /usr/share/ibus/ui/gtk/main.py
jamie     4367  0.0  0.1 136124  6100 ?        S    12:59   0:00 /usr/lib/ibus/ibus-x11 --kill-daemon
jamie     4437  0.0  0.1  76896  5184 ?        S    12:59   0:00 /usr/lib/ibus-pinyin/ibus-engine-pinyin --ibus
jamie@jamie-Inspiron-N5010:~$ 

```

---

### Post by Zorael on 2011-04-07
I'm not familiar with QQ and I don't see it in the repositories, so I can't easily see what dependencies it has. But from minor googling, it seems like it is written in GTK, and as such it ought to work with what you already have installed.

Have you installed a 32-bit version of it onto a 64-bit installation? If so, it could be related to [this bug](https://bugs.launchpad.net/ibus/+bug/646954). There seems to have been a fix released for this in version **20090808ubuntu11** of package **ia32-libs**. It doesn't seem to be in the maverick repositories (yet?), but it is in natty. I managed to install it manually onto my machine, at least.

Get the deb from [packages.ubuntu.com](http://packages.ubuntu.com/natty/ia32-libs[/url), and install it with '**sudo dpkg -i ia32-libs_20090808ubuntu11_amd64.deb**'. In my case it complained about **lib32ncursesw5** not being installed, so I just grabbed that from the maverick repositories with '**sudo aptitude install lib32ncursesw5**', and then it configured ia32-libs properly.

```
zorael@fortress:/storage/downloads$ **sudo dpkg -i ia32-libs_20090808ubuntu11_amd64.deb** 
(Reading database ... 136673 files and directories currently installed.)
Preparing to replace ia32-libs 20090808ubuntu9 (using ia32-libs_20090808ubuntu11_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on lib32ncursesw5; however:
  Package lib32ncursesw5 is not installed.
dpkg: error processing ia32-libs (--install):
 dependency problems - leaving unconfigured
Processing triggers for libglib2.0-0 ...
Errors were encountered while processing:
 ia32-libs

zorael@fortress:/storage/downloads$ **sudo aptitude install lib32ncursesw5**
The following NEW packages will be installed:
  lib32ncursesw5 
The following packages will be REMOVED:
  lib32ffi5{u} 
The following partially installed packages will be configured:
  ia32-libs 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 372kB of archives. After unpacking 590kB will be used.
Do you want to continue? [Y/n/?] 
Get:1 http://se.archive.ubuntu.com/ubuntu/ maverick/main lib32ncursesw5 amd64 5.7+20100626-0ubuntu1 [372kB]
Fetched 372kB in 1s (189kB/s)          
Selecting previously deselected package lib32ncursesw5.
(Reading database ... 137233 files and directories currently installed.)
Unpacking lib32ncursesw5 (from .../lib32ncursesw5_5.7+20100626-0ubuntu1_amd64.deb) ...
(Reading database ... 137246 files and directories currently installed.)
Removing lib32ffi5 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Setting up lib32ncursesw5 (5.7+20100626-0ubuntu1) ...
Setting up ia32-libs (20090808ubuntu11) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
Current status: 0 broken [-1].
```

---

### Post by Falc7 on 2011-04-10
Yes I have installed a 32 bit application onto my 64 bit OS.

I installed the deb just fine, but now the QQ program starts and runs, but the application window dosen't get displayed

---

### Post by Zorael on 2011-04-11
Try starting it from the terminal and see if it outputs any interesting error messages. Perhaps this solution with natty's ia32-libs plain won't work.

---

### Post by Falc7 on 2011-04-12
Here is the output

```
jamie@jamie-Inspiron-N5010:~$ qq

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `GDK_IS_PIXBUF (src_pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `GDK_IS_PIXBUF (src_pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `GDK_IS_PIXBUF (src_pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `GDK_IS_PIXBUF (src_pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `GDK_IS_PIXBUF (src_pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: Object class GtkComboBoxEx doesn't implement property 'editing-canceled' from interface 'GtkCellEditable'

(qq:6050): GLib-GObject-CRITICAL **: Object class GtkEntryEx doesn't implement property 'editing-canceled' from interface 'GtkCellEditable'

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_subpixbuf: assertion `GDK_IS_PIXBUF (src_pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GdkPixbuf-CRITICAL **: gdk_pixbuf_add_alpha: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(qq:6050): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(qq:6050): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(qq:6050): Gtk-WARNING **: Loading IM context type 'ibus' failed
  
```

---

### Post by jaambutt on 2011-04-12
**Best Answer - Chosen by Asker**

                               Offline- You can't contact anyone and if someone is online, it says they're offline.
Invisible- It looks like you are offline but you are online and you can chat with everyone.

---

### Post by Zorael on 2011-04-12
> **Falc7 said:**
> [code](qq:6050): Gtk-WARNING **: /usr/**[COLOR="Red"]lib[/COLOR]**/gtk-2.0/2.10.0/immodules/im-ibus.so: **wrong ELF class: ELFCLASS64**

I'm not sure why it's trying to load the library from **/usr/lib** there instead of **/usr/lib32**.

You do have a **/usr/lib32/gtk-2.0/2.10.0/immodules/im-ibus.so** file now with the new ia32-libs, right?

---

### Post by Falc7 on 2011-04-16
Yep I do indeed have that file, is there any way to change where its looking?

---

### Post by Falc7 on 2011-04-27
bump

---

### Post by Zorael on 2011-04-28
I'm not sure. Try preloading the library.

```
$ LD_PRELOAD=/usr/lib32/gtk-2.0/2.10.0/immodules/im-ibus.so qq &
```

If the **qq** executable is a script (and not a binary), it may be that you can do a textual search of it and see if the im-ibus.so file is mentioned somewhere. Perhaps you can change the path there.

---

