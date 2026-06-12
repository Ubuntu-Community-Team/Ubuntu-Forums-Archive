---
title: "Ubuntu not running as it used to"
date: 2012-02-11
forum: General Help
---

### Post by louisgonick on 2012-02-11
Well, here I am back in the forum after months.

This week I booted up my machine to Ubuntu to work in some projects. It was pretty much as slow as windows is on my machine, it took about 40 seconds to boot up (compared to the 20 it took when it was brand new) and apps launched in about 5 or 7 seconds. I've always had issues with ubuntu since the day I installed it, it randomly froze and all I have left is to reboot (loosing all of my work). My WLAN card never worked properly and I have to turn it on manually. Lately my trackpad stops working and there is no way I can turn it on. Since 11.10 update manager has been acting strange, it wont fully update my system and always comes up with an error just before its done updating. 

My Ubuntu system has slowly become just like its opponent, cluttered, slow, and very crash prone.

Any suggestions?

---

### Post by Dlambert on 2012-02-11
UBUNTU TWEAK to clean it out!

---

### Post by Dlambert on 2012-02-11
BleachBit also works well if not better!

---

### Post by louisgonick on 2012-02-11
> **Dlambert said:**
> UBUNTU TWEAK to clean it out!

> **Dlambert said:**
> BleachBit also works well if not better!

Sorry, but in my months away from the Linux world I forgot where to find all the software... is it on the software center.

---

### Post by Dlambert on 2012-02-11
Google! Not sure if one software center

---

### Post by bluexrider on 2012-02-11
should be able to 

```
sudo apt-get install gnome-tweak-tool
```

---

### Post by louisgonick on 2012-02-11
> **bluexrider said:**
> should be able to 

```
sudo apt-get install gnome-tweak-tool
```

thanks, I still have trouble updating the OS though.

---

### Post by Dlambert on 2012-02-11
> **louisgonick said:**
> thanks, I still have trouble updating the OS though.

How so? try in terminal? ```
sudo apt-get upgrade
``` or ```
sudo apt-get dist-update
``` I believe those are the codes

---

### Post by louisgonick on 2012-02-11
> **Dlambert said:**
> How so? try in terminal? ```
sudo apt-get upgrade
``` or ```
sudo apt-get dist-update
``` I believe those are the codes

I get this:
Failed to download package files

Check your Internet connection.
Failed to fetch 
Details:
[http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser-l10n_15.0.874.106~r107270-0ubuntu0.11.10.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser-l10n_15.0.874.106~r107270-0ubuntu0.11.10.1_all.deb) 404  Not Found [IP: 91.189.92.176 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-codecs-ffmpeg_15.0.874.106~r107270-0ubuntu0.11.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-codecs-ffmpeg_15.0.874.106~r107270-0ubuntu0.11.10.1_i386.deb) 404  Not Found [IP: 91.189.92.176 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser_15.0.874.106~r107270-0ubuntu0.11.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser_15.0.874.106~r107270-0ubuntu0.11.10.1_i386.deb) 404  Not Found [IP: 91.189.92.176 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/nux/libnux-1.0-0_1.16.0-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nux/libnux-1.0-0_1.16.0-0ubuntu1_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/nux/libnux-1.0-common_1.16.0-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nux/libnux-1.0-common_1.16.0-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/unity/libunity-core-4.0-4_4.24.0-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/unity/libunity-core-4.0-4_4.24.0-0ubuntu2.1_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-services_4.24.0-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-services_4.24.0-0ubuntu2.1_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/unity/unity_4.24.0-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/unity/unity_4.24.0-0ubuntu2.1_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-common_4.24.0-0ubuntu2.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-common_4.24.0-0ubuntu2.1_all.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/nux/nux-tools_1.16.0-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nux/nux-tools_1.16.0-0ubuntu1_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.04~dfsg-0ubuntu11.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.04~dfsg-0ubuntu11.4_all.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_9.04~dfsg-0ubuntu11.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_9.04~dfsg-0ubuntu11.4_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.04~dfsg-0ubuntu11.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.04~dfsg-0ubuntu11.4_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.04~dfsg-0ubuntu11.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.04~dfsg-0ubuntu11.4_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_3.2.1-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_3.2.1-0ubuntu2.1_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evince/libevince3-3_3.2.1-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evince/libevince3-3_3.2.1-0ubuntu2.1_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evince/evince-common_3.2.1-0ubuntu2.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evince/evince-common_3.2.1-0ubuntu2.1_all.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_9.0.1+build1-0ubuntu0.11.10.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_9.0.1+build1-0ubuntu0.11.10.2_i386.deb) 404  Not Found [IP: 91.189.92.183 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_9.0.1+build1-0ubuntu0.11.10.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_9.0.1+build1-0ubuntu0.11.10.2_i386.deb) 404  Not Found [IP: 91.189.92.183 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_9.0.1+build1-0ubuntu0.11.10.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_9.0.1+build1-0ubuntu0.11.10.2_i386.deb) 404  Not Found [IP: 91.189.92.183 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_9.0.1+build1-0ubuntu0.11.10.2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_9.0.1+build1-0ubuntu0.11.10.2_all.deb) 404  Not Found [IP: 91.189.92.183 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.04~dfsg-0ubuntu11.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.04~dfsg-0ubuntu11.4_i386.deb) 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_8.0+build1-0ubuntu0.11.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_8.0+build1-0ubuntu0.11.10.1_i386.deb) 404  Not Found [IP: 91.189.92.183 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_8.0+build1-0ubuntu0.11.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_8.0+build1-0ubuntu0.11.10.1_i386.deb) 404  Not Found [IP: 91.189.92.183 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_8.0+build1-0ubuntu0.11.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_8.0+build1-0ubuntu0.11.10.1_i386.deb) 404  Not Found [IP: 91.189.92.183 80]

---

### Post by Dlambert on 2012-02-11
Are you connected to the internet? I know, dumb question. But maybe some settings are wrong, maybe delete the connection in settings and reset it to default, or try LAN/wifi?

---

### Post by louisgonick on 2012-02-11
> **Dlambert said:**
> Are you connected to the internet? I know, dumb question. But maybe some settings are wrong, maybe delete the connection in settings and reset it to default, or try LAN/wifi?

already deleted the network and re-connected and it doesn't even try to download updates... as soon as I try I get the same error message. This started happening since I updated to Oneiric back in October. Maybe it can be because my wireless card is not very friendly with ubuntu, I have to turn it on manually. 

Any suggestions?

possibly somethings wrong with the servers in canonical?

---

### Post by bluexrider on 2012-02-12
None of those archives are correct. There is an added portion to the link. 

all of the files are here:

[http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/](http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/)

You need to correct your PPA sources to reflect the correct one.

---

### Post by louisgonick on 2012-02-12
> **bluexrider said:**
> None of those archives are correct. There is an added portion to the link. 

all of the files are here:

[http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/](http://archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/)

You need to correct your PPA sources to reflect the correct one.

I tried adding it through system settings>software sources and it refuses to add the link you gave me.

---

### Post by bluexrider on 2012-02-12
I was pointing out that the files were at the link provided. It was not intended to be added to the software sources.list however, I can help you edit the list and make the correction.

Lets begin with posting the result of ```
cat /etc/apt/sources.list
``` so I can see what you got going on.

---

### Post by louisgonick on 2012-02-12
> **bluexrider said:**
> I was pointing out that the files were at the link provided. It was not intended to be added to the software sources.list however, I can help you edit the list and make the correction.

Lets begin with posting the result of ```
cat /etc/apt/sources.list
``` so I can see what you got going on.

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu oneiric main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric universe
deb-src http://archive.ubuntu.com/ubuntu oneiric universe
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu oneiric multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ec.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://ec.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb http://archive.ubuntu.com/ubuntu oneiric-security universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-security universe
deb http://archive.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.ubuntu.com/ubuntu oneiric-backports restricted main multiverse universe

```

---

### Post by bluexrider on 2012-02-12
I do not see any issues with the sources.list so lets clean the cache and remove any junk. 

Run each command separately and please post any errors 

```
sudo apt-get clean
``````
sudo apt-get autoremove
``````
sudo apt-get update
```

---

### Post by louisgonick on 2012-02-12
> **bluexrider said:**
> I do not see any issues with the sources.list so lets clean the cache and remove any junk. 

Run each command separately and please post any errors 

```
sudo apt-get clean
``````
sudo apt-get autoremove
``````
sudo apt-get update
```

I got it to update... thanks

---

### Post by bluexrider on 2012-02-12
Glad to get you going again. Please mark this one
(SOLVED)

---

