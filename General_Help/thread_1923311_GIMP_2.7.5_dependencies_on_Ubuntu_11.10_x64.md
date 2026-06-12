---
title: "GIMP 2.7.5 dependencies on Ubuntu 11.10 x64"
date: 2012-02-10
forum: General Help
---

### Post by Bucic on 2012-02-10
Solution / answer in this post
[http://ubuntuforums.org/showpost.php?p=11726223&postcount=54](http://ubuntuforums.org/showpost.php?p=11726223&postcount=54)
(or [http://ubuntuforums.org/showpost.php?p=11683286&postcount=35](http://ubuntuforums.org/showpost.php?p=11683286&postcount=35))
_______________________

Recently I got updates to some gimp-related libraries through update manager. Unfortunately I allowed it to do a partial upgrade which involved removing my GIMP 2.7.4 installation. Now I see (in the SC) that 2.7.5 is available but I can't install it due to missing libraries / wrong versions. I have always used the matthaeus svn ppa.

When I tried to install it through Software Center I got
```
The following packages have unmet dependencies:

gimp: Depends: python-gtk2 (>= 2.8.0) but 2.24.0-2 is to be installed
      Depends: libc6 (>= 2.11) but 2.13-20ubuntu5 is to be installed
      Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu2 is to be installed
      Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
      Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
      Depends: libgs9 (>= 8.61.dfsg.1) but 9.04~dfsg-0ubuntu11.5 is to be installed
      Depends: libgtk2.0-0 (>= 2.24.0) but 2.24.6-0ubuntu5 is to be installed
      Depends: libgudev-1.0-0 (>= 147) but 1:173-0ubuntu4.1 is to be installed
      Depends: libjpeg62 (>= 6b1) but 6b1-1ubuntu2 is to be installed
      Depends: librsvg2-2 (>= 2.14.4) but 2.34.1-2 is to be installed
      Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
```

I used the 'dep' command and got
```
~$ sudo apt-get build-dep gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gawk krb5-multidev libaa1-dev libart-2.0-dev libasound2-dev libbabl-0.0-0-dev
  libcups2-dev libcupsimage2-dev libcurl4-openssl-dev libffi-dev libgegl-0.0-dev
  libgs-dev libgssrpc4 libgtk-3-dev libhal-dev libidn11-dev libijs-dev libjasper-dev
  libjbig2dec0-dev libjpeg62-dev libkadm5clnt-mit8 libkadm5srv-mit8 libkdb5-5
  libkrb5-dev liblcms1-dev libldap2-dev libmng-dev libncurses5-dev libpaper-dev
  libpoppler-dev libpoppler-glib-dev librsvg2-dev libsigsegv2 libslang2-dev libssl-dev
  libtiff4-dev libtiffxx0c2 libtinfo-dev libwmf-dev libxmu-dev libxmu-headers libxpm-dev
  libxt-dev libzip-dev libzip1 patchutils python-dev python-gobject-2-dev
  python-gobject-dev python-gtk2-dev python-rsvg python2.7-dev xvfb
0 upgraded, 53 newly installed, 0 to remove and 0 not upgraded.
Need to get 24,6 MB of archives.
After this operation, 99,7 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Y
```
```

~$ sudo apt-get install gimp

.
.
.
The following packages have unmet dependencies:
 gimp : Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
E: Unable to correct problems, you have held broken packages.

```
So it looks like I had narrowed it down to one missing library. How can I resolve this? I need GIMP for my work!

EDIT:
The script [http://www.zanshine.com/blog/stephane-richard/software/2011-10-05/cutting-edge-gimp-in-latest-ubuntu/](http://www.zanshine.com/blog/stephane-richard/software/2011-10-05/cutting-edge-gimp-in-latest-ubuntu/) also reported the same problem with libglib2.0-0 (>= 2.31.2)

EDIT:
I tried installing the package from [http://packages.debian.org/sid/libglib2.0-0](http://packages.debian.org/sid/libglib2.0-0) but I got 
```
~/Downloads$ sudo dpkg -i libglib2.0-0_2.30.2-6_amd64.deb
[sudo] password for hg1: 
(Reading database ... 342598 files and directories currently installed.)
Preparing to replace libglib2.0-0 2.30.0-0ubuntu4 (using libglib2.0-0_2.30.2-6_amd64.deb) ...
De-configuring libglib2.0-0:i386 ...
Unpacking replacement libglib2.0-0 ...
dpkg: error processing libglib2.0-0 (--install):
 libglib2.0-0:amd64 2.30.2-6 cannot be configured because libglib2.0-0:i386 is in a different version (2.30.0-0ubuntu4)
dpkg: error processing libglib2.0-0:i386 (--install):
 libglib2.0-0:i386 2.30.0-0ubuntu4 cannot be configured because libglib2.0-0:amd64 is in a different version (2.30.2-6)
Errors were encountered while processing:
 libglib2.0-0
 libglib2.0-0:i386

```

---

### Post by matvancormick on 2012-02-10
Same problem on Ubuntu 11.10 32bit. Any idea???

---

### Post by Bucic on 2012-02-10
Did you also recently get som lib* updates and you also use the matthaeus ppa?

---

### Post by luk1don on 2012-02-10
It seems like the packager built this version of Gimp on Ubuntu Precise or some Debian. I am looking for another repo. You may try to build latest Gimp from source (git). There is not big difference between Gimp 2.7.4 and Gimp 2.7.5...

---

### Post by jerrrys on 2012-02-10
GIMP 2.7.x is a developmental release.  Wouldn't a stable release (2.6) be a better choice for a work environment?

---

### Post by alexan on 2012-02-10
The 2.3**_1_**.16-0ubuntu1 dependencies are currently available only for precise pangolin.

---

### Post by matvancormick on 2012-02-10
> **Bucic said:**
> Did you also recently get som lib* updates and you also use the matthaeus ppa?

Yes, at all. I did partial upgrade from 2.7.4

---

### Post by matvancormick on 2012-02-10
> **luk1don said:**
> It seems like the packager built this version of Gimp on Ubuntu Precise or some Debian. I am looking for another repo. You may try to build latest Gimp from source (git). There is not big difference between Gimp 2.7.4 and Gimp 2.7.5...

```
Changes in GIMP 2.7.5
=====================


UI:

 - Minor application menu fixes on the Mac
 - Make the toolbox arbitrarily resizable again
 - Add axis labels to the dynamics curves to make them more obvious
 - Fix dockable showing to do the right thing in both MWM and SWM
 - Fix some glitches in the tool preset UI, like proper sensitivity


Core:

 - Restore autoshrink functionality in the rectangle tools
 - Allow smudge to work with dynamic brushes
 - Make sure tool presets and tool options are consistent after loading


Plug-ins:

 - Proper toplevel item sorting in the help browser
 - Use libraries instead of launching programs in file-compressor
 - Use the Ghostscript library instead of launching ghostscript
 - Allow to switch off antialiasing when importing from PDF


Data:

 - Add a new set of default brushes and tool presets from Ramon Miranda


Source and build system:

 - Remove the unmaintained makefile.msc build system
 - Explicitly link plug-ins to -lm when needed
 - Also create .xz tarballs


General:

 - Lots of bug fixes
 - Tons and tons of translation updates
```

---

### Post by matvancormick on 2012-02-10
> **jerrrys said:**
> GIMP 2.7.x is a developmental release.  Wouldn't a stable release (2.6) be a better choice for a work environment?

Stable release have not Single Window Mode. Gimp 2.7.x have it.

---

### Post by Bucic on 2012-02-10
OK, so if it's not possible to fix the dependencies then how do I revert to 2.7.4? The script linked above suffer from the same dependency problem, so it's a no go ;)

---

### Post by matvancormick on 2012-02-10
> **Bucic said:**
> OK, so if it's not possible to fix the dependencies then how do I revert to 2.7.4? The script linked above suffer from the same dependency problem, so it's a no go ;)

Hey Bucic, I tried to install gimp 2.7.5 on ubuntu 12.04 LTS alpha 2. Same problem! Nothing to do! So you can:

1. Wait until matthaeus fix it

or

2. Get source code of 2.7.4 then compile & install it

3. If you have "old" 2.7.4 deb packages in /var/cache/apt/archives then reinstall gimp and gimp-data (remove 2.7.5 and all matthaeus' repositories first!)

Hope it helps.
Matheus

---

### Post by ZaydHumsy on 2012-02-10
I would guess it's not? (I'm having this same issue.)

---

### Post by cartoonist on 2012-02-10
Just piling on. I already had Gimp installed, and after an automatic system update, it just disappeared on me! Trying to install it again, I got the exact same message as the first poster in the thread.

---

### Post by ZaydHumsy on 2012-02-10
> **cartoonist said:**
> Just piling on. I already had Gimp installed, and after an automatic system update, it just disappeared on me! Trying to install it again, I got the exact same message as the first poster in the thread.

Yeah, same thing happened to me.

---

### Post by lewmnik on 2012-02-10
If you are using oneiric:

GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main

deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main

---

### Post by forrestcupp on 2012-02-10
> **lewmnik said:**
> If you are using oneiric:

GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main

deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main

Wow! That did the trick. Thank you. I was searching for a solution earlier today.

A side note: for anyone who has installed a ppa that ends up having problems, and you'd just like to be able to at least go back to old versions, there is a package in the repos called ppa-purge that is pretty helpful with that.

---

### Post by Buster95 on 2012-02-11
I have the same problem but this solution didn't work for me. The download progressed normally, including those from the repositories mentioned above. However, when I tried to run Gimp, I got the message:

 "Gtk+ version too old (micro mismatch)

GIMP requires GTK+ version 2.24.7 or later.
Installed GTK+ version is 2.24.6.

Somehow you or your software packager managed
to install GIMP with an older GTK+ version.

Please upgrade to GTK+ version 2.24.7 or later."

Any thoughts?

---

### Post by lewmnik on 2012-02-11
> **Buster95 said:**
> I have the same problem but this solution didn't work for me. The download progressed normally, including those from the repositories mentioned above. However, when I tried to run Gimp, I got the message:

 "Gtk+ version too old (micro mismatch)

GIMP requires GTK+ version 2.24.7 or later.
Installed GTK+ version is 2.24.6.

Somehow you or your software packager managed
to install GIMP with an older GTK+ version.

Please upgrade to GTK+ version 2.24.7 or later."

Any thoughts?

Not being cheeky, but did you first:
```
sudo apt-get upgrade
```
before reinstalling gimp?

---

### Post by eMirage on 2012-02-11
from: [https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)





GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos
 deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main
 deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main

---

### Post by Bao2 on 2012-02-11
> **eMirage said:**
> from: [https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)

GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos
 deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main
 deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main

After doing that, gimp installed but unable to launch because it lacked then another lib gtk+ 2.24.7 (I could not find it anywhere).
BUT: also after add these two reps I had then this Nautilus:

[IMG]http://desmond.imageshack.us/Himg707/scaled.php?server=707&filename=gonet.jpg&res=medium[/IMG]

So I recovered Ubuntu from a backup I did with Acronis days ago, and I will not permit a partial update never again.

---

### Post by eMirage on 2012-02-11
> **Bao2 said:**
> After doing that, gimp installed but unable to launch because it lacked then another lib gtk+ 2.24.7 (I could not find it anywhere).
BUT: also after add these two reps I had then this Nautilus:

[IMG]http://desmond.imageshack.us/Himg707/scaled.php?server=707&filename=gonet.jpg&res=medium[/IMG]

So I recovered Ubuntu from a backup I did with Acronis days ago, and I will not permit a partial update never again.

I got the same problem but fixed this by changing the color theme on the appearance panel !

---

### Post by mister_k81 on 2012-02-11
> **matvancormick said:**
> 

3. If you have "old" 2.7.4 deb packages in /var/cache/apt/archives then reinstall gimp and gimp-data (remove 2.7.5 and all matthaeus' repositories first!)

Hope it helps.
Matheus

I tried doing this, but it gives me this error when I try to install the main gimp_2.7.4-2011102201~oo_i386.deb file: 

> Error: Breaks existing package 'gimp-data' that conflict: 'gimp-python'. But the '/var/cache/apt/archives/gimp_2.7.4-2011102201~oo_i386.deb' provides it via: 'gimp-helpbrowser,gimp-python'

And this is after uninstalling the Gimp 2.7.5 packages and matthaeus' repositories. Any idea what is happening here?

---

### Post by MathUHenry on 2012-02-11
> **lewmnik said:**
> If you are using oneiric:

GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main

deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main

Thank you Lewmnik - you saved my breakfast!!!

---

### Post by leftfinger on 2012-02-11
> **lewmnik said:**
> If you are using oneiric:

GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main

deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main

Seems after added this 2 into repo and did an upgrade, all my web browsers(chromium and firefox) stopped to play flash. The place should originally be a flash video now shows an interface of totem.
Anyone encountered same issue as me? I'm using ubuntu 11.10 amd64 and firefox 10.

Edit: I solved this problem using firefox extention suggested by winh8r (thanks!): flash aid. Just install the latest beta flash plugin and then it worked. Thread here: [http://ubuntuforums.org/showthread.php?t=1923846](http://ubuntuforums.org/showthread.php?t=1923846)
Anyone encountered same issue can try if this works. :)

---

### Post by rebek94 on 2012-02-11
I've solved it:
1. Remove ppa matthaeus123/mrw-gimp-svn from your computer
2. (x86) Download [this]("https://launchpadlibrarian.net/83533717/gimp_2.7.4-2011102201~oo_i386.deb"), [this]("https://launchpadlibrarian.net/83533716/libgimp2.0_2.7.4-2011102201~oo_i386.deb") and [this]("https://launchpadlibrarian.net/83533715/gimp-data_2.7.4-2011102201~oo_all.deb").
2. (x64 )Download [this]("https://launchpadlibrarian.net/83516214/gimp_2.7.4-2011102201~oo_amd64.deb"), [this]("https://launchpadlibrarian.net/83516213/libgimp2.0_2.7.4-2011102201~oo_amd64.deb") and [this]("https://launchpadlibrarian.net/83533715/gimp-data_2.7.4-2011102201~oo_all.deb").
3. (x86) Open a terminal, go to the folder where you downloaded the file and type:
```
sudo dpkg -i libgimp2.0_2.7.4-2011102201~oo_i386.deb
sudo dpkg -i gimp_2.7.4-2011102201~oo_i386.deb
sudo dpkg -i gimp-data_2.7.4-2011102201~oo_all.deb
sudo apt-get install -f
```
3. (x64) Open a terminal, go to the folder where you downloaded the file and type:
```
sudo dpkg -i libgimp2.0_2.7.4-2011102201~oo_AMD64.deb
sudo dpkg -i gimp_2.7.4-2011102201~oo_AMD64.deb
sudo dpkg -i gimp-data_2.7.4-2011102201~oo_all.deb
sudo apt-get install -f
```
4. Now you have Gimp installed again :P

---

### Post by Simeo on 2012-02-11
> **rebek94 said:**
> I've solved it:
1. Remove ppa matthaeus123/mrw-gimp-svn from your computer
2. (x86) Download [this]("https://launchpadlibrarian.net/83533717/gimp_2.7.4-2011102201%7Eoo_i386.deb"), [this]("https://launchpadlibrarian.net/83533716/libgimp2.0_2.7.4-2011102201%7Eoo_i386.deb") and [this]("https://launchpadlibrarian.net/83533715/gimp-data_2.7.4-2011102201%7Eoo_all").
2. (x64 )Download [this]("https://launchpadlibrarian.net/83533717/gimp_2.7.4-2011102201%7Eoo_AMD64.deb"), [this]("https://launchpadlibrarian.net/83533716/libgimp2.0_2.7.4-2011102201%7Eoo_AMD64.deb") and [this]("https://launchpadlibrarian.net/83533715/gimp-data_2.7.4-2011102201%7Eoo_all").
3. (x86) Open a terminal, go to the folder where you downloaded the file and type:
```
sudo dpkg -i libgimp2.0_2.7.4-2011102201~oo_i386.deb
sudo dpkg -i gimp_2.7.4-2011102201~oo_i386.deb
sudo dpkg -i gimp-data_2.7.4-2011102201~oo_all.deb
sudo apt-get install -f
```3. (x64) Open a terminal, go to the folder where you downloaded the file and type:
```
sudo dpkg -i libgimp2.0_2.7.4-2011102201~oo_AMD64.deb
sudo dpkg -i gimp_2.7.4-2011102201~oo_AMD64.deb
sudo dpkg -i gimp-data_2.7.4-2011102201~oo_all.deb
sudo apt-get install -f
```4. Now you have Gimp installed again :P

I would love to but "this, this, and this" don't work... please help?

---

### Post by fragos on 2012-02-11
> **rebek94 said:**
> I've solved it:
1. Remove ppa matthaeus123/mrw-gimp-svn from your computer
2. (x86) Download [this]("https://launchpadlibrarian.net/83533717/gimp_2.7.4-2011102201~oo_i386.deb"), [this]("https://launchpadlibrarian.net/83533716/libgimp2.0_2.7.4-2011102201~oo_i386.deb") and [this]("https://launchpadlibrarian.net/83533715/gimp-data_2.7.4-2011102201~oo_all").
2. (x64 )Download [this]("https://launchpadlibrarian.net/83533717/gimp_2.7.4-2011102201~oo_AMD64.deb"), [this]("https://launchpadlibrarian.net/83533716/libgimp2.0_2.7.4-2011102201~oo_AMD64.deb") and [this]("https://launchpadlibrarian.net/83533715/gimp-data_2.7.4-2011102201~oo_all").
3. (x86) Open a terminal, go to the folder where you downloaded the file and type:
```
sudo dpkg -i libgimp2.0_2.7.4-2011102201~oo_i386.deb
sudo dpkg -i gimp_2.7.4-2011102201~oo_i386.deb
sudo dpkg -i gimp-data_2.7.4-2011102201~oo_all.deb
sudo apt-get install -f
```
3. (x64) Open a terminal, go to the folder where you downloaded the file and type:
```
sudo dpkg -i libgimp2.0_2.7.4-2011102201~oo_AMD64.deb
sudo dpkg -i gimp_2.7.4-2011102201~oo_AMD64.deb
sudo dpkg -i gimp-data_2.7.4-2011102201~oo_all.deb
sudo apt-get install -f
```
4. Now you have Gimp installed again :P

The 1st two are available for download but [https://launchpadlibrarian.net/83533715/gimp-data_2.7.4-2011102201~oo_all](https://launchpadlibrarian.net/83533715/gimp-data_2.7.4-2011102201~oo_all) is missing it's .deb. I copied the link added the .deb and was able to download.

And still it won't work, gimp itself woudn't install so I deinstalled the two that did and went back to 2.6.

---

### Post by Simeo on 2012-02-11
I'm running 64 bit. I don't have any of the downloads except the last one then...?

---

### Post by apochry on 2012-02-11
> **lewmnik said:**
> If you are using oneiric:

GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main

deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main

Sorry for the noob question, but how do I do that?

Thanks!

---

### Post by ZaydHumsy on 2012-02-11
> **apochry said:**
> Sorry for the noob question, but how do I do that?

Thanks!

Ubuntu Software Center-> Edit->Software Sources->Add-> copy and paste the each PPAs listed( deb....onieric main)

---

### Post by rebek94 on 2012-02-11
Sorry, I've just updated the links! ;)

---

### Post by Buster95 on 2012-02-12
> **lewmnik said:**
> Not being cheeky, but did you first:
```
sudo apt-get upgrade
```
before reinstalling gimp?

Yes

---

### Post by Bucic on 2012-02-12
> **lewmnik said:**
> If you are using oneiric:

GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main

deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main
Manually?
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by pasipasi on 2012-02-12
> **lewmnik said:**
> If you are using oneiric:

GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main

deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main

This did the trick. I was without gimp for a few days. :D

---

### Post by Bucic on 2012-02-12
> **pasipasi said:**
> This did the trick. I was without gimp for a few days. :D
Can you tell me how to do it step by step?

EDIT:
The following ppas added
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

I had to use sudo upgrade **-f** to make it work. 
To sum it up:
1. GIMP 2.7.x installation [http://askubuntu.com/a/71153](http://askubuntu.com/a/71153)
2. Fixing dpendencies
```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update
sudo apt-get upgrade -f
sudo apt-get install gimp
```

One question though. After I did the upgrade and installed GIMP I got a lot of other stuff from those ppas in my Update manager. Is it safe to install them / should I install them? For now I disabled the ppas right after installing GIMP. No side effects so far and finally the GIMP splash screen is less fetishist now :P

EDIT:
Not only there's no side effects, I also got light grey menus (GIMP, Firefox, nautilus context menu...) instead of those very dark grey. I'd like to keep them!

---

### Post by em007 on 2012-02-12
> **Bao2 said:**
> After doing that, gimp installed but unable to launch because it lacked then another lib gtk+ 2.24.7 (I could not find it anywhere).
BUT: also after add these two reps I had then this Nautilus:

[IMG]http://desmond.imageshack.us/Himg707/scaled.php?server=707&filename=gonet.jpg&res=medium[/IMG]

So I recovered Ubuntu from a backup I did with Acronis days ago, and I will not permit a partial update never again.

I have the same problem as the pic above after the partial update. Anyone else have this problem and know how to correct it?

---

### Post by JRBASTIEN on 2012-02-12
I have the same problem as Bao2 but for my Ambiance & Radiance Colors theme (from RAVEfinity).  These custom theme are broken since I installed these ppas.  Notice that if I select the standard Ambiance theme, it is working.  I would recommend Bao2 that you try switching to a non-Ambiance or Radiance theme then switch back to the standard theme.

But I'm definitly mad of having broken my nice looking Ubuntu to make GIMP work.  If someone knows a less agressive workaround, please let us know.

---

### Post by fragos on 2012-02-12
> **em007 said:**
> I have the same problem as the pic above after the partial update. Anyone else have this problem and know how to correct it?

It looks like text color got changed to white. 1st thing to try is to change themes to see if this goes away. You can also go to /usr/share/themes and open the folder for the theme you're using. Colors for GTK 2 and 3 apps are handled in their respective folders. Nautilus is GTK 3 so open the gtk-3.0 folder. there are two files which control colors, gtk.css and settings.ini. They appear to set the same variable names with the same values. These files are editable. You may need to log out and back in to see the color changes take place in every place they are referenced.

---

### Post by UltimateCat on 2012-02-12
There should be an aid to you in the repositories for GIMP

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I have 10.04 and use GIMP 2.6 on a regular basis....maybe this book would be of help to you. 
" GIMP From Novice to Professional - 2 Edition.pdf
or the 
GIMP Bible both of these books I found online at:

[http://ebookee.org/](http://ebookee.org/)

[http://www.gimp.org/](http://www.gimp.org/)

Do you have broken dependencies?

---

### Post by naazgull on 2012-02-13
The gnome3 ppa repository worked for me, with a slight problem: the menu bar for gtk applications appears both in the global menu bar area and in the application window. It happened to anybody? Does anyone knows how to tweak it? Thanks.

---

### Post by von Stalhein on 2012-02-14
I had installed GIMPshop on this 32-bit system, didn't like it and decided to go back to the original.

It's taken me two days to get back to that stage - I had no trouble installing GIMP on Oneiric after my upgrade from Natty.

Whatever I did, in either Synaptic (broken packages but no repair), or the terminal, I got this:
```
The following packages have unmet dependencies:
 gimp : Depends: libglib2.0-0 (>= 2.31.2) but 2.30.2-4ubuntu1~oneiric1 is to be installed
```

Any application of sudo commands to repair, update, purge, reinstall etc failed. I had the repositories as recommended but for some reason it wouldn't work.

Google was not my friend so I returned to ubuntuforums - first place I should have tried (IDIOT!!!)

The info from lewmnick & Bucic did the trick.

Thanks very much :):)

I've not rebooted yet, but I shouldn't expect any issues surely, it's not like I'm in Windows or anything 
/crosses appendages/

---

### Post by slumbergod on 2012-02-14
Adding the other repos does indeed work but it does have the potential to break more than it fixes.

Cheese broke for me so I gave up and purged the new repos.

---

### Post by Fintan on 2012-02-15
Hello all.
First off I'd like to thank you all for the tips and tricks found here.
I installed the repos as suggested above and was able to install gimp. 

Gimp starts up and works in single window mode but didn't give me any layers window so I deleted .gimp2.7 from /home and all the windows works again:D

Cheers
Fintan

---

### Post by Mie1 on 2012-02-16
Thanks.... worked like a bomb!  Help appreciated!

---

### Post by Bucic on 2012-02-16
> **Fintan said:**
> 
Gimp starts up and works in single window mode but didn't give me any layers window so I deleted .gimp2.7 from /home and all the windows works again:D

Cheers
Fintan
You should have switch the single window mode on/off first before taking such drastic measures :D

---

### Post by jjyoder on 2012-02-17
I have been able to re-install Gimp 2.6, however, it does not run. When I launch it from the terminal it give me an error. 

jerry@jerry-laptop:~$ gimp-2.6
gimp-2.6: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory

Does anyone have an idea what this means? I am somewhat new to Ubuntu, but you probably new that.

Thanks for your help.

jjyoder

I was able to fix it from a post by n0dix: 
sudo apt-get update ; sudo apt-get purge gimp libgegl* libbabl* ; sudo apt-get install gimp ; sudo apt-get clean

---

### Post by fragos on 2012-02-17
The problem is that the libgegl you have is left over from installing Gimp 2.7. Uninstall it and whatever else it tells you it has to remove, including gimp. Now you can re-install lingegl again and then gimp. There may be another library with the same issue that pops up. Follow the process for it. That's what worked for me and I'm back to Gimp 2.6 again.

---

### Post by pasipasi on 2012-02-20
Adding the repos, and installing the dependencies that Gimp needed, broke Spotify for me. It now crashes every time a few seconds after it's up with some gtk problems.

Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.8/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window
GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.8/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window

---

### Post by von Stalhein on 2012-02-21
> **pasipasi said:**
> Adding the repos, and installing the dependencies that Gimp needed, broke Spotify for me. It now crashes every time a few seconds after it's up with some gtk problems.

Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.8/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window
GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.8/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window

Not sure but that looks like Spotify doesn't like the GTK version.

Googling shows some people have had X-session and Spotify error segfaults similar to the above. 
Many seem to recommend clearing the Spotify cache and config dirs: ```
rm -r ~/.cache/spotify/ ~/.config/spotify/ 
```

That from [here]("https://getsatisfaction.com/spotify/topics/try_out_the_linux_apps_client_beta_preview") for instance. 

YMMV. Might be somewhere to start anyway.

---

### Post by Veazer on 2012-02-27
> **rebek94 said:**
> I've solved it:
1. Remove ppa matthaeus123/mrw-gimp-svn from your computer
2. (x86) Download [this]("https://launchpadlibrarian.net/83533717/gimp_2.7.4-2011102201~oo_i386.deb"), [this]("https://launchpadlibrarian.net/83533716/libgimp2.0_2.7.4-2011102201~oo_i386.deb") and [this]("https://launchpadlibrarian.net/83533715/gimp-data_2.7.4-2011102201~oo_all.deb").
2. (x64 )Download [this]("https://launchpadlibrarian.net/83516214/gimp_2.7.4-2011102201~oo_amd64.deb"), [this]("https://launchpadlibrarian.net/83516213/libgimp2.0_2.7.4-2011102201~oo_amd64.deb") and [this]("https://launchpadlibrarian.net/83533715/gimp-data_2.7.4-2011102201~oo_all.deb").
3. (x86) Open a terminal, go to the folder where you downloaded the file and type:
```
sudo dpkg -i libgimp2.0_2.7.4-2011102201~oo_i386.deb
sudo dpkg -i gimp_2.7.4-2011102201~oo_i386.deb
sudo dpkg -i gimp-data_2.7.4-2011102201~oo_all.deb
sudo apt-get install -f
```
3. (x64) Open a terminal, go to the folder where you downloaded the file and type:
```
sudo dpkg -i libgimp2.0_2.7.4-2011102201~oo_AMD64.deb
sudo dpkg -i gimp_2.7.4-2011102201~oo_AMD64.deb
sudo dpkg -i gimp-data_2.7.4-2011102201~oo_all.deb
sudo apt-get install -f
```
4. Now you have Gimp installed again :P

Do you happen to have copies of these files? This worked for me and but I re-installed today and now the files have been pulled from launchpad librarian.

How do you search and get those links, btw?

I tried adding the other repos recommend to run 2.7.5 but it messed up a few things on my system. I really think he made a bad choice by releasing 2.7.5 with the issues it has.

---

### Post by squee on 2012-02-27
2.7.5 has been pulled from gimp.org from what I can see. Any particular reason why? (except that countless people are having trouble with it)

I'm still on 2.6.11, after problems with gnome-shell when using those extra repos, the new gimp wasn't worth the hassle of another re-install. Waiting for 2.8 I guess, unless anyone has a better idea.

---

### Post by capricornday on 2012-02-28
> **leftfinger said:**
> Seems after added this 2 into repo and did an upgrade, all my web browsers(chromium and firefox) stopped to play flash. The place should originally be a flash video now shows an interface of totem.
Anyone encountered same issue as me? I'm using ubuntu 11.10 amd64 and firefox 10.

Edit: I solved this problem using firefox extention suggested by winh8r (thanks!): flash aid. Just install the latest beta flash plugin and then it worked. Thread here: [http://ubuntuforums.org/showthread.php?t=1923846](http://ubuntuforums.org/showthread.php?t=1923846)
Anyone encountered same issue can try if this works. :)

Afer install gimp, i have same problem with you on my firefox. thanks for the solving. 
In the other hand, after install gimp, my web cam application (cheese)is missing too. 
And if i install again with  sudo apt-get install cheese the result is : 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cheese : Depends: libcheese-gtk20 (>= 3.0.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```How can i get my cheese again? 
Thank you

---

### Post by Veazer on 2012-02-28
Does anyone have the x64 .deb files for 2.7.4?

[LIST]
[*]If I add the new repositories i'm not able to run some apps, as others have noted, and my system menus all have strange scroll arrows.
[*]I can't build from scratch or I get the error "Could not run GTK+ test program, checking why..." (see [here]("http://www.linuxquestions.org/questions/linux-software-2/gimp-2-install-how-to-163358/"))
[*]I can't use the 2.6.x stable because it can't open the files created by 2.7.4. I can't open many of my files now. 
[/LIST]

I'm kind of stuck until I can get ahold of the 2.7.4 debs, if anyone can upload them I would greatly appreciate it.

---

### Post by skarard on 2012-02-28
Hey I have been having the same issues today.

I managed to find a ppa that is using 2.7.4 and is working nice with my post 2.6 edited files.

The ppa is question is:
[https://launchpad.net/~jmou/+archive/ppa/](https://launchpad.net/~jmou/+archive/ppa/)

Here is a an easy way to do it.

Remove all versions of gimp previously installed and use **ppa-purge** and get rid of the ppas you that broke your system.

Open up a terminal and pop in
```

sudo add-apt-repository ppa:jmou/ppa
sudo apt-get update
sudo apt-get install gimp
```

I disabled the ppa from software sources after the install just in case jmou updates something my system don't like.

hope this helps someone.

---

### Post by Veazer on 2012-02-29
> **skarard said:**
> Hey I have been having the same issues today.

I managed to find a ppa that is using 2.7.4 and is working nice with my post 2.6 edited files.

The ppa is question is:
[https://launchpad.net/~jmou/+archive/ppa/](https://launchpad.net/~jmou/+archive/ppa/)

Here is a an easy way to do it.

Remove all versions of gimp previously installed and use **ppa-purge** and get rid of the ppas you that broke your system.

Open up a terminal and pop in
```

sudo add-apt-repository ppa:jmou/ppa
sudo apt-get update
sudo apt-get install gimp
```

I disabled the ppa from software sources after the install just in case jmou updates something my system don't like.

hope this helps someone.

Thanks for that, but unfortunately most keyboard shortcuts don't seem to be working in this version. I can't even use copy paste. If I press 'm' for the move tool I get layer merge instead. Are they working on your install? 

At least I am able to open my files though, thanks.

EDIT: Correction - the keyboard shortcuts work but are different in this version and some are conflicting with eachother.

---

### Post by dsmithnc on 2012-03-01
> **MathUHenry said:**
> Thank you Lewmnik - you saved my breakfast!!!

And I echo that.  Note to self: next time check the forums first!  Would have saved two weeks of brutal frustration.

****

---

### Post by squee on 2012-03-01
> **Veazer said:**
> Thanks for that, but unfortunately most keyboard shortcuts don't seem to be working in this version. I can't even use copy paste. If I press 'm' for the move tool I get layer merge instead. Are they working on your install? 

At least I am able to open my files though, thanks.

EDIT: Correction - the keyboard shortcuts work but are different in this version and some are conflicting with eachother.

Wow, that ppa is perfect. GIMP runs great! Many of the shortcuts are the same, but without the modifier ctrl/shift buttons that go with them. C to copy, P to paste...

---

### Post by Vinca on 2012-03-01
> **skarard said:**
> Hey I have been having the same issues today.

I managed to find a ppa that is using 2.7.4 and is working nice with my post 2.6 edited files.

The ppa is question is:
[https://launchpad.net/~jmou/+archive/ppa/](https://launchpad.net/~jmou/+archive/ppa/)

Here is a an easy way to do it.

Remove all versions of gimp previously installed and use **ppa-purge** and get rid of the ppas you that broke your system.

Open up a terminal and pop in
```

sudo add-apt-repository ppa:jmou/ppa
sudo apt-get update
sudo apt-get install gimp
```

I disabled the ppa from software sources after the install just in case jmou updates something my system don't like.

hope this helps someone.

how to ppa-purge exactly? i added the gnome3-team and ricotz and this totally screwed up my install... afraid to reboot/log out...

---

### Post by Veazer on 2012-03-02
> **squee said:**
> Wow, that ppa is perfect. GIMP runs great! **Many of the shortcuts are the same, but without the modifier ctrl/shift buttons that go with them. C to copy, P to paste...**

Right, but some of his shortcut modifications conflict because he removed the shift or ctrl and there was already an existing command for that key. I'm going to try find a standard keyboard shortcut file and switch back. The file is:

~/.gimp-2.7/menurc

---

### Post by melissanikol on 2012-03-10
Has anyone who ended up with broken Cheese & themes figured out how to fix this?  It's driving me up the wall.

---

### Post by fragos on 2012-03-10
A while back Gimp 2.7.5 worked reasonably well without causing serious problems with other aps in 11.10. As the updates past that point came in the troubles started. 2.7.5 is probably a better fit with 12.04 and is after all a development vs stable release. Eventually I went back to 2.6 but with the webup8 ppa I got 2.6.12 which had the fixes for Wacom tablets that were my main reason for going to 2.7.5 in the first place. Given that the Gimp team can say when the 2.8 stable release will come out and 12.04 will stay with 2.6, so will I. I do however recommend using the webup8 ppa because Ubuntu 11.10 has the older 2.6.11. The following link will take you to the launchpad for the webup8 ppa.

[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

---

### Post by Veazer on 2012-03-11
> **melissanikol said:**
> Has anyone who ended up with broken Cheese & themes figured out how to fix this?  It's driving me up the wall.

The best solution, imho, is to _not_ add the 'gnome3-team/gnome3' and 'ricotz/testing' ppas but instead stick with gimp 2.7.4 using the 'jmou/ppa' ppa. You might want to grab the keyboard layout from 2.7.5 (~/.gimp-2.7/menurc) before you downgrade, as the jmou version has his own custom layout that i don't care for.

The ricotz and gnome3 ppas just break too many things on my system, and who knows what other apps may have issues that i haven't yet installed.

---

### Post by TedinOz on 2012-03-24
> **fragos said:**
> A while back Gimp 2.7.5 worked reasonably well without causing serious problems with other aps in 11.10. As the updates past that point came in the troubles started. 2.7.5 is probably a better fit with 12.04 and is after all a development vs stable release. Eventually I went back to 2.6 but with the webup8 ppa I got 2.6.12 which had the fixes for Wacom tablets that were my main reason for going to 2.7.5 in the first place. Given that the Gimp team can say when the 2.8 stable release will come out and 12.04 will stay with 2.6, so will I. I do however recommend using the webup8 ppa because Ubuntu 11.10 has the older 2.6.11. The following link will take you to the launchpad for the webup8 ppa.

[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)
This was the best advice throughout this excellent thread. I am running x32 and was tempted into installing Gimp 2.7.5 only to suffer all of the problems reported here. Thanks to many good pointers and after much purging and re-installing I am now back to v 2.6.12 and working again which I will definitely stay with until later releases are compatible and stable.
Thanks for good advice :)

---

