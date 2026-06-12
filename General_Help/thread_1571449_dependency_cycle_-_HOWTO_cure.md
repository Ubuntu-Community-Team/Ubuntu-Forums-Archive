---
title: "dependency cycle - HOWTO cure?"
date: 2010-09-09
forum: General Help
---

### Post by ilna on 2010-09-09
Hi!

With up to date Kubuntu Lucid (with backports) I have:

```
sudo apt-get --reinstall install x11-common x11-xkb-utils
[sudo] password for anli: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/504kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
E: Couldn't configure pre-depend x11-common for x11-xkb-utils, probably a dependency cycle.
```

This error prevents from upgrading to Maveric. How to resolve the issue? How to find all others cycles (the thing is, upgrade procedure fetches all files at first, and then reports error)?

Additional information: temporary I had 'proposed' archive in my sources list. Probably, some evil trails still exist. How to clean them? And - how to regenerate all packages information? - I mean to force 'apt-get update' to reget all information and to rebuild all packages-related caches.

I see, too many questions :)

---

### Post by xbruce on 2010-09-11
Any solution to this problem?
I have the same problem though I am using the update-manager. 
I am using Lucid and upgrading to the Maveric beta.
I get a window pop up that says "Could Not Install the upgrades. Error during commit."
The error message is: 

> 'E:Couldn't configure pre-depend x11-common for x11-xkb-utils, probably a dependency cycle.'
Restoring original system state

Any help or ideas appreciated.

---

### Post by ilna on 2010-09-11
From console I have removed x11-xkb-utils (with all related packages from dependencies tree), and then installed 'xorg' (again, with all deps, of course). Now I'm writing from Maverick.

It's sad there are no common ways (or nobody knows) to resolve/answer all those question from the first thread message. They are essencial for every day use.

---

### Post by coffeecat on 2010-09-11
I should think it's the Backports repository that's causing problems when trying to upgrade to a release that's still in development. The Maverick backports repository is probably in an inconsistent state at the moment. Disable the backports repo, do a 'sudo apt-get update' and 'sudo apt-get upgrade' and then try your dist-upgrade again.

And @xbruce, [do not use update-manager while Maverick is still in development]("http://ubuntuforums.org/showthread.php?t=1479146").

@ilna, another thing. About the proposed repository. Are you aware of this:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

>  Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.**Edit**, @ilna, I see that you've managed to upgrade to Maverick, but...

> They are essencial for every day use.Upgrading to a development version is not "everyday use". The development version is provided for experienced users to try out in order to find bugs. Expect a rough ride before a version goes final.

---

### Post by ilna on 2010-09-11
> **coffeecat said:**
> I should think it's the Backports repository that's causing problems when trying to upgrade to a release that's still in development. The Maverick backports repository is probably in an inconsistent state at the moment. Disable the backports repo, do a 'sudo apt-get update' and 'sudo apt-get upgrade' and then try your dist-upgrade again.
As you can see in the first message, the problem isn't related to Maverick at all. It was just discovered on the way to Maverick.

---

### Post by coffeecat on 2010-09-11
> **ilna said:**
> As you can see in the first message, the problem isn't related to Maverick at all. It was just discovered on the way to Maverick.

Indeed. I misread your first post. Apologies.

Anyway, I should imagine the problem stems from either the Lucid backports or proposed repository. You said you temporarily enabled the proposed repo. Did you install anything from it? That's what I would point my finger at first. I see you removed x11-xkb-utils (with dependencies) and then reinstalled xorg. Was that after disabling proposed?

If not, I guess it was something from the backports repository which was the problem. Although the link I posted says of backports...

> they can contain new features, but may also break compatibility with  their older version. However, they are compiled specifically for your  version of Ubuntu. In effect it saves you the hassle of broken  dependencies and major downloads. ... perhaps in this case there was a dependency error.

---

### Post by ilna on 2010-09-11
> **coffeecat said:**
> Was that after disabling proposed?Yes. 

My main wonder is how to obtain information useful for resolving a problem. Used way - "try and see" - isn't most productive, I think :)

---

### Post by coffeecat on 2010-09-11
> **ilna said:**
> Yes. 

My main wonder is how to obtain information useful for resolving a problem. Used way - "try and see" - isn't most productive, I think :)

There's an easy answer to your first sentence. Post a support thread on this forum **before** trying and seeing. :p

Good luck!

---

### Post by ilna on 2010-09-11
> **coffeecat said:**
> There's an easy answer to your first sentence. Post a support thread on this forum **before** trying and seeing. :pI'm sure, the answer (if one does exist) doesn't depend on my experiments :) In fact, I think some kind of "how to detect and resolve common packaging problems" tutorial is absolute must-have for Ubuntu (or any apt/deb based distro). Probably, I wasn't lucky to find one.

---

### Post by xbruce on 2010-09-11
> From console I have removed x11-xkb-utils (with all related packages  from dependencies tree), and then installed 'xorg' (again, with all  deps, of course). Now I'm writing from Maverick.


Thanks ilna, that worked. 

(Disabling backport repos didn't work, but thanks for the advice, coffeecat.)

---

### Post by BuZZ-dEE on 2010-09-23
hello, i have done this:

```

buzz-dee@buzz-dee-laptop:~$ sudo apt-get remove x11-xkb-utils
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht länger benötigt:
  libterm-progressbar-perl libexporter-lite-perl libnet-ip-perl
  libnet-dns-perl libxml-perl libossp-uuid-perl libemail-find-perl
  liblog-tracemessages-perl libarchive-zip-perl libxmltv-perl
  libhtml-fromtext-perl libunicode-string-perl libfcgi-perl
  libdatetime-timezone-perl xmltv-util libfile-slurp-perl libtext-bidi-perl
  libsoap-lite-perl libclass-methodmaker-perl libxml-writer-perl
  libparams-validate-perl libdatetime-format-strptime-perl libdatetime-perl
  libxml-regexp-perl libdatetime-locale-perl libtask-weaken-perl
  libnet-domain-tld-perl libregexp-common-perl libemail-valid-perl
  libxml-libxslt-perl liblingua-preferred-perl libossp-uuid16 libxml-dom-perl
  libclass-singleton-perl libemail-address-perl libdigest-hmac-perl
  libhttp-cache-transparent-perl
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden Pakete werden ENTFERNT:
  fglrx fglrx-amdcccle gdm gdm-guest-session gnome-applets
  gnome-control-center gnome-panel gnome-screensaver gnome-session
  gnome-settings-daemon indicator-applet indicator-applet-session indicator-me
  libgnomekbd4 libxklavier16 ontv pidgin-awayonlock x11-xkb-utils
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 aktualisiert, 0 neu installiert, 58 zu entfernen und 2 nicht aktualisiert.
Nach dieser Operation werden 154MB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? 
(Lese Datenbank ... 428783 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne fglrx-amdcccle ...
Entferne fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: Entferne manuell ausgewählte Alternative - wechsle gl_conf zu Auto-Modus
update-alternatives: Verwende /usr/lib/mesa/ld.so.conf, um /etc/ld.so.conf.d/GL.conf (gl_conf) in Auto-Modus bereitzustellen.
update-initramfs: deferring update (trigger activated)
Entferne gdm-guest-session ...
Entferne gdm ...
Entferne gnome-applets ...
Entferne indicator-me ...
Entferne indicator-applet-session ...
Entferne indicator-applet ...
Entferne ontv ...
Entferne gnome-session ...
Entferne gnome-panel ...
Entferne gnome-control-center ...
Entferne pidgin-awayonlock ...
Entferne gnome-screensaver ...
Entferne gnome-settings-daemon ...
Entferne libgnomekbd4 ...
Entferne libxklavier16 ...
Entferne xserver-xorg-video-all ...
Entferne xserver-xorg-video-voodoo ...
Entferne xserver-xorg-video-vmware ...
Entferne xserver-xorg-video-vesa ...
Entferne xserver-xorg-video-v4l ...
Entferne xserver-xorg-video-tseng ...
Entferne xserver-xorg-video-trident ...
Entferne xserver-xorg-video-tdfx ...
Entferne xserver-xorg-video-sisusb ...
Entferne xserver-xorg-video-sis ...
Entferne xserver-xorg-video-siliconmotion ...
Entferne xserver-xorg-video-savage ...
Entferne xserver-xorg-video-s3virge ...
Entferne xserver-xorg-video-s3 ...
Entferne xserver-xorg-video-rendition ...
Entferne xserver-xorg-video-ati ...
Entferne xserver-xorg-video-radeon ...
Entferne xserver-xorg-video-r128 ...
Entferne xserver-xorg-video-openchrome ...
Entferne xserver-xorg-video-nv ...
Entferne xserver-xorg-video-nouveau ...
Entferne xserver-xorg-video-neomagic ...
Entferne xserver-xorg-video-mga ...
Entferne xserver-xorg-video-mach64 ...
Entferne xserver-xorg-video-intel ...
Entferne xserver-xorg-video-i128 ...
Entferne xserver-xorg-video-fbdev ...
Entferne xserver-xorg-video-cirrus ...
Entferne xserver-xorg-video-chips ...
Entferne xserver-xorg-video-ark ...
Entferne xserver-xorg-input-all ...
Entferne xserver-xorg-input-wacom ...
Entferne xserver-xorg-input-vmmouse ...
Entferne xserver-xorg-input-synaptics ...
Entferne xserver-xorg-input-mouse ...
Entferne xserver-xorg-core ...
Entferne xserver-xorg ...
Entferne xserver-common ...
Entferne x11-xkb-utils ...
dpkg: Warnung: Während Entfernens von x11-xkb-utils ist Verzeichnis »/var/lib/xkb« nicht leer, wird daher nicht gelöscht.
Entferne xserver-xorg-video-apm ...
Entferne xserver-xorg-input-evdev ...
Verarbeite Trigger für python-gmenu ...
Rebuilding /usr/share/applications/desktop.de_DE.utf8.cache...
Verarbeite Trigger für libc-bin ...
ldconfig deferred processing now taking place
Verarbeite Trigger für ureadahead ...
Verarbeite Trigger für man-db ...
Verarbeite Trigger für initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Verarbeite Trigger für desktop-file-utils ...
Verarbeite Trigger für hicolor-icon-theme ...
Verarbeite Trigger für menu ...
Verarbeite Trigger für python-support ...
buzz-dee@buzz-dee-laptop:~$ sudo apt-get autoremove 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Die folgenden Pakete werden ENTFERNT:
  libarchive-zip-perl libclass-methodmaker-perl libclass-singleton-perl
  libdatetime-format-strptime-perl libdatetime-locale-perl libdatetime-perl
  libdatetime-timezone-perl libdigest-hmac-perl libemail-address-perl
  libemail-find-perl libemail-valid-perl libexporter-lite-perl libfcgi-perl
  libfile-slurp-perl libhtml-fromtext-perl libhttp-cache-transparent-perl
  liblingua-preferred-perl liblog-tracemessages-perl libnet-dns-perl
  libnet-domain-tld-perl libnet-ip-perl libossp-uuid-perl libossp-uuid16
  libparams-validate-perl libregexp-common-perl libsoap-lite-perl
  libtask-weaken-perl libterm-progressbar-perl libtext-bidi-perl
  libunicode-string-perl libxml-dom-perl libxml-libxslt-perl libxml-perl
  libxml-regexp-perl libxml-writer-perl libxmltv-perl xmltv-util
0 aktualisiert, 0 neu installiert, 37 zu entfernen und 2 nicht aktualisiert.
Nach dieser Operation werden 45,6MB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? n     
Abbruch.
buzz-dee@buzz-dee-laptop:~$ sudo rm -rf /var/lib/x
x11/      xfonts/   xkb/      xml-core/ 
buzz-dee@buzz-dee-laptop:~$ sudo rm -rf /var/lib/xkb/
buzz-dee@buzz-dee-laptop:~$ sudo apt-get install xorg
xorg                   xorg-docs              xorg-driver-synaptics
xorg-build-macros      xorg-docs-core         xorg-sgml-doctools
xorg-common            xorg-driver-fglrx      
xorg-dev               xorg-driver-fglrx-dev  
buzz-dee@buzz-dee-laptop:~$ sudo apt-get install xorg
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht länger benötigt:
  libterm-progressbar-perl libexporter-lite-perl libnet-ip-perl
  libnet-dns-perl libxml-perl libossp-uuid-perl libemail-find-perl
  liblog-tracemessages-perl libarchive-zip-perl libxmltv-perl
  libhtml-fromtext-perl libunicode-string-perl libfcgi-perl
  libdatetime-timezone-perl xmltv-util libfile-slurp-perl libtext-bidi-perl
  libsoap-lite-perl libclass-methodmaker-perl libxml-writer-perl
  libparams-validate-perl libdatetime-format-strptime-perl libdatetime-perl
  libxml-regexp-perl libdatetime-locale-perl libtask-weaken-perl
  libnet-domain-tld-perl libregexp-common-perl libemail-valid-perl
  libxml-libxslt-perl liblingua-preferred-perl libossp-uuid16 libxml-dom-perl
  libclass-singleton-perl libemail-address-perl libdigest-hmac-perl
  libhttp-cache-transparent-perl
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden zusätzlichen Pakete werden installiert:
  x11-xkb-utils xserver-common xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
Vorgeschlagene Pakete:
  xorg-docs gpointing-device-settings touchfreeze firmware-linux
Die folgenden NEUEN Pakete werden installiert:
  x11-xkb-utils xorg xserver-common xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 aktualisiert, 42 neu installiert, 0 zu entfernen und 2 nicht aktualisiert.
Es müssen noch 1.498B von 6.981kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 16,9MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? 
Hole:1 http://de.archive.ubuntu.com/ubuntu/ lucid/main xorg 1:7.5+5ubuntu1 [1.498B]
Es wurden 1.498B in 0s geholt (4.319B/s)
Extrahiere Templates aus Paketen: 100%
Wähle vormals abgewähltes Paket x11-xkb-utils.
(Lese Datenbank ... 427661 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke x11-xkb-utils (aus .../x11-xkb-utils_7.5+1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-common.
Entpacke xserver-common (aus .../xserver-common_2%3a1.7.6-2ubuntu7.3_all.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-core.
Entpacke xserver-xorg-core (aus .../xserver-xorg-core_2%3a1.7.6-2ubuntu7.3_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-apm.
Entpacke xserver-xorg-video-apm (aus .../xserver-xorg-video-apm_1%3a1.2.2-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-ark.
Entpacke xserver-xorg-video-ark (aus .../xserver-xorg-video-ark_1%3a0.7.2-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-r128.
Entpacke xserver-xorg-video-r128 (aus .../xserver-xorg-video-r128_6.8.1-2ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-mach64.
Entpacke xserver-xorg-video-mach64 (aus .../xserver-xorg-video-mach64_6.8.2-2_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-radeon.
Entpacke xserver-xorg-video-radeon (aus .../xserver-xorg-video-radeon_1%3a6.13.0-1ubuntu5_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-ati.
Entpacke xserver-xorg-video-ati (aus .../xserver-xorg-video-ati_1%3a6.13.0-1ubuntu5_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-chips.
Entpacke xserver-xorg-video-chips (aus .../xserver-xorg-video-chips_1%3a1.2.2-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-cirrus.
Entpacke xserver-xorg-video-cirrus (aus .../xserver-xorg-video-cirrus_1%3a1.3.2-1ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-fbdev.
Entpacke xserver-xorg-video-fbdev (aus .../xserver-xorg-video-fbdev_1%3a0.4.1-1ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-i128.
Entpacke xserver-xorg-video-i128 (aus .../xserver-xorg-video-i128_1%3a1.3.3-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-intel.
Entpacke xserver-xorg-video-intel (aus .../xserver-xorg-video-intel_2%3a2.9.1-3ubuntu5_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-mga.
Entpacke xserver-xorg-video-mga (aus .../xserver-xorg-video-mga_1%3a1.4.11.dfsg-2ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-neomagic.
Entpacke xserver-xorg-video-neomagic (aus .../xserver-xorg-video-neomagic_1%3a1.2.4-2_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-nouveau.
Entpacke xserver-xorg-video-nouveau (aus .../xserver-xorg-video-nouveau_1%3a0.0.15+git20100219+9b4118d-0ubuntu5_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-nv.
Entpacke xserver-xorg-video-nv (aus .../xserver-xorg-video-nv_1%3a2.1.15-1ubuntu3_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-rendition.
Entpacke xserver-xorg-video-rendition (aus .../xserver-xorg-video-rendition_1%3a4.2.3-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-s3.
Entpacke xserver-xorg-video-s3 (aus .../xserver-xorg-video-s3_1%3a0.6.3-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-s3virge.
Entpacke xserver-xorg-video-s3virge (aus .../xserver-xorg-video-s3virge_1%3a1.10.4-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-savage.
Entpacke xserver-xorg-video-savage (aus .../xserver-xorg-video-savage_1%3a2.3.1-1ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-siliconmotion.
Entpacke xserver-xorg-video-siliconmotion (aus .../xserver-xorg-video-siliconmotion_1%3a1.7.3-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-sis.
Entpacke xserver-xorg-video-sis (aus .../xserver-xorg-video-sis_1%3a0.10.2-2_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-sisusb.
Entpacke xserver-xorg-video-sisusb (aus .../xserver-xorg-video-sisusb_1%3a0.9.3-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-tdfx.
Entpacke xserver-xorg-video-tdfx (aus .../xserver-xorg-video-tdfx_1%3a1.4.3-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-trident.
Entpacke xserver-xorg-video-trident (aus .../xserver-xorg-video-trident_1%3a1.3.3-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-tseng.
Entpacke xserver-xorg-video-tseng (aus .../xserver-xorg-video-tseng_1%3a1.2.3-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-vesa.
Entpacke xserver-xorg-video-vesa (aus .../xserver-xorg-video-vesa_1%3a2.3.0-1ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-openchrome.
Entpacke xserver-xorg-video-openchrome (aus .../xserver-xorg-video-openchrome_1%3a0.2.904+svn827-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-voodoo.
Entpacke xserver-xorg-video-voodoo (aus .../xserver-xorg-video-voodoo_1%3a1.2.3-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-v4l.
Entpacke xserver-xorg-video-v4l (aus .../xserver-xorg-video-v4l_1%3a0.2.0-4_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-vmware.
Entpacke xserver-xorg-video-vmware (aus .../xserver-xorg-video-vmware_1%3a10.16.9-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-video-all.
Entpacke xserver-xorg-video-all (aus .../xserver-xorg-video-all_1%3a7.5+5ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-input-evdev.
Entpacke xserver-xorg-input-evdev (aus .../xserver-xorg-input-evdev_1%3a2.3.2-5ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-input-synaptics.
Entpacke xserver-xorg-input-synaptics (aus .../xserver-xorg-input-synaptics_1.2.2-1ubuntu4_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-input-mouse.
Entpacke xserver-xorg-input-mouse (aus .../xserver-xorg-input-mouse_1%3a1.5.0-1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-input-vmmouse.
Entpacke xserver-xorg-input-vmmouse (aus .../xserver-xorg-input-vmmouse_1%3a12.6.5-4ubuntu2_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-input-wacom.
Entpacke xserver-xorg-input-wacom (aus .../xserver-xorg-input-wacom_1%3a0.10.5-0ubuntu4_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg-input-all.
Entpacke xserver-xorg-input-all (aus .../xserver-xorg-input-all_1%3a7.5+5ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket xserver-xorg.
Entpacke xserver-xorg (aus .../xserver-xorg_1%3a7.5+5ubuntu1_amd64.deb) ...
Wähle vormals abgewähltes Paket xorg.
Entpacke xorg (aus .../xorg_1%3a7.5+5ubuntu1_amd64.deb) ...
Verarbeite Trigger für man-db ...
Richte x11-xkb-utils ein (7.5+1) ...
Richte xserver-common ein (2:1.7.6-2ubuntu7.3) ...
Richte xserver-xorg-core ein (2:1.7.6-2ubuntu7.3) ...

Richte xserver-xorg-video-apm ein (1:1.2.2-1) ...
Richte xserver-xorg-video-ark ein (1:0.7.2-1) ...
Richte xserver-xorg-video-r128 ein (6.8.1-2ubuntu1) ...
Richte xserver-xorg-video-mach64 ein (6.8.2-2) ...
Richte xserver-xorg-video-radeon ein (1:6.13.0-1ubuntu5) ...

Richte xserver-xorg-video-ati ein (1:6.13.0-1ubuntu5) ...
Richte xserver-xorg-video-chips ein (1:1.2.2-1) ...
Richte xserver-xorg-video-cirrus ein (1:1.3.2-1ubuntu1) ...
Richte xserver-xorg-video-fbdev ein (1:0.4.1-1ubuntu1) ...
Richte xserver-xorg-video-i128 ein (1:1.3.3-1) ...
Richte xserver-xorg-video-intel ein (2:2.9.1-3ubuntu5) ...

Richte xserver-xorg-video-mga ein (1:1.4.11.dfsg-2ubuntu1) ...
Richte xserver-xorg-video-neomagic ein (1:1.2.4-2) ...
Richte xserver-xorg-video-nouveau ein (1:0.0.15+git20100219+9b4118d-0ubuntu5) ...
Richte xserver-xorg-video-nv ein (1:2.1.15-1ubuntu3) ...
Richte xserver-xorg-video-rendition ein (1:4.2.3-1) ...
Richte xserver-xorg-video-s3 ein (1:0.6.3-1) ...
Richte xserver-xorg-video-s3virge ein (1:1.10.4-1) ...
Richte xserver-xorg-video-savage ein (1:2.3.1-1ubuntu1) ...
Richte xserver-xorg-video-siliconmotion ein (1:1.7.3-1) ...
Richte xserver-xorg-video-sis ein (1:0.10.2-2) ...
Richte xserver-xorg-video-sisusb ein (1:0.9.3-1) ...
Richte xserver-xorg-video-tdfx ein (1:1.4.3-1) ...
Richte xserver-xorg-video-trident ein (1:1.3.3-1) ...
Richte xserver-xorg-video-tseng ein (1:1.2.3-1) ...
Richte xserver-xorg-video-vesa ein (1:2.3.0-1ubuntu1) ...
Richte xserver-xorg-video-openchrome ein (1:0.2.904+svn827-1) ...

Richte xserver-xorg-video-voodoo ein (1:1.2.3-1) ...
Richte xserver-xorg-video-v4l ein (1:0.2.0-4) ...
Richte xserver-xorg-video-vmware ein (1:10.16.9-1) ...
Richte xserver-xorg-video-all ein (1:7.5+5ubuntu1) ...
Richte xserver-xorg-input-evdev ein (1:2.3.2-5ubuntu1) ...
Richte xserver-xorg-input-synaptics ein (1.2.2-1ubuntu4) ...

Richte xserver-xorg-input-mouse ein (1:1.5.0-1) ...
Richte xserver-xorg-input-vmmouse ein (1:12.6.5-4ubuntu2) ...

Richte xserver-xorg-input-wacom ein (1:0.10.5-0ubuntu4) ...

Richte xserver-xorg-input-all ein (1:7.5+5ubuntu1) ...
Richte xserver-xorg ein (1:7.5+5ubuntu1) ...

Richte xorg ein (1:7.5+5ubuntu1) ...
Verarbeite Trigger für libc-bin ...
ldconfig deferred processing now taking place
buzz-dee@buzz-dee-laptop:~$ 

```

but i can't still upgrade to maverik beta. (backports and proposed are disabled)

what can i do now?

---

### Post by zabsv on 2010-10-04
I was experiencing the same problem when trying to upgrade to Maverick, and I found a solution that may help others in the same situation.
Like you I had activated the proposed packages and that seems to have messed up the dependencies. 
Unfortunately there doesn't seem to be any way to easily revert to an older version of a package but I was lucky enough to find a older copy in the apt cache.

what I did was:
$ cd /var/cache/apt/archives
$ ls|grep xkb-utils
x11-xkb-utils_7.5+1_amd64.deb
x11-xkb-utils_7.5+5_amd64.deb

$ dpkg -i ./x11-xkb-utils_7.5+1_amd64.deb
 - cut install info text here -

$ ls|grep x11-common
x11-common_1%3a7.5+6ubuntu3_all.deb

$ sudo dpkg -i ./x11-common_1%3a7.5+6ubuntu3_all.deb

Förbereder att ersätta x11-common 1:7.5+5ubuntu1 (med .../x11-common_1%3a7.5+6ubuntu3_all.deb)

- cut install info -

Note that although there is only one copy of x11-common in my cache, which should be the installed one, dpkg upgrades an older version.

I'm not sure why this happens, and I wouldn't be surprised if using dpkg to install packages from the cache creates other problems. But at least it seems to be possible to solve some dependency issues this way.

---

### Post by robyshot on 2010-10-06
> **zabsv said:**
> I was experiencing the same problem when trying to upgrade to Maverick, and I found a solution that may help others in the same situation.
Like you I had activated the proposed packages and that seems to have messed up the dependencies. 
Unfortunately there doesn't seem to be any way to easily revert to an older version of a package but I was lucky enough to find a older copy in the apt cache.

what I did was:
$ cd /var/cache/apt/archives
$ ls|grep xkb-utils
x11-xkb-utils_7.5+1_amd64.deb
x11-xkb-utils_7.5+5_amd64.deb

$ dpkg -i ./x11-xkb-utils_7.5+1_amd64.deb
 - cut install info text here -

$ ls|grep x11-common
x11-common_1%3a7.5+6ubuntu3_all.deb

$ sudo dpkg -i ./x11-common_1%3a7.5+6ubuntu3_all.deb

Förbereder att ersätta x11-common 1:7.5+5ubuntu1 (med .../x11-common_1%3a7.5+6ubuntu3_all.deb)

- cut install info -

Note that although there is only one copy of x11-common in my cache, which should be the installed one, dpkg upgrades an older version.

I'm not sure why this happens, and I wouldn't be surprised if using dpkg to install packages from the cache creates other problems. But at least it seems to be possible to solve some dependency issues this way.
this didn't work for me and if i try to remove these packages and reinstall xorg (as proprosed earlier) kpackagekit tries to remove 1.9 gb of apps and deps
how can i procede?

---

### Post by robyshot on 2010-10-07
> **robyshot said:**
> this didn't work for me and if i try to remove these packages and reinstall xorg (as proprosed earlier) kpackagekit tries to remove 1.9 gb of apps and deps
how can i procede?
i resolved using this commands 

```
dpkg --force-depends --remove x11-xkb-utils

dpkg --force-depends --remove x11-common
```

---

### Post by glenstewart on 2010-10-07
I want to confirm that this sequence allows an upgrade for me too, going from Lucid Lubuntu, to Maverick Lubuntu:

sudo apt-get remove x11-xkb-utils
sudo do-release-upgrade -d



Thanks!

---

### Post by kbrower on 2010-10-10
> **zabsv said:**
> I was experiencing the same problem when trying to upgrade to Maverick, and I found a solution that may help others in the same situation.
Like you I had activated the proposed packages and that seems to have messed up the dependencies. 
Unfortunately there doesn't seem to be any way to easily revert to an older version of a package but I was lucky enough to find a older copy in the apt cache.

what I did was:
$ cd /var/cache/apt/archives
$ ls|grep xkb-utils
x11-xkb-utils_7.5+1_amd64.deb
x11-xkb-utils_7.5+5_amd64.deb

$ dpkg -i ./x11-xkb-utils_7.5+1_amd64.deb
 - cut install info text here -

$ ls|grep x11-common
x11-common_1%3a7.5+6ubuntu3_all.deb

$ sudo dpkg -i ./x11-common_1%3a7.5+6ubuntu3_all.deb

Förbereder att ersätta x11-common 1:7.5+5ubuntu1 (med .../x11-common_1%3a7.5+6ubuntu3_all.deb)

- cut install info -

Note that although there is only one copy of x11-common in my cache, which should be the installed one, dpkg upgrades an older version.

I'm not sure why this happens, and I wouldn't be surprised if using dpkg to install packages from the cache creates other problems. But at least it seems to be possible to solve some dependency issues this way.

Thanks this solution worked for me, after trying everything else up to this point in the thread.

---

### Post by davidudin on 2010-10-20
I didn't have two versions of the x11-xkb-utils_7.5+5_amd64.deb, but simply doing the 

$ sudo dpkg -i ./x11-common_1%3a7.5+6ubuntu3_all.deb

got me around the dependency problem.

Cheers.

---

### Post by Fazer2 on 2010-11-07
> **davidudin said:**
> I didn't have two versions of the x11-xkb-utils_7.5+5_amd64.deb, but simply doing the 

$ sudo dpkg -i ./x11-common_1%3a7.5+6ubuntu3_all.deb

got me around the dependency problem.

Cheers.
Thanks, I had the same problem and this solved it!

---

### Post by Binda on 2011-01-04
> **davidudin said:**
> I didn't have two versions of the x11-xkb-utils_7.5+5_amd64.deb, but simply doing the 

$ sudo dpkg -i ./x11-common_1%3a7.5+6ubuntu3_all.deb

got me around the dependency problem.

Cheers.

Worked for me too, after I switched to /var/cache/apt/archives 

cd /var/cache/apt/archives
sudo dpkg -i ./x11-common_1%3a7.5+6ubuntu3_all.deb

thanx

---

### Post by Everyday user on 2011-01-06
Hello ,
As my user-name said , I am a complete layman , in
the computing -world . But I like to use linux , and I've
the same problem : "E:Couldn't configure pre-depend x11-common for x11-xkb-utils, probably a dependency cycle."

The big difference is , your computer -language is worse than Chinese to me .
Has anyone a solution for me ?

Thank you .

---

