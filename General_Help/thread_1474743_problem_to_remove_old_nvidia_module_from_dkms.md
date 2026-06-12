---
title: "problem to remove old nvidia module from dkms"
date: 2010-05-06
forum: General Help
---

### Post by domak on 2010-05-06
Hi all,

I upgraded from karmic to lucid few days ago. On karmic, I had the nvidia driver installed from ftp (not from distrib).
After upgrade, fglxgears was not running, so I reinstalled the driver from ftp (195.36.24).

During install, I had some error message from dkms. These messages are
the same that the ones from dkms status:

[FONT="Courier New"]
sony-laptop-zseries, 0.9np5, 2.6.31-17-generic, x86_64: built
sony-laptop-zseries, 0.9np5, 2.6.31-19-generic, x86_64: built
sony-laptop-zseries, 0.9np5, 2.6.31-20-generic, x86_64: built
sony-laptop-zseries, 0.9np5, 2.6.31-21-generic, x86_64: built
sony-laptop-zseries, 0.9np5, 2.6.31-18-generic, x86_64: built
sony-laptop-zseries, 0.9np5, 2.6.31-16-generic, x86_64: built
sony-laptop-zseries, 0.9np5, 2.6.32-22-generic, x86_64: installed
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
nvidia, 190.53, 2.6.31-17-generic, x86_64: built
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
nvidia, 190.53, 2.6.31-19-generic, x86_64: built
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
nvidia, 190.53, 2.6.31-20-generic, x86_64: built
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
nvidia, 190.53, 2.6.31-21-generic, x86_64: installed
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
nvidia, 190.53, 2.6.31-18-generic, x86_64: built
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.
nvidia, 190.53, 2.6.32-22-generic, x86_64: installed[/FONT]

That's weird because I have only one kernel, the 2.6.32-22 and still
have this messages, even after removing driver with janitor script.
I tried to remove the nvidia module from dkms with:

[FONT="Courier New"]domak@domakistan-laptop:~$ sudo dkms remove -m nvidia -v 190.53 --all
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
File: /var/lib/dkms/nvidia/190.53/source/dkms.conf does not represent
a valid dkms.conf file.
[/FONT]

The /var/lib/dkms/nvidia/190.53/source is a link on a directory that
doesn't exist:
[FONT="Courier New"]lrwxrwxrwx 1 root root   22 2009-12-24 16:04 source ->
/usr/src/nvidia-190.53[/FONT]

I don't know if dkms is the real problem but when I try to install the
driver from distrib, I have some messages that seems to confirm that:
[FONT="Courier New"] dmesg:
[   27.028319] NVRM: API mismatch: the client has the version 195.36.15,
but
[   27.028321] NVRM: this kernel module has the version 190.53.  Please
[   27.028329] NVRM: make sure that this kernel module and all NVIDIA
driver
[   27.028330] NVRM: components have the same version.[/FONT]

What should I do to remove this module without breaking my system (I
have only some very basic knowledge on linux)?

Thanks,

Christophe

---

