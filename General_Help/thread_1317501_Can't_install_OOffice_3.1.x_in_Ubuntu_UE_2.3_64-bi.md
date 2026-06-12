---
title: "Can't install OOffice 3.1.x in Ubuntu UE 2.3 64-bit"
date: 2009-11-06
forum: General Help
---

### Post by stir-crazy on 2009-11-06
Fot those wondering, UE 2.3 is based on Ubuntu 9.04, just has some extra repositories and razzle-dazzle.

I have enabled (I believe...) the correct repositories:

```

deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
```

Then, in terminal, I optain the GPG key by entering:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247D1CFF
```

Which gives me the following:

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 247D1CFF
gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: key 247D1CFF: "Launchpad PPA for OpenOffice.org Scribblers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

Either in the  CLI, or through Synaptic, or through Ultimatix, etc., I don't seem to be able to upgrade OOffice to 3.1.x; it's still just 3.0.x

I haven't seemed to have this trouble on my laptop, 32bit processor running Karmic (Kubuntu).  Should my above commands/repositories also work in a 64-bit system?  TIA!

---

### Post by scouser73 on 2009-11-06
Firstly, go to the OpenOffice website: [[COLOR="Red"]**OpenOffice.org**[/COLOR]]("http://download.openoffice.org/other.html") and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m19_native_packed-1_en-US.9420**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

### Post by stir-crazy on 2009-11-06
Thanks scouser73; I'll probably end up doing that.

Was just hoping to have something that would actively be maintained through Synaptic for updates though.  I suppose once UE 2.4 comes out (based on 9.10) everything will be just right then.

---

