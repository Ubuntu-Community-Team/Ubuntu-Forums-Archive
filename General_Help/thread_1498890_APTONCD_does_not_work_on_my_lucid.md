---
title: "APTONCD does not work on my lucid"
date: 2010-06-01
forum: General Help
---

### Post by maizuddin35 on 2010-06-01
[I]Hello guys!
Id installed aptoncd on my lucid using the software center.
When i want to use it, the aptoncd does not appear at all.

when i run it using terminal, the output is this :

anidah@anidah-laptop:~$ aptoncd

(process:3319): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/aptoncd", line 28, in <module>
    from APTonCD.core import constants
  File "/usr/lib/python2.6/dist-packages/APTonCD/core/constants.py", line 41, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
[/I]

can anyone help with this one.

---

### Post by dino99 on 2010-06-01
goto synaptic and remove/purge it then reinstall it

or get the latest from sourceforge:

[http://linux.dipin.info/2009/08/aptoncd-create-local-removable.html](http://linux.dipin.info/2009/08/aptoncd-create-local-removable.html)

---

### Post by maizuddin35 on 2010-06-01
For your information not only APTONCD have the problem.
There are some application also have problem like this one.
I installed an application called caffeine , it does not work, when i run it using terminal the output is this :

[I]anidah@anidah-laptop:~$ caffeine

(process:3379): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/caffeine", line 38, in <module>
    import caffeine
  File "/usr/bin/../lib/python2.6/dist-packages/caffeine/__init__.py", line 161, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
anidah@anidah-laptop:~$ 
[/I]

---

### Post by maizuddin35 on 2010-06-01
I already try to purge/install it back. still did not work.

---

### Post by dino99 on 2010-06-01
several things to check:

open synaptic and :
-check that the repo are only "lucid" ones, unselect third parties and ppa if any
- remove/purge and reinstall locales and language-support-* packages

into a console, copy/paste line by line:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure python
sudo dpkg-reconfigure python2.6

---

### Post by maizuddin35 on 2010-06-01
thanks for the reply , now im trying to reinstall back the language-support. will looks what will happen

---

### Post by maizuddin35 on 2010-06-01
when i apt-get update there is some part that shows this :

[I]perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_TIME = "Sunday.UTF-8",
	LANG = "en_US.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
[/I]

what does that mean?
i think of something , that i need to do ..

---

### Post by maizuddin35 on 2010-06-01
@dino99 i have done reinstalling those things and do everything with the apt-get and dpkg, but still when i run use the terminal this time running aptoncd , this shows;

[I]anidah@anidah-laptop:~$ aptoncd

(process:6654): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/aptoncd", line 28, in <module>
    from APTonCD.core import constants
  File "/usr/lib/python2.6/dist-packages/APTonCD/core/constants.py", line 41, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
anidah@anidah-laptop:~$ [/I]

---

