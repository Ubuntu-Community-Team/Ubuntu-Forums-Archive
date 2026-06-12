---
title: "why don't install gnome-desktop"
date: 2010-12-31
forum: General Help
---

### Post by zcrself on 2010-12-31
```

ncgr@ncgr-desktop:/sv$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: bicyclerepair but it is not going to be installed
                  Depends: bluez-pcmcia-support but it is not going to be installed
                  Depends: foomatic-db-gutenprint but it is not going to be installed
                  Depends: gnome-app-install but it is not going to be installed
                  Depends: gnome-cups-manager but it is not going to be installed
                  Depends: hwdb-client but it is not going to be installed
                  Depends: irssi but it is not going to be installed
                  Depends: language-selector but it is not going to be installed
                  Depends: libglib2.0-data but it is not going to be installed
                  Depends: metacity but it is not going to be installed
                  Depends: python-adns but it is not going to be installed
                  Depends: python-cddb but it is not going to be installed
                  Depends: python-clientcookie but it is not going to be installed
                  Depends: python-crypto but it is not going to be installed
                  Depends: python-egenix-mxproxy but it is not going to be installed
                  Depends: python-egenix-mxstack but it is not going to be installed
                  Depends: python-egenix-mxtexttools but it is not going to be installed
                  Depends: python-egenix-mxtools but it is not going to be installed
                  Depends: python-epydoc but it is not going to be installed
                  Depends: python-eunuchs but it is not going to be installed
                  Depends: python-examples but it is not going to be installed
                  Depends: python-gadfly but it is not going to be installed
                  Depends: python-gd but it is not going to be installed
                  Depends: python-genetic but it is not going to be installed
                  Depends: python-geoip but it is not going to be installed
                  Depends: python-htmlgen but it is not going to be installed
                  Depends: python-htmltmpl but it is not going to be installed
                  Depends: python-id3lib but it is not going to be installed
                  Depends: python-imaging-sane but it is not going to be installed
                  Depends: python-jabber but it is not going to be installed
                  Depends: python-kjbuckets but it is not going to be installed
                  Depends: python-ldap but it is not going to be installed
                  Depends: python-mysqldb but it is not going to be installed
                  Depends: python-netcdf but it is not going to be installed
                  Depends: python-newt but it is not going to be installed
                  Depends: python-pam but it is not going to be installed
                  Depends: python-parted but it is not going to be installed
                  Depends: python-pexpect but it is not going to be installed
                  Depends: python-pgsql but it is not going to be installed
                  Depends: python-pisock but it is not going to be installed
                  Depends: python-pqueue but it is not going to be installed
                  Depends: python-pyao but it is not going to be installed
                  Depends: python-pylibacl but it is not going to be installed
                  Depends: python-pyopenssl but it is not going to be installed
                  Depends: python-pyvorbis but it is not going to be installed
                  Depends: python-pyxattr but it is not going to be installed
                  Depends: python-reportlab but it is not going to be installed
                  Depends: python-simpletal but it is not going to be installed
                  Depends: python-soappy but it is not going to be installed
                  Depends: python-sqlite but it is not going to be installed
                  Depends: python-stats but it is not going to be installed
                  Depends: python-syck but it is not going to be installed
                  Depends: python-unit but it is not going to be installed
                  Depends: python-xmpp but it is not going to be installed
                  Depends: python2.4-dbus but it is not going to be installed
                  Depends: python2.4-libxml2 but it is not going to be installed
                  Depends: python2.4-libxslt1 but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
E: Broken packages
ncgr@ncgr-desktop:/sv$


```

---

### Post by ajgreeny on 2010-12-31
You seem to have a broken package so run ```
sudo apt-get install -f
```to try and fix it or use synaptic **Edit->Fix broken packages**

---

### Post by zcrself on 2011-01-03
> **ajgreeny said:**
> You seem to have a broken package so run ```
sudo apt-get install -f
```to try and fix it or use synaptic **Edit->Fix broken packages**

```

ncgr@ncgr-desktop:/sv$ sudo apt-get install -f
[sudo] password for ncgr:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ncgr@ncgr-desktop:/sv$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: bicyclerepair but it is not going to be installed
                  Depends: bluez-pcmcia-support but it is not going to be installed
                  Depends: foomatic-db-gutenprint but it is not going to be installed
                  Depends: gnome-app-install but it is not going to be installed
                  Depends: gnome-cups-manager but it is not going to be installed
                  Depends: hwdb-client but it is not going to be installed
                  Depends: irssi but it is not going to be installed
                  Depends: language-selector but it is not going to be installed
                  Depends: libglib2.0-data but it is not going to be installed
                  Depends: metacity but it is not going to be installed
                  Depends: python-adns but it is not going to be installed
                  Depends: python-cddb but it is not going to be installed
                  Depends: python-clientcookie but it is not going to be installed
                  Depends: python-crypto but it is not going to be installed
                  Depends: python-egenix-mxproxy but it is not going to be installed
                  Depends: python-egenix-mxstack but it is not going to be installed
                  Depends: python-egenix-mxtexttools but it is not going to be installed
                  Depends: python-egenix-mxtools but it is not going to be installed
                  Depends: python-epydoc but it is not going to be installed
                  Depends: python-eunuchs but it is not going to be installed
                  Depends: python-examples but it is not going to be installed
                  Depends: python-gadfly but it is not going to be installed
                  Depends: python-gd but it is not going to be installed
                  Depends: python-genetic but it is not going to be installed
                  Depends: python-geoip but it is not going to be installed
                  Depends: python-htmlgen but it is not going to be installed
                  Depends: python-htmltmpl but it is not going to be installed
                  Depends: python-id3lib but it is not going to be installed
                  Depends: python-imaging-sane but it is not going to be installed
                  Depends: python-jabber but it is not going to be installed
                  Depends: python-kjbuckets but it is not going to be installed
                  Depends: python-ldap but it is not going to be installed
                  Depends: python-mysqldb but it is not going to be installed
                  Depends: python-netcdf but it is not going to be installed
                  Depends: python-newt but it is not going to be installed
                  Depends: python-pam but it is not going to be installed
                  Depends: python-parted but it is not going to be installed
                  Depends: python-pexpect but it is not going to be installed
                  Depends: python-pgsql but it is not going to be installed
                  Depends: python-pisock but it is not going to be installed
                  Depends: python-pqueue but it is not going to be installed
                  Depends: python-pyao but it is not going to be installed
                  Depends: python-pylibacl but it is not going to be installed
                  Depends: python-pyopenssl but it is not going to be installed
                  Depends: python-pyvorbis but it is not going to be installed
                  Depends: python-pyxattr but it is not going to be installed
                  Depends: python-reportlab but it is not going to be installed
                  Depends: python-simpletal but it is not going to be installed
                  Depends: python-soappy but it is not going to be installed
                  Depends: python-sqlite but it is not going to be installed
                  Depends: python-stats but it is not going to be installed
                  Depends: python-syck but it is not going to be installed
                  Depends: python-unit but it is not going to be installed
                  Depends: python-xmpp but it is not going to be installed
                  Depends: python2.4-dbus but it is not going to be installed
                  Depends: python2.4-libxml2 but it is not going to be installed
                  Depends: python2.4-libxslt1 but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
E: Broken packages
ncgr@ncgr-desktop:/sv$

```

Following your suggestion, there are also some problems.

---

### Post by Bucky Ball on 2011-01-03
As ajgreeny suggests; System->Administration->Synaptic Package Manager->Edit->Fix Broken Packages.

What happens?

---

### Post by zcrself on 2011-01-04
> **Bucky Ball said:**
> As ajgreeny suggests; System->Administration->Synaptic Package Manager->Edit->Fix Broken Packages.

What happens?
I can run the following command:
```

sudo apt-get install -f

```but I can't find the following software according to your suggestion:
```

Synaptic Package Manager

```I now install synaptic
```

sudo apt-get install synaptic

```

---

### Post by Bucky Ball on 2011-01-04
Any luck? If you can install that you are in business. From there you can install ubuntu-desktop.

Mind you, if you can install synaptic, try this:

```
sudo apt-get install ubuntu-desktop
```

That will help.

Then you can boot into recovery kernel, drop to a root shell, and try:

```
startx
```

THAT might bring up a desktop. You will be logged in as root but will be easier to sort out from there. ;)

---

### Post by andriansah on 2011-02-14
Dear all

I found the same problem installing ubuntu-desktop, then i found out this solution
apt-get install --install-recommends ubuntu-desktop


It works

---

