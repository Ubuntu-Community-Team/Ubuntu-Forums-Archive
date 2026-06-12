---
title: "cannot write to home dir"
date: 2009-07-24
forum: General Help
---

### Post by viralmeme on 2009-07-24
Hi there. Just checked out the most recent Ubuntu. Am impressed, installation was a breeze on my desktop computer. It even asked if I wanted to keep the old version or overwrite it. The GUI looks a polished and professional piece of work. Makes nonsence of that 'not yet ready for the desktop' nonsence.

Problem: I installed Ubuntu to a USB device using the 'USB Startup disk creator' utility. Cannot write to /home directory, cannot import bookmarks - how to fix please :confused:
--

../IcedTeaPlugin.cc:5885: Error: Failed to create data directory: /home/ubuntu/.icedteaplugin: No space left on device

$mkdir /home/ubuntu/test

cannot create directory `test': No space left on device

$ubuntu@ubuntu:~$ df -h | grep "/dev/sd"

/dev/sdb1             3.9G  1.5G  2.4G  40% /cdrom
/dev/sda1              49G  9.5G   40G  20% /media/disk
--

update:

GeeWizz, I used something called** 'the Google' **and found this tutorial .. :o

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

updated update:

that only works on a standard Ubuntu. Problem: still cannot write to home or install plugins. Any help would be greatly appreciated::
--

Trying to install flash plugin::

Download done.
install: writing 'usr/lib/flashplugin-installer/libflashplayer.so No space left on device

debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new No space left on device

..

E: flashplugin-installer: subprocess post-installation script returned exit status 1
--

Success finally:

Using qpart I created two partitions a 1.5GB fat and a 2GB ext4 casper-rw partition. Then I ran the 'USB Startup disk creator' and selected 500MB for savign files. Booted from the USB and it hangs on loading the ramdisk. Went back and selected 200MB and sucess. It runs and saves settings, at least for user.

---

