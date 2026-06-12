---
title: "Firefox - Gnome dependencies"
date: 2009-07-02
forum: General Help
---

### Post by volchara on 2009-07-02
Hi All,

For the last few days I was curious to try out the new Firefox 3.5.

When I try installing it from the repos, it turns out that it has a whole bunch of dependencies on Gnome stuff:
```
The following NEW packages will be installed:
  apturl docbook-xml esound-clients esound-common firefox-3.5 firefox-3.5-branding gamin gksu gnome-app-install gnome-icon-theme gnome-keyring gnome-mime-data gnome-mount gvfs
  gvfs-backends libaudiofile0 libavahi-glib1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo-perl libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcroco3
  libesd-alsa0 libgail-common libgail18 libgamin0 libgcr0 libgksu2-0 libglib-perl libgnome-keyring0 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgsf-1-114 libgsf-1-common libgtk2-perl
  libgtkhtml2-0 libgtop2-7 libgtop2-common libgvfscommon0 liblaunchpad-integration1 libpam-gnome-keyring libpolkit-gnome0 libproxy0 librsvg2-2 librsvg2-common libscrollkeeper0
  libsoup-gnome2.4-1 libsoup2.4-1 libtdb1 libvte-common libvte9 policykit-gnome python-cairo python-gconf python-glade2 python-gst0.10 python-gtk2 python-gtkhtml2
  python-launchpad-integration python-pyorbit python-sexy python-vte scrollkeeper sgml-data software-properties-gtk synaptic ubufox xulrunner-1.9.1

```

So I have three questions:

1. Does it really need all that crap? How come FF 3 didn't need all that?
2. How would it affect my system(I have a brand new Kubuntu Jaunty)
3. Is there anything that could be done to avoid installing it all?

Thanks!

---

### Post by CatKiller on 2009-07-02
They aren't dependencies, they are suggested packages. I'm sure there's a way to configure whatever package manager that you're using not to install suggested packages.

---

### Post by volchara on 2009-07-02
> **CatKiller said:**
> They aren't dependencies, they are suggested packages. I'm sure there's a way to configure whatever package manager that you're using not to install suggested packages.

No, these are dependencies. There are also suggested packages, but they are not installed by default. Here's the full output of sudo apt-get install firefox-3.5:

```

xbo@xbo-t61:~/temp$ sudo apt-get install firefox-3.5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apturl docbook-xml esound-clients esound-common firefox-3.5-branding gamin gksu gnome-app-install gnome-icon-theme gnome-keyring gnome-mime-data gnome-mount gvfs gvfs-backends
  libaudiofile0 libavahi-glib1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo-perl libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcroco3 libesd-alsa0
  libgail-common libgail18 libgamin0 libgcr0 libgksu2-0 libglib-perl libgnome-keyring0 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgsf-1-114 libgsf-1-common libgtk2-perl
  libgtkhtml2-0 libgtop2-7 libgtop2-common libgvfscommon0 liblaunchpad-integration1 libpam-gnome-keyring libpolkit-gnome0 libproxy0 librsvg2-2 librsvg2-common libscrollkeeper0
  libsoup-gnome2.4-1 libsoup2.4-1 libtdb1 libvte-common libvte9 policykit-gnome python-cairo python-gconf python-glade2 python-gst0.10 python-gtk2 python-gtkhtml2
  python-launchpad-integration python-pyorbit python-sexy python-vte scrollkeeper sgml-data software-properties-gtk synaptic ubufox xulrunner-1.9.1
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide firefox-3.5-gnome-support latex-xft-fonts cryptsetup libbonobo2-bin libcanberra-gtk0 esound desktop-base libgnomevfs2-bin
  libgtk2-perl-doc librsvg2-bin python-gconf-dbg python-gtk2-doc python-gst0.10-dbg python-numpy python-gnome2-extras-doc python-launchpad-integration-dbg python-pyorbit-dbg perlsgml
  doc-html-w3 opensp dwww menu deborphan
The following NEW packages will be installed:
  apturl docbook-xml esound-clients esound-common firefox-3.5 firefox-3.5-branding gamin gksu gnome-app-install gnome-icon-theme gnome-keyring gnome-mime-data gnome-mount gvfs
  gvfs-backends libaudiofile0 libavahi-glib1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo-perl libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcroco3
  libesd-alsa0 libgail-common libgail18 libgamin0 libgcr0 libgksu2-0 libglib-perl libgnome-keyring0 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgsf-1-114 libgsf-1-common libgtk2-perl
  libgtkhtml2-0 libgtop2-7 libgtop2-common libgvfscommon0 liblaunchpad-integration1 libpam-gnome-keyring libpolkit-gnome0 libproxy0 librsvg2-2 librsvg2-common libscrollkeeper0
  libsoup-gnome2.4-1 libsoup2.4-1 libtdb1 libvte-common libvte9 policykit-gnome python-cairo python-gconf python-glade2 python-gst0.10 python-gtk2 python-gtkhtml2
  python-launchpad-integration python-pyorbit python-sexy python-vte scrollkeeper sgml-data software-properties-gtk synaptic ubufox xulrunner-1.9.1
0 upgraded, 83 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.0MB of archives.
After this operation, 128MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

---

### Post by CatKiller on 2009-07-02
> **volchara said:**
> No, these are dependencies. There are also suggested packages, but they are not installed by default.

My mistake. They still aren't dependencies, but you're right that they aren't suggested packages either. They are recommended packages. Or, at least, ubufox is, which is what's pulling in apturl, which in turn is pulling in gnome-app-install and the icon stuff and a whole bunch of python bits. I didn't turn up what's bringing in the esound stuff; that's pretty crazy.

But still, you can tell whatever package manager not to install the recommended packages either. For apt-get, that would be with the --no-install-recommends option.

---

### Post by volchara on 2009-07-02
> **CatKiller said:**
> 
But still, you can tell whatever package manager not to install the recommended packages either. For apt-get, that would be with the --no-install-recommends option.

Thank you!!!! 

```
xbo@xbo-t61:~/temp$ sudo apt-get --no-install-recommends install firefox-3.5
[sudo] password for xbo:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-3.5-branding xulrunner-1.9.1
Suggested packages:
  firefox-3.5-gnome-support latex-xft-fonts
Recommended packages:
  ubufox libcanberra0
The following NEW packages will be installed:
  firefox-3.5 firefox-3.5-branding xulrunner-1.9.1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.

```

Looks so much better!

---

### Post by mikro on 2009-09-05
CatKiller, many thanks!!! I was really desperate, I didn't notice since some debian/ubuntu version, recommended packages are installed automatically, you've saved me from using Konqueror (to which I get used to after some time :))

---

### Post by nortexoid on 2010-12-28
JUSSSST what I was looking for!

---

