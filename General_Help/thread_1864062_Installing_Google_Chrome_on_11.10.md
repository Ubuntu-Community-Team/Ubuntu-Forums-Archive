---
title: "Installing Google Chrome on 11.10"
date: 2011-10-18
forum: General Help
---

### Post by Salpiche on 2011-10-18
I searched the forums and the www still I have not found a working solution for installing Google Chrome on my netbook running 11.10. Tried doing the same things I had to do for when I had 11.4 on my desktop and no go. every time I try I get the same error.
Here is an example 

```

jose@Buntu-netbox:~/Downloads$ sudo apt-get install google-chrome-stable_current_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google-chrome-stable_current_i386.deb
E: Couldn't find any package by regex 'google-chrome-stable_current_i386.deb'
jose@Buntu-netbox:~/Downloads$ 


```

any ideas or help with this???
 thanks tons

---

### Post by mc4man on 2011-10-18
Edit: thru a post here & in opera site the issue is the lack of the lzma package by default in 11.10
So just - 
```
sudo apt-get install lzma
```
Then SC or  gdebi will work
============================================================

Atm software-center & gdebi will not install this package so you can use dpkg -i
It' quite possible you may be missing a few dep, if so then using dpkg will cause broken packages, doesn't really matter, easy to fix & complete the install

Or you can 1st. install the deps, then use dpkg
Here the 2 missing deps were libnspr4-0d libxss1 so you could install them first.
The dpkg command would be
```
sudo dpkg -i ~/Downloads/google-chrome-stable_current_i386.deb
```
If the install has issues & doesn't complete then just run
```
sudo apt-get -f install
```

Here's an Ex. where those 2 deps where not installed - start to finish
> 
~$ sudo dpkg -i /home/doug/Downloads/google-chrome-stable_current_i386.deb
[sudo] password for doug: 
Selecting previously deselected package google-chrome-stable.
(Reading database ... 191758 files and directories currently installed.)
Unpacking google-chrome-stable (from .../google-chrome-stable_current_i386.deb) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libnspr4-0d (>= 4.7.3-0ubuntu1~); however:
  [COLOR="Red"]Package libnspr4-0d is not installed.[/COLOR]
 google-chrome-stable depends on libxss1; however:
  [COLOR="Red"]Package libxss1 is not installed.[/COLOR]
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Errors were encountered while processing:
 google-chrome-stable


doug@doug-XPS-M1330:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libflac++6 libindicate-qt1 liblastfm0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnspr4-0d libxss1
[COLOR="Blue"]The following NEW packages will be installed:
  libnspr4-0d libxss1[/COLOR]
0 upgraded, 2 newly installed, 0 to remove and 87 not upgraded.
1 not fully installed or removed.
Need to get 0 B/19.7 kB of archives.
After this operation, 143 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libnspr4-0d.
(Reading database ... 191846 files and directories currently installed.)
Unpacking libnspr4-0d (from .../libnspr4-0d_4.8.7-0ubuntu3_i386.deb) ...
Selecting previously deselected package libxss1.
Unpacking libxss1 (from .../libxss1_1%3a1.2.1-2_i386.deb) ...
Setting up libnspr4-0d (4.8.7-0ubuntu3) ...
Setting up libxss1 (1:1.2.1-2) ...
Setting up google-chrome-stable (14.0.835.202-r103287) ...
update-alternatives: using /usr/bin/google-chrome to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
update-alternatives: using /usr/bin/google-chrome to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
doug@doug-XPS-M1330:~$

---

### Post by rojaasensei on 2011-10-21
sudo apt-get install lzma worked for me.

Thank you very much for your advice!

---

