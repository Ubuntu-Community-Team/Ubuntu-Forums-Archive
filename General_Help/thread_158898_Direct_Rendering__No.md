---
title: "Direct Rendering : No"
date: 2006-04-11
forum: General Help
---

### Post by tokez on 2006-04-11
I have just recently began learn Ubuntu and I am still pretty much a noob. However, I have an extensive knowledge in computers so I should fair fine with any terms and what-not, also, I am a google pro :P


My problem:

Recently installed counterstrike using wine and it works fine. However, with direct rendering set to no (glxinfo), the only video mode that I can currently use is a Software OpenGL. This is highly unacceptable with my computer set up and my expectations from linux gaming. If there is a way to fix this problem and correct my direct rendering, please let me know.

In case you prefer email, its [email]triton04@cox.net[/email] .

Thanks in advance.

---

### Post by dcstar on 2006-04-11
[QUOTE=tokez]I have just recently began learn Ubuntu and I am still pretty much a noob. However, I have an extensive knowledge in computers so I should fair fine with any terms and what-not, also, I am a google pro :P


My problem:

Recently installed counterstrike using wine and it works fine. However, with direct rendering set to no (glxinfo), the only video mode that I can currently use is a Software OpenGL. This is highly unacceptable with my computer set up and my expectations from linux gaming. If there is a way to fix this problem and correct my direct rendering, please let me know.

In case you prefer email, its [email]triton04@cox.net[/email] .

Thanks in advance.[/QUOTE]

It depends entirely on your video card, do a forum search on it and you may find instructions on how to get it working.

---

### Post by verbalshadow on 2006-04-11
This largely depends of what video card you have.
If you have an ATI or Nvidia card try their drivers.
otherwise search the forums

---

### Post by tokez on 2006-04-11
I went to ATI and downloaded the newest driver for my card I could find and used the guide for installation.

My card is an ATI Radeon 9700 (R300) and I have been doing some minor searching, but nothing is really pin-pointing my problem. Trying to work in a slow fashion as to not destroy my GUI while still making progress.

I will continue to look for the information because I am determined to correct it, but if you have a link on hand please post it.

---

### Post by taurus on 2006-04-12
Or maybe this guide helps, [http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)...

---

### Post by tokez on 2006-04-12
I tried that guide at that website and it seemed to be working ok except for a few minor (or major?) issues.

1st: sudo apt-get install xorg-driver-fglrx  returned ..

```

andrew@andrew:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 8325kB of archives.
After unpacking 24.1MB of additional disk space will be used.
Get:1 http://security.ubuntu.com breezy-security/restricted xorg-driver-fglrx 6.8.0-8.16.20-0ubuntu16.1 [8325kB]
Fetched 8325kB in 25s (330kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 71194 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Setting up locales (2.3.5-1ubuntu12.5.10.1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en.ISO-8859-1...cannot open locale definition file `en': No such file or directory
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 4
Setting up xorg-driver-fglrx (6.8.0-8.16.20-0ubuntu16.1) ...
Errors were encountered while processing:
 locales
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

2nd: sudo apt-get install linux-restricted-modules-$(andrew -r)  returned similar results in regards to the locale settings and the dpkg error.

3rd: sudo dpkg-reconfigure xserver-xorg  ran as i suppose was intended, however, did not correct the Direct Rendering issue.

___

If you need additional information to assist troubleshooting my problem feel free to ask.

Also, fglrxinfo returned the following:

andrew@andrew:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Mesa should have been changed to my Radeon 9700 (R300) if all went well correct?


Thanks in advance.

---

### Post by taurus on 2006-04-12
Looks like you are having problem with locale!!!  Use synaptic and search for locale.  Install it and go thru the guide again.

---

### Post by tokez on 2006-04-12
When using synaptic to install locales, I am still having problems with the locales it seems. Is it trying to contact current locales in order to install the new one?

Just in case its of use, here's the return of Synaptic>Locales:

E: locales: subprocess post-installation script returned error exit status 4

The terminal buffer proves that the error message is identical to the other messgae regarding locales.

---

### Post by tokez on 2006-04-13
```

andrew@andrew:/usr/share/locale$ sudo apt-get install belocs-locales-data
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  belocs-locales-bin
The following packages will be REMOVED:
  locales
The following NEW packages will be installed:
  belocs-locales-bin belocs-locales-data
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 4118kB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com breezy/universe belocs-locales-bin 2.3.4-8 [158kB]
Get:2 http://archive.ubuntu.com breezy/universe belocs-locales-data 2.3.4-16ubuntu1 [3960kB]
Fetched 4118kB in 12s (326kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...
Selecting previously deselected package belocs-locales-bin.
(Reading database ... 86401 files and directories currently installed.)
Unpacking belocs-locales-bin (from .../belocs-locales-bin_2.3.4-8_i386.deb) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Adding `diversion of /usr/bin/locale to /usr/bin/locale.glibc by belocs-locales-bin'
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Adding `diversion of /usr/share/man/man1/locale.1.gz to /usr/share/man/man1/locale.glibc.1.gz by belocs-locales-bin'
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Adding `diversion of /usr/bin/localedef to /usr/bin/localedef.glibc by belocs-locales-bin'
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Adding `diversion of /usr/share/man/man1/localedef.1.gz to /usr/share/man/man1/localedef.glibc.1.gz by belocs-locales-bin'
dpkg: error processing /var/cache/apt/archives/belocs-locales-bin_2.3.4-8_i386.deb (--unpack):
 trying to overwrite `/usr/sbin/locale-gen', which is also in package locales
Errors were encountered while processing:
 /var/cache/apt/archives/belocs-locales-bin_2.3.4-8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@andrew:/usr/share/locale$

```

---

### Post by Kevinator on 2006-04-13
[QUOTE=tokez]2nd: sudo apt-get install linux-restricted-modules-$(andrew -r)  returned similar results in regards to the locale settings and the dpkg error.[/QUOTE]

Uh, did you interpret 'uname' as 'your username here'? uname is actually the name of the command you want in the parens. It returns information about your system.

---

### Post by rabidphage on 2006-04-13
sudo dpkg-reconfigure locales
try this
might help

---

