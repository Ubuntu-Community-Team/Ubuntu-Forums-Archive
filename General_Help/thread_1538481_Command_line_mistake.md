---
title: "Command line mistake"
date: 2010-07-25
forum: General Help
---

### Post by Piro ko on 2010-07-25
[COLOR=Black]ooookay,
so I'm a newby to Ubuntu, and decided to download google earth.
I checked a website that had instructions.
Sadly, I didn't notice the website wasn't exactly recent, and as a result got the following:

owner@Laptop:~$ sudo aptitude install googleearth
[sudo] password for owner:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find package "googleearth".  However, the following
packages contain "googleearth" in their name:
  googleearth-package 
Couldn't find package "googleearth".  However, the following
packages contain "googleearth" in their name:
  googleearth-package 
The following packages will be REMOVED:
  akonadi-server{u} build-essential{u} dpkg-dev{u} fakeroot{u} g++{u} 
  g++-4.4{u} gwibber-service{u} kdebase-workspace-bin{u} 
  kdebase-workspace-data{u} kdebase-workspace-kgreet-plugins{u} 
  kdepim-runtime{u} ksysguardd{u} libao2{u} libglademm-2.4-1c2a{u} 
  libkephal4{u} libkfontinst4{u} libkscreensaver5{u} libksgrd4{u} 
  libkworkspace4{u} libplasma-applet-system-monitor4{u} 
  libplasma-geolocation-interface4{u} libplasmaclock4{u} 
  libplasmagenericshell4{u} libprocesscore4{u} libprocessui4{u} 
  libsolidcontrol4{u} libsolidcontrolifaces4{u} libstdc++6-4.4-dev{u} 
  libtaskmanager4{u} libweather-ion4{u} linux-headers-2.6.32-22{u} 
  linux-headers-2.6.32-22-generic{u} mysql-client-core-5.1{u} 
  mysql-server-core-5.1{u} patch{u} plasma-dataengines-workspace{u} 
  plasma-widgets-workspace{u} python-egenix-mxdatetime{u} 
  python-egenix-mxtools{u} python-gtkspell{u} python-indicate{u} 
  python-pycurl{u} python-wnck{u} xz-utils{u} 
0 packages upgraded, 0 newly installed, 44 to remove and 10 not upgraded.
Need to get 0B of archives. After unpacking 167MB will be freed.
Do you want to continue? [Y/n/?] y ((((yes, this is where the real problem is, my fault))))
Writing extended state information... Done
(Reading database ... 171753 files and directories currently installed.)
Removing kdebase-workspace-bin ...
Removing plasma-widgets-workspace ...
Removing kdepim-runtime ...
Removing akonadi-server ...
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
Removing build-essential ...
Removing dpkg-dev ...
Removing fakeroot ...
update-alternatives: using /usr/bin/fakeroot-tcp to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Removing g++ ...
Removing gwibber-service ...
Removing kdebase-workspace-data ...
Removing kdebase-workspace-kgreet-plugins ...
Removing ksysguardd ...
Removing libao2 ...
Removing libglademm-2.4-1c2a ...
Removing plasma-dataengines-workspace ...
Removing libtaskmanager4 ...
Removing libkephal4 ...
Removing libkfontinst4 ...
Removing libkscreensaver5 ...
Removing libksgrd4 ...
Removing libplasmagenericshell4 ...
Removing libkworkspace4 ...
Removing libplasma-applet-system-monitor4 ...
Removing libplasma-geolocation-interface4 ...
Removing libplasmaclock4 ...
Removing libprocessui4 ...
Removing libprocesscore4 ...
Removing libsolidcontrol4 ...
Removing libsolidcontrolifaces4 ...
Removing libweather-ion4 ...
Removing linux-headers-2.6.32-22-generic ...
Removing linux-headers-2.6.32-22 ...
Removing mysql-client-core-5.1 ...
Removing mysql-server-core-5.1 ...
Removing patch ...
Removing python-egenix-mxdatetime ...
Removing python-egenix-mxtools ...
Removing python-gtkspell ...
Removing python-indicate ...
Removing python-pycurl ...
Removing python-wnck ...
Removing xz-utils ...
Removing libstdc++6-4.4-dev ...
Removing g++-4.4 ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for hicolor-icon-theme ...
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

Processing triggers for python-support ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

owner@Laptop:~$ 

[/COLOR]            [COLOR=Black]This is when I look back at the list of things going on and say "oh crap.... what did I do?"
So now what?
There is no "undo" or "go back" feature I know of, but what's the simplest way of going through the long work of replacing what has been removed and/or removing what shouldn't have been added?
And PLEASE make this as simple as possible. I'm new and only understand utter basics, such as the fact that removing when I want to be adding is not a good thing. 8-[[/COLOR]

---

### Post by Piro ko on 2010-07-25
Also if I posted this in the wrong place, or if there is a better one, give me a heads up and I'll do what I can. But I'm not super familiar with the layout of the forums here, they're pretty extensive.

---

### Post by DeMus on 2010-07-25
Is your computer still working, or doesn't it do anything anymore?
Please tell us some more about this.

---

### Post by theozzlives on 2010-07-25
if google earth works, don't worry about it. If not, the installer has a uninstall feature.

---

### Post by WorMzy on 2010-07-25
Don't restart.

For some reason you've removed your linux kernels and several very important applications which are needed for Ubuntu to run properly. Run
```
sudo apt-get --reinstall ubuntu-desktop
```, and if that doesn't reinstall anything, run
```
sudo apt-get install g++ gwibber-service kdebase-workspace-data kdebase-workspace-kgreet-plugins ksysguardd libao2 libglademm-2.4-1c2a plasma-dataengines-workspace libtaskmanager4 libkephal4 libkfontinst4 libkscreensaver5 libksgrd4 libplasmagenericshell4 libkworkspace4 libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasmaclock4 libprocessui4 libprocesscore4 libsolidcontrol4 libsolidcontrolifaces4 libweather-ion4 linux-headers-2.6.32-22-generic linux-headers-2.6.32-22 mysql-client-core-5.1 mysql-server-core-5.1 patch python-egenix-mxdatetime python-egenix-mxtools python-gtkspell python-indicate python-pycurl python-wnck xz-utils libstdc++
```

---

### Post by powerpleb on 2010-07-25
Sometimes aptitude uninstalls unused packages at unexpected times. 
The kernel headers that were uninstalled look like quite an old version (you still might want to check that a newer version is still installed by running **sudo dpkg -l linux***, the most recent on my machine is linux-headers-2.6.32-24). The rest seems to be mostly odd dependencies that come with KDE4 (have you installed KDE4 previously?) and some development software. I wouldn't worry too much.

---

### Post by Piro ko on 2010-07-25
[COLOR=Black]@WorMzy:
I haven't restarted.
I feared the possibility that doing so would cause some troubles. I also figured that I should just straight up run sudo apt+get install (list of all things removed) but wasn't sure if it would be that simple. 
I was also hoping to find out WHY so many things were removed as a result of not finding the properly named package.
[/COLOR][COLOR=Black]
@Theozzlives:
I was told that after doing the install of google earth I should have an option in my App>Internet folder to use it. I currently do not. It may be amended after a system reboot/restart but I'm afraid of the other problems/changes that will cause due to so many things being deleted without my intent to delete anything.

@Powerpleb:
I am fairly sure I have installed KDE4 previously, though I'm not sure if any of that is being used now since I am running Compiz Fusion and the theme packages that "ship with" 9.10 Karmic Koala. I downloaded Lucid Lynx, but kept some of my old settings and things because I'd already seen and didn't like having the window close and maximize buttons on the top left. Plus I wasn't sure if my Compiz Fusion settings and things would run properly with the new settings and didn't want to spend two hours tweaking everything "juuuuust so".

@EVERYONE:
Thanks so much, I've been thoroughly impressed (since coming to read a little in the forums) at just how great a community there is behind linux on this site. Your time and knowledge is greatly appreciated. And remember that for every post you write an answer for, there's a LOT of people that go on to read it later, and learn from your answers. Thanks. ;)
[/COLOR]

---

### Post by Piro ko on 2010-07-26
[COLOR=Black]> **WorMzy said:**
> Don't restart.

For some reason you've removed your linux kernels and several very important applications which are needed for Ubuntu to run properly. Run[/COLOR][COLOR=Black]
```
sudo apt-get --reinstall ubuntu-desktop
```, and if that doesn't reinstall anything, run
```
sudo apt-get install g++ gwibber-service kdebase-workspace-data kdebase-workspace-kgreet-plugins ksysguardd libao2 libglademm-2.4-1c2a plasma-dataengines-workspace libtaskmanager4 libkephal4 libkfontinst4 libkscreensaver5 libksgrd4 libplasmagenericshell4 libkworkspace4 libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasmaclock4 libprocessui4 libprocesscore4 libsolidcontrol4 libsolidcontrolifaces4 libweather-ion4 linux-headers-2.6.32-22-generic linux-headers-2.6.32-22 mysql-client-core-5.1 mysql-server-core-5.1 patch python-egenix-mxdatetime python-egenix-mxtools python-gtkspell python-indicate python-pycurl python-wnck xz-utils libstdc++
```

[/COLOR][COLOR=Black]So WorMzy my question is this:
The list you gave wasn't exactly the same as the list removed. Couldn't I just put:
```
sudo apt-get install kdebase-workspace-bin plasma-widgets-workspace kdepim-runtime akonadi-server build-essential dpkg-dev fakeroot g++ gwibber-service kdebase-workspace-data kdebase-workspace-kgreet-plugins ksysguardd libao2 libglademm-2.4-1c2a 
plasma-dataengines-workspace libtaskmanager4 libkephal4 libkfontinst4 libkscreensaver5 
libksgrd4 libplasmagenericshell4 libkworkspace4 libplasma-applet-system-monitor4 
libplasma-geolocation-interface4 libplasmaclock4 libprocessui4 libprocesscore4 libsolidcontrol4 libsolidcontrolifaces4 libweather-ion4 linux-headers-2.6.32-22-generic 
linux-headers-2.6.32-22 mysql-client-core-5.1 mysql-server-core-5.1 patch python-egenix-mxdatetime python-egenix-mxtools python-gtkspell python-indicate python-pycurl python-wnck xz-utils libstdc++6-4.4-dev g++-4.4 
```In the terminal? It's the EXACT list of what was removed as listed in my original post.
I see most of it is in your second list of code:
```
sudo apt-get install g++ gwibber-service kdebase-workspace-data  kdebase-workspace-kgreet-plugins ksysguardd libao2 libglademm-2.4-1c2a  plasma-dataengines-workspace libtaskmanager4 libkephal4 libkfontinst4  libkscreensaver5 libksgrd4 libplasmagenericshell4 libkworkspace4  libplasma-applet-system-monitor4 libplasma-geolocation-interface4  libplasmaclock4 libprocessui4 libprocesscore4 libsolidcontrol4  libsolidcontrolifaces4 libweather-ion4 linux-headers-2.6.32-22-generic  linux-headers-2.6.32-22 mysql-client-core-5.1 mysql-server-core-5.1  patch python-egenix-mxdatetime python-egenix-mxtools python-gtkspell  python-indicate python-pycurl python-wnck xz-utils libstdc++
```So what's the difference?
Can it be done my way as well? I want to try it, but I'm not sure if I'm missing something. 8-[[/COLOR]

---

### Post by prodigy_ on 2010-07-26
> **Piro ko said:**
> Can it be done my way as well?
With the full list of removed packages? Sure.

---

There's a more interesting question though, since I don't see any reason why these packages were removed at all: did you install or remove anything **before** even trying to install this Google Earth package?

---

### Post by Piro ko on 2010-07-26
[COLOR=Black]> **prodigy_ said:**
> With the full list of removed packages? Sure.

---[/COLOR][COLOR=Black]

There's a more interesting question though, since I don't see any reason why these packages were removed at all: did you install or remove anything [/COLOR][COLOR=Black]before even trying to install this Google Earth package?

[/COLOR][COLOR=Black]You've solved my problem for me in that case. I'm going to restore what was removed.
However I want to know as well, what caused this.
I'm completely at a loss as to what caused it.
I'm not familiar with the terminal, and one of the previous posts claims that sometimes this "just happens". No idea if that is true.
To CLEARLY answer your question though: No, I did not install or remove anything BEFORE even trying to install the Google Earth package. Not via command line anyway. Just opened the terminal, and put in what you see.
My guess is that it could be related to my using the update manager a few hours prior? I figured that perhaps some of these had been listed for removal and just hadn't been removed yet. However according to WorMzy I had some of my linux kernels removed. I'm still a bit unsure what a kernel really is/does, but I know enough to know it's not just some extra stuff you won't miss.
So my guess is as good as yours.  :-s

[/COLOR][COLOR=Black]Thanks a bunch BTW, I'm going to run the apt-get install I listed earlier, and see if anything happens. I'll post if any noticeable changes take place.[/COLOR]

---

### Post by prodigy_ on 2010-07-26
When aptitude (or apt-get for that matter) automatically removes packages it's usually due to unmet dependencies. That's why I asked if you removed anything prior to installing Google Earth.

There are some log files (**/var/log/aptitude**, **/var/log/apt/history.log** and **/var/log/apt/term.log**) that might help you to find out what caused this behavior.

---

### Post by lisati on 2010-07-26
@Piro ko: please use the default font colour in your posts.

---

### Post by Piro ko on 2010-07-26
[COLOR=Black]In case  anyone is interested, here is what I got from the terminal after attempting to reinstall everything off the list exactly as it was listed for removal:

user@Laptop:~$ sudo apt-get install kdebase-workspace-bin plasma-widgets-workspace kdepim-runtime akonadi-server build-essential dpkg-dev fakeroot g++ gwibber-service kdebase-workspace-data kdebase-workspace-kgreet-plugins ksysguardd libao2 libglademm-2.4-1c2a 
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++-4.4 libkephal4 libkfontinst4 libkscreensaver5 libksgrd4 libkworkspace4
  libplasma-applet-system-monitor4 libplasma-geolocation-interface4
  libplasmaclock4 libplasmagenericshell4 libprocesscore4 libprocessui4
  libsolidcontrol4 libsolidcontrolifaces4 libstdc++6-4.4-dev libtaskmanager4
  libweather-ion4 mysql-client-core-5.1 mysql-server-core-5.1 patch
  plasma-dataengines-workspace python-egenix-mxdatetime python-egenix-mxtools
  python-indicate python-pycurl xz-utils
Suggested packages:
  debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc
  libstdc++6-4.4-dbg plasma-scriptengines libstdc++6-4.4-doc diffutils-doc
  python-egenix-mxdatetime-dbg python-egenix-mxtools-dbg
  python-egenix-mxtools-doc libcurl4-gnutls-dev python-pycurl-dbg
The following NEW packages will be installed:
  akonadi-server build-essential dpkg-dev fakeroot g++ g++-4.4 gwibber-service
  kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdepim-runtime ksysguardd libao2
  libglademm-2.4-1c2a libkephal4 libkfontinst4 libkscreensaver5 libksgrd4
  libkworkspace4 libplasma-applet-system-monitor4
  libplasma-geolocation-interface4 libplasmaclock4 libplasmagenericshell4
  libprocesscore4 libprocessui4 libsolidcontrol4 libsolidcontrolifaces4
  libstdc++6-4.4-dev libtaskmanager4 libweather-ion4 mysql-client-core-5.1
  mysql-server-core-5.1 patch plasma-dataengines-workspace
  plasma-widgets-workspace python-egenix-mxdatetime python-egenix-mxtools
  python-indicate python-pycurl xz-utils
0 upgraded, 40 newly installed, 0 to remove and 10 not upgraded.
Need to get 25.7MB/26.5MB of archives.
After this operation, 81.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libstdc++6-4.4-dev 4.4.3-4ubuntu5 [1,491kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main g++-4.4 4.4.3-4ubuntu5 [4,950kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main g++ 4:4.4.3-1ubuntu1 [1,442B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main xz-utils 4.999.9beta+20091116-1 [228kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main patch 2.6-2ubuntu1 [123kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main build-essential 11.4build1 [7,278B]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main fakeroot 1.14.4-1ubuntu1 [118kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main python-egenix-mxtools 3.1.3-2ubuntu1 [80.4kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main python-egenix-mxdatetime 3.1.3-2ubuntu1 [72.7kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main python-pycurl 7.19.0-3 [57.3kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main python-indicate 0.3.0-0ubuntu1 [16.3kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libkephal4 4:4.4.2-0ubuntu14 [96.7kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libkfontinst4 4:4.4.2-0ubuntu14 [86.6kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libkscreensaver5 4:4.4.2-0ubuntu14 [56.0kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libkworkspace4 4:4.4.2-0ubuntu14 [74.8kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libplasmagenericshell4 4:4.4.2-0ubuntu14 [96.6kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libprocesscore4 4:4.4.2-0ubuntu14 [68.8kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libprocessui4 4:4.4.2-0ubuntu14 [276kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libsolidcontrolifaces4 4:4.4.2-0ubuntu14 [57.1kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libsolidcontrol4 4:4.4.2-0ubuntu14 [66.4kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libplasma-applet-system-monitor4 4:4.4.2-0ubuntu14 [61.2kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libplasmaclock4 4:4.4.2-0ubuntu14 [94.4kB]
Get:23 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libksgrd4 4:4.4.2-0ubuntu14 [70.5kB]
Get:24 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libplasma-geolocation-interface4 4:4.4.2-0ubuntu14 [52.6kB]
Get:25 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libtaskmanager4 4:4.4.2-0ubuntu14 [78.7kB]
Get:26 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libweather-ion4 4:4.4.2-0ubuntu14 [53.3kB]
Get:27 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main plasma-dataengines-workspace 4:4.4.2-0ubuntu14 [352kB]
Get:28 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main mysql-server-core-5.1 5.1.41-3ubuntu12.3 [4,712kB]
Get:29 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main mysql-client-core-5.1 5.1.41-3ubuntu12.3 [177kB]
Get:30 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main akonadi-server 1.3.1-0ubuntu3 [2,719kB]
Get:31 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main kdepim-runtime 4:4.4.2-0ubuntu1 [1,088kB]
Get:32 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main plasma-widgets-workspace 4:4.4.2-0ubuntu14 [506kB]
Get:33 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main kdebase-workspace-data 4:4.4.2-0ubuntu14 [5,772kB]
Get:34 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main kdebase-workspace-kgreet-plugins 4:4.4.2-0ubuntu14 [69.6kB]
Get:35 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main kdebase-workspace-bin 4:4.4.2-0ubuntu14 [1,829kB]
Get:36 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main ksysguardd 4:4.4.2-0ubuntu14 [88.1kB]
Fetched 25.7MB in 1min 36s (268kB/s)                                           
Extracting templates from packages: 100%
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 151046 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.3-4ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package xz-utils.
Unpacking xz-utils (from .../xz-utils_4.999.9beta+20091116-1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.5.6ubuntu4.1_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4build1_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package python-egenix-mxtools.
Unpacking python-egenix-mxtools (from .../python-egenix-mxtools_3.1.3-2ubuntu1_i386.deb) ...
Selecting previously deselected package python-egenix-mxdatetime.
Unpacking python-egenix-mxdatetime (from .../python-egenix-mxdatetime_3.1.3-2ubuntu1_i386.deb) ...
Selecting previously deselected package python-pycurl.
Unpacking python-pycurl (from .../python-pycurl_7.19.0-3_i386.deb) ...
Selecting previously deselected package python-indicate.
Unpacking python-indicate (from .../python-indicate_0.3.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package gwibber-service.
Unpacking gwibber-service (from .../gwibber-service_2.30.1-0ubuntu1_all.deb) ...
Selecting previously deselected package libkephal4.
Unpacking libkephal4 (from .../libkephal4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libkfontinst4.
Unpacking libkfontinst4 (from .../libkfontinst4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libkscreensaver5.
Unpacking libkscreensaver5 (from .../libkscreensaver5_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libkworkspace4.
Unpacking libkworkspace4 (from .../libkworkspace4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libplasmagenericshell4.
Unpacking libplasmagenericshell4 (from .../libplasmagenericshell4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libprocesscore4.
Unpacking libprocesscore4 (from .../libprocesscore4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libprocessui4.
Unpacking libprocessui4 (from .../libprocessui4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libsolidcontrolifaces4.
Unpacking libsolidcontrolifaces4 (from .../libsolidcontrolifaces4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libsolidcontrol4.
Unpacking libsolidcontrol4 (from .../libsolidcontrol4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libplasma-applet-system-monitor4.
Unpacking libplasma-applet-system-monitor4 (from .../libplasma-applet-system-monitor4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libplasmaclock4.
Unpacking libplasmaclock4 (from .../libplasmaclock4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libksgrd4.
Unpacking libksgrd4 (from .../libksgrd4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libplasma-geolocation-interface4.
Unpacking libplasma-geolocation-interface4 (from .../libplasma-geolocation-interface4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libtaskmanager4.
Unpacking libtaskmanager4 (from .../libtaskmanager4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libweather-ion4.
Unpacking libweather-ion4 (from .../libweather-ion4_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package plasma-dataengines-workspace.
Unpacking plasma-dataengines-workspace (from .../plasma-dataengines-workspace_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package mysql-server-core-5.1.
Unpacking mysql-server-core-5.1 (from .../mysql-server-core-5.1_5.1.41-3ubuntu12.3_i386.deb) ...
Selecting previously deselected package mysql-client-core-5.1.
Unpacking mysql-client-core-5.1 (from .../mysql-client-core-5.1_5.1.41-3ubuntu12.3_i386.deb) ...
Selecting previously deselected package akonadi-server.
Unpacking akonadi-server (from .../akonadi-server_1.3.1-0ubuntu3_i386.deb) ...
Selecting previously deselected package kdepim-runtime.
Unpacking kdepim-runtime (from .../kdepim-runtime_4%3a4.4.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package plasma-widgets-workspace.
Unpacking plasma-widgets-workspace (from .../plasma-widgets-workspace_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package kdebase-workspace-data.
Unpacking kdebase-workspace-data (from .../kdebase-workspace-data_4%3a4.4.2-0ubuntu14_all.deb) ...
Selecting previously deselected package kdebase-workspace-kgreet-plugins.
Unpacking kdebase-workspace-kgreet-plugins (from .../kdebase-workspace-kgreet-plugins_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package kdebase-workspace-bin.
Unpacking kdebase-workspace-bin (from .../kdebase-workspace-bin_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package ksysguardd.
Unpacking ksysguardd (from .../ksysguardd_4%3a4.4.2-0ubuntu14_i386.deb) ...
Selecting previously deselected package libao2.
Unpacking libao2 (from .../libao2_0.8.8-5ubuntu2_i386.deb) ...
Selecting previously deselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.7-2build1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
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

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up xz-utils (4.999.9beta+20091116-1) ...
Setting up patch (2.6-2ubuntu1) ...
Setting up dpkg-dev (1.15.5.6ubuntu4.1) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up python-egenix-mxtools (3.1.3-2ubuntu1) ...

Setting up python-pycurl (7.19.0-3) ...

Setting up python-indicate (0.3.0-0ubuntu1) ...

Setting up libkephal4 (4:4.4.2-0ubuntu14) ...

Setting up libkfontinst4 (4:4.4.2-0ubuntu14) ...

Setting up libkscreensaver5 (4:4.4.2-0ubuntu14) ...

Setting up libkworkspace4 (4:4.4.2-0ubuntu14) ...

Setting up libplasmagenericshell4 (4:4.4.2-0ubuntu14) ...

Setting up libprocesscore4 (4:4.4.2-0ubuntu14) ...

Setting up libprocessui4 (4:4.4.2-0ubuntu14) ...

Setting up libsolidcontrolifaces4 (4:4.4.2-0ubuntu14) ...

Setting up libsolidcontrol4 (4:4.4.2-0ubuntu14) ...

Setting up libplasma-applet-system-monitor4 (4:4.4.2-0ubuntu14) ...

Setting up libplasmaclock4 (4:4.4.2-0ubuntu14) ...

Setting up libksgrd4 (4:4.4.2-0ubuntu14) ...

Setting up libplasma-geolocation-interface4 (4:4.4.2-0ubuntu14) ...

Setting up libtaskmanager4 (4:4.4.2-0ubuntu14) ...

Setting up libweather-ion4 (4:4.4.2-0ubuntu14) ...

Setting up plasma-dataengines-workspace (4:4.4.2-0ubuntu14) ...
Setting up mysql-server-core-5.1 (5.1.41-3ubuntu12.3) ...
Setting up mysql-client-core-5.1 (5.1.41-3ubuntu12.3) ...
Setting up akonadi-server (1.3.1-0ubuntu3) ...
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]

Setting up kdepim-runtime (4:4.4.2-0ubuntu1) ...

Setting up plasma-widgets-workspace (4:4.4.2-0ubuntu14) ...
Setting up kdebase-workspace-data (4:4.4.2-0ubuntu14) ...
Setting up kdebase-workspace-kgreet-plugins (4:4.4.2-0ubuntu14) ...
Setting up kdebase-workspace-bin (4:4.4.2-0ubuntu14) ...

Setting up ksysguardd (4:4.4.2-0ubuntu14) ...
Setting up libao2 (0.8.8-5ubuntu2) ...

Setting up libglademm-2.4-1c2a (2.6.7-2build1) ...

Processing triggers for python-central ...
Setting up python-egenix-mxdatetime (3.1.3-2ubuntu1) ...

Processing triggers for python-central ...
Setting up gwibber-service (2.30.1-0ubuntu1) ...

Processing triggers for python-central ...
Setting up g++-4.4 (4.4.3-4ubuntu5) ...
Setting up libstdc++6-4.4-dev (4.4.3-4ubuntu5) ...
Setting up g++ (4:4.4.3-1ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4build1) ...
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


very long, very very long. But it looks all good to me, so far as I can see.
I find the fact there were suggested packages to install both very interesting and a bit confusing. But I'm taking the advice and will apt-get install those too.
*proceeded with install and will now reboot to see how things go*
[/COLOR]

---

### Post by Piro ko on 2010-07-26
[COLOR=Black]After restart everything seems fine. No immediately noticeable changes.

@prodigy_:
I'm not exactly sure what "unmet dependencies" are. But I haven't removed a whole lot from my system recently. I DID however use synaptic package manager to remove a game called "Laby", one called "Powder" and a SNES emulator, a few hours prior to this event. Would that have caused it?
[/COLOR]

---

### Post by Piro ko on 2010-07-26
> **lisati said:**
> @Piro ko: please use the default font colour in your posts.
Yes sir! :)
Sorry, I forgot about the *proper* use for coloring in the forums.

---

