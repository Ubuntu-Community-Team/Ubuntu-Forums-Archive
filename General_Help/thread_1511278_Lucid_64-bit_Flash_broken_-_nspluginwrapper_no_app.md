---
title: "Lucid 64-bit Flash broken - nspluginwrapper: no appropriate viewer found..."
date: 2010-06-16
forum: General Help
---

### Post by 3hough on 2010-06-16
I've searched all over and I seem to be the only one experiencing a very odd failure installing Flash. Everything was working great until I tried to "upgrade" from the 64-bit Flash plugin to the 32-bit one (v. 10.1.53.64).

I've been using [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/") w/ Firefox to keep Flash up to date, and previous to this it's been working great.

The error I'm getting from apt-get is:

> nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so

I did some investigating and tried to run nspluginwrapper manually:

```
$ nspluginwrapper -v -i /usr/lib/flashplugin-installer/libflashplayer.so 
/usr/bin/linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
```

Of course, I've tried removing/installing nspluginwrapper, flashplugin-installer, and flashplugin-nonfree many times. Here are some relevant system details... would appreciate any pointrs. Thanks!

Running Lucid 10.04 LTS, 2.6.32-23-generic #37-Ubuntu SMP x86_64 GNU/Linux

---

### Post by lovinglinux on 2010-06-19
Do you get any errors in the terminal executed by FLASH-AID?

---

### Post by 3hough on 2010-06-21
Thanks for your reply. Yes, there are errors from the FLASH-AID terminal window as well. I've omitted the download parts for brevity:

```


Please wait...DON'T CLOSE THIS TERMINAL!
[sudo] password for hough: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up flashplugin-installer (10.1.53.64ubuntu0.10.04.1) ...
Downloading...
--2010-06-21 08:04:24--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4739416 (4.5M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.1.53.64.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 15.2M 0s
    50K .......... .......... .......... .......... ..........  2% 12.8M 0s

  4500K .......... .......... .......... .......... .......... 98% 13.1M 0s
  4550K .......... .......... .......... .......... .......... 99% 13.2M 0s
  4600K .......... .......... ........                        100% 13.7M=0.4s

2010-06-21 08:05:01 (12.7 MB/s) - `./adobe-flashplugin_10.1.53.64.orig.tar.gz' saved [4739416/4739416]

Download done.
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
Finished! You can close this terminal. You must restart Firefox now.

```

Thanks for any insight.

---

### Post by lovinglinux on 2010-06-21
Try to disable the partner repository and run FLASH-AID again.

---

### Post by 3hough on 2010-06-21
Fixed! Thanks for the pointer. In case anyone else hits this error, the solution was to

[LIST=1]
[*]Disable the partner repository
[*]```
sudo apt-get purge nspluginwrapper
```
[*]```
sudo apt-get autoremove
```
[*]Reinstall the dozen or so packages that nspluginwrapper depends on directly. Find the list by running ```
apt-cache depends nspluginwrapper
```
[*]Run FLASH-AID if you're using Firefox, or
```
sudo apt-get install flashplugin-installer
```
[/LIST]

---

### Post by gabak on 2010-06-21
another word around it is just get google chrome and u will watch all utube with no flash plugin

or 

youtube.com/html5   ---->> u need some browser with html5 capability

no flash needed

---

