---
title: "No Flash plugin in Firefox or Chrome"
date: 2010-05-01
forum: General Help
---

### Post by blevitin on 2010-05-01
As the title states, I'm having trouble getting Flash to work in either Firefox or Chrome.  I'm on 32-bit Lucid.

These are the methods I've tried:

[http://whatan00b.com/enabling-flash-in-chrome-on-ubuntu-10-04](http://whatan00b.com/enabling-flash-in-chrome-on-ubuntu-10-04)
 ^ When I ask it to locate libflashplayer.so, I get this:
> brenna@otter:~$ locate libflashplayer.so
/usr/lib/chromium-browser/plugins/libflashplayer.so
and yet Flash in Chrome still doesn't work.

I've tried > sudo apt-get install flashplugin-nonfree, but considering I'm still not able to view Flash in Firefox, I'm not sure what (if anything) it did.

I've tried going into Synaptic and downloading the Restricted Extras, but even with them there, nothing in either browser.

I've tried this [http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1), which got me to here: > brenna@otter:/$ sudo apt-get remove swfdec-mozilla
[sudo] password for brenna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  firefox-3.5-branding
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
The next two commands also yielded a 'not installed'.
> brenna@otter:/$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  firefox-3.5-branding
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
brenna@otter:/$

I've also tried > [SIZE=1][SIZE=2][SIZE=1]sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/share/ubufox/plugins/ which got me > cp: cannot stat `/usr/lib/flashplugin-installer/libflashplayer.so': No such file or directory.[/SIZE]

Any help would be much appreciated.
[/SIZE]
[/SIZE]

---

### Post by dino99 on 2010-05-01
you need to clean your tweaks first (remove/purge), then install ubuntu-restricted-extras and flashplugin-installer

if you have made lot of testing, you may use gconf-cleaner to wipe all the broken symlinks and wrong settings left behind

---

### Post by blevitin on 2010-05-01
> **dino99 said:**
> you need to clean your tweaks first (remove/purge), then install ubuntu-restricted-extras and flashplugin-installer

I have them both installed.  Do you mean remove the libflashplayer.so s from their respective hiding places?

---

