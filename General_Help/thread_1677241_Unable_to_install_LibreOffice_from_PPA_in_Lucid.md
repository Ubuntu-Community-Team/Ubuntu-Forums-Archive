---
title: "Unable to install LibreOffice from PPA in Lucid"
date: 2011-01-28
forum: General Help
---

### Post by veroslav on 2011-01-28
Hi,

I am trying to install LibreOffice 3.3 by following the instructions I found at [http://www.omgubuntu.co.uk/2011/01/libreoffice-3-3-released/]("http://www.omgubuntu.co.uk/2011/01/libreoffice-3-3-released/")

Below is the output I get after running these commands:

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update && sudo apt-get install libreoffice
```

Output:


```
user@user-laptop:~$ sudo add-apt-repository ppa:libreoffice/ppa
[sudo] password for user: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 36E81C9267FD1383FCC4490983FBA1751378B444
gpg: requesting key 1378B444 from hkp server keyserver.ubuntu.com
gpg: key 1378B444: "Launchpad PPA for LibreOffice Packaging" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```

```
user@user-laptop:~$ sudo apt-get update && sudo apt-get install libreoffice
Hit http://security.ubuntu.com lucid-security Release.gpg
...
Hit http://ppa.launchpad.net lucid/main Packages
Fetched 36,4kB in 1s (31,3kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libreoffice: Depends: libreoffice-core (= 1:3.3.0-1lucid1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-report-builder-bin but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.3.0~) but it is not going to be installed
E: Broken packages
```

I am running Ubuntu 10.04 and I have OpenOffice installed. Is it possible to install LibreOffice 3.3 from PPA even though it is said that the commands target Maverick? Do I have to uninstall OpenOffice before installing LibreOffice?

Thank you in advance.

Regards,
Veroslav

---

### Post by Irony on 2011-01-28
Follow the instructions here; [http://maketecheasier.com/replace-openoffice-with-libreoffice-in-ubuntu/2011/01/26](http://maketecheasier.com/replace-openoffice-with-libreoffice-in-ubuntu/2011/01/26)

---

### Post by veroslav on 2011-01-28
Thank you very much, that fixed it! :D

Kind Regards,
Veroslav

---

### Post by TedinOz on 2011-06-03
I have been contemplating changing from OpenOffice to LibreOffice,  since from what I have read, LibreOffice is now the current operative.

My question is that if I follow the procedure here, would I lose all the files currently active under Open Office?.. and if so could I store those files in an external drive and re-introduce them into Libre Office after the install? Would this be the way to go here or is there a more simplified way I could achieve it.

Thanks

---

### Post by linuxinstalledfromhdd on 2011-06-03
As long as you have your files that you want to keep in your home folder, you will be fine.

It a good upgrade process, and just make sure you follow the part of the instructions where you completely remove OpenOffice before you attempt to install it.

Here are the plugins I use with my system once I have LibreOffice Installed.

 ```
 sudo apt-get install libreoffice-gnome
```  Kubuntu users should run:
 ```
 sudo apt-get install libreoffice-kde
```  To enable PDF import capability:
 ```
 sudo apt-get install libreoffice-pdfimport
```  To enable English spellcheck capability
 ```
 sudo apt-get install language-support-en
```  To enable Mozilla Office plugin
 ```
 sudo apt-get install mozilla-libreoffice
```

---

### Post by TedinOz on 2011-06-03
> **linuxinstalledfromhdd said:**
> As long as you have your files that you want to keep in your home folder, you will be fine.

It a good upgrade process, and just make sure you follow the part of the instructions where you completely remove OpenOffice before you attempt to install it.

Here are the plugins I use with my system once I have LibreOffice Installed.

 ```
 sudo apt-get install libreoffice-gnome
```  Kubuntu users should run:
 ```
 sudo apt-get install libreoffice-kde
```  To enable PDF import capability:
 ```
 sudo apt-get install libreoffice-pdfimport
```  To enable English spellcheck capability
 ```
 sudo apt-get install language-support-en
```  To enable Mozilla Office plugin
 ```
 sudo apt-get install mozilla-libreoffice
```

Thanks so much and for the quick reply. Will try this. Can you explain what the Mozilla Office plugin is all about please. I use Chromium as my default browser and occasionally Firefox but not as default. What does the plugin do and do I need it?

Many thanks again.

---

### Post by linuxinstalledfromhdd on 2011-06-03
That particular plugin will allow you to open up doc's (and other related types of office files) from inside the browser itself. :) 

I'm not sure if such a plugin for Chrome/Chromium exists yet.  Maybe someone else here knows? :)

---

### Post by TedinOz on 2011-06-03
Okay! All done and dusted. Working well.

Thanks to everyone :)

---

### Post by Tootler on 2011-07-19
This is what I have been looking for. Before I proceed, I have a further query.

Is it possible to transfer custom setting (customised toolbars etc.) from Open Office to Libre Office?

Can I copy the contents of ~/.openoffice.org to the LibreOffice  configuration location work - or even selected files from ~/openoffice.org?

---

### Post by sgtrock on 2011-09-17
> **linuxinstalledfromhdd said:**
> As long as you have your files that you want to keep in your home folder, you will be fine.

It a good upgrade process, and just make sure you follow the part of the instructions where you completely remove OpenOffice before you attempt to install it.

Here are the plugins I use with my system once I have LibreOffice Installed.

 ```
 sudo apt-get install libreoffice-gnome
```  Kubuntu users should run:
 ```
 sudo apt-get install libreoffice-kde
```  To enable PDF import capability:
 ```
 sudo apt-get install libreoffice-pdfimport
```  To enable English spellcheck capability
 ```
 sudo apt-get install language-support-en
```  To enable Mozilla Office plugin
 ```
 sudo apt-get install mozilla-libreoffice
```

I got the following error message in 10.04 LTS when I tried this:
```
  sudo apt-get install libreoffice-kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libreoffice-kde is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libreoffice-kde has no installation candidate
```

All other steps succeeded.  Since I use KDE as my primary environment, this kind of surprised me.  All dependencies should be in place.  Any thoughts as to what I should check?

TIA

---

### Post by oldos2er on 2011-09-17
Looks like libreoffice-kde is only available for Maverick and higher versions.

---

