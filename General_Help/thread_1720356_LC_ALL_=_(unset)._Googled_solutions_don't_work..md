---
title: "LC_ALL = (unset). Googled solutions don't work."
date: 2011-04-03
forum: General Help
---

### Post by lampak on 2011-04-03
Every time I try to install anything with apt-get, I get the following error:
```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_GB:en",
	LC_ALL = (unset),
	LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```

For example: 
```
lampak@laptop:/etc$ sudo apt-get install hello
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  unixodbc libipc-run-perl libio-pty-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  hello
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/34.4kB of archives.
After this operation, 664kB of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_GB:en",
	LC_ALL = (unset),
	LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously deselected package hello.
(Reading database ... 351008 files and directories currently installed.)
Unpacking hello (from .../archives/hello_2.5-1_i386.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_GB:en",
	LC_ALL = (unset),
	LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_GB:en",
	LC_ALL = (unset),
	LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct
Setting up hello (2.5-1) ...

```

The packages do get installed, however. But what's worse, I can't type any diacritics in the console - all I get is question marks. But I can in Gnome. I suspect it's an issue with UTF-8.

[SIZE="1"](I'm Polish but I prefer to use the British English locale with the Polish keyset)[/SIZE]

After a bit of googling, I found out it's quite a common problem. The problem is, the solutions which worked for others don't work for me. The ones I've tried:

1) ```
sudo apt-get install --reinstall language-pack-en
```
Usually it's advised to install language-pack-en. The problem is, I've got it already installed. 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/219kB of archives.
After this operation, 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_GB:en",
	LC_ALL = (unset),
	LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 356139 files and directories currently installed.)
Preparing to replace language-pack-en 1:10.10+20101204 (using .../language-pack-en_1%3a10.10+20101204_all.deb) ...
Unpacking replacement language-pack-en ...
Processing triggers for software-center ...

(process:13105): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
WARNING:root:setlocale failed with 'unsupported locale setting'
Processing triggers for python-central ...
Setting up language-pack-en (1:10.10+20101204) ...

```
No improvement.

2) ```

sudo locale-gen
sudo dpkg-reconfigure locales

```
```

lampak@laptop:~$ sudo locale-gen
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  pl_PL.UTF-8... up-to-date
Generation complete.
lampak@laptop:~$ sudo dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_GB:en",
	LC_ALL = (unset),
	LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  pl_PL.UTF-8... up-to-date
Generation complete.

```
No improvement again. 

3) removing and reinstalling "locale" package

Do you know of something else I can try? 

Don't you hate it when your system breaks down without you doing anything apart from keeping it up-to-date?

---

### Post by lampak on 2011-04-03
Answering myself: 
I've managed to solve the problem by adding 
```
LC_ALL="en_GB.utf8"
```
to /etc/environment and rebooting.

---

### Post by beithon on 2011-09-22
This worked for me! Hurray!

---

### Post by cepal on 2011-10-26
correct solution, esp. if found on virtual system (VPS hosting), would be following:

```
sudo locale-gen en_US.UTF-8
```

Of course, you may want to replace that locale by another one...

Source:
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)
CePal

---

### Post by Gundars on 2011-12-10
> **lampak said:**
> Answering myself: 
I've managed to solve the problem by adding 
```
LC_ALL="en_GB.utf8"
```to /etc/environment and rebooting.

This worked for me too! 

Ubuntu 11.10

Šitais man ari nostr&#257;daja! lv_LV.UTF8

---

### Post by Chris_Z on 2012-07-14
> **Gundars said:**
> This worked for me too! 

Ubuntu 11.10



It solved the same problem after upgrading Ubuntu from 10.10 to 12.04. 

Thanks!

---

