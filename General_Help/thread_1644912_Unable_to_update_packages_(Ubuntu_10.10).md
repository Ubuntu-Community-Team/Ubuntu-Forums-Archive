---
title: "Unable to update packages (Ubuntu 10.10)"
date: 2010-12-13
forum: General Help
---

### Post by azrael191 on 2010-12-13
I've tried a couple of things from other threads with no luck:
sudo dpkg --configure -a (returns no output)
falling back to an old version of /var/lib/dpkg/status (which, after it didn't work, I switched back)
sudo apt-get clean (redownloads updates then throws the same error)

Thanks in advance!

Error output when I try to update using Update Manager:

```
installArchives() failed: 
Extracting templates from packages: 36%
Extracting templates from packages: 72%
Extracting templates from packages: 100%
Preconfiguring packages ...

Extracting templates from packages: 36%
Extracting templates from packages: 72%
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `libgtk2.0-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkimap4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmailtools-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.

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
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `xserver-xorg-video-rendition' contains empty filename
```

---

### Post by Krytarik on 2010-12-14
You want to update your installed packages? Why don't you do it via the tool which is meant to do exactly that: "System -> Administration -> Update Manager"?

---

### Post by azrael191 on 2010-12-14
That's the output from me trying to do exactly that. Sorry I left that part out. Those were my attempts, based on what I read in similar threads, to resolve the issue. Any ideas?

---

### Post by Krytarik on 2010-12-14
> **azrael191 said:**
> That's the output from me trying to do exactly that. Sorry I left that part out. Those were my attempts, based on what I read in similar threads, to resolve the issue. Any ideas?
Oh, you wrote it in the middle between the outputs, I have overlooked that, sorry!
Please place outputs, commands and similar text between code-tags (the #), makes it easier to read your post.

As for the errors, unfortunately I haven't seen that kind until now.:-k So please wait a little for someone who might be better able to help you. I'll also keep an eye on your thread.

---

### Post by Krytarik on 2010-12-14
Forgot to mention: It could be helpful if you provide some details about what you've done before that may have led to this state.;)

---

### Post by azrael191 on 2010-12-14
Updated, forgot to restart for a couple of days, restarted and since then it's been happening.

---

### Post by Krytarik on 2010-12-14
What about this?:
```
sudo apt-get --fix-missing install
```and/or```
sudo apt-get --fix-broken install
```[http://manpages.ubuntu.com/manpages/maverick/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/apt-get.8.html)

---

### Post by azrael191 on 2010-12-14
Both commands produce the same output:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hplip-cups linux-headers-2.6.35-22 kdesudo linux-headers-2.6.35-22-generic
  update-manager-kde
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 84 not upgraded.

```

And since that package wasn't being removed I tried the command suggested which results in this output:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hplip-cups kdesudo linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
  update-manager-kde
0 upgraded, 0 newly installed, 5 to remove and 84 not upgraded.
After this operation, 91.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `libgtk2.0-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkimap4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmailtools-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `xserver-xorg-video-rendition' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Looks like the same issue. Thanks for continuing to follow up.

---

### Post by Krytarik on 2010-12-14
As the packages mentioned in the error messages are always the same, I would try to re-install exactly those.

---

### Post by karthick87 on 2010-12-14
Execute the following in terminal one by one,

```
sudo cp -pr /var/lib/dpkg/info /var/lib/dpkg/info.backup
```
```
sudo aptitude -V reinstall libgtk2.0-bin
```
```
sudo aptitude -V reinstall libkimap4
```
```
sudo aptitude -V reinstall python-ubuntuone
```
```
sudo aptitude -V reinstall libmailtools-perl
```
```
sudo aptitude -V reinstall ssl-cert
```

---

### Post by azrael191 on 2010-12-14
```
sudo apt-get install libgtk2.0-bin
```
Produces the following output:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-bin is already the newest version.
The following packages were automatically installed and are no longer required:
  hplip-cups linux-headers-2.6.35-22 kdesudo linux-headers-2.6.35-22-generic
  update-manager-kde
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 84 not upgraded.

```

When I try to remove it, it warns that some 33 other packages will have to be removed because they are dependent. So I tried:
```

sudo aptitude reinstall libgtk2.0-bin

```

Which throws:

```

The following packages will be REINSTALLED:
  libgtk2.0-bin 
The following packages will be REMOVED:
  hplip-cups{u} kdesudo{u} linux-headers-2.6.35-22{u} 
  linux-headers-2.6.35-22-generic{u} update-manager-kde{u} 
0 packages upgraded, 0 newly installed, 1 reinstalled, 5 to remove and 84 not upgraded.
Need to get 41.6kB of archives. After unpacking 91.9MB will be freed.
Do you want to continue? [Y/n/?] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main libgtk2.0-bin all 2.22.0-0ubuntu1 [41.6kB]
Fetched 41.6kB in 1s (27.6kB/s)       
(Reading database ... 
dpkg: warning: files list file for package `libgtk2.0-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkimap4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmailtools-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `xserver-xorg-video-rendition' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

```

At which point it hangs then returns nothing.

---

### Post by azrael191 on 2010-12-14
```

sudo cp -pr /var/lib/dpkg/info /var/lib/dpkg/info.backup

```

Hangs for a while before returning no output.

```

sudo aptitude -V reinstall libgtk2.0-bin

```

Returns:

```


The following packages will be REINSTALLED:
  libgtk2.0-bin  
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 84 not upgraded.
Need to get 0B/41.6kB of archives. After unpacking 0B will be used.
(Reading database ...                    
dpkg: warning: files list file for package `libgtk2.0-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkimap4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmailtools-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `xserver-xorg-video-rendition' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

```

I tried the next one in the list but it encountered the same error.

---

### Post by Krytarik on 2010-12-14
1.) No ouput from the first command is the expected result, since it's just a copy command.

2.) Thus I would enclose all of those packages in one single re-install command.

EDIT: Oh, the package concerned in the command was also listed as error, forget the last one, sorry.

EDIT: Earlier today I found this: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)
        It looked a bit too comprehensive at the first glance, but maybe you should try this now.

---

### Post by karthick87 on 2010-12-14
Post the complete output of,

```
sudo apt-get update
```

---

### Post by azrael191 on 2010-12-15
```

Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en                                                        
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US                                                     
Get:2 http://dl.google.com stable Release.gpg [197B]                                                   
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en                                                         
Hit http://extras.ubuntu.com maverick Release.gpg                                                                            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                      
Hit http://archive.ubuntu.com maverick Release.gpg                   
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en   
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://extras.ubuntu.com maverick Release                        
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Get:3 http://dl.google.com stable Release [1,347B]                   
Hit http://extras.ubuntu.com maverick/main i386 Packages                
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Get:4 http://dl.google.com stable Release [1,347B]                     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Get:5 http://dl.google.com stable/main i386 Packages [1,060B]
Get:6 http://dl.google.com stable/main i386 Packages [735B]          
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick Release
Hit http://archive.ubuntu.com maverick-security Release
Hit http://archive.ubuntu.com maverick-updates Release
Hit http://archive.ubuntu.com maverick/main Sources
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/universe Sources
Hit http://archive.ubuntu.com maverick/multiverse Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/universe Sources
Hit http://archive.ubuntu.com maverick-security/multiverse Sources
Hit http://archive.ubuntu.com maverick-security/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Fetched 4,883B in 1s (2,485B/s)
Reading package lists... Done


```

---

### Post by karthick87 on 2010-12-15
The update seems to be fine,what you get when you type

```
sudo apt-get upgrade
```

---

### Post by azrael191 on 2010-12-15
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bind9-host dnsutils empathy empathy-common firefox firefox-branding firefox-gnome-support google-chrome-beta google-talkplugin gwibber gwibber-service
  ibus ibus-gtk icedtea-6-jre-cacao imagemagick libbind9-60 libc-bin libc-dev-bin libc6 libc6-dev libdns66 libgexiv2-0 libgssapi-krb5-2 libibus2 libisc60
  libisccc60 libisccfg60 libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2 liblwres60 libmagickcore3 libmagickcore3-extra libmagickwand3 libqt4-dbus
  libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite
  libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libsmbclient libssl0.9.8 libsyncdaemon-1.0-1 libvlc5 libvlccore4 libwbclient0
  libx264-98 linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic linux-libc-dev nautilus-sendto-empathy openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openssl python-ibus python-ubuntuone-client samba-common samba-common-bin smbclient software-center
  telepathy-haze tomboy ttf-mscorefonts-installer ubuntu-docs ubuntuone-client ubuntuone-client-gnome update-inetd vlc vlc-data vlc-nox vlc-plugin-notify
  vlc-plugin-pulse winbind xdg-utils xulrunner-1.9.2
89 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/207MB of archives.
After this operation, 1331kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `libgtk2.0-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkimap4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmailtools-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `xserver-xorg-video-rendition' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by sikander3786 on 2010-12-15
I know you tried replacing your dpkg/status with dpkg/status-old but lets do it once more.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

and then, post the output of

```
sudo apt-get upgrade
```

---

### Post by azrael191 on 2010-12-15
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bind9-host dnsutils empathy empathy-common firefox firefox-branding firefox-gnome-support google-chrome-beta google-talkplugin gwibber gwibber-service
  ibus ibus-gtk icedtea-6-jre-cacao imagemagick libbind9-60 libc-bin libc-dev-bin libc6 libc6-dev libdns66 libgexiv2-0 libgssapi-krb5-2 libibus2 libisc60
  libisccc60 libisccfg60 libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2 liblwres60 libmagickcore3 libmagickcore3-extra libmagickwand3 libqt4-dbus
  libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite
  libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libsmbclient libssl0.9.8 libsyncdaemon-1.0-1 libvlc5 libvlccore4 libwbclient0
  libx264-98 linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic linux-libc-dev nautilus-sendto-empathy openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openssl python-ibus python-ubuntuone-client samba-common samba-common-bin smbclient software-center
  telepathy-haze tomboy ttf-mscorefonts-installer ubuntu-docs ubuntuone-client ubuntuone-client-gnome update-inetd vlc vlc-data vlc-nox vlc-plugin-notify
  vlc-plugin-pulse winbind xdg-utils xulrunner-1.9.2
89 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/207MB of archives.
After this operation, 1331kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `libgtk2.0-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkimap4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmailtools-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `xserver-xorg-video-rendition' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

---

### Post by sikander3786 on 2010-12-15
```
sudo mv /var/lib/dpkg/info/xserver-xorg-video-rendition.list /var/lib/dpkg/info/xserver-xorg-video-rendition.list.old
```

Then search Synaptic for xserver-xorg-video-rendition and install it. It might give some errors like list file is missing but it would be re-created once installed.

---

### Post by azrael191 on 2010-12-15
```

michael@Disco-Tom:~$ sudo mv /var/lib/dpkg/info/xserver-xorg-video-rendition.list /var/lib/dpkg/info/xserver-xorg-video-rendition.list.old
[sudo] password for michael: 
michael@Disco-Tom:~$ sudo apt-get install xserver-xorg-video-rendition
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-rendition is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 89 not upgraded.
michael@Disco-Tom:~$ sudo aptitude reinstall xserver-xorg-video-rendition
The following packages will be REINSTALLED:
  xserver-xorg-video-rendition 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 89 not upgraded.
Need to get 30.5kB of archives. After unpacking 0B will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-rendition i386 1:4.2.4-0ubuntu1 [30.5kB]
Fetched 30.5kB in 1s (27.8kB/s)                      
(Reading database ... 
dpkg: warning: files list file for package `libgtk2.0-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkimap4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-rendition' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmailtools-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `compiz-fusion-plugins-main' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

```

No luck.

---

### Post by sikander3786 on 2010-12-15
I am not in front of my Linux sytem at preset. If I remember correctly, there might be backups for Status file under /var/backups. Copy from there to your /var/lib/dpkg directory, name it status and see how it goes.

Otherwise, attach your status file. I'll try and see how it goes on my testing system.

---

### Post by azrael191 on 2010-12-15
There are backups, I tried one and it threw the same error. I attached the (original) file to this post.

---

### Post by Krytarik on 2010-12-15
> **azrael191 said:**
> There are backups, I tried one and it threw the same error. I attached the (original) file to this post.
If you remember roughly when the errors began, and it's not to long ago, you should try the last backup before that date. Did you?

---

### Post by azrael191 on 2010-12-15
I tried several different backups (going back as far as 11/4, which is well before the problem occured) and it still throws the same error. I tried
```

sudo apt-get clean

```
between each for shits and giggles.

---

### Post by sikander3786 on 2010-12-16
Try this command first.

```
sudo dpkg --configure -a
```

If that still returns the same errors, backup your lists, remove them and try to recreate them by running apt-get update.

```
sudo cp -r /var/lib/apt/lists /var/lib/apt/lists.bad
```

```
cd /var/lib/apt/lists
```

```
sudo rm -r *
```

```
sudo apt-get update
```

---

### Post by azrael191 on 2010-12-16
No luck, looks like the same error. I really appreciate everyone continuing to follow up on this! Thanks, guys.

---

### Post by sikander3786 on 2010-12-16
> **azrael191 said:**
> No luck, looks like the same error. I really appreciate everyone continuing to follow up on this! Thanks, guys.
I just hope it isn't the same error. Can you please post the output of this command once more.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by azrael191 on 2010-12-16
```

Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en                                                        
Get:2 http://dl.google.com stable Release.gpg [197B]                                                                         
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en                                                         
Get:3 http://dl.google.com stable Release [1347B]                                                                            
Get:4 http://dl.google.com stable Release [1347B]                                                                                                   
Get:5 http://dl.google.com stable/main i386 Packages [1062B]                                                                                        
Get:6 http://dl.google.com stable/main i386 Packages [735B]                                
Get:7 http://extras.ubuntu.com maverick Release.gpg [65B]              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://archive.ubuntu.com maverick Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Get:8 http://archive.ubuntu.com maverick-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Hit http://extras.ubuntu.com maverick Release  
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Hit http://archive.ubuntu.com maverick-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Hit http://archive.ubuntu.com maverick Release 
Get:9 http://archive.ubuntu.com maverick-security Release [27.2kB]
Hit http://extras.ubuntu.com maverick/main i386 Packages                   
Hit http://archive.ubuntu.com maverick-updates Release 
Hit http://archive.ubuntu.com maverick/main Sources
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/universe Sources
Hit http://archive.ubuntu.com maverick/multiverse Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Get:10 http://archive.ubuntu.com maverick-security/main Sources [16.9kB]
Get:11 http://archive.ubuntu.com maverick-security/restricted Sources [14B]
Get:12 http://archive.ubuntu.com maverick-security/universe Sources [5410B]
Get:13 http://archive.ubuntu.com maverick-security/multiverse Sources [649B]
Get:14 http://archive.ubuntu.com maverick-security/main i386 Packages [54.3kB]
Get:15 http://archive.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:16 http://archive.ubuntu.com maverick-security/universe i386 Packages [21.4kB]
Get:17 http://archive.ubuntu.com maverick-security/multiverse i386 Packages [1655B]
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Fetched 133kB in 2s (53.3kB/s)                  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bind9-host dnsutils empathy empathy-common firefox firefox-branding firefox-gnome-support google-chrome-beta google-talkplugin gwibber gwibber-service
  ibus ibus-gtk icedtea-6-jre-cacao imagemagick libbind9-60 libc-bin libc-dev-bin libc6 libc6-dev libdns66 libgexiv2-0 libgssapi-krb5-2 libibus2 libisc60
  libisccc60 libisccfg60 libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2 liblwres60 libmagickcore3 libmagickcore3-extra libmagickwand3 libqt4-dbus
  libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite
  libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libsmbclient libssl0.9.8 libsyncdaemon-1.0-1 libvlc5 libvlccore4 libwbclient0
  libx264-98 linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic linux-libc-dev nautilus-sendto-empathy openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openssl python python-ibus python-minimal python-ubuntuone-client samba-common samba-common-bin smbclient
  software-center telepathy-haze tomboy ttf-mscorefonts-installer ubuntu-docs ubuntuone-client ubuntuone-client-gnome update-inetd vlc vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse winbind xdg-utils xulrunner-1.9.2
91 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.5MB/207MB of archives.
After this operation, 3047kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-beta i386 9.0.597.19-r68937 [23.3MB]
Get:2 http://dl.google.com/linux/talkplugin/deb/ stable/main google-talkplugin i386 1.7.1.0-1 [6217kB]                                                       
Fetched 29.5MB in 18s (1571kB/s)                                                                                                                             
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `libgtk2.0-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkimap4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-rendition' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmailtools-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `compiz-fusion-plugins-main' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by sikander3786 on 2010-12-16
We have removed the lists and recreated them using apt-get update so why is that error still there? I fear I'm running out of ideas. I would request another senior member to take a look at this thread and they might be able to figure out some solution. Please hang in there.

---

### Post by azrael191 on 2010-12-26
So, anyone have any more ideas?

---

### Post by trimmer on 2012-02-21
I began getting these errors as well and these are the circumstances that led me to the errors:

I have an older machine with mismatched memory (ecc/non-ecc) that will not correctly run the install from CD, ever.

I followed the instructions at [https://help.ubuntu.com/community/Installation/OverSSH](https://help.ubuntu.com/community/Installation/OverSSH) to install a working Lucid bootstrap with linux-image-3.0.0-15-generic-pae as my chosen kernel.

The system boots properly and gives me access to the install repors for apt-get or aptitude, whichever I choose.

Errors such as these began during the first installation command which was apt-get install ubuntu-desktop but not the exact error...

The error:
```
(Reading database ... 
dpkg: warning: files list file for package `filename' missing, assuming package has no files currently installed.

```
began when I performed dpkg -P `filename' to resolve the issue of not being able to apt-get remove `filename' or apt-get purge `filename'. When I performed the dpkg -p it was certain to remove the .deb and all it's settings and when I performed apt-get install `filename' it installed the package and reported it properly but for some reason did not update the dpkg status file and now dpkg reports still that the package has been purged even though apt has reinstalled it.

I am onceagain, in the middle of apt-get install ubuntu-desktop faced with additional errors, but purging the packages, cleaning the apt cached files removing all downloads, lists, status fules and so on are not working...

The files I am faced with fixing are:
```
 libxp6
 ubuntu-mono
 light-themes
 libwpd8c2a
 libwps-0.1-1
```

This is the output I get when attempting to install any of the above mentioned packages which are part of the ubuntu-desktop dependancy package...

```
root@lucid-desktop:/usr/share/locale# aptitude -V reinstall ubuntu-mono
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be REINSTALLED:
  ubuntu-mono  
The following partially installed packages will be configured:
  libwpd8c2a  libwps-0.1-1  libxp6  light-themes  
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 55 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up libwpd8c2a (0.8.14-1build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libwpd8c2a (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libwps-0.1-1:
 libwps-0.1-1 depends on libwpd8c2a; however:
  Package libwpd8c2a is not configured yet.
dpkg: error processing libwps-0.1-1 (--configure):
 dependency problems - leaving unconfigured
Setting up libxp6 (1:1.0.0.xsf1-2build1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxp6 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up ubuntu-mono (0.0.18) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ubuntu-mono (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on ubuntu-mono; however:
  Package ubuntu-mono is not configured yet.
dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
              Errors were encountered while processing:
 libwpd8c2a
 libwps-0.1-1
 libxp6
 ubuntu-mono
 light-themes
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libxp6 (1:1.0.0.xsf1-2build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxp6 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up ubuntu-mono (0.0.18) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ubuntu-mono (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on ubuntu-mono; however:
  Package ubuntu-mono is not configured yet.
dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
Setting up libwpd8c2a (0.8.14-1build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libwpd8c2a (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libwps-0.1-1:
 libwps-0.1-1 depends on libwpd8c2a; however:
  Package libwpd8c2a is not configured yet.
dpkg: error processing libwps-0.1-1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxp6
 ubuntu-mono
 light-themes
 libwpd8c2a
 libwps-0.1-1
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

I am attempting all of the following in different combinations:
```
apt-cache clean
apt-get clean all
dpkg --configure -a
apt-get install -f
rm /var/cache/apt/*.bin
rm /var/lib/apt/lists/* -vf
apt-get update
apt-get upgrade
cp -pr /var/lib/dpkg/info /var/lib/dpkg/info.backup
mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED
cp /var/lib/dpkg/status-old /var/lib/dpkg/status
apt-get update && apt-get upgrade
```

It appears we really need to focus on resolving package installation order to help resolve dependencies.

I am still in need of help if anyone has any further input.


[UPDATE] [SOLVED]
It turns out that when downloading so many packages at once(sudo apt-get install ubuntu-desktop) that the chance exists for file corruption. In the case of this error, the corruption caused 2 very necessary files for installed packages(`filename'.postinst and `filename'.postrm located in /var/lib/dpkg/info) to be blank containing none of the necessary post-installation script calls to process triggers and the likes same for post-removal calls.

To solve this issue I basically had to lie to the computer. This is what I did and it worked well:
```
apt-get purge `filename'
```
this did not work completely because the `filename'.postrm script was blank, but it did work to the point that apt thought the file was removed. Using the install command by itself at this point did not work because the package was already downloaded and purge did not remove that reference.

The second step to repair the problem:
```
apt-get -d install `filename'
```
this command will force a re-download of the package and repairs the 2 script files in /var/lib/dpkg/info that were corrupted.

Performing these 2 things allowed the install command for apt-get to work at this point. I had to go through this several times because throughout the process of apt-get install ubuntu-desktop, I experiences this kind of corruption more than once.

---

