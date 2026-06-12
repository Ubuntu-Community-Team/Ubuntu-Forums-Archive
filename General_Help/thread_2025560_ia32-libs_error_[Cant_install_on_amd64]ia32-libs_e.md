---
title: "ia32-libs error [Cant install on amd64]ia32-libs error [Cant install on amd64]"
date: 2012-07-14
forum: General Help
---

### Post by ranger1021994 on 2012-07-14
I've been trying to install ia32-libs from Synaptic after upgrading to Precise
I get this :
```
(Reading database ... 301842 files and directories currently installed.)
Unpacking libsdl1.2debian:i386 (from .../libsdl1.2debian_1.2.14-6.4ubuntu3_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid code lengths set'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libsdl1.2debian_1.2.14-6.4ubuntu3_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/i386-linux-gnu/libSDL-1.2.so.0.11.3'
Selecting previously unselected package libsdl-image1.2:i386.
Unpacking libsdl-image1.2:i386 (from .../libsdl-image1.2_1.2.10-3_i386.deb) ...
Selecting previously unselected package libsdl-mixer1.2:i386.
Unpacking libsdl-mixer1.2:i386 (from .../libsdl-mixer1.2_1.2.11-7_i386.deb) ...
Selecting previously unselected package libsdl-net1.2:i386.
Unpacking libsdl-net1.2:i386 (from .../libsdl-net1.2_1.2.7-5_i386.deb) ...
Selecting previously unselected package libsdl-ttf2.0-0:i386.
Unpacking libsdl-ttf2.0-0:i386 (from .../libsdl-ttf2.0-0_2.0.9-1.1ubuntu1_i386.deb) ...
Selecting previously unselected package ia32-libs-multiarch:i386.
Unpacking ia32-libs-multiarch:i386 (from .../ia32-libs-multiarch_20090808ubuntu36_i386.deb) ...


```

And on reinstalling ia32-libs:multiarch from Synaptic using Broken filter i get this :

```
dpkg: dependency problems prevent configuration of ia32-libs-multiarch:i386:
 ia32-libs-multiarch:i386 depends on libsdl1.2debian; however:
  Package libsdl1.2debian:i386 is not installed.
dpkg: error processing ia32-libs-multiarch:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsdl-net1.2:i386:
 libsdl-net1.2:i386 depends on libsdl1.2debian (>= 1.2.10-1); however:
  Package libsdl1.2debian:i386 is not installed.
dpkg: error processing libsdl-net1.2:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsdl-image1.2:i386:
 libsdl-image1.2:i386 depends on libsdl1.2debian (>= 1.2.10-1); however:
  Package libsdl1.2debian:i386 is not installed.
dpkg: error processing libsdl-image1.2:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on ia32-libs-multiarch; however:
  Package ia32-libs-multiarch is not installed.
  Package ia32-libs-multiarch:i386 is not configured yet.
dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsdl-mixer1.2:i386:
 libsdl-mixer1.2:i386 depends on libsdl1.2debian (>= 1.2.10-1); however:
  Package libsdl1.2debian:i386 is not installed.
dpkg: error processing libsdl-mixer1.2:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsdl-ttf2.0-0:i386:
 libsdl-ttf2.0-0:i386 depends on libsdl1.2debian (>= 1.2.10-1); however:
  Package libsdl1.2debian:i386 is not installed.
dpkg: error processing libsdl-ttf2.0-0:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ia32-libs-multiarch:i386
 libsdl-net1.2:i386
 libsdl-image1.2:i386
 ia32-libs
 libsdl-mixer1.2:i386
 libsdl-ttf2.0-0:i386

```

Any idea of Short Read problem on amd64 PC ?
:confused: :confused:

---

### Post by ranger1021994 on 2012-07-15
Bump

---

### Post by Flash Kid on 2012-07-16
I've had the same error as well trying to install Skype on my machine.  The 32-bit version won't install because it doesn't overwrite a config file (which I even tried renaming to no avail) and the 64-bit version will not install because "Cannot install ia32-libs".  When I force installed the ia32 libs, a whole lot of errors began occuring on my system.  Part of me actually wonders if I should have just installed 32-bit Ubuntu on my 64-bit machine...

FK

---

### Post by dekker on 2012-07-17
> **Flash Kid said:**
> I've had the same error as well trying to install Skype on my machine.  The 32-bit version won't install because it doesn't overwrite a config file (which I even tried renaming to no avail) and the 64-bit version will not install because &quot;Cannot install ia32-libs&quot;.  When I force installed the ia32 libs, a whole lot of errors began occuring on my system.  Part of me actually wonders if I should have just installed 32-bit Ubuntu on my 64-bit machine...

FK

 +1 here too, gone back to v2.2

---

### Post by james_xxx on 2012-07-24
It would be great to find a solution to this problem.

Oddly, I upgraded a half-dozen 64-bit desktops to Precise, but this problem was only encountered on one of those machines.

---

### Post by ranger1021994 on 2012-09-13
Miraculously solved...Maybe recent updates might have fixed it.

Thank you all for your interest :)

---

### Post by baijea on 2012-09-18
I had a similar problem with broken dependencies when trying to install **wine** and **acroread**, just after upgrading to **12.04** from **11.04** (passing over 11.10). It seems that some ppa's I had in 11.04 installed **newer versions of applications** in the system. After upgrading, the remains of these apps seemed to do some mess in the dependencies.

The solution that seems to work (until now), was found on a german ubuntu board ([http://forum.ubuntuusers.de]("http://forum.ubuntuusers.de/topic/paketabhaengigkeit-mit-ia32-libs-kann-nicht-au/2/"), posts from user Lasall):

First a downgrade is required and done with the following:
create the 'preferences' file:
```
sudo vi /etc/apt/preferences
```
and insert the following lines:
```

Package: *       
Pin: release a=precise*
Pin-Priority: 2012

```
Pin-Priority must be greater than 1000.

Then you may downgrade the programs with:
```
sudo apt-get dist-upgrade
```
Then you may install packages that complained about dependencies, like
```
sudo apt-get install ia32-libs-multiarch
```, or ```
sudo apt-get install ia32-libs
```

Finally, you should remove the file you just created:
```
rm /etc/apt/preferences
```
because else no new updates would be found.

Hope this helps you too!

---

### Post by cscj01 on 2012-09-20
> **baijea said:**
> I had a similar problem with broken dependencies when trying to install **wine** and **acroread**, just after upgrading to **12.04** from **11.04** (passing over 11.10). It seems that some ppa's I had in 11.04 installed **newer versions of applications** in the system. After upgrading, the remains of these apps seemed to do some mess in the dependencies.

The solution that seems to work (until now), was found on a german ubuntu board ([http://forum.ubuntuusers.de]("http://forum.ubuntuusers.de/topic/paketabhaengigkeit-mit-ia32-libs-kann-nicht-au/2/"), posts from user Lasall):

First a downgrade is required and done with the following:
create the 'preferences' file:
```
sudo vi /etc/apt/preferences
```
and insert the following lines:
```

Package: *       
Pin: release a=precise*
Pin-Priority: 2012

```
Pin-Priority must be greater than 1000.

Then you may downgrade the programs with:
```
sudo apt-get dist-upgrade
```
Then you may install packages that complained about dependencies, like
```
sudo apt-get install ia32-libs-multiarch
```, or ```
sudo apt-get install ia32-libs
```

Finally, you should remove the file you just created:
```
rm /etc/apt/preferences
```
because else no new updates would be found.

Hope this helps you too!

This solved a problem for me as well about installing prereqs for Wine.  However, I'm not sure how you came about the file entries that were needed and why the file needed to be in /etc/apt.  I know you reference the German board, but I couldn't get enough out of that to understand why it worked.  Do you know why that particular file is what we needed?  In particular, why did the file entries allow everything to be downgraded to the current level in Main?  I'd really like to understand this, because it is very useful for those of us who use PPA's.  I had tried to purge all my PPA's as a solution, but that did not work for me.

---

### Post by baijea on 2012-09-22
Hi,

as far as I know, /etc/apt/preferences is used for **pinning**; see **[PinningHowto]("http://help.ubuntu.com/community/PinningHowto")** and also, sorry, German Wiki translated: **[wiki.ubuntuusers.de/Apt-Pinning]("http://translate.google.com/translate?hl=en&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FApt-Pinning")**. This page is based on ```
man apt_preferences
```

The man page states that 
> P (priority) > 1000 causes a version to be installed even if this constitutes a downgrade of the package
this is what was desired here.

Glad it could help ;)

---

### Post by cscj01 on 2012-09-23
> **baijea said:**
> Hi,

as far as I know, /etc/apt/preferences is used for **pinning**; see **[PinningHowto]("http://help.ubuntu.com/community/PinningHowto")** and also, sorry, German Wiki translated: **[wiki.ubuntuusers.de/Apt-Pinning]("http://translate.google.com/translate?hl=en&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FApt-Pinning")**. This page is based on ```
man apt_preferences
```

The man page states that 

this is what was desired here.

Glad it could help ;)

Thanks for the references.  I now understand the file entries.  The rest makes sense in light of that.

---

### Post by gbz on 2012-12-12
Wow, this saved my life. Thanks!

> **baijea said:**
> I had a similar problem with broken dependencies when trying to install **wine** and **acroread**, just after upgrading to **12.04** from **11.04** (passing over 11.10). It seems that some ppa's I had in 11.04 installed **newer versions of applications** in the system. After upgrading, the remains of these apps seemed to do some mess in the dependencies.

The solution that seems to work (until now), was found on a german ubuntu board ([http://forum.ubuntuusers.de]("http://forum.ubuntuusers.de/topic/paketabhaengigkeit-mit-ia32-libs-kann-nicht-au/2/"), posts from user Lasall):

First a downgrade is required and done with the following:
create the 'preferences' file:
```
sudo vi /etc/apt/preferences
```and insert the following lines:
```

Package: *       
Pin: release a=precise*
Pin-Priority: 2012

```Pin-Priority must be greater than 1000.

Then you may downgrade the programs with:
```
sudo apt-get dist-upgrade
```Then you may install packages that complained about dependencies, like
```
sudo apt-get install ia32-libs-multiarch
```, or ```
sudo apt-get install ia32-libs
```Finally, you should remove the file you just created:
```
rm /etc/apt/preferences
```because else no new updates would be found.

Hope this helps you too!

---

