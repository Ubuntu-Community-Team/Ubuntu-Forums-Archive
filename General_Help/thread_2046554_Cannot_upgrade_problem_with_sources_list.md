---
title: "Cannot upgrade: problem with sources list"
date: 2012-08-23
forum: General Help
---

### Post by geo909 on 2012-08-23
Hi all,

I have a desktop with 11.04 (Natty) on. This particular 
one hasn't been updated since more than a year. I now 
run synaptic, "mark all upgrades" and after I click 
"apply" I get the following long error message.

Any ideas? I also post my /etc/apt/sources.list in the 
end..  I guess it has to do with that and the fact that 
there hasn't been any update for a while?

Many thanks in advance!


```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/python-httplib2/python-httplib2_0.7.2-1ubuntu2~0.11.04.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python-minimal_2.7.1-0ubuntu5.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python_2.7.1-0ubuntu5.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-dev-bin_2.13-0ubuntu13.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.13-0ubuntu13.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.13-0ubuntu13.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.13-0ubuntu13.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.38-15.60_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2012b-0ubuntu0.11.04_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libt/libtasn1-3/libtasn1-3_2.7-1ubuntu1.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gnutls26/libgnutls26_2.8.6-1ubuntu2.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser-l10n_18.0.1025.151~r130497-0ubuntu0.11.04.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-codecs-ffmpeg_18.0.1025.151~r130497-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.4.4-1ubuntu2.3_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.44-1ubuntu3.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser_18.0.1025.151~r130497-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser-inspector_18.0.1025.151~r130497-0ubuntu0.11.04.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_19.0.1084.56-r140965_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.4-5ubuntu6.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.38-13-generic_2.6.38-13.57_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.38-15-generic_2.6.38-15.60_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_1.2.1-0ubuntu2.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.13.2ubuntu4.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8o-5ubuntu1.7_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/multiarch-support_2.13-0ubuntu13.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.8.13.2ubuntu4.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.6.1-0ubuntu3.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.6.1-0ubuntu3.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.6.1-0ubuntu3.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.6.1-0ubuntu3.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.8.dfsg-2ubuntu0.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.3.dfsg-1ubuntu2.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.3.dfsg-1ubuntu2.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc62_9.7.3.dfsg-1ubuntu2.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns69_9.7.3.dfsg-1ubuntu2.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.3.dfsg-1ubuntu2.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg62_9.7.3.dfsg-1ubuntu2.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.3.dfsg-1ubuntu2.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.3.dfsg-1ubuntu2.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_11.2.202.236-0natty1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.236-0natty1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-partner/app-install-data-partner_12.11.04.4_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.13.2ubuntu4.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_13.0+build1-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_13.0+build1-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_13.0+build1-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_13.0+build1-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-el_13.0+build1-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_13.0+build1-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gdm-guest-session/gdm-guest-session_0.24ubuntu0.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-user-docs/gnome-user-guide_3.0.0+git20110406ubuntu12_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/grub-gfxpayload-lists/grub-gfxpayload-lists_0.2.3_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gsettings-desktop-schemas/gsettings-desktop-schemas_3.0.0-0ubuntu1.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore3_6.6.2.6-1ubuntu4.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickwand3_6.6.2.6-1ubuntu4.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick_6.6.2.6-1ubuntu4.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick++3_6.6.2.6-1ubuntu4.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore3-extra_6.6.2.6-1ubuntu4.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.1/mysql-common_5.1.63-0ubuntu0.11.04.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.1/libmysqlclient16_5.1.63-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.5.8~dfsg-1ubuntu2.5_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.5.8~dfsg-1ubuntu2.5_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp-base_5.4.3~dfsg-2ubuntu1.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp15_5.4.3~dfsg-2ubuntu1.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.6.2-0ubuntu2.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-storage-protocol/python-ubuntuone-storageprotocol_1.6.1-0ubuntu1.2_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/libsyncdaemon-1.0-1_1.6.2-0ubuntu2.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_1.6.2-0ubuntu2.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.6.2-0ubuntu2.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisfile3_1.3.2-1ubuntu1.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisenc2_1.3.2-1ubuntu1.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbis0a_1.3.2-1ubuntu1.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.8.dfsg-2ubuntu0.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.38.15.30_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.38.15.30_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-13_2.6.38-13.57_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-13-generic_2.6.38-13.57_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-15_2.6.38-15.60_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-15-generic_2.6.38-15.60_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.38.15.30_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8o-5ubuntu1.7_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.8.dfsg-2ubuntu0.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/python-pam/python-pam_0.4.2-12.2ubuntu2.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.5.8~dfsg-1ubuntu2.5_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.5.8~dfsg-1ubuntu2.5_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.5.8~dfsg-1ubuntu2.5_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.7.4p4-5ubuntu7.2_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-locale-en_12.0.1+build1-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-locale-en-us_12.0.1+build1-0ubuntu0.11.04.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-locale-en-gb_12.0.1+build1-0ubuntu0.11.04.1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-locale-el_12.0.1+build1-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_12.0.1+build1-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_12.0.1+build1-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/ubufox/xul-ext-ubufox_0.9.5-0ubuntu1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_0.9.5-0ubuntu1_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.150.5.4_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.150.5.4_i386.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon_0.41+bzr661-0ubuntu0.2_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon-data_0.41+bzr661-0ubuntu0.2_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon-gtk_0.41+bzr661-0ubuntu0.2_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon.gtk3widgets_0.41+bzr661-0ubuntu0.2_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon.gtkwidgets_0.41+bzr661-0ubuntu0.2_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon_0.41+bzr661-0ubuntu0.2_all.deb
  407  Proxy Authentication Required


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.28+build1+nobinonly-0ubuntu0.11.04.1_i386.deb
  407  Proxy Authentication Required

```

Source.list file:

```
@oldfella:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.canonical.com/ natty partner
deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository
deb http://security.ubuntu.com/ubuntu/ natty-security restricted main multiverse universe

```

---

### Post by lechien73 on 2012-08-23
Does this machine access the Internet through a proxy server? It looks like proxy settings and authentication need to be set.

---

### Post by 2F4U on 2012-08-23
You need to configure apt-get to use a proxy server. Here is how to do it:

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by geo909 on 2012-08-23
A proxy server? Hmmm, reading the errors again I guess that 
makes sense! :S This is not my computer so I'll have to ask 
to confirm but it seems this is what I need..

Thanks!

---

### Post by geo909 on 2012-09-03
It's been a long time since my last post but the 
problem is not yet solved.. Apparently the computer
is not under a proxy and I get a different error 
message now (again, this is not my computer so I'm 
not sure what it has been done in the meanwhile).

Here is what I get now when I try to update:
```

$ sudo apt-get update


Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://archive.ubuntu.com natty-updates InRelease                          
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Ign http://archive.canonical.com natty InRelease                               
Ign http://security.ubuntu.com natty-security InRelease                        
Get:3 http://dl.google.com stable Release.gpg [198 B]                          
Get:4 http://dl.google.com stable Release                                      
Get:5 http://archive.ubuntu.com natty Release.gpg [198 B]                      
Ign http://linux.dropbox.com natty InRelease                                   
Get:6 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Get:7 http://extras.ubuntu.com natty Release.gpg [72 B]                        
Ign http://dl.google.com stable Release                                        
Get:8 http://archive.canonical.com natty Release.gpg [198 B]                   
Get:9 http://security.ubuntu.com natty-security Release.gpg [198 B]            
Get:10 http://dl.google.com stable Release                                     
Ign http://dl.google.com stable Release                                        
Get:11 http://dl.google.com stable Release                                     
Ign http://dl.google.com stable Release                                        
Get:12 http://archive.ubuntu.com natty-updates Release.gpg [198 B]             
Get:13 http://ppa.launchpad.net natty Release [9,733 B]                        
Get:14 http://archive.canonical.com natty Release.gpg [198 B]                  
Get:15 http://extras.ubuntu.com natty Release [9,753 B]                        
Get:16 http://dl.google.com stable/main i386 Packages [1,244 B]                
Get:17 http://security.ubuntu.com natty-security Release [39.8 kB]             
Ign http://dl.google.com stable/main TranslationIndex                          
Get:18 http://linux.dropbox.com natty Release.gpg [489 B]                      
Get:19 http://dl.google.com stable/main i386 Packages [464 B]                  
Ign http://dl.google.com stable/main TranslationIndex                          
Get:20 http://archive.ubuntu.com natty Release [39.8 kB]                       
Get:21 http://dl.google.com stable/main i386 Packages [776 B]                  
Get:22 http://archive.canonical.com natty Release [5,916 B]                    
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://ppa.launchpad.net natty Release                                     
Ign http://archive.canonical.com natty Release                                 
Ign http://extras.ubuntu.com natty Release                                     
Get:23 http://linux.dropbox.com natty Release [2,599 B]                        
Ign http://linux.dropbox.com natty Release                                     
Get:24 http://archive.canonical.com natty Release [5,916 B]                    
Ign http://archive.canonical.com natty Release                                 
Get:25 http://ppa.launchpad.net natty/main Sources [595 B]                     
Ign http://security.ubuntu.com natty-security Release                          
Get:26 http://extras.ubuntu.com natty/main i386 Packages [14 B]                
Get:27 http://linux.dropbox.com natty/main i386 Packages [1,029 B]             
Get:28 http://archive.canonical.com natty/partner i386 Packages [7,342 B]      
Ign http://archive.canonical.com natty/partner TranslationIndex                
Get:29 http://ppa.launchpad.net natty/main i386 Packages [322 B]               
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:30 http://security.ubuntu.com natty-security/restricted i386 Packages [4,822 B]
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://archive.ubuntu.com natty Release                                    
Get:31 http://archive.canonical.com natty/partner i386 Packages [7,342 B]      
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://linux.dropbox.com natty/main TranslationIndex                       
Get:32 http://security.ubuntu.com natty-security/main i386 Packages [358 kB]   
Get:33 http://archive.ubuntu.com natty-updates Release [39.8 kB]               
Get:34 http://security.ubuntu.com natty-security/multiverse i386 Packages [3,559 B]
Get:35 http://security.ubuntu.com natty-security/universe i386 Packages [101 kB]
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://linux.dropbox.com natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://linux.dropbox.com natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://archive.ubuntu.com natty-updates Release                            
Get:36 http://archive.ubuntu.com natty/main Sources [862 kB]                   
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:37 http://archive.ubuntu.com natty/restricted Sources [4,104 B]            
Get:38 http://archive.ubuntu.com natty/universe Sources [4,380 kB]             
Get:39 http://archive.ubuntu.com natty/multiverse Sources [155 kB]             
Get:40 http://archive.ubuntu.com natty/main i386 Packages [1,550 kB]           
Get:41 http://archive.ubuntu.com natty/restricted i386 Packages [8,986 B]      
Get:42 http://archive.ubuntu.com natty/universe i386 Packages [6,021 kB]       
Get:43 http://archive.ubuntu.com natty/multiverse i386 Packages [183 kB]       
Ign http://archive.ubuntu.com natty/main TranslationIndex                      
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Ign http://archive.ubuntu.com natty/universe TranslationIndex                  
Get:44 http://archive.ubuntu.com natty-updates/main Sources [170 kB]           
Get:45 http://archive.ubuntu.com natty-updates/restricted Sources [2,116 B]    
Get:46 http://archive.ubuntu.com natty-updates/universe Sources [51.3 kB]      
Get:47 http://archive.ubuntu.com natty-updates/multiverse Sources [3,107 B]    
Get:48 http://archive.ubuntu.com natty-updates/main i386 Packages [490 kB]     
Get:49 http://archive.ubuntu.com natty-updates/restricted i386 Packages [6,257 B]
Get:50 http://archive.ubuntu.com natty-updates/universe i386 Packages [160 kB] 
Get:51 http://archive.ubuntu.com natty-updates/multiverse i386 Packages [6,383 B]
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Ign http://archive.ubuntu.com natty/main Translation-en_US                     
Ign http://archive.ubuntu.com natty/main Translation-en                        
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US               
Ign http://archive.ubuntu.com natty/multiverse Translation-en                  
Ign http://archive.ubuntu.com natty/restricted Translation-en_US               
Ign http://archive.ubuntu.com natty/restricted Translation-en                  
Ign http://archive.ubuntu.com natty/universe Translation-en_US                 
Ign http://archive.ubuntu.com natty/universe Translation-en                    
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US             
Ign http://archive.ubuntu.com natty-updates/main Translation-en                
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US       
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en          
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en          
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com natty-updates/universe Translation-en            
Fetched 14.7 MB in 51s (286 kB/s)                                              
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: Unknown error executing gpgv
W: GPG error: http://dl.google.com stable Release: Unknown error executing gpgv
W: GPG error: http://dl.google.com stable Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net natty Release: Unknown error executing gpgv
W: GPG error: http://archive.canonical.com natty Release: Unknown error executing gpgv
W: GPG error: http://extras.ubuntu.com natty Release: Unknown error executing gpgv
W: GPG error: http://linux.dropbox.com natty Release: Unknown error executing gpgv
W: GPG error: http://archive.canonical.com natty Release: Unknown error executing gpgv
W: GPG error: http://security.ubuntu.com natty-security Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com natty Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com natty-updates Release: Unknown error executing gpgv


```

Btw I did the following before (I found another similar post where somebody solved his problems with this) but it doesn't seem to help me:

```

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update


```

Many thanks in advance..

---

