---
title: "Archive Automatic Signing Keys 10.10"
date: 2011-05-14
forum: General Help
---

### Post by Onoku on 2011-05-14
Initially I had a problem installing restricted extras. However, it appears the problem is more than a media problem, so I moved my [thread]("http://ubuntuforums.org/showthread.php?t=1757607&page=2") here. I copied over what I thought the relevant code was from my previous thread. Anyone have ideas on how I can fix this?


```
onoku@onoku-MacBook:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for onoku: 
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Get:2 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Get:3 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Get:4 http://iq.archive.ubuntu.com maverick Release.gpg [198B]                 
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Get:5 http://extras.ubuntu.com maverick Release [9,762B]                       
Err http://extras.ubuntu.com maverick Release                                  
  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Get:6 http://ppa.launchpad.net maverick Release [39.8kB]             
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Get:7 http://archive.canonical.com maverick Release.gpg [198B]       
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Get:8 http://archive.canonical.com maverick Release.gpg [198B]       
Get:9 http://security.ubuntu.com maverick-security Release [31.4kB]           
Err http://security.ubuntu.com maverick-security Release               
  
Get:10 http://iq.archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://archive.canonical.com/ maverick/partner Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.canonical.com/ maverick/partner Translation-en_US           
Get:11 http://archive.canonical.com maverick Release [5,925B]
Ign http://archive.canonical.com maverick Release                       
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Get:12 http://archive.canonical.com maverick Release [5,925B]
Ign http://archive.canonical.com maverick Release 
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Hit http://archive.canonical.com maverick/partner i386 Packages
Hit http://archive.canonical.com maverick/partner i386 Packages
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:13 http://iq.archive.ubuntu.com maverick Release [39.8kB]
Err http://iq.archive.ubuntu.com maverick Release 
  
Get:14 http://iq.archive.ubuntu.com maverick-updates Release [31.4kB]
Err http://iq.archive.ubuntu.com maverick-updates Release
  
Fetched 1,385B in 23s (60B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 8DB7F87A2B97B7B8 Launchpad PPA for Mactel Support
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```I ran 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys

```for both keys, only one of them updated.

---

### Post by Onoku on 2011-05-14
Here is what the code looked like when I tried to update my keys

```
onoku@onoku-MacBook:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
[sudo] password for onoku: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
onoku@onoku-MacBook:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
onoku@onoku-MacBook:~$ 

```

---

### Post by mc4man on 2011-05-14
I'd try opening software sources, make sure 1st 4 are enabled in screen 1, the 2 in screen 2 and switch your server to either Main or United States, -  no matter what it's on now switch it.
Then click close and reload.
After open a terminal and run sudo apt-get update, then try to install whatever it is you wanted

---

### Post by Onoku on 2011-05-14
Thanks for the reply. I switched to the US server, which seemed to be progress. However when I reloaded, it downloaded a bunch of stuff, but I also got errors about my keys again.

```
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 8DB7F87A2B97B7B8 Launchpad PPA for Mactel Support
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Onoku on 2011-05-14
I went ahead and tried to install restricted extras and it seems to be working (downloading). I am worried my internet connection will drop before it is finished though.

---

### Post by mc4man on 2011-05-14
> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)

If you get a chance open up software sources > click on the authentication tab, go Alt+Print (Prnt Scrn button) and attach the screenshot to a post
Ex. attached

Edit: basically in your other post I believe you imported an incorrect key for the ubuntu repos, you should delete it and import the proper one
Though  I'd prefer to see what you have rather than say delete blah, blah

---

### Post by Onoku on 2011-05-14
I feel really stupid, but I can't figure out how to save my screenshot. I am using a mac so there is no print screen button. I used the "take screenshot" tool in applications instead, but after it takes the screen shot I don't know how to save it. >.<

edit: also, I can't open synaptic at the moment because my terminal window is still doin' it's thing with restricted extras.

---

### Post by mc4man on 2011-05-14
With that screenshot tool normally there is a pop up, if so just click on save. (it will go to your desktop
If trying the option to take a shot off a window then set a delay of several seconds.

Anyway - in the screen I posted you notice I highlighted the "Ubuntu Archive ..." listing
You may also have  one that says something like 'Ubuntu Extra...'
Highlight just the Ubuntu one and then click delete, you're okay on the 'Extra' one, leave alone 

( If you happen to have 2 of the same "Ubuntu Archive ..." listings, delete both 
Then close out software sources, open a terminal and use this

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

Then run sudo apt-get update

---

### Post by Onoku on 2011-05-15
So I woke up this morning and most of the restricted extras installed, but there were also several failures. I am at work now, so I will have to post the code later. I seem to be making progress though, as my computer prompted me for a ton of updates this morning as well. The screenshot tool had no pop-up, which is what confused me. I'll follow the instructions you just gave me when I get off of work.
 
Thanks for your help so far, mc4man.

---

### Post by Onoku on 2011-05-15
I followed your instructions, deleted the key, requested it again, then did update. It gave me the same errors as previously. 

Also, the update manager was working earlier, but now when I try to install updates, it gives me an error.

"The action would require the installation of packages from not authenticated sources."

Description:
```
alsa-utils app-install-data-partner apparmor apparmor-utils apport apport-gtk apt apt-transport-https apt-utils aptdaemon avahi-autoipd avahi-daemon avahi-utils bash-completion bind9-host brasero brasero-cdrkit brasero-common bsdutils compiz compiz-core compiz-gnome compiz-plugins computer-janitor computer-janitor-gtk cups cups-bsd cups-client cups-common cups-ppdc dbus dbus-x11 dhcp3-client dhcp3-common dnsutils dpkg empathy empathy-common evince evince-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins firefox firefox-branding firefox-gnome-support fuse-utils gcalctool gconf-defaults-service gconf2 gconf2-common gdb gdm gdm-guest-session gnome-keyring gnome-power-manager gnome-screensaver gnome-settings-daemon gnome-system-tools gnome-terminal gnome-terminal-data gvfs gvfs-backends gvfs-fuse gwibber gwibber-service hpijs hplip hplip-cups hplip-data humanity-icon-theme ibus ibus-gtk ifupdown indicator-application indicator-sound initscripts jockey-common jockey-gtk language-pack-en language-pack-gnome-en language-selector language-selector-common libapparmor-perl libapparmor1 libappindicator0.1-cil libappindicator1 libasound2 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libbind9-60 libblkid1 libbrasero-media1 libc-bin libc-dev-bin libc6 libc6-dev libcairo2 libcamel1.2-14 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdbus-1-3 libdecoration0 libdns66 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13 libevdocument3 libevolution libevview3 libfreetype6 libfuse2 libgconf2-4 libgcr0 libgdata-google1.2-1 libgdata1.2-1 libgexiv2-0 libglib2.0-0 libglib2.0-data libgp11-0 libgpod-common libgpod4 libgssapi-krb5-2 libgudev-1.0-0 libgvfscommon0 libhpmud0 libibus2 libisc60 libisccc60 libisccfg60 libjson-glib-1.0-0 libk5crypto3 libkrb5-3 libkrb5support0 liblcms1 libldap-2.4-2 liblwres60 libmagickcore3 libmagickwand3 libnautilus-extension1 libnss3-1d libpam-gnome-keyring libpam-modules libpam-runtime libpam0g libpango1.0-0 libpango1.0-common libparted0debian1 libpcsclite1 libperl5.10 libplymouth2 libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpoppler-glib5 libpoppler7 libpst4 libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libpurple-bin libpurple0 libsane-hpaio libslp1 libsmbclient libsqlite3-0 libssl0.9.8 libsyncdaemon-1.0-1 libtiff4 libudev0 libutouch-grail1 libuuid1 libvte-common libvte9 libwbclient0 libwebkit-1.0-2 libwebkit-1.0-common libxml2 libxml2-utils light-themes linux-firmware linux-generic linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic linux-headers-2.6.35-28 linux-headers-2.6.35-28-generic linux-headers-generic linux-image-2.6.35-22-generic linux-image-2.6.35-28-generic linux-image-generic linux-libc-dev login media-player-info mount nautilus nautilus-data nautilus-sendto-empathy nautilus-share ntpdate nvidia-96-modaliases openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer openssh-client openssl parted passwd perl perl-base perl-modules pitivi plymouth plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text pm-utils policykit-1 poppler-utils pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python python-appindicator python-apport python-apt python-aptdaemon python-aptdaemon-gtk python-avahi python-cupshelpers python-gnomeapplet python-gnomekeyring python-gtkspell python-ibus python-libxml2 python-minimal python-papyon python-problem-report python-ubuntuone-client python-uno python-vte python-wnck rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store rsync samba-common samba-common-bin simple-scan smbclient software-center ssh-askpass-gnome sudo system-config-printer-common system-config-printer-gnome system-config-printer-udev sysv-rc sysvinit-utils tar telepathy-gabble telepathy-haze tomboy transmission-common transmission-gtk ttf-opensymbol ttf-ubuntu-font-family tzdata ubufox ubuntu-docs ubuntu-sso-client ubuntuone-client ubuntuone-client-gnome udev uno-libs3 update-inetd update-manager update-manager-core upstart ure usb-creator-common usb-creator-gtk util-linux uuid-runtime vino w3m x11-xserver-utils xdg-utils xkb-data xserver-common xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-video-geode xserver-xorg-video-intel xserver-xorg-video-savage xul-ext-ubufox xulrunner-1.9.2
```


edit: I just tried to install GIMP just to see if it would work, and I got the same error.

---

### Post by Onoku on 2011-05-15
I am running

```
sudo apt-get update && sudo apt-get upgrade
```

It is installing stuff, so that might fix (part of) my issue.

---

### Post by Onoku on 2011-05-16
Due to a shoddy internet connection I haven't been able to run
 
```
sudo apt-get upgrade
```
 
without interruption. My download speed is like 6 kb/s so my 33.8MB download takes like 6 hours... my internet cuts out about every 20 minutes. Is there any way to do the upgrade in chunks?
 
Also, the key and package updater problems still exist, though I am hoping that somehow the upgrade will solve it.

---

### Post by Onoku on 2011-05-16
I was able to access faster internet and my problem was resolved after the upgrade. Thanks for the help. 

(not sure how to change the thread title to solved)

---

