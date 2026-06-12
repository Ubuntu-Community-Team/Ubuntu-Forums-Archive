---
title: "dmesg's after Nautilus crashed: what do this mean ?"
date: 2011-09-26
forum: General Help
---

### Post by astrobob.tk on 2011-09-26
Hello

What does the following dmesg's mean (i used dmesg when two nautilus suddenly crashed while copying files; it happened two times, sequencially):

```
[62956.871035] nautilus[30836]: segfault at c ip 0811d8a1 sp bfec10b0 error 4 in nautilus[8048000+196000]
[63253.022886] nautilus[20597]: segfault at c ip 0811d8a1 sp bff43710 error 4 in nautilus[8048000+196000]
```

thanks

---

### Post by mikewhatever on 2011-09-26
Segfault usually means the program tried to access memory it wasn't supposed to access.
I am sure Wikipedia has a more elaborate explanation:
[https://secure.wikimedia.org/wikipedia/en/wiki/Segmentation_fault](https://secure.wikimedia.org/wikipedia/en/wiki/Segmentation_fault)

---

### Post by astrobob.tk on 2011-09-29
> **mikewhatever said:**
> Segfault usually means the program tried to access memory it wasn't supposed to access.
I am sure Wikipedia has a more elaborate explanation:
[https://secure.wikimedia.org/wikipedia/en/wiki/Segmentation_fault](https://secure.wikimedia.org/wikipedia/en/wiki/Segmentation_fault)

I tried understand the article, but all I got is what u said: trying to access memory that doesn't exist ? or?

Moreover, recently I've been facing some other errors & weir behaviour particularly with skype & empathy:

from system log viewer: ```
process `skype' is using obsolete setsockopt SO_BSDCOMPAT
```

& from dmesg when empathy was crashing: ```
empathy[24848]: segfault at 0 ip b59a9fe0 sp bfb8043c error 4 in libc-2.11.1.so[b58c9000+153000]
```

I opened a thread about skype (& included empathy) here: [http://ubuntuforums.org/showthread.php?p=11294563]("http://ubuntuforums.org/showthread.php?p=11294563")

Besides I think there's something weird about "free" results:

```
$ free -tm
             total       used       free     shared    buffers     cached
Mem:          3987       3519        468          0        130       1286
-/+ buffers/cache:       2101       1885
Swap:         4767          0       4767
Total:        8755       3519       5236
```

If I udnerstand correctly, the free RAM is 468 MB ?
Why then does my "screenlet"  show that I'm using only 52% (i.e. 2GB) ?

am I reading it wrong ? & why are those failings happenning ?

thanks

---

### Post by dino99 on 2011-09-29
do some cleaning:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a

and pay attention to temperature (fans running, system not too dusty) 
at last 1 of your stick memory is maybe faulty

---

### Post by astrobob.tk on 2011-09-29
> **dino99 said:**
> do some cleaning:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a


I often do all of these except for the last two of them.

The last command gave:

```
adgui.bittorrent to provide /usr/bin/btdownloadgui (btdownloadgui) in auto mode.
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic-pae
update-alternatives: using /usr/bin/bsd-write to provide /usr/bin/write (write) in auto mode.
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
done.
done.
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

 * Stopping ClamAV daemon clamd                                                                                                                                                               [ OK ] 
 * Starting ClamAV daemon clamd                                                                                                                                                                      Bytecode: Security mode set to "TrustSigned".
                                                                                                                                                                                              [ OK ]
 * Stopping ClamAV virus database updater freshclam                                                                                                                                           [ OK ] 
 * Starting ClamAV virus database updater freshclam                                                                                                                                           [ OK ] 
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic-pae
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
install-info: No dir file specified; try --help for more information.

```

> and pay attention to temperature (fans running, system not too dusty) 
at last 1 of your stick memory is maybe faulty

I do that; i follow the temperature using acpi -t & usually its in the range of 45~70 (70 being only when doing video/image & having several other programs running). Right now, am browsing in Opera & Chromium & using Tomboy, have several screenle> ts running & & have a gedit open along with nautilus. The temp. is:
```
Thermal 0: ok, 51.0 degrees C
Thermal 1: ok, 47.0 degrees C
Thermal 2: ok, 49.0 degrees C

```

i didn't get this: system not too dusty !!! what do u mean ?

Moreover, stick faulty ? It's been only a 13~14 months since i bought the laptop. How might a stick get faulty ? & how can I make sure it is (not) ?


Note: Today before running my system, I ran a live disc & mad: ```
sudo fsck /dev/sda7
```. All seemed ok.

I ran my system & now have been running empathy (from terminal) since i logged in & nothing weird happened yet.

---

