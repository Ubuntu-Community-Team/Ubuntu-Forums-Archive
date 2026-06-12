---
title: "Google Earth"
date: 2010-08-12
forum: General Help
---

### Post by BSG Fan on 2010-08-12
hey guys. Salutes from my part.

I downloaded the Google Earth (GoogleEarthWin.exe) and later I did the following operation:
[COLOR="Lime"]make-googleearth-package --file Google EarthLinux.bin--force[/COLOR]



But the $64,000 question is:
Where the heck is the Google Earth in my pc?
It is no located in the Applications + Internet, etc, etc.
Where it is so I can use it? lol

Help

BSG Fan

:/

---

### Post by [Shawn] on 2010-08-12
I'm not an expert on finding things.
But you can run  Application finder and then if it shows up drag it onto your desktop.

---

### Post by BSG Fan on 2010-08-12
This is what it says:

An error occurred while loading the archive.

Archive:  /home/@@@@@$/Downloads/GoogleEarthWin.exe

[/home/@@@@@$/Downloads/GoogleEarthWin.exe]

  End-of-central-directory signature not found.  Either this file is not

  a zipfile, or it constitutes one disk of a multi-part archive.  In the

  latter case the central directory and zipfile comment will be found on

  the last disk(s) of this archive.

note:  /home/@@@@@$/Downloads/GoogleEarthWin.exe may be a plain executable, not an archive

zipinfo:  cannot find zipfile directory in one of /home/@@@@@$/Downloads/GoogleEarthWin.exe or

          /home/@@@@@$/Downloads/GoogleEarthWin.exe.zip, and cannot find /home/@@@@@$/Downloads/GoogleEarthWin.exe.ZIP, period.

Any idea people?
:confused:

=======================
I went here:
[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)
and I did:
# The file you downloaded should be called GoogleEarthLinux.bin. Find this file, right mouse click on it and select Open with Other Application.
# Click to expand the Use a custom command section of the Open With dialog. Type sh, and click Open.

but nothing happened.

---

### Post by cj.surrusco on 2010-08-12
Maybe you could try the alternative installation option in the following link, it looks easy enough to be worth a shot.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

I actually just tried it myself, and it worked perfectly.

---

### Post by jcolyn on 2010-08-12
I copied the below from a previous post I made in reference to googleearth This is the only version I have found that works properly..

> Most versions of GoogleEarth don't work right but there is a better fix. Go to [http://packages.medibuntu.org/](http://packages.medibuntu.org/) and click on the Medibuntu link at the top. Next [Repository Howto]("http://help.ubuntu.com/community/Medibuntu")  and follow the directions. Once done go to a terminal and enter sudo  apt-get update. After this go to your Synaptics package manager and in  the search box type googleearth. Mark it for install and then apply.

Be sure to remove any old versions first..

---

### Post by BSG Fan on 2010-08-12
> **cj.surrusco said:**
> Maybe you could try the alternative installation option in the following link, it looks easy enough to be worth a shot.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

I actually just tried it myself, and it worked perfectly.


Hi
I am trying but doesn't work.

Now I am trying again the following (shorted)


.
.
.
rt.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libspatial.so'

Checking shlib deps: libspatial.so

dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'

Checking shlib deps: libGLU.so.1

Checking shlib deps: libcommon.so

dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_platform.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libfusioncommon.so'

dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'

Checking shlib deps: libmath.so

dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'

Checking shlib deps: libIGUtils.so

Checking shlib deps: libfusioncommon.so

dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'

Checking shlib deps: libcomponentframework.so

dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'

Package: googleearth

Version: 5.2.1.1329+0.5.7-1

Section: non-free/science

Priority: optional

Maintainer:  <TY$#@@TY$#@-desktop>

Architecture: i386

Depends: ttf-dejavu | ttf-bitstream-vera | msttcorefonts, libc6 (>= 2.0), libc6 (>= 2.1.3), libc6 (>= 2.3), libc6 (>= 2.3.2), libc6 (>= 2.3.6-6~), libc6 (>= 2.4), libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libstdc++6 (>= 4.1.1), libstdc++6 (>= 4.2.1), libx11-6, libx11-6 (>= 0), libxext6, libxext6 (>= 0), libxrender1, zlib1g (>= 1:1.1.4), zlib1g (>= 1:1.2.0) 

Description: Google Earth, a 3D map/planet viewer

 Package built with googleearth-package.

dpkg-deb: building package `googleearth' in `./googleearth_5.2.1.1329+0.5.7-1_i386.deb'.

dpkg-deb: unable to create `./googleearth_5.2.1.1329+0.5.7-1_i386.deb': Permission denied

Success!

You can now install the package with e.g. sudo dpkg -i <package>.deb

TY$#@@TY$#@-desktop:~$ 


Now what I do?

In my first attempt I pasted 
sudo dpkg -i ./googleearth_5.1.3535.3218+0.5.7-1_i386.deb

this in the terminal but I got error...

so what I do now?

---

### Post by x86scorpion on 2010-08-13
You just did the right thing. 

```
sudo apt-get install googleearth-package
make-googleearth-package --force
```


..but you must install it like this

```
sudo dpkg -i googleearth*.deb
```


..and to view its location, try

```
whereis googleearth
```


..mine shows

> googleearth: /usr/bin/googleearth /usr/lib/googleearth


..or you can find Google Earth under 

> Applications > Internet > Google Earth

---

### Post by BSG Fan on 2010-08-13
> **x86scorpion said:**
> You just did the right thing. 

```
sudo apt-get install googleearth-package
make-googleearth-package --force
```


..but you must install it like this

```
sudo dpkg -i googleearth*.deb
```


..and to view its location, try

```
whereis googleearth
```


..mine shows




..or you can find Google Earth under

I am checking...
wait

---

### Post by BSG Fan on 2010-08-13
I did it!
======================

%$$$###@%$$$###-desktop:~$ sudo apt-get install googleearth-package

[sudo] password for %$$$###: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

googleearth-package is already the newest version.

The following packages were automatically installed and are no longer required:

  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

%$$$###@%$$$###-desktop:~$ sudo dpkg -i googleearth*.deb

Selecting previously deselected package googleearth.

(Reading database ... 162108 files and directories currently installed.)

Unpacking googleearth (from googleearth_5.2.1.1329+0.5.7-1_i386.deb) ...

Setting up googleearth (5.2.1.1329+0.5.7-1) ...



Processing triggers for shared-mime-info ...

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



Processing triggers for desktop-file-utils ...

Processing triggers for python-gmenu ...

Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...

Processing triggers for python-support ...

%$$$###@%$$$###-desktop:~$ whereis googleearth

googleearth: /usr/bin/googleearth /usr/lib/googleearth

%$$$###@%$$$###-desktop:~$ 


=======================

and I went to "File System" 
=> Bin 
=> right clicked the file 
=> Typed "Sh"
=> Open
and its showed up yn Applications => Internet
======================

Thanks you!

---

### Post by NuxIT on 2011-01-20
Holy crap. I can't believe I spent hours trying to install GE on xubuntu 10.10 by following all these crazy installation instructions that did not work for me!! 

Turns out all I had to do was VERY simple (DOH):

> Google Earth now has pre-compiled .deb packages (32 & 64-bit) directly available for Ubuntu:

[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

Just double-click the file name where you have saved it and the package installer will run. 

---

