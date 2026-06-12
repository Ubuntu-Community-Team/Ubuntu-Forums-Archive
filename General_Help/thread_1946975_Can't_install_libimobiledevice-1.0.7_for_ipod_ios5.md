---
title: "Can't install libimobiledevice-1.0.7 for ipod ios5"
date: 2012-03-25
forum: General Help
---

### Post by seventyeights on 2012-03-25
I'm sure many people would love to get their ipods working with linux. Now that this update is out, I hope someone can show us how to get it working. I'm no genius but I already gave it a try:

Update is from:
[http://www.libimobiledevice.org/]("http://www.libimobiledevice.org/")

From the Readme:
> Requirements
============

Development Packages of:
	libgnutls
	libgcrypt
	glib2.0
	libplist
	libusbmuxd (within usbmuxd package, see below)

Software:
	usbmuxd (git clone git://git.marcansoft.com/usbmuxd.git)
	make
	autoheader
	automake
	autoconf
	libtool
	gcc

I got all the dev packs installed plus had to install dev packs for python and libplist++

I can now configure, make, and make install with no errors. However, I still have the same old symptoms (ipod won't recognize transferred music).

I believe that the new version is installed but the system is not using it. 

Ultimately though, I have no idea what I'm doing.

---

### Post by lorqvonray on 2012-03-28
Same here.  learned how to run the install and finally got it to install with no errors, but   dpkg -l | grep libimobiledevice still returns 1.0.7 not the 1.1.2 I 'made'   ii  libimobiledevice-utils                1.0.6-1ubuntu1~lucid3                           Library for communicating with iPhone and iPod Touch dev ii  libimobiledevice0                     0.9.7-1ubuntu1.2                                Library for communicating with the iPhone and iPod Touch ii  libimobiledevice1                     1.0.6-1ubuntu1~lucid3                           Library for communicating with the iPhone and iPod Touch        I also think I have got the new package in but am missing some kind of redirect to get ubuntu to use the new version.  Any help would be appreciated.

---

### Post by seventyeights on 2012-03-29
I can't make sense of the libimobiledevice page. In one place it says that ios5 works fine, but the chart says that there is still no support for music transfers. Not really my definition of "fine".

After performing some desparate naughtyness with my /usr/lib, and I've decided that there is no support yet. But I'll wait for the update to come down the pipes til I say for sure.

---

### Post by seventyeights on 2012-04-07
As a workaround. I've purchased and installed Windows, and then transcoded 22k flacs to an mp3 folder on that partition.

Then I installed itunes. But I can't get it to automatically scan the entire collection.

There is no rescan button in itunes.

I've spent hours moving folders and libraries around, deleting the db, reinstalling. All kinds of foolishness. No change.

It will only scan either 33, 50, or 51 songs. I've been seeing these same numbers over and over. I can raise that limit by adding individual artist folders, but I'm not doing that 800 times.

Anyway, that's where I'm at. No need to reply. Thanks for listening.

---

### Post by idoitprone on 2012-04-07
> **seventyeights said:**
> As a workaround. I've purchased and installed Windows, and then transcoded 22k flacs to an mp3 folder on that partition.

Then I installed itunes. But I can't get it to automatically scan the entire collection.

There is no rescan button in itunes.

I've spent hours moving folders and libraries around, deleting the db, reinstalling. All kinds of foolishness. No change.

It will only scan either 33, 50, or 51 songs. I've been seeing these same numbers over and over. I can raise that limit by adding individual artist folders, but I'm not doing that 800 times.

Anyway, that's where I'm at. No need to reply. Thanks for listening.

[https://launchpad.net/ubuntu/+source/libimobiledevice](https://launchpad.net/ubuntu/+source/libimobiledevice)

please do yourself a favor and use a ppa. packagemanagement is not easy.

---

### Post by seventyeights on 2012-04-14
Marking as solved because it installs easily in 12.04.

---

