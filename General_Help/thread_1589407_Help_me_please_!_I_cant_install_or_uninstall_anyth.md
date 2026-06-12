---
title: "Help me please ! I cant install or uninstall anything on my pc !"
date: 2010-10-06
forum: General Help
---

### Post by Lisaac10 on 2010-10-06
i always get an error when updating my pc, when am installing a program or package, and when am uninstalling something. 
I tried: 
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade  And this is what i get 

guest24@isaac-desktop:~$ sudo apt-get -f install
[sudo] password for guest24: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-22 linux-headers-2.6.32-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 186 not upgraded.
guest24@isaac-desktop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [191B]
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,310B]                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [964B]               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 2,465B in 0s (2,560B/s)
Reading package lists... Done
guest24@isaac-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.32-25 linux-headers-2.6.32-25-generic
  linux-image-2.6.32-25-generic
The following packages will be upgraded:
  acpi-support acroread adobe-flashplugin alien apt apt-transport-https
  apt-utils aptdaemon avahi-autoipd avahi-daemon avahi-utils base-files
  binutils binutils-static bogofilter bogofilter-bdb bogofilter-common bzip2
  cabextract clamav clamav-base clamav-freshclam coreutils dpkg dpkg-dev
  fglrx-modaliases firefox firefox-3.0 firefox-3.0-gnome-support firefox-3.5
  firefox-3.5-branding firefox-branding firefox-gnome-support gdebi gdebi-core
  gdebi-kde gdm ghostscript ghostscript-cups ghostscript-x gnome-keyring
  gnome-terminal gnome-terminal-data google-chrome-beta grub-common gwibber
  gwibber-service gzip hpijs hplip hplip-data icedtea-6-jre-cacao
  icedtea6-plugin ifupdown language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-pack-kde-en
  language-pack-kde-en-base lftp libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core6 libavahi-glib1
  libavahi-gobject0 libavahi-qt3-1 libavahi-ui0 libbz2-1.0 libclamav6
  libcouchdb-glib-1.0-2 libdbusmenu-glib1 libdbusmenu-gtk1
  libdesktopcouch-glib-1.0-2 libdjvulibre-text libdjvulibre21 libfreetype6
  libgcr0 libgdiplus libgksu2-0 libgp11-0 libgs8 libgssapi-krb5-2
  libgudev-1.0-0 libhpmud0 libk5crypto3 libkpathsea5 libkrb5-3 libkrb5support0
  libldap-2.4-2 libmikmod2 libmysqlclient16 libpackagekit-glib2-12
  libpackagekit-qt-12 libpam-gnome-keyring libpam-smbpass libpcsclite1
  libphonon4 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4
  libsmbclient libsmbios2 libssl0.9.8 libudev0 libwbclient0 libwww-perl
  linux-generic linux-headers-generic linux-image-generic linux-libc-dev
  mktemp mountall mupen64plus mysql-client-core-5.1 mysql-common
  mysql-server-core-5.1 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  openssl packagekit packagekit-backend-apt pcmanfm-nohal phonon pyroom
  python-apt python-aptdaemon python-aptdaemon-gtk python-avahi python-imaging
  python-lazr.restfulclient python-mako python-packagekit
  python-software-properties samba samba-common samba-common-bin screen
  seamonkey-browser seamonkey-chatzilla smbclient software-center
  software-properties-gtk software-properties-kde sreadahead sudo tar
  thunderbird tzdata tzdata-java ubufox ubuntu-system-service udev
  update-manager update-manager-core update-manager-kde upstart ureadahead
  usb-creator usb-creator-common usb-creator-gtk w3m wget winbind
  xserver-common xserver-xorg-core xulrunner-1.9.2
186 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/326MB of archives.
After this operation, 202MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 85%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'apparmor-utils' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
guest24@isaac-desktop:~$

---

### Post by indytim on 2010-10-06
> files list file for package 'apparmor-utils' is missing final newline

This is probably a hint of what's going on (about the 3rd line from the bottom of your output).

IndyTim

---

### Post by Lisaac10 on 2010-10-06
> **indytim said:**
> This is probably a hint of what's going on (about the 3rd line from the bottom of your output).

IndyTim

Yeah but how can i fix that?

---

### Post by andrewthomas on 2010-10-06
post the output of 

```
sudo aptitude reinstall apparmor-utils
```

---

### Post by Lisaac10 on 2010-10-06
> **andrewthomas said:**
> post the output of 

```
sudo aptitude reinstall apparmor-utils
```

This is what happened after i did that>>

guest24@isaac-desktop:~$ sudo aptitude reinstall apparmor-utils
[sudo] password for guest24: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  apparmor-utils 
The following packages will be REMOVED:
  linux-headers-2.6.32-22{u} linux-headers-2.6.32-22-generic{u} 
0 packages upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 186 not upgraded.
Need to get 105kB of archives. After unpacking 85.3MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main apparmor-utils 2.5-0ubuntu3 [105kB]
Fetched 105kB in 0s (132kB/s)      
(Reading database ... 85%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'apparmor-utils' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

guest24@isaac-desktop:~$ 
Its still the same :(

---

### Post by drs305 on 2010-10-06
The error states: "files list file for package 'apparmor-utils' is missing final newline"

To add the newline, run this command, then try the update again. We'll make a backup copy of the file first.


```
sudo cp /var/lib/dpkg/info/apparmor-utils.list /var/lib/dpkg/info/apparmor-utils.list.old
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/apparmor-utils.list
sudo apt-get update && sudo apt-get upgrade  # or dist-upgrade

```

---

### Post by Lisaac10 on 2010-10-06
> **drs305 said:**
> The error states: "files list file for package 'apparmor-utils' is missing final newline"

To add the newline, run this command, then try the update again. We'll make a backup copy of the file first.


```
sudo cp /var/lib/dpkg/info/apparmor-utils.list /var/lib/dpkg/info/apparmor-utils.list.old
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/apparmor-utils.list
sudo apt-get update && sudo apt-get upgrade  # or dist-upgrade

```

Hey i did that. It seemed to work a bit, but now it says: files list file for package 'apparmor-utils' contains empty filename

---

### Post by Lisaac10 on 2010-10-06
> **drs305 said:**
> The error states: "files list file for package 'apparmor-utils' is missing final newline"

To add the newline, run this command, then try the update again. We'll make a backup copy of the file first.


```
sudo cp /var/lib/dpkg/info/apparmor-utils.list /var/lib/dpkg/info/apparmor-utils.list.old
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/apparmor-utils.list
sudo apt-get update && sudo apt-get upgrade  # or dist-upgrade

```

Should i reinstall aparmor ?

---

### Post by drs305 on 2010-10-06
Apparently it doesn't like the extra line, so open the file as root:
```

gksu gedit /var/lib/dpkg/info/apparmor-utils.list

```

Go to the last line - it should be blank. Backspace to the end of the preceding line and press DEL. That should leave no space after the last entry. On mine, the last entry is: /usr/sbin/aa-genprof

Save the file and try again. Try reinstalling apparmor-utils.  If it still doesn't work, post the contents of apparmor-utils.list

---

### Post by Lisaac10 on 2010-10-06
> **drs305 said:**
> Apparently it doesn't like the extra line, so open the file as root:
```

gksu gedit /var/lib/dpkg/info/apparmor-utils.list

```

Go to the last line - it should be blank. Backspace to the end of the preceding line and press DEL. That should leave no space after the last entry. On mine, the last entry is: /usr/sbin/aa-genprof

Save the file and try again. Try reinstalling apparmor-utils.  If it still doesn't work, post the contents of apparmor-utils.list

Hey, i wrote the code on my terminal and when i put the password for root it doesnt open the file. It says that /var/lib/dpkg/info/apparmor-utils.list cant be open. That gedit has not been able to detect the character encoding

---

### Post by drs305 on 2010-10-06
> **Lisaac10 said:**
> Hey, i wrote the code on my terminal and when i put the password for root it doesnt open the file. It says that /var/lib/dpkg/info/apparmor-utils.list cant be open. That gedit has not been able to detect the character encoding

The list file is a simple text file, so it's possbile it's corrupted. If you still have the backup we made earlier, try renaming the current file so that apparmor-utils.list doesn't exist at all. 

```
sudo mv /var/lib/dpkg/info/apparmor-utils.list /var/lib/dpkg/info/apparmor-utils.list.bad
``` 

When you try to install apparmor-utils it will say something to the effect that the list is missing. Just continue the installation.

---

### Post by Lisaac10 on 2010-10-06
> **drs305 said:**
> The list file is a simple text file, so it's possbile it's corrupted. If you still have the backup we made earlier, try renaming the current file so that apparmor-utils.list doesn't exist at all. 

```
sudo mv /var/lib/dpkg/info/apparmor-utils.list /var/lib/dpkg/info/apparmor-utils.list.bad
``` 

When you try to install apparmor-utils it will say something to the effect that the list is missing. Just continue the installation.

heyyy man i fixed it ! Thanks ! :)

---

### Post by kanishkdudeja on 2011-01-10
please mark the thread as solved.

---

