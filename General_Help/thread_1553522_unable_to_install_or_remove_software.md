---
title: "unable to install or remove software"
date: 2010-08-15
forum: General Help
---

### Post by rockager on 2010-08-15
when i tried to install gwibber, ubuntu software center is said that it is unable to install the software (this was the error report):

installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously deselected package gwibber.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 170778 files and directories currently installed.)
Unpacking gwibber (from .../gwibber_2.30.1-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Rebuilding /usr/share/applications/desktop.en_IN.ISO8859-1.cache...
WARNING: System locale is invalid
Processing triggers for python-support ...
Setting up linux-image-2.6.32-24-generic (2.6.32-24.39) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.38 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.38 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/bin/sh: Illegal option -

User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gwibber (2.30.1-0ubuntu1) ...

Processing triggers for python-central ...
Errors were encountered while processing:
 linux-image-2.6.32-24-generic
Setting up linux-image-2.6.32-24-generic (2.6.32-24.39) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.38 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.38 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/bin/sh: Illegal option -

User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2

it gives the same message whenever i try to install or remove any software.:confused:

---

### Post by jmfal on 2010-08-15
open a terminal: applications>accessories>terminal

   ```
 sudo dpkg --configure -a
```   (type the command, not the code in brackets)

press enter, enter password, press enter, may ask if you want to continue>y/n

press y, then enter,  might need to restart,

---

### Post by rockager on 2010-08-15
i tried but this is what happened (my login name is yash):

yash@yash-desktop:~$  sudo dpkg --configure -a
[sudo] password for yash: 
Setting up linux-image-2.6.32-24-generic (2.6.32-24.39) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.38 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.38 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/bin/sh: Illegal option -
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.32-24-generic
yash@yash-desktop:~$

---

