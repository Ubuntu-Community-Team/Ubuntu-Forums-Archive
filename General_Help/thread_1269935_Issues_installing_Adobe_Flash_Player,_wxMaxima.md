---
title: "Issues installing Adobe Flash Player, wxMaxima"
date: 2009-09-18
forum: General Help
---

### Post by TheMatt on 2009-09-18
Hey guys. So after arriving at college I found that a lot of program compatibilities allowed me to use my somewhat old Kubuntu 6.06 distro (that I have setup as a dual boot with XP) for the majority of the time instead of XP. There are two issues that I have run into however:

1. I downloaded Adobe Flash Player 10 for use in Firefox 1.5. I ran in console the sudo dpkg -i but I got a ton of dependency errors.

```
mattmodica@Dothan:~$ pwd
/home/mattmodica
mattmodica@Dothan:~$ sudo dpkg -i install_flash_player_10_linux.deb
(Reading database ... 129879 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.32.18-1 (using install_flash_player_10_linux.deb) ...
Unpacking replacement adobe-flashplugin ...
dpkg: dependency problems prevent configuration of adobe-flashplugin:
 adobe-flashplugin depends on libnspr4-dev; however:
  Package libnspr4-dev is not installed.
 adobe-flashplugin depends on libnss3-dev; however:
  Package libnss3-dev is not installed.
 adobe-flashplugin depends on libatk1.0-0 (>= 1.13.2); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 adobe-flashplugin depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 adobe-flashplugin depends on libcairo2 (>= 1.4.0); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.2.
 adobe-flashplugin depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-1.1ubuntu12.
 adobe-flashplugin depends on libfreetype6 (>= 2.3.5); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.6.
 adobe-flashplugin depends on libgcc1 (>= 1:4.2.1); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 adobe-flashplugin depends on libglib2.0-0 (>= 2.14.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 adobe-flashplugin depends on libgtk2.0-0 (>= 2.12.0); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
 adobe-flashplugin depends on libpango1.0-0 (>= 1.18.3); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.1.
 adobe-flashplugin depends on libstdc++6 (>= 4.2.1); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing adobe-flashplugin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobe-flashplugin

```/CODE]

When I try to fix these dependencies myself however I get other errors:

```
mattmodica@Dothan:~$ sudo apt-get install libnspr4-dev
Reading package lists... Done
Building dependency tree... Done
Package libnspr4-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libnspr4-dev has no installation candidate

```

I also get this

```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  adobe-flashplugin: Depends: libnspr4-dev but it is not installable
                     Depends: libnss3-dev but it is not installable
                     Depends: libatk1.0-0 (>= 1.13.2) but 1.11.4-0ubuntu1 is to be installed
                     Depends: libc6 (>= 2.6-1) but 2.3.6-0ubuntu20.5 is to be installed
                     Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1.2 is to be installed
                     Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
                     Depends: libfreetype6 (>= 2.3.5) but 2.1.10-1ubuntu2.6 is to be installed
                     Depends: libgcc1 (>= 1:4.2.1) but 1:4.0.3-1ubuntu5 is to be installed
                     Depends: libglib2.0-0 (>= 2.14.0) but 2.10.3-0ubuntu1 is to be installed
                     Depends: libgtk2.0-0 (>= 2.12.0) but 2.8.20-0ubuntu1.1 is to be installed
                     Depends: libpango1.0-0 (>= 1.18.3) but 1.12.3-0ubuntu3.1 is to be installed
                     Depends: libstdc++6 (>= 4.2.1) but 4.0.3-1ubuntu5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Any ideas? I would like to be able to watch youtube on linux.


Oh also I installed wxMaxima. But when I run anything on it I get 

CLIENT: Lost socket connection ...Restart maxima with 'Maxima->Restart maxima'.

If I do this I get the same thing. Its an endless loop and I would like to get this math program working.


Thanks!!!

---

### Post by yabbadabbadont on 2009-09-18
The only file you need out of that deb archive is libflashplayer.so.  You can open the deb with archivemanager and extract that one file.  Then simply put it into the .mozilla/plugins directory in your home directory.

Restart firefox and it should then show up in about:plugins.

---

### Post by mikewhatever on 2009-09-18
I think the problem is that flash 10 is too new for Ubuntu 6.06. You may have downloaded the newer flash from Adobe's webpage, but it requires newer dependencies not available for 6.06. In short, it's time to upgrade or to reinstall.

---

### Post by TheMatt on 2009-09-18
> **mikewhatever said:**
> I think the problem is that flash 10 is too new for Ubuntu 6.06. You may have downloaded the newer flash from Adobe's webpage, but it requires newer dependencies not available for 6.06. In short, it's time to upgrade or to reinstall.

I think you're right mike, it may be time to upgrade. Ark is giving me all sorts of errors when I try to open the .deb.

What version is the latest LTS release? And would upgrading be as simple as changing the repositories as I did when I tried out edgy? I don't want to have to do a full reinstall (that's the whole reason I avoid windoez).

Thanks for the swift replies

---

### Post by mikewhatever on 2009-09-18
8.04 is the latest LST for Ubuntu, but I don't think Kubuntu 8.04 is. There were problems with KDE4 just then, and they didn't want to stick to KDE3. You can read about upgrading here [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades). I am no expert, never tried upgrading in my life.:)

---

### Post by TheMatt on 2009-09-19
Thanks mike. I followed the steps in the link and the update manager found 8.04 hardy, so it looks like that will be my next stop. I will let you know how it goes

---

### Post by TheMatt on 2009-09-19
Upgrade went well, just one issue:

[http://ubuntuforums.org/showthread.php?t=1270644](http://ubuntuforums.org/showthread.php?t=1270644)

---

### Post by pduijves on 2009-11-24
> **yabbadabbadont said:**
> The only file you need out of that deb archive is libflashplayer.so.  You can open the deb with archivemanager and extract that one file.  Then simply put it into the .mozilla/plugins directory in your home directory.

Restart firefox and it should then show up in about:plugins.

on kubuntu 9.10 with firefox 3.5.5 i couldn't find the .mozilla/plugins/ directory in the home directory, but moved libflashplayer.so to /usr/lib/mozilla/plugins/ instead, and then stuff worked after restarting firefox...

---

### Post by yabbadabbadont on 2009-11-24
> **pduijves said:**
> on kubuntu 9.10 with firefox 3.5.5 i couldn't find the .mozilla/plugins/ directory in the home directory, but moved libflashplayer.so to /usr/lib/mozilla/plugins/ instead, and then stuff worked after restarting firefox...

If your .mozilla directory didn't have a plugins sub-directory, you just needed to create it...  ;)

---

