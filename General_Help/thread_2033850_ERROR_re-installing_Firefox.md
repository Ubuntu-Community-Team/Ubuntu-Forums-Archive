---
title: "ERROR re-installing Firefox"
date: 2012-07-27
forum: General Help
---

### Post by Dhongsabshesh on 2012-07-27
Hi,

I am new to Ubuntu and I messed up Firefox, so I decided remove it but now I can't re-install it.

I am getting this after revoking this command from the terminal:

sudo apt-get install firefox

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  latex-xft-fonts firefox-gnome-support firefox-kde-support
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/18.9 MB of archives.
After this operation, 39.3 MB of additional disk space will be used.
(Reading database ... 304568 files and directories currently installed.)
Unpacking firefox (from .../firefox_14.0.1+build1-0ubuntu0.12.04.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_14.0.1+build1-0ubuntu0.12.04.1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/firefox/plugins', which is also in package adobe-flashplugin 11.2.202.236-0precise1
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_14.0.1+build1-0ubuntu0.12.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have searched the forum but it seems that the problem is new. Any help will be greatly appreciated. Thanks

---

### Post by ajgreeny on 2012-07-27
It looks as if perhaps you need to purge firefox rather than simply remove it. Try ```
sudo apt-get purge firefox
``` It is also possible that the firefox package in your cache is corrupt so it may be worth removing it with ```
sudo rm /var/cache/apt/archives/firefox_14.0.1+build1-0ubuntu0.12.04.1_i386.deb
``` then trying the installation again.

---

### Post by albandy on 2012-07-27
> **ajgreeny said:**
> It looks as if perhaps you need to purge firefox rather than simply remove it. Try ```
sudo apt-get purge firefox
``` It is also possible that the firefox package in your cache is corrupt so it may be worth removing it with ```
sudo rm /var/cache/apt/archives/firefox_14.0.1+build1-0ubuntu0.12.04.1_i386.deb
``` then trying the installation again.

Before erasing manually a package, try to do an apt-get clean:

sudo apt-get clean

this should remove the cached file.

---

### Post by Dhongsabshesh on 2012-07-27
Thanks for replying so quickly friends. I appreciate that.

After digging into the forum I found this thread ([http://ubuntuforums.org/showthread.php?p=11322854#post11322854](http://ubuntuforums.org/showthread.php?p=11322854#post11322854)). I ran:

sudo dpkg -i --force-overwrite /var/cache/apt/archives/firefox_14.0.1+build1-0ubuntu0.12.04.1_i386.deb 

and that solved the problem. Thanks again everybody.

---

