---
title: "skype and Amarok"
date: 2009-07-07
forum: General Help
---

### Post by jhapk on 2009-07-07
Hi,

I installed a Ubuntu 9.04 on my machine and then I installed amarok using 
```
$sudo apt-get install amarok 

```and it installed amarok2.0 on my machine. Then I tried to install skype using 
```

$sudo apt-get install skype
```but it failed and gave me the following message.
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libqt4-core (>= 4.2.1) but it is not going to be installed
         Depends: libqt4-gui (>= 4.2.1) but it is not going to be installed
```I updated my repositories once more, but Skype still gives me the same error and for 
some reason now that I open amarok, it opens amarok version 1.4. By any chances these two problems connected? 
Also, how do I upgrade my Amarok back to version 2.0 again and how do I install skype?

Thanks

---

### Post by jenkinbr on 2009-07-07
Could you try clicking the following link ( [libqt4-core,libqt4-gui](apt:libqt4-core,libqt4-gui) ) or running the commands below, and then installing skype.

```

sudo apt-get install libqt4-core libqt4-gui
sudo apt-get install skype

```?

---

### Post by jhapk on 2009-07-07
Hi,

when I run the command
sudo apt-get install libqt4-core libqt4-gui

I get the following output
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libqt4-core: Depends: libqtcore4 (= 4.4.3-0ubuntu1.2) but 4.5.0-0ubuntu4.1 is to be installed
               Depends: libqt4-network (= 4.4.3-0ubuntu1.2) but 4.5.0-0ubuntu4.1 is to be installed
               Depends: libqt4-script (= 4.4.3-0ubuntu1.2) but 4.5.0-0ubuntu4.1 is to be installed
               Depends: libqt4-xml (= 4.4.3-0ubuntu1.2) but 4.5.0-0ubuntu4.1 is to be installed
               Depends: libqt4-dbus (= 4.4.3-0ubuntu1.2) but 4.5.0-0ubuntu4.1 is to be installed
               Depends: libqt4-test (= 4.4.3-0ubuntu1.2) but 4.5.0-0ubuntu4.1 is to be installed
  libqt4-gui: Depends: libqtgui4 (= 4.4.3-0ubuntu1.2) but 4.5.0-0ubuntu4.1 is to be installed
              Depends: libqt4-svg (= 4.4.3-0ubuntu1.2) but 4.5.0-0ubuntu4.1 is to be installed
              Depends: libqt4-opengl (= 4.4.3-0ubuntu1.2) but 4.5.0-0ubuntu4.1 is to be installed
              Depends: libqt4-designer (= 4.4.3-0ubuntu1.2) but 4.5.0-0ubuntu4.1 is to be installed
              Depends: libqt4-assistant (= 4.4.3-0ubuntu1.2) but it is not going to be installed
E: Broken packages
```

Even the link you sent says there are broken packages.

---

### Post by jenkinbr on 2009-07-07
odd. (the link and the commands do pretty much the same thing, so they should both throw the same errors)

Could you post output to the following:

```
uname -a
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d

```

---

### Post by jhapk on 2009-07-07
Hi,

here are the outputs.

for $uname -a 

```
Linux chhotu 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux
```

for cat /etc/apt/sources.list

```
# Ubuntu supported packages (GPG key: 437D05B5)
deb http://tw.archive.ubuntu.com/ubuntu intrepid main restricted multiverse universe
deb http://tw.archive.ubuntu.com/ubuntu intrepid-security main restricted multiverse universe
deb http://tw.archive.ubuntu.com/ubuntu intrepid-updates main restricted multiverse universe
deb http://tw.archive.ubuntu.com/ubuntu intrepid-proposed main restricted multiverse universe
deb http://tw.archive.ubuntu.com/ubuntu intrepid-backports main restricted multiverse universe
deb-src http://tw.archive.ubuntu.com/ubuntu intrepid main restricted multiverse universe
deb-src http://tw.archive.ubuntu.com/ubuntu intrepid-security main restricted multiverse universe
deb-src http://tw.archive.ubuntu.com/ubuntu intrepid-updates main restricted multiverse universe
deb-src http://tw.archive.ubuntu.com/ubuntu intrepid-proposed main restricted multiverse universe
deb-src http://tw.archive.ubuntu.com/ubuntu intrepid-backports main restricted multiverse universe
#Canonical Commercial Repository (GPG key: 1135D466)
deb http://archive.canonical.com/ intrepid partner
deb http://archive.canonical.com/ intrepid-backports partner
deb http://archive.canonical.com/ intrepid-proposed partner
deb http://archive.canonical.com/ intrepid-security partner
deb http://archive.canonical.com/ intrepid-updates partner
deb-src http://archive.canonical.com/ intrepid partner
deb-src http://archive.canonical.com/ intrepid-backports partner
deb-src http://archive.canonical.com/ intrepid-proposed partner
deb-src http://archive.canonical.com/ intrepid-security partner
deb-src http://archive.canonical.com/ intrepid-updates partner
# Bleeding edge wine packages (GPG key: 387EE263)
deb http://wine.budgetdedicated.com/apt intrepid main
deb-src http://wine.budgetdedicated.com/apt intrepid main
#Opera
deb http://deb.opera.com/opera/ lenny non-free
## Medibuntu
# GPG key-file: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ intrepid non-free free
deb http://packages.medibuntu.org/ intrepid-staging non-free free
deb-src http://packages.medibuntu.org/ intrepid free non-free
deb-src http://packages.medibuntu.org/ intrepid-staging free non-free
# Skype packages
deb http://download.skype.com/linux/repos/debian/ stable non-free
# Virtualbox
# wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
#Deluge
deb http://ppa.launchpad.net/zachtib/ubuntu intrepid main universe
# MySQL Workbench
deb ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ binary/
deb-src ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ source/
#awn
deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
#GNOME Do
deb http://ppa.launchpad.net/do-core/ubuntu intrepid main
# Depot PlayOnLinux
# KEY GPG: wget -q http://deb.mulx.net/pol.gpg -O- | sudo apt-key add -
deb http://deb.mulx.net/ intrepid main
# Ubuntu tweak
deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
#Terminator
deb http://ppa.launchpad.net/gnome-terminator/ubuntu intrepid main
#GScrot
deb http://ppa.launchpad.net/gscrot/ubuntu intrepid main
#OpenOffice.org
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
#Google
deb http://dl.google.com/linux/deb/ stable non-free
```

for ls -l /etc/apt/sources.list.d
```

total 4
-rw-r--r-- 1 root root 280 2009-05-01 12:26 medibuntu.list
```

thanks

---

### Post by jenkinbr on 2009-07-07
Did you do an upgrade from Intrepid to Jaunty?

Because you are running the Jaunty kernel, but You have Intrepid Package Lists.

Your /etc/apt/sources.list needs to be updated.

Run ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.intrepid
``` followed by [gksudo gedit /etc/apt/sources.list[/code]

That will open /etc/apt/sources.list in gedit as root. Find and replace all instances of intrepid with jaunty withing this file.  You will need to do the same for /etc/apt/sources.list.d/medibuntu.list as well.

Your /etc/apt/sources.list file should look like:
```
# Ubuntu supported packages (GPG key: 437D05B5)
deb http://tw.archive.ubuntu.com/ubuntu jaunty main restricted multiverse universe
deb http://tw.archive.ubuntu.com/ubuntu jaunty-security main restricted multiverse universe
deb http://tw.archive.ubuntu.com/ubuntu jaunty-updates main restricted multiverse universe
deb http://tw.archive.ubuntu.com/ubuntu jaunty-proposed main restricted multiverse universe
deb http://tw.archive.ubuntu.com/ubuntu jaunty-backports main restricted multiverse universe
deb-src http://tw.archive.ubuntu.com/ubuntu jaunty main restricted multiverse universe
deb-src http://tw.archive.ubuntu.com/ubuntu jaunty-security main restricted multiverse universe
deb-src http://tw.archive.ubuntu.com/ubuntu jaunty-updates main restricted multiverse universe
deb-src http://tw.archive.ubuntu.com/ubuntu jaunty-proposed main restricted multiverse universe
deb-src http://tw.archive.ubuntu.com/ubuntu jaunty-backports main restricted multiverse universe
#Canonical Commercial Repository (GPG key: 1135D466)
deb http://archive.canonical.com/ jaunty partner
deb http://archive.canonical.com/ jaunty-backports partner
deb http://archive.canonical.com/ jaunty-proposed partner
deb http://archive.canonical.com/ jaunty-security partner
deb http://archive.canonical.com/ jaunty-updates partner
deb-src http://archive.canonical.com/ jaunty partner
deb-src http://archive.canonical.com/ jaunty-backports partner
deb-src http://archive.canonical.com/ jaunty-proposed partner
deb-src http://archive.canonical.com/ jaunty-security partner
deb-src http://archive.canonical.com/ jaunty-updates partner
# Bleeding edge wine packages (GPG key: 387EE263)
deb http://wine.budgetdedicated.com/apt jaunty main
deb-src http://wine.budgetdedicated.com/apt jaunty main
#Opera
deb http://deb.opera.com/opera/ lenny non-free
## Medibuntu
# GPG key-file: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ jaunty non-free free
deb http://packages.medibuntu.org/ jaunty-staging non-free free
deb-src http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty-staging free non-free
# Skype packages
deb http://download.skype.com/linux/repos/debian/ stable non-free
# Virtualbox
# wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
#Deluge
deb http://ppa.launchpad.net/zachtib/ubuntu jaunty main universe
# MySQL Workbench
deb ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ binary/
deb-src ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ source/
#awn
deb http://ppa.launchpad.net/awn-testing/ubuntu jaunty main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu jaunty main
#GNOME Do
deb http://ppa.launchpad.net/do-core/ubuntu jaunty main
# Depot PlayOnLinux
# KEY GPG: wget -q http://deb.mulx.net/pol.gpg -O- | sudo apt-key add -
deb http://deb.mulx.net/ jaunty main
# Ubuntu tweak
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
#Terminator
deb http://ppa.launchpad.net/gnome-terminator/ubuntu jaunty main
#GScrot
deb http://ppa.launchpad.net/gscrot/ubuntu jaunty main
#OpenOffice.org
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main
#Google
deb http://dl.google.com/linux/deb/ stable non-free
```

Also run [code]cat /etc/apt/sources.list.d/medibuntu.list

I have a feeling you don't need it, as you have those lines in your normal sources.list file.

---

