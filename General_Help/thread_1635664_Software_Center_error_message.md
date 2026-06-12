---
title: "Software Center error message"
date: 2010-12-02
forum: General Help
---

### Post by bsbh on 2010-12-02
Hi,

I am not able to start software center from the Applications menu. All it does it to show the busy cursor for a couple of seconds and then nothing.

Trying to start software-center in terminal shows the following error message:

```

Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 37, in <module>
    from softwarecenter.db.application import Application, DebFileApplication
  File "/usr/share/software-center/softwarecenter/db/application.py", line 19, in <module>
    from apt.debfile import DebPackage
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 35, in <module>
    apt_pkg.init()
SystemError: E:Unable to read /etc/apt/apt.conf.d/ - opendir (13: Permission denied)

```

However, starting with software-center with sudo works just fine.

I have noticed that a few other applications that require authentication also failed to run e.g. "Additional Drivers" and "Update Manager".

I am running Ubuntu 10.10 64 bit.

Appreciate any assistance on the above.

---

### Post by sisco311 on 2010-12-02
Welcome to the forums!

Please post the output of:
```
pgrep -l polkit
```
and 
```
pkexec echo test
```

---

### Post by bsbh on 2010-12-02
pgrep -l polkit shows the following:

```

1790 polkitd
2652 polkit-gnome-au

```

pkexec echo test prompted for password

```

test

```

Thanks for prompt response :)

---

### Post by sisco311 on 2010-12-02
Well, policykit works, that's good. :)

*SystemError: E:Unable to read /etc/apt/apt.conf.d/ - opendir (13: Permission denied)* indicates that is something wrong with the permissions of /etc/apt/apt.conf.d 

What's the output of:
```
ls -ald /etc
ls -ald /etc/apt
ls -ald /etc/apt/apt.conf.d
```
?

---

### Post by bsbh on 2010-12-02
Here are the permission:

```

bsbh@laptop:~$ ls -ald /etc
drwxr-xr-x 150 root root 12288 2010-12-02 20:12 /etc
bsbh@laptop:~$ ls -ald /etc/apt
drwxr-xr-x 6 root root 4096 2010-12-02 17:23 /etc/apt
bsbh@laptop:~$ ls -ald /etc/apt/apt.conf.d/
drwx------ 2 root root 4096 2010-12-01 23:16 /etc/apt/apt.conf.d/

```

---

### Post by sisco311 on 2010-12-02
The permissions of /etc/apt/apt.conf.d/ should be 0755 (read/write/execute for the owner, read/execute for the group and others), run:
```
sudo chmod 0755 /etc/apt/apt.conf.d/
```
to restore the default permissions.

---

### Post by bsbh on 2010-12-02
Changed the permission as suggested.

```

bsbh@laptop:~$ sudo chmod 0755 /etc/apt/apt.conf.d/
[sudo] password for bsbh: 
bsbh@laptop:~$ ls -ald /etc/apt/apt.conf.d/
drwxr-xr-x 2 root root 4096 2010-12-01 23:16 /etc/apt/apt.conf.d/

```

Then tried running software-center from Applications menu, still no show. :(

---

### Post by sisco311 on 2010-12-02
Check the content of the directory:
```
ls -al /etc/apt/apt.conf.d/
```
All files from the directory should have -rw-r--r-- (0644) permissions: 
```
sudo chmod 0644 /etc/apt/apt.conf.d/*
```

---

### Post by bsbh on 2010-12-02
```
bsbh@laptop:~$ sudo chmod 0644 /etc/apt/apt.conf.d/*
bsbh@laptop:~$ cd /etc/apt/apt.conf.d/
bsbh@laptop:/etc/apt/apt.conf.d$ ls -al
total 52
drwxr-xr-x 2 root root 4096 2010-12-01 23:16 .
drwxr-xr-x 6 root root 4096 2010-12-02 17:23 ..
-rw-r--r-- 1 root root   40 2010-12-01 23:10 00trustcdrom
-rw-r--r-- 1 root root  395 2010-12-01 23:10 01autoremove
-rw-r--r-- 1 root root  157 2010-12-01 23:10 05aptitude
-rw-r--r-- 1 root root  129 2010-12-01 23:10 10periodic
-rw-r--r-- 1 root root  108 2010-12-01 23:10 15update-stamp
-rw-r--r-- 1 root root   85 2010-12-01 23:10 20archive
-rw-r--r-- 1 root root  243 2010-12-01 23:10 20dbus
-rw-r--r-- 1 root root 1169 2010-12-01 23:10 50unattended-upgrades
-rw-r--r-- 1 root root  182 2010-12-01 23:10 70debconf
-rw-r--r-- 1 root root   32 2010-12-02 17:21 99synaptic
-rw-r--r-- 1 root root  231 2010-12-01 23:10 99update-notifier
bsbh@laptop:/etc/apt/apt.conf.d$ 
```

still no love :(

---

### Post by sisco311 on 2010-12-02
Is the error message still the same?

---

### Post by bsbh on 2010-12-02
Different errors this time:

```
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 105, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 88, in __init__
    self.open(progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 126, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Unable to read /etc/apt/preferences.d/ - opendir (13: Permission denied)
2010-12-02 21:44:43,587 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/view/widgets/mkit_themes.py', 675, 'retrieve')'
2010-12-02 21:44:43,587 - root - WARNING - No styling hints for Equinox Glass were found... using Human hints.
Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 316, in __init__
    self.view_switcher = ViewSwitcher(self.view_manager, datadir, self.db, self.cache, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 59, in __init__
    store = ViewSwitcherList(view_manager, datadir, db, cache, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 321, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 399, in _update_channel_list
    self._update_channel_list_installed_view()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 452, in _update_channel_list_installed_view
    if (pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 128, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'

```

---

### Post by bsbh on 2010-12-02
Got it working.

Had to apply 0755 to /etc/apt/preference.d/ and 0644 to /etc/apt/*, assuming these are the default permissions.

Thanks!!

---

### Post by sisco311 on 2010-12-02
You're welcome!


Yes, 0755 are the default permissions for directories and 0644 are the defaults for files.


Oh, and don't forget to mark this thread as [SOLVED]. At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

