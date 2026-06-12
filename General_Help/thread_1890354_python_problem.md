---
title: "python problem"
date: 2011-12-03
forum: General Help
---

### Post by Dan Z on 2011-12-03
while trying to fix a python related problem with Autokey, I screwed up python for other programs. (it was not pointing to the correct python)

I still have a problem with Autokey, and now cant get Ubuntu software center or nssbackup to run. 

when I try to run software centrer I get error 

"Failed to execute child process "/usr/bin/software-center" (Permission denied)"

Nssbackup wont run at all.

Here is what python was on Nov 28, before I screwed it up:

here is python status:Nov 28

:/usr/bin$ ls -la python*
lrwxrwxrwx 1 root root      24 2011-11-28 19:03 python -> /etc/
alternatives/python
lrwxrwxrwx 1 root root       9 2010-05-09 07:07 python2 -> python2.6
-rwxr-xr-x 1 root root 1027748 2010-01-21 18:28 python2.4
-rwxr-xr-x 1 root root 2288240 2010-04-16 10:06 python2.6

Here is what it looks like now:

/usr/bin$ ls -la python*
-rw-r--r-- 1 root root       0 2011-11-28 20:53 python
lrwxrwxrwx 1 root root       9 2010-05-09 07:07 python2 -> python2.6
-rwxr-xr-x 1 root root 1027748 2010-01-21 18:28 python2.4
-rwxr-xr-x 1 root root 2288240 2010-04-16 10:06 python2.6


It looks like the link python -> /etc/
alternatives/python is gone. 

And:
/etc/alternatives$ ls -la python
lrwxrwxrwx 1 root root 18 2011-11-28 19:03 python -> /usr/bin/python2.6


I tried to create python -> /etc/
alternatives/python 

/usr/bin$ ln -s /etc/alternatives/python python
ln: creating symbolic link `python': File exists

Thinking I got it wrong I tried:

/usr/bin$ ln -s python /etc/alternatives/python 
ln: creating symbolic link `/etc/alternatives/python': File exists

then I tried:

/etc/alternatives$ ln -s python /usr/bin/python 
ln: creating symbolic link `/usr/bin/python': File exists

and then:

/etc/alternatives$ ln -s /usr/bin/python python 
ln: creating symbolic link `python': File exists


nothing changed, as expected:

/usr/bin$ ls -la python*
-rw-r--r-- 1 root root       0 2011-11-28 20:53 python
lrwxrwxrwx 1 root root       9 2010-05-09 07:07 python2 -> python2.6
-rwxr-xr-x 1 root root 1027748 2010-01-21 18:28 python2.4
-rwxr-xr-x 1 root root 2288240 2010-04-16 10:06 python2.6

I do not even know if this is the reason python wont work.

Can anyone help me out here???

Thanks in advance.

dan

---

### Post by Dan Z on 2011-12-03
> **Dan Z said:**
> while trying to fix a python related problem with Autokey, I screwed up python for other programs. (it was not pointing to the correct python)

I still have a problem with Autokey, and now cant get Ubuntu software center or nssbackup to run. 

when I try to run software centrer I get error 

"Failed to execute child process "/usr/bin/software-center" (Permission denied)"

Nssbackup wont run at all.

Here is what python was on Nov 28, before I screwed it up:

here is python status:Nov 28

:/usr/bin$ ls -la python*
lrwxrwxrwx 1 root root      24 2011-11-28 19:03 python -> /etc/
alternatives/python
lrwxrwxrwx 1 root root       9 2010-05-09 07:07 python2 -> python2.6
-rwxr-xr-x 1 root root 1027748 2010-01-21 18:28 python2.4
-rwxr-xr-x 1 root root 2288240 2010-04-16 10:06 python2.6

Here is what it looks like now:

/usr/bin$ ls -la python*
-rw-r--r-- 1 root root       0 2011-11-28 20:53 python
lrwxrwxrwx 1 root root       9 2010-05-09 07:07 python2 -> python2.6
-rwxr-xr-x 1 root root 1027748 2010-01-21 18:28 python2.4
-rwxr-xr-x 1 root root 2288240 2010-04-16 10:06 python2.6


It looks like the link python -> /etc/
alternatives/python is gone. 

And:
/etc/alternatives$ ls -la python
lrwxrwxrwx 1 root root 18 2011-11-28 19:03 python -> /usr/bin/python2.6


I tried to create python -> /etc/
alternatives/python 

/usr/bin$ ln -s /etc/alternatives/python python
ln: creating symbolic link `python': File exists

Thinking I got it wrong I tried:

/usr/bin$ ln -s python /etc/alternatives/python 
ln: creating symbolic link `/etc/alternatives/python': File exists

then I tried:

/etc/alternatives$ ln -s python /usr/bin/python 
ln: creating symbolic link `/usr/bin/python': File exists

and then:

/etc/alternatives$ ln -s /usr/bin/python python 
ln: creating symbolic link `python': File exists


nothing changed, as expected:

/usr/bin$ ls -la python*
-rw-r--r-- 1 root root       0 2011-11-28 20:53 python
lrwxrwxrwx 1 root root       9 2010-05-09 07:07 python2 -> python2.6
-rwxr-xr-x 1 root root 1027748 2010-01-21 18:28 python2.4
-rwxr-xr-x 1 root root 2288240 2010-04-16 10:06 python2.6

I do not even know if this is the reason python wont work.

Can anyone help me out here???

Thanks in advance.

dan

Here is added info that may help:

 sudo apt-get install autokey-qt 
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autokey-qt is already the newest version.
autokey-qt set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-36-generic (2.6.32-36.79) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-36-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-36-generic
Found kernel: /boot/vmlinuz-2.6.32-35-generic
Found kernel: /boot/vmlinuz-2.6.32-34-generic
Found kernel: /boot/vmlinuz-2.6.32-33-generic
Found kernel: /boot/vmlinuz-2.6.32-32-generic
Found kernel: /boot/vmlinuz-2.6.32-31-generic
Found kernel: /boot/vmlinuz-2.6.32-30-generic
Found kernel: /boot/vmlinuz-2.6.32-29-generic
Found kernel: /boot/vmlinuz-2.6.32-28-generic
Found kernel: /boot/vmlinuz-2.6.32-27-generic
Found kernel: /boot/vmlinuz-2.6.32-26-generic
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found kernel: /boot/vmlinuz-2.6.32-23-generic
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.28-18-generic
Found kernel: /boot/vmlinuz-2.6.27-17-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-36-generic /boot/vmlinuz-2.6.32-36-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-36-generic /boot/vmlinuz-2.6.32-36-generic
/etc/kernel/postinst.d/nvidia-common: /usr/bin/nvidia-detector: /usr/bin/python: bad interpreter: Permission denied
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 126
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-36-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-36-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up autokey-common (0.81.1-0~lucid) ...
/var/lib/dpkg/info/autokey-common.postinst: 36: pycentral: Permission denied
dpkg: error processing autokey-common (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of autokey-qt:
 autokey-qt depends on autokey-common; however:
  Package autokey-common is not configured yet.
dpkg: error processing autokey-qt (--configure):
 dependency problems - leaving unconfigured
Setting up gedit-plugins (2.30.0-0ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          /var/lib/dpkg/info/gedit-plugins.postinst: 6: gconf-schemas: Permission denied
dpkg: error processing gedit-plugins (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports is reached already
                                                              Setting up python-gmenu (2.30.0-0ubuntu4) ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
/var/lib/dpkg/info/python-gmenu.postinst: 1: /usr/share/gnome-menus/update-gnome-menus-cache: Permission denied
/var/lib/dpkg/info/python-gmenu.postinst: 25: update-python-modules: Permission denied
dpkg: error processing python-gmenu (--configure):
 subprocess installed post-installation script returned error exit status 126
Setting up software-center (2.0.7) ...
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/software-center.postinst: 12: pycentral: Permission denied
dpkg: error processing software-center (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.32-36-generic
 autokey-common
 autokey-qt
 gedit-plugins
 python-gmenu
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mutley89 on 2011-12-03
To fix the symlink, the following will reset it to how it was:
```

sudo ln -sf /etc/alternatives/python /usr/bin/python
sudo ln -sf /usr/bin/python2.6 /etc/alternatives/python

```What was the problem with Autokey?

---

### Post by Dan Z on 2011-12-03
thanks, that took care of it.

Problem with autokey is this:

sudo apt-get autoremove autokey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package autokey is not installed, so not removed
The following packages will be REMOVED:
  autokey-common autokey-qt libqscintilla2-5 python-qscintilla2 python-xlib
  wmctrl
0 upgraded, 0 newly installed, 6 to remove and 13 not upgraded.
3 not fully installed or removed.
After this operation, 4,796kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 502704 files and directories currently installed.)
Removing autokey-qt ...
Removing autokey-common ...
It does not seem Autokey is installed. Exiting...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error processing autokey-common (--remove):
 subprocess installed pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Removing python-qscintilla2 ...
Removing libqscintilla2-5 ...
Removing python-xlib ...
Removing wmctrl ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for install-info ...
Errors were encountered while processing:
 autokey-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thanks much

Dan

---

### Post by Dan Z on 2011-12-04
came across another problem when trying to update---

E: /var/cache/apt/archives/update-manager_1%3a0.134.11.1_all.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/update-manager-core_1%3a0.134.11.1_i386.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/update-manager-kde_1%3a0.134.11.1_all.deb: subprocess new pre-removal script returned error exit status 1


Thanks Dan

> **Dan Z said:**
> thanks, that took care of it.

Problem with autokey is this:

sudo apt-get autoremove autokey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package autokey is not installed, so not removed
The following packages will be REMOVED:
  autokey-common autokey-qt libqscintilla2-5 python-qscintilla2 python-xlib
  wmctrl
0 upgraded, 0 newly installed, 6 to remove and 13 not upgraded.
3 not fully installed or removed.
After this operation, 4,796kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 502704 files and directories currently installed.)
Removing autokey-qt ...
Removing autokey-common ...
It does not seem Autokey is installed. Exiting...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error processing autokey-common (--remove):
 subprocess installed pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Removing python-qscintilla2 ...
Removing libqscintilla2-5 ...
Removing python-xlib ...
Removing wmctrl ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for install-info ...
Errors were encountered while processing:
 autokey-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thanks much

Dan

---

### Post by Dan Z on 2011-12-04
solution found


sudo rm /usr/bin/python && sudo ln -s python2.6 /usr/bin/python

now everthing is back to normal, except autokey.

IT removes ok, but when installing still has a problem:

sudo apt-get install autokey-qt 
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  autokey-common
The following NEW packages will be installed:
  autokey-common autokey-qt
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/100kB of archives.
After this operation, 684kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package autokey-common.
(Reading database ... 521072 files and directories currently installed.)
Unpacking autokey-common (from .../autokey-common_0.81.1-0~lucid_all.deb) ...
Selecting previously deselected package autokey-qt.
Unpacking autokey-qt (from .../autokey-qt_0.71.3-0~lucid_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up autokey-common (0.81.1-0~lucid) ...
XRecord is available
update-rc.d: warning: autokey start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: autokey stop runlevel arguments (none) do not match LSB Default-Stop values (0 1 6)
 Disabling system startup links for /etc/init.d/autokey ...
 Removing any system startup links for /etc/init.d/autokey ...
   /etc/rc0.d/K20autokey
   /etc/rc1.d/K20autokey
   /etc/rc2.d/K80autokey
   /etc/rc3.d/K80autokey
   /etc/rc4.d/K80autokey
   /etc/rc5.d/K80autokey
   /etc/rc6.d/K20autokey
 Adding system startup for /etc/init.d/autokey ...
   /etc/rc0.d/K20autokey -> ../init.d/autokey
   /etc/rc1.d/K20autokey -> ../init.d/autokey
   /etc/rc6.d/K20autokey -> ../init.d/autokey
   /etc/rc2.d/K80autokey -> ../init.d/autokey
   /etc/rc3.d/K80autokey -> ../init.d/autokey
   /etc/rc4.d/K80autokey -> ../init.d/autokey
   /etc/rc5.d/K80autokey -> ../init.d/autokey

Processing triggers for python-central ...
Setting up autokey-qt (0.71.3-0~lucid) ...

Processing triggers for python-central ...
dan@ACER-ub:~$ 

When I try to run form terminal:

/usr/bin$ autokey-qt
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
Traceback (most recent call last):
  File "/usr/bin/autokey-qt", line 20, in <module>
    from autokey.qtapp import Application
  File "/usr/lib/python2.6/dist-packages/autokey/qtapp.py", line 28, in <module>
    import service
  File "/usr/lib/python2.6/dist-packages/autokey/service.py", line 23, in <module>
    from gtkui.popupmenu import *
ImportError: No module named gtkui.popupmenu

Can anyone help! thanks Dan



> **Dan Z said:**
> came across another problem when trying to update---

E: /var/cache/apt/archives/update-manager_1%3a0.134.11.1_all.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/update-manager-core_1%3a0.134.11.1_i386.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/update-manager-kde_1%3a0.134.11.1_all.deb: subprocess new pre-removal script returned error exit status 1


Thanks Dan

---

### Post by Dan Z on 2011-12-06
This fix work---it came from autokey forum

would suggest removing all AutoKey packages, and then adding the PPA
(sudo add-apt-repository ppa:cdekter/ppa && sudo apt-get update) and
then installing again (sudo apt-get install autokey-common autokey-gtk)

---

