---
title: "Unable to locate Gimpshop after installation"
date: 2009-07-10
forum: General Help
---

### Post by Solipsil on 2009-07-10
Hello

(beginner here)

I've just installed latest Gimpshop and installation went fine. However, I was unable to locate the program anywhere. I restarted the laptop, thinking the system needed to update settings to show the newly installed program but I still ca't find it. Looking for it in the terminal resulted in pretty much nothing. It returned ```
bash: gimpshop: command not found
```.
I'm running Linux Ubuntu 9.04.

Any help appreciated.

---

### Post by zvacet on 2009-07-11
System>preferences>main menu>graphics and see if it is there.Maybe it is but not checked.In terminal you can search for it with 

```
locate gimpshop
```

---

### Post by Solipsil on 2009-07-11
It's not listed under Graphics in Sys Preferences-Main Menu.
I ran the command in terminal and got this:

```
odessa@Mack:~$ locate gimpshop
/usr/doc/gimpshop-2.2.11
/usr/doc/gimpshop-2.2.11/AUTHORS
/usr/doc/gimpshop-2.2.11/COPYING
/usr/doc/gimpshop-2.2.11/ChangeLog
/usr/doc/gimpshop-2.2.11/HACKING
/usr/doc/gimpshop-2.2.11/INSTALL
/usr/doc/gimpshop-2.2.11/LICENSE
/usr/doc/gimpshop-2.2.11/NEWS
/usr/doc/gimpshop-2.2.11/README
/usr/doc/gimpshop-2.2.11/README.i18n
/usr/doc/gimpshop-2.2.11/README.win32
/usr/doc/gimpshop-2.2.11/docs
/usr/doc/gimpshop-2.2.11/docs/Makefile
/usr/doc/gimpshop-2.2.11/docs/Makefile.am
/usr/doc/gimpshop-2.2.11/docs/Makefile.in
/usr/doc/gimpshop-2.2.11/docs/Wilber.svg
/usr/doc/gimpshop-2.2.11/docs/Wilber.xcf.gz
/usr/doc/gimpshop-2.2.11/docs/Wilber.xcf.gz.README
/usr/doc/gimpshop-2.2.11/docs/Wilber_Construction_Kit.xcf.gz
/usr/doc/gimpshop-2.2.11/docs/gimp-2.2.1
/usr/doc/gimpshop-2.2.11/docs/gimp-remote-2.2.1
/usr/doc/gimpshop-2.2.11/docs/gimp-remote.1.in
/usr/doc/gimpshop-2.2.11/docs/gimp.1.in
/usr/doc/gimpshop-2.2.11/docs/gimprc-2.2.5
/usr/doc/gimpshop-2.2.11/docs/gimprc.5.in
/usr/doc/gimpshop-2.2.11/docs/gimptool-2.0.1
/usr/doc/gimpshop-2.2.11/docs/gimptool.1.in
/usr/doc/gimpshop-2.2.11/docs/keybindings.txt
/usr/doc/gimpshop-2.2.11/docs/quick_reference.ps
/usr/doc/gimpshop-2.2.11/docs/quick_reference.tar.gz
/var/lib/dpkg/info/gimpshop.list
```

But I can't navigate to its folder.

---

### Post by FrissonArt on 2009-08-07
> **Solipsil said:**
> Hello

(beginner here)

I've just installed latest Gimpshop and installation went fine. However, I was unable to locate the program anywhere. I restarted the laptop, thinking the system needed to update settings to show the newly installed program but I still ca't find it. Looking for it in the terminal resulted in pretty much nothing. It returned ```
bash: gimpshop: command not found
```.
I'm running Linux Ubuntu 9.04.

Any help appreciated.

Try opening a terminal and typing the word gimp at the prompt. It worked for me (U9.04), see link below.

Terry

[http://blog.dipinkrishna.info/2009/06/gimpshop-photoshop-in-ubuntu-linux.html](http://blog.dipinkrishna.info/2009/06/gimpshop-photoshop-in-ubuntu-linux.html)

---

