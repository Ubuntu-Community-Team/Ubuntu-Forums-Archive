---
title: "Unknown program not working..."
date: 2006-03-29
forum: General Help
---

### Post by riwa on 2006-03-29
It may have something to do with 'dpkg' or I don't know. I comes up every time i use apt-get. 

```
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

On 'Xian''s request i tried the following commands: 
```

sudo dpkg-reconfigure locales
sudo apt-get -f install
```

With the following output:

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

I'm stuck. The programs I installed all work but somethings wrong since I get error messages all the time. 

Regards
Richard

---

### Post by dcstar on 2006-03-30
[QUOTE=riwa]........
I'm stuck. The programs I installed all work but somethings wrong since I get error messages all the time. 
[/QUOTE]
I suggest re-installing the locales package, and run the following commands:
```
locale
validlocale en_US
validlocale en
```
My locale is **en_AU**, I'm not sure **en** is a valid locale.

---

