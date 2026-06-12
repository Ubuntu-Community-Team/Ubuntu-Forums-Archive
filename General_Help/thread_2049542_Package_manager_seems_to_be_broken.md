---
title: "Package manager seems to be broken"
date: 2012-08-28
forum: General Help
---

### Post by Sublymonal on 2012-08-28
Lately I've been donating my unused processing time to the World Community Grid. I mostly use Windows 7, but since classes are about to start up I decided to update ubuntu. As part of that, I tried to install boinc, the program that facilitates my donation. Things went to hell shortly thereafter.

My first hint that things were going wrong was when, for about a minute, the terminal showed that it was rapidly selecting and unselecting packages (it was scrolling too fast for me to see if it was toggling the same exact packages or just messing with many of them).

Then, after a few minutes, it completely failed. I was informed that I should try using "sudo apt-get -f install" but it ended up throwing out the same exact error. Now I can't install or uninstall any packages at all.

Full message from "sudo apt-get -f install" :

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-gnome2 python-pyorbit libgnomeui-0 libgnomeui-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libqtcore4:i386
The following NEW packages will be installed:
  libqtcore4:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0 B/2,068 kB of archives.
After this operation, 9,041 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 209127 files and directories currently installed.)
Unpacking libqtcore4:i386 (from .../libqtcore4_4%3a4.8.1-0ubuntu4.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqtcore4_4%3a4.8.1-0ubuntu4.2_i386.deb (--unpack):
 conffile './etc/xdg/Trolltech.conf' is not in sync with other instances of the same package
dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libqtcore4_4%3a4.8.1-0ubuntu4.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I also get told this in the bar at the top:

> An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount>0'. This usually means that your installed packages have unmet dependencies.

I've tried purging boinc, but get this:

```
The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: libqtcore4:i386 but it is not going to be installed
 libqt4-dbus:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-declarative:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-designer:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-network:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-opengl:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-qt3support:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-script:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-scripttools:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-sql:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-sql-mysql:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-svg:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-test:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-xml:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqt4-xmlpatterns:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqtgui4:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.2) but it is not going to be installed
 libqtwebkit4:i386 : Depends: libqtcore4:i386 (>= 4:4.8.0~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Also, the update manager wants to install the Qt 4 Core Module, but when I try it brings up a dialog that says:

> The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

AND ALSO THE FOLLOWING AS MORE DETAILS:

The following packages have unmet dependencies:

ia32-libs-multiarch:i386: Depends: gtk2-engines-pixbuf but it is not installed
                          Depends: gtk2-engines-oxygen but it is not installed
                          Depends: libaio1 but it is not installed
                          Depends: libao4 but it is not installed
                          Depends: libesd0 but it is not installed
                          Depends: libqt4-qt3support but it is not installed
                          Depends: libsdl-net1.2 but it is not installed
                          Depends: libstdc++5 but it is not installed
                          Depends: xaw3dg but it is not installed
libqt4-dbus:i386: Depends: libqt4-xml (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                  Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-declarative:i386: Depends: libqt4-network (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                         Depends: libqt4-script (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                         Depends: libqt4-sql (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                         Depends: libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                         Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                         Depends: libqtgui4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-designer:i386: Depends: libqt4-script (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                      Depends: libqt4-xml (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                      Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                      Depends: libqtgui4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-network:i386: Depends: libqt4-dbus (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                     Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-opengl:i386: Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                    Depends: libqtgui4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-qt3support:i386: Depends: libqt4-designer (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                        Depends: libqt4-network (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                        Depends: libqt4-sql (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                        Depends: libqt4-xml (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                        Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                        Depends: libqtgui4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-script:i386: Depends: libqt4-dbus (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                    Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-scripttools:i386: Depends: libqt4-script (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                         Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                         Depends: libqtgui4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-sql-mysql:i386: Depends: libqt4-sql (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                       Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-sql:i386: Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-svg:i386: Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                 Depends: libqtgui4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-test:i386: Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-xml:i386: Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqt4-xmlpatterns:i386: Depends: libqt4-network (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                         Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqtgui4:i386: Depends: libqt4-declarative (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
                Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.2) but 4:4.8.1-0ubuntu4.2 is installed
libqtwebkit4:i386: Depends: libc6 (>= 2.4) but 2.15-0ubuntu10 is installed
                   Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
                   Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is installed
                   Depends: libqt4-network (>= 4:4.8.0~) but 4:4.8.1-0ubuntu4.2 is installed
                   Depends: libqtcore4 (>= 4:4.8.0~) but 4:4.8.1-0ubuntu4.2 is installed
                   Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.2 is installed
                   Depends: libsqlite3-0 (>= 3.5.9) but 3.7.9-2ubuntu1.1 is installed
                   Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is installed


It's times like these that I REALLY wish ubuntu had some sort of system restore

---

### Post by oldos2er on 2012-08-29
Try ```
sudo apt-get autoremove

sudo apt-get clean

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Jack Waugh on 2012-08-31
> **Sublymonal said:**
> 
It's times like these that I REALLY wish ubuntu had some sort of system restore

You could copy your root file system to another part of disk with 'gpartd'.  (I never do so, however; rather I make an informal list of the modifications to make after a re-installation of the system, and I keep my personal files off of the root FS).

---

### Post by Terrie Harlan on 2012-10-08
I have this very same problem.  I tried your suggestion, but it does nothing -- still unmet dependencies and try using -f install

Any other suggestions?

Thanks!

---

