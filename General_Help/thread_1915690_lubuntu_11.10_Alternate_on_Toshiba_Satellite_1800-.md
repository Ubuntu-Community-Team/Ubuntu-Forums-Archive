---
title: "lubuntu 11.10 Alternate on Toshiba Satellite 1800-100"
date: 2012-01-26
forum: General Help
---

### Post by ciaopaulo on 2012-01-26
Hi,

I'm having problems getting this install to complete.

Here's the first error:

------------------
[LEFT][I][!!] Install the base system

[COLOR=Black]Debootstrap warning[/COLOR][/I]  [I]

Warning: Failure trying to run:chroot /target dpkg --force-depends --install /var/cache/apt/archives/libc6_2.12-20ubuntu5_i386.deb[/I] 
[/LEFT]
------------------
and then...

-----------------
[I][!!] Install the base system
 
Failed to install the base system
The base system installation into /target/ failed/[/I]

*Check /var/log/syslog or see virtual console 4 for the details.*
------------------

The relevant contents of [I]virtual console 4:

-----------------
debootstrap: Unpacking libc6 (from ../libc6_2-20ubuntu5_i386.deb) ..
[/I][I]debootstrap: dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
[/I][I]debootstrap: dpkg: error processing /var/cache/apt/archives/libc6_2.13-20ubuntu5_i386.deb (--install):
[/I][I]debootstrap: subprocess dpkg-deb --fsys-tarfile returned error exist status 2
[/I][I]debootstrap: Errors were encountered while processing:
[/I]*debootstrap: *[I]/var/cache/apt/archives/libc6_2.13-20ubuntu5_i386.deb
base-installer: error: exiting on error base-installer/deboostrap-failed[/I]
*-----------------*

Something to do with the floppy drive? What? Why?

 [I'm using alternate because I need to manually configure xorg. Standard install ends in black screen.Install is from CD iso. The image has been validated.]

---

### Post by hhh on 2012-01-26
> **ciaopaulo said:**
> [I'm using alternate because I need to manually configure xorg. Standard install ends in black screen.
Sorry that this isn't a direct answer to your question, but have you tried booting the standard install with the boot parameter 'nomodeset' (without quotes)? This will usually start X with a low resolution and then you can configure xorg from there.

---

### Post by ciaopaulo on 2012-01-26
Strangely I had a floppy left in the drive, while trying to save the  logs. Thinking this might have strangely affected the install I reran it  and got this similar error message:

-----------------------------
[I]dependency problem:
debootstrap: dpkg predepends on zlib1g (>=1:1.1.4)
debootstrap: dpkg: warning: ignoring dependency problem!
debootstrap: dpkg: regarding .../dpkg_1.16.0.3ubuntu5_1386.deb containing dpkg, rep-
dependency problem:
debootstrap: dpkg predepends on coreutils (>=5.93.1)
debootstrap: dpkg: warning: ignoring dependency problem!
debootstrap: dpkg: regarding .../dpkg_1.16.0.3ubuntu5_1386.deb containing dpkg, rep-
dependency problem:
debootstrap: dpkg predepends on xz-utils
debootstrap:  xz-utils is not installed.
debootstrap: dpkg: warning: ignoring dependency problem!
debootstrap: 117 files and directories currently installed.)
debootstrap: Preparing to replace dpkg 1.16.0.3ubuntu5 (using .../dpkg_1.16.0.3ubuntu5_i386.deb) ...
debootstrap: Unpacking replacement dpkg ...
debootstrap: dpkg-deb: (subprocess): data: internal gzip read error: '<fd:0>: data error'
debootstrap: dpkg-deb:error: subprocess <decompress> returned error exit status 2
debootstrap: dpkg: error processing /var/cache/apt/archives/dpkg_1.16.0.3ubuntu5_i386.deb (install):
debootstrap: subprocess dpkg-deb --fsys-tarfile returned error status 2
debootstrap: Errors were encountered while processing:
debootstrap: /car/cache/apt/archives/dpkg_1.16.0.3ubuntu5_i386.deb
base-installer: error: exiting on error base-installer/debootstrap-failed[/I]
-----------------------------

> **hhh said:**
> have you tried booting the standard install with the boot parameter 'nomodeset' (without quotes)?

I'll burn the CD and give it a go now.

---

### Post by ciaopaulo on 2012-01-26
[s]Hmm. No joy I'm afraid **hhh**.

When I chose nomodeset, I get dropped to a terminal prompt.

I then edit /etc/X11/xorg.conf as in this file: [http://michaelminn.com/linux/toshiba1800/](http://michaelminn.com/linux/toshiba1800/)
with Option "NoDDC"

Then running "startx" gives me a blank screen again.[/s]

I retyped out my xorg.xonf and it started working! (in LiveCD mode, not done a full install yet)

Does xorg not like tabs perhaps? Hmm probably a typo.

Anyway I got it working but it crashed as soon as I launched Chromium. Too little RAM I guess. (Only 256Mb)

Still confused as to why the alternate failed so spectacularly.

---

### Post by hhh on 2012-01-26
With only 256M Ram, can I recommend Lubuntu to you?...
[http://lubuntu.net/about](http://lubuntu.net/about)

---

### Post by Rodney9 on 2012-01-27
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by ciaopaulo on 2012-01-27
> **hhh said:**
> With only 256M Ram, can I recommend Lubuntu to you?...
[http://lubuntu.net/about](http://lubuntu.net/about)

This is a Lubuntu install issue. See title of thread.

---

### Post by hhh on 2012-01-27
> **ciaopaulo said:**
> This is a Lubuntu install issue. See title of thread.
Akk! Brain fart, sorry. A lightweight (but buggy, last time I checked) browser to try is Midori...
[http://packages.ubuntu.com/oneiric/midori](http://packages.ubuntu.com/oneiric/midori)

---

### Post by ciaopaulo on 2012-01-27
Hehe no worries.

I don't think it's a RAM issue anymore. Lubuntu should be able to run (including apps) with the given memory. Slow perhaps but it should still get there.

The system can't go into a full install from the LiveCD. (Ie clicking on the "Install Lubuntu" icon in the top left). It crashes (screen freeze) every time.

---

### Post by Rodney9 on 2012-01-27
> **ciaopaulo said:**
> Hehe no worries.

I don't think it's a RAM issue anymore. Lubuntu should be able to run (including apps) with the given memory. Slow perhaps but it should still get there.

The system can't go into a full install from the LiveCD. (Ie clicking on the "Install Lubuntu" icon in the top left). It crashes (screen freeze) every time.

> [COLOR="Blue"]Lubuntu[/COLOR] System requirements
A Pentium II or Celeron system with 128MB of RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. It should be possible to install and run Lubuntu with less memory, but the result will likely not be suitable for practical use.

How to install [COLOR="Blue"]Lubuntu[/COLOR] - 
[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

You may want to check the CD as well - 

[https://help.ubuntu.com/community/Lubuntu/Documentation/CheckISO_CD](https://help.ubuntu.com/community/Lubuntu/Documentation/CheckISO_CD)

When one has downloaded an ISO file for installing or trying Ubuntu, it is recommended to test that the file is correct and safe to use. The MD5 calculation gives a checksum (called a hash value), which must equal the MD5 value of a correct ISO.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


Rodney

---

### Post by ciaopaulo on 2012-01-28
Yep, as I said in my OP the disk has been verified.

---

