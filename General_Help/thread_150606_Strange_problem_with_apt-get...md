---
title: "Strange problem with apt-get.."
date: 2006-03-26
forum: General Help
---

### Post by riwa on 2006-03-26
I get this annoying message when I use apt-get or synaptics. Most programs work though. I guess the erroneus part is the: 

"E: Sub-process /usr/bin/dpkg returned an error code (1)"

But I have no idea what it means...

Any hints??

Here the whole message....

```

riwa@wilma:~$ sudo apt-get update
Get:1 http://koti.mbnet.fi breezy/ Release.gpg [65B]
Ign http://deb.opera.com etch Release.gpg
Get:2 http://koti.mbnet.fi breezy/ Release [702B]
Ign http://people.ubuntu.com ./ Release.gpg
Get:3 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:5 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:6 http://kubuntu.org breezy Release.gpg [189B]
Get:7 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Ign http://people.ubuntu.com ./ Release
Hit http://archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security Release
Hit http://kubuntu.org breezy Release
Ign http://deb.opera.com etch Release
Hit http://archive.ubuntu.com breezy-backports Release
Ign http://people.ubuntu.com ./ Packages
Get:8 ftp://ftp.free.fr breezy Release.gpg
Ign http://deb.opera.com etch/non-free Packages
Ign http://koti.mbnet.fi breezy/ Packages
Hit http://deb.opera.com etch/non-free Packages
Hit http://people.ubuntu.com ./ Packages
Ign http://koti.mbnet.fi breezy/ Sources
Hit http://archive.ubuntu.com breezy/main Sources
Ign ftp://ftp.free.fr breezy Release.gpg
Hit http://koti.mbnet.fi breezy/ Packages
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Ign http://wine.sourceforge.net binary/ Release.gpg
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Get:9 ftp://ftp.free.fr breezy Release
Hit http://koti.mbnet.fi breezy/ Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://security.ubuntu.com breezy-security/main Packages
Ign ftp://ftp.free.fr breezy Release
Hit http://kubuntu.org breezy/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://theli.free.fr ./ Release.gpg
Get:10 ftp://ftp.free.fr breezy/free Packages
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Ign ftp://ftp.free.fr breezy/free Packages
Get:11 ftp://ftp.free.fr breezy/non-free Packages
Ign ftp://ftp.free.fr breezy/non-free Packages
Get:12 ftp://ftp.free.fr breezy/free Sources
Ign ftp://ftp.free.fr breezy/free Sources
Get:13 ftp://ftp.free.fr breezy/non-free Sources
Ign http://theli.free.fr ./ Release
Ign ftp://ftp.free.fr breezy/non-free Sources
Hit ftp://ftp.free.fr breezy/free Packages
Hit ftp://ftp.free.fr breezy/non-free Packages
Hit ftp://ftp.free.fr breezy/free Sources
Ign http://theli.free.fr ./ Packages
Hit ftp://ftp.free.fr breezy/non-free Sources
Hit http://theli.free.fr ./ Packages
Hit http://wine.sourceforge.net binary/ Release
Ign http://wine.sourceforge.net binary/ Packages
Hit http://wine.sourceforge.net binary/ Packages
Fetched 708B in 7s (98B/s)
Reading package lists... Done
riwa@wilma:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
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
Errors were encountered while processing:
 locales
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Ramses de Norre on 2006-03-26
> 1 not fully installed or removed Any idea which program it is? You can try to just install it again then (sudo apt-get install) or reinstall (sudo apt-get reinstall) and remove it again after that (sudo apt-get remove).

---

### Post by Xian on 2006-03-26
What is the output of these commands: ?

$ sudo dpkg-reconfigure locales
$ sudo apt-get -f install

---

### Post by riwa on 2006-03-26
well I guess its the dpkg program that't not working but I don't know how to re-install it. 

I don't have access to the computer at the moment but I'll try the commands when I do. How, for example, can I fetch a single program from the Ubuntu-disk?

/Richard

++
My bad. I saw that the '1' was the problem. Didn't understand what you meant. How do I find which program it is?

It comes up when I use the apt-get command. Not sure with the synaptic PM
--

---

### Post by riwa on 2006-03-27
This is the output of the two commands. Got no clue except that I think it's something to do about dpkg.. How to re-install it?

```

190415~$ sudo dpkg-reconfigure locales
Password:
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
/usr/sbin/dpkg-reconfigure: locales is broken or not fully installed

190458~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
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
Errors were encountered while processing:
 locales
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by 4deck on 2006-05-18
I have a similar problem...Did you ever resolve yours?

---

### Post by hagen00 on 2006-05-18
1. run locale -a to see which locales are available. 
2. You can add those manually to /etc/locale.gen
3. After making changes to that file, just run locale-gen. 

Might help

Edit: PS. I think your problem is not with apt-get but with locales.

---

