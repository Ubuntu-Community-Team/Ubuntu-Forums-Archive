---
title: "Help me to install this emulator"
date: 2010-10-27
forum: General Help
---

### Post by asifnaz on 2010-10-27
I searched online and found this
[SIZE="5"][I]Hi fellows,

As retro games fan that i'm, here it's an EASY How to for you to install gngeo 0.7 with Xgngeo 1.6 Final.

1 - Download and Install gngeo 0.7 deb package bellow.

2 - Download the Xgngeo bellow and do this from the directory you download to:

sudo tar -vxjpf XGngeo-16.tar.bz2

cd XGngeo-16

sudo python setup.py install

NOW in the applications menu, there you have it XGngeo, when you enter the 1st time it will ask for you to give the right path to roms and bios.

Hope you enjoy this one[/I][/SIZE]
I have dowloaded and installed deb file but dont know how to install 2nd one using commands provided by that person .
Assume I have that .bz2 file downloaded on the desktop what command should I give to install the file

---

### Post by ubudog on 2010-10-27
Untar it using the graphical tool.  Go to the desktop, by clicking, not in the terminal.  Then double click on the .bz2 file, and select "extract".  Then that folder should be on the desktop.  Finish the steps.

After untaring:
```
cd Desktop/filename
```

```
sudo python setup.py install
```

Should do it, let me know if you have issues. :)

---

### Post by asifnaz on 2010-10-27
well see what i did
[I]asif@asif-desktop:~$ cd Desktop/XGngeo-16
asif@asif-desktop:~/Desktop/XGngeo-16$ 
asif@asif-desktop:~/Desktop/XGngeo-16$ sudo python setup.py install
[sudo] password for asif: 
running install
running build
running build_py
creating build
creating build/lib.linux-i686-2.6
creating build/lib.linux-i686-2.6/xgngeo
copying data/py/rominfos.py -> build/lib.linux-i686-2.6/xgngeo
copying data/py/history.py -> build/lib.linux-i686-2.6/xgngeo
copying data/py/command.py -> build/lib.linux-i686-2.6/xgngeo
copying data/py/configfile.py -> build/lib.linux-i686-2.6/xgngeo
copying data/py/__init__.py -> build/lib.linux-i686-2.6/xgngeo
copying data/py/emulator.py -> build/lib.linux-i686-2.6/xgngeo
running install_lib
creating /usr/local/lib/python2.6/dist-packages/xgngeo
copying build/lib.linux-i686-2.6/xgngeo/rominfos.py -> /usr/local/lib/python2.6/dist-packages/xgngeo
copying build/lib.linux-i686-2.6/xgngeo/history.py -> /usr/local/lib/python2.6/dist-packages/xgngeo
copying build/lib.linux-i686-2.6/xgngeo/command.py -> /usr/local/lib/python2.6/dist-packages/xgngeo
copying build/lib.linux-i686-2.6/xgngeo/configfile.py -> /usr/local/lib/python2.6/dist-packages/xgngeo
copying build/lib.linux-i686-2.6/xgngeo/__init__.py -> /usr/local/lib/python2.6/dist-packages/xgngeo
copying build/lib.linux-i686-2.6/xgngeo/emulator.py -> /usr/local/lib/python2.6/dist-packages/xgngeo
byte-compiling /usr/local/lib/python2.6/dist-packages/xgngeo/rominfos.py to rominfos.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/xgngeo/history.py to history.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/xgngeo/command.py to command.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/xgngeo/configfile.py to configfile.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/xgngeo/__init__.py to __init__.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/xgngeo/emulator.py to emulator.pyc
running install_data
creating /usr/local/share/xgngeo
creating /usr/local/share/xgngeo/img
copying data/img/key_START.png -> /usr/local/share/xgngeo/img
copying data/img/icon.png -> /usr/local/share/xgngeo/img
copying data/img/key_B.png -> /usr/local/share/xgngeo/img
copying data/img/key_D.png -> /usr/local/share/xgngeo/img
copying data/img/hotkey2.png -> /usr/local/share/xgngeo/img
copying data/img/key_C.png -> /usr/local/share/xgngeo/img
copying data/img/minilogo.png -> /usr/local/share/xgngeo/img
copying data/img/key_COIN.png -> /usr/local/share/xgngeo/img
copying data/img/europe.png -> /usr/local/share/xgngeo/img
copying data/img/key_LEFT.png -> /usr/local/share/xgngeo/img
copying data/img/key_RIGHT.png -> /usr/local/share/xgngeo/img
copying data/img/key_DOWN.png -> /usr/local/share/xgngeo/img
copying data/img/key_UP.png -> /usr/local/share/xgngeo/img
copying data/img/key_A.png -> /usr/local/share/xgngeo/img
copying data/img/japan.png -> /usr/local/share/xgngeo/img
copying data/img/hotkey1.png -> /usr/local/share/xgngeo/img
copying data/img/usa.png -> /usr/local/share/xgngeo/img
copying data/img/hotkey3.png -> /usr/local/share/xgngeo/img
copying data/img/hotkey4.png -> /usr/local/share/xgngeo/img
copying data/img/xgngeo.png -> /usr/local/share/xgngeo/img
copying data/img/chprod.png -> /usr/local/share/xgngeo/img
copying data/rominfos.xml -> /usr/local/share/xgngeo
copying data/rominfos.dtd -> /usr/local/share/xgngeo
copying LICENSE.txt -> /usr/local/share/xgngeo
creating /usr/local/share/xgngeo/doc
copying doc/xgngeo-doc.txt -> /usr/local/share/xgngeo/doc
creating /usr/local/share/applications
copying data/misc/xgngeo.desktop -> /usr/local/share/applications
creating /usr/local/share/xgngeo/locale
creating /usr/local/share/xgngeo/locale/es
creating /usr/local/share/xgngeo/locale/es/LC_MESSAGES
copying data/locale/es/LC_MESSAGES/xgngeo.mo -> /usr/local/share/xgngeo/locale/es/LC_MESSAGES
creating /usr/local/share/xgngeo/locale/de
creating /usr/local/share/xgngeo/locale/de/LC_MESSAGES
copying data/locale/de/LC_MESSAGES/xgngeo.mo -> /usr/local/share/xgngeo/locale/de/LC_MESSAGES
creating /usr/local/share/xgngeo/locale/fr
creating /usr/local/share/xgngeo/locale/fr/LC_MESSAGES
copying data/locale/fr/LC_MESSAGES/xgngeo.mo -> /usr/local/share/xgngeo/locale/fr/LC_MESSAGES
creating /usr/local/share/xgngeo/locale/pl
creating /usr/local/share/xgngeo/locale/pl/LC_MESSAGES
copying data/locale/pl/LC_MESSAGES/xgngeo.mo -> /usr/local/share/xgngeo/locale/pl/LC_MESSAGES
creating /usr/local/share/xgngeo/locale/pt_BR
creating /usr/local/share/xgngeo/locale/pt_BR/LC_MESSAGES
copying data/locale/pt_BR/LC_MESSAGES/xgngeo.mo -> /usr/local/share/xgngeo/locale/pt_BR/LC_MESSAGES
running install_egg_info
Writing /usr/local/lib/python2.6/dist-packages/XGngeo-16.egg-info
XGngeo start-up script put into `/usr/bin'.
asif@asif-desktop:~/Desktop/XGngeo-16$[/I]
[COLOR="Green"]It is installed but not working any idea what i did wrong here[/COLOR]

---

### Post by ubudog on 2010-10-27
How did you try to start it?

---

### Post by asifnaz on 2010-10-27
i went to games>XGngeo clicked it and nothing happens

---

### Post by ubudog on 2010-10-27
Type the following into the terminal and see if it gives any errors:

```
xgngeo
```

---

### Post by asifnaz on 2010-10-27
asif@asif-desktop:~$ xgngeo
Traceback (most recent call last):
  File "/usr/bin/xgngeo", line 39, in <module>
    execfile(os.path.join(package_dir, "__init__.py"))
IOError: [Errno 2] No such file or directory: '/usr/lib/python2.6/site-packages/xgngeo/__init__.py'
asif@asif-desktop:~$

---

### Post by ubudog on 2010-10-27
Well, there's the problem.  I'll do some Google searches and post back...

---

### Post by ubudog on 2010-10-27
Could you please give me a link of the how-to, so I can download and try to modify some stuff?

---

### Post by asifnaz on 2010-10-27
I really appreciate your help .Thank you for your precious time .This is why I love this great community of humans .

Oh I forgot to mention I am using lxd desktop instead of gnome

---

### Post by ubudog on 2010-10-27
> **asifnaz said:**
> I really appreciate your help .Thank you for your precious time .This is why I love this great community of humans .

Oh I forgot to mention I am using lxd desktop instead of gnome

No problem.

I don't think it would matter whether you use LXDE or GNOME, it's just a file missing error, or maybe even a simple misspelling. (in the program)

---

### Post by asifnaz on 2010-10-27
this link might help
[www.ubuntuhowtos.com](www.ubuntuhowtos.com)

---

### Post by ubudog on 2010-10-27
Thanks for the link, I'll see what I can do, and post back. :)

---

### Post by asifnaz on 2010-10-27
sorry that how to link is

[http://ubuntuforums.org/showthread.php?t=868884](http://ubuntuforums.org/showthread.php?t=868884)

---

### Post by ubudog on 2010-10-27
> **asifnaz said:**
> sorry that how to link is

[http://ubuntuforums.org/showthread.php?t=868884](http://ubuntuforums.org/showthread.php?t=868884)

Thanks.

---

### Post by ubudog on 2010-10-27
> **asifnaz said:**
> this link might help
[www.ubuntuhowtos.com](www.ubuntuhowtos.com)

This site does have some awesome tutorials...

---

### Post by ubudog on 2010-10-27
Have you tried the .deb yet?  You may need to uninstall the current version first, in order for that to work.

I'm off, until tomorrow. :)

---

### Post by asifnaz on 2010-10-27
> **ubudog said:**
> This site does have some awesome tutorials...

My pleasure if I can do a little favor of yours

---

### Post by ubudog on 2010-10-27
> **asifnaz said:**
> My pleasure if I can do a little favor of yours

:) Thanks.

---

### Post by ntrung90 on 2011-03-01
> **asifnaz said:**
> asif@asif-desktop:~$ xgngeo
Traceback (most recent call last):
  File "/usr/bin/xgngeo", line 39, in <module>
    execfile(os.path.join(package_dir, "__init__.py"))
IOError: [Errno 2] No such file or directory: '/usr/lib/python2.6/site-packages/xgngeo/__init__.py'
asif@asif-desktop:~$

[SIZE="3"][SIZE="4"][SIZE="3"][B]try this:

+ with root permission,

+ open /usr/lib/python2.6 and create the missing 'site-packages' and 'xgngeo' folders

+ open the XGngeo-16 package you've download.
the missing __init__.py file is in data/py subfolder of the package.
Just simply _copy all .py files_ to /usr/lib/python2.6/site-packages/xgngeo/

+ create /usr/share/xgngeo folder.
copy /data/img folder from the XGngeo-16 package to /usr/share/xgngeo

that's how it's done.
have fun.[/B][/SIZE][/SIZE][/SIZE]

---

### Post by ashickur.noor on 2011-05-24
> **ntrung90 said:**
> [SIZE="3"][SIZE="4"][SIZE="3"][B]try this:

+ with root permission,

+ open /usr/lib/python2.6 and create the missing 'site-packages' and 'xgngeo' folders

+ open the XGngeo-16 package you've download.
the missing __init__.py file is in data/py subfolder of the package.
Just simply _copy all .py files_ to /usr/lib/python2.6/site-packages/xgngeo/

+ create /usr/share/xgngeo folder.
copy /data/img folder from the XGngeo-16 package to /usr/share/xgngeo

that's how it's done.
have fun.[/B][/SIZE][/SIZE][/SIZE]
Thanks for the valuable help.

---

