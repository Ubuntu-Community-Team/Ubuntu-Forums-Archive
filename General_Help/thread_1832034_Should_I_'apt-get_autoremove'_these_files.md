---
title: "Should I 'apt-get autoremove' these files?"
date: 2011-08-24
forum: General Help
---

### Post by demonboy on 2011-08-24
When I sudo apt-get update and install in terminal I get the following message:

> The following packages were automatically installed and are no longer required:
  libkcmutils4 mesa-utils libmarblewidget11 libkldap4 libmono2.0-cil libqca2
  libmono-data-tds2.0-cil liblensfun-data python-renderpm
  libmono-system-data2.0-cil libmicroblog4 libgdata1.7-cil libkjsembed4
  oxygen-icon-theme libmono-zeroconf1.0-cil kdebase-data libkemoticons4
  xulrunner-2.0 libkdecore5 libgkeyfile1.0-cil libkidletime4 python-numeric
  docbook-xsl libmono-system-runtime2.0-cil libgps19 shared-desktop-ontologies
  libsqlite0 python-lxml python-reportlab-accel odbcinst libntrack-qt4-1
  libkatepartinterfaces4 libubuntuone1.0-cil libsolid4 virtuoso-minimal
  libgtk-sharp-beans-cil libkde3support4 libnepomuk4 python-gtkmozembed
  libkdewebkit5 libqjson0 libsyncdaemon-1.0-1 libmono-messaging2.0-cil
  libpolkit-qt-1-1 libkdnssd4 libkparts4 libmono-system-messaging2.0-cil
  plasma-scriptengine-declarative libqapt1 libkabc4 python-tz kdelibs5-data
  libkresources4 kdoctools xulrunner-2.0-mozjs libvirtodbc0 libkpimutils4
  odbcinst1debian2 libubuntuone-1.0-1 libkprintutils4 libtaglib2.0-cil
  libkonq5a libthreadweaver4 libmono-system-data-linq2.0-cil libnepomukutils4
  libmono-sqlite2.0-cil libwmf-bin libkmediaplayer4 libkcal4 libntrack0
  python-rsvg libkfile4 libknewstuff3-4 libqapt-runtime
  libmono-system-web2.0-cil python-dateutil libkpty4 libwnck2.20-cil libkimap4
  libmagick++3 liblensfun0 libstreamanalyzer0 python-uniconvertor
  libknotifyconfig4 libkntlm4 libgudev1.0-cil python-wxversion libplasma3
  libkmime4 kdelibs-bin libktexteditor4 libattica0 python-evolution
  libkonq5-templates libkio5 libkjsapi4 libstreams0 libgnome-keyring1.0-cil
  python-wxgtk2.8 virtuoso-opensource-6.1-common marble-data
  plasma-scriptengine-javascript libssh-4 perlmagick marble-plugins
  kdebase-runtime-data libgtkglext1 libreadline5 python-reportlab libkhtml5
  libkdeui5 libkdesu5 kdelibs5-plugins libmono-wcf3.0-cil
  virtuoso-opensource-6.1-bin libkutils4 ntrack-module-libnl-0 libkrosscore4
  libgdiplus libnotify0.4-cil libnepomukquery4a libgnomedesktop2.20-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


A month ago I had an issue with an accidental deletion of an essential desktop lib, which was resolved. Is this left over from that? Is it safe to remove these files?

---

### Post by sbraz on 2011-08-24
normally using autoremove you uninstall packages with no dependancies with any other package (aka useless). i've never had problems with this so far.

---

### Post by SoFl W on 2011-08-24
I had one problem with autoremove, after that I stopped using it.  However the program I had a problem with was not installed with apt-get so I am not surprised if autoremoved didn't know about the dependency.

---

### Post by raja.genupula on 2011-08-24
autoremove will removes the lib's if your system don't have any use of them .so freely you can use it .

---

### Post by Bucky Ball on 2011-08-24
Are you using Kubuntu, the KDE desktop, or have removed KDE lately?

---

### Post by demonboy on 2011-08-24
No, I don't use Kubuntu.

---

### Post by WyleECoyote on 2011-08-24
> **SoFl W said:**
> I had one problem with autoremove, after that I stopped using it.  However the program I had a problem with was not installed with apt-get so I am not surprised if autoremoved didn't know about the dependency.

+1

I have had several problems with autoremove removing packages I use and need so I will never autoremove again because leaving files rarely hurts the system and I have plenty of hdd space to hold any system files/packages

---

### Post by raja.genupula on 2011-08-25
> **WyleECoyote said:**
> +1

I have had several problems with autoremove removing packages I use and need so I will never autoremove again because leaving files rarely hurts the system and I have plenty of hdd space to hold any system files/packages


yeah now a days  we no need to go for autoremove because high stoarge harddisk  . but in older days storage is too less & valuable , so i thought that they regularly usued to autoremove to free up the harddisk space .

---

### Post by realzippy on 2011-08-25
+1
those libs don't eat any bread.

---

### Post by demonboy on 2011-08-25
Furry muff. I just like to maintain my housekeeping and avoid useless rubbish on the computer, but I can live with leaving them on there.

---

