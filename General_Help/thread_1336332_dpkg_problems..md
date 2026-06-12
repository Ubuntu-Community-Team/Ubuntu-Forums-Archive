---
title: "dpkg problems."
date: 2009-11-24
forum: General Help
---

### Post by mick8985 on 2009-11-24
whenever I try to install anything I get problems regarding the package python-support, this began when I tried to uninstall the package screenlets. Here is an example:

```
Unpacking sl (from .../archives/sl_3.03-16_amd64.deb) ...
Processing triggers for man-db ...
Setting up python-support (1.0.3ubuntu1) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 492, in <module>
    post_change_stuff(py)
  File "/usr/sbin/update-python-modules", line 326, in post_change_stuff
    os.remove(abspath)
OSError: [Errno 5] Input/output error: '/usr/lib/pymodules/python2.6/screenlets/__init__.pyc'
dpkg: error processing python-support (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up sl (3.03-16) ...
Errors were encountered while processing:
 python-support
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

sudo dpkg-reconfigure python-support produces:
```
michael@michael-desktop:~$ sudo dpkg-reconfigure python-support
/usr/sbin/dpkg-reconfigure: python-support is broken or not fully installed.

```
 Any ideas?

---

### Post by Darael on 2009-11-24
Hmm... I assume you've tried [FONT=Courier New]sudo aptitude purge[FONT=Verdana]-ing it?[/FONT][/FONT]

---

### Post by mick8985 on 2009-11-24
A great many important packages depend on it, I think that would pretty must destroy my system

---

### Post by Darael on 2009-11-24
Ah.  Hmm... apt-get install --reinstall --purge?
Else, not a clue.

---

### Post by mick8985 on 2009-11-24
Nope.
Similar things to this have happened for me on ubuntu before, and a good number of them have forced me to reinstall an otherwise perfectly functioning system..

---

### Post by earthpigg on 2009-11-24
```
sudo apt-get clean
sudo apt-get --reinstall install python support
```

---

### Post by mick8985 on 2009-11-24
> **earthpigg said:**
> ```
sudo apt-get clean
sudo apt-get --reinstall install python support
```

That results in the same error](*,)

---

### Post by earthpigg on 2009-11-24
i think you are just going to have to bite the bullet and uninstall that package. that would be my next step in your shoes, anyways.

don't worry to much about other stuff being removed -- you can sudo apt-get install it back... and your settings for various programs will be kept on your computer waiting to be used when the program to be reinstalled.

as always, have a solid backup just in case.

---

### Post by mick8985 on 2009-11-28
It ended up being a problem with a filesystem, which made certain files impossible to edit or delete, it was corrected by booting a livecd and running "e2fsck -fc /dev/sda1" Hope this doesn't indicate that I have a faulty drive that is likely to die soon...

---

### Post by earthpigg on 2009-11-28
> **mick8985 said:**
> Hope this doesn't indicate that I have a faulty drive that is likely to die soon...

[http://sourceforge.net/apps/trac/smartmontools/wiki](http://sourceforge.net/apps/trac/smartmontools/wiki)

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

:D

---

