---
title: "X upgrade when trying out XGL - how to revert?"
date: 2006-06-16
forum: General Help
---

### Post by mbeierl on 2006-06-16
So I thought I'd try out XGL, following the general howto thread, and got started by adding the following to my apt sources:

[http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx
[http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

Well, after the apt-get update, it tells me there are newer versions of about 11 files to download, so I happily get them all.  Now my X server is slightly messed up:  text is missing from some windows, but forcing a repaint sometimes makes it show up, etc.

So, I thought I'd try to use synaptic to force the original version to go back.  So I started with libxfixes3.  But trying to downgrade that back to the dapper version tells me it has to remove many other packages, such as:
  evolution-dev
  libbonoboui2-dev
  libgail-dev
  libglade2-dev
  ...

and so on.  This doesn't seem right.  [-X 

Does anyone know how to gracefully reset packages back to the current dapper version?

---

### Post by jstueve on 2006-06-16
try removing the  debs from your apt-sources

apt-get update
apt-get dist-upgrade  

see what happens... also the .debs for the packages might be in /var/cache/apt/archives and you could manually install the debs with 'sudo dpkg -i <debpkgname>.deb'

---

### Post by mbeierl on 2006-06-16
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove

Drat!  It was a good idea, though...

---

### Post by mbeierl on 2006-06-16
Okay, now I'm really messed up.  I managed to downgrade most of the packages and remove the extraneous ones, but now I cannot re-install some of them because they think they depend on the ones from xgl.compix.info:

sudo apt-get install libqt3-mt-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: xlibmesa-gl-dev but it is not installable or
                          libgl-dev
                 Depends: libglu1-xorg-dev but it is not installable or
                          libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages

My apt sources:

# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-extras main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-extras main restricted universe multiverse

# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
# deb-src [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main universe multiverse restricted

# Wine:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Hibernate script:
# deb [http://cp.yi.org/apt/hibernate](http://cp.yi.org/apt/hibernate) ./

## PLF repositories
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

# Opera Browser - Production release
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) testing non-free
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

# Opera Browser - Beta release
deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable non-free
# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) testing non-free
# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) unstable non-free

#deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx
#deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
> 

---

### Post by mbeierl on 2006-06-16
Okay, I got it:

I still had some mesa-gl libraries at the xgl.compiz version and forcing their version caused me to have to remove x-window-system-core, which sounded frightening.

But I did it anyway, and then re-installed x-window..., ubuntu-desktop, etc and now I can put back my qt-dev stuff and I appear to be back in good shape.

Ouch!  For just a moment there I thought I was dealing with RPM again :(

---

