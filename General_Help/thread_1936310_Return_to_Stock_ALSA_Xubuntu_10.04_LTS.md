---
title: "Return to Stock ALSA Xubuntu 10.04 LTS"
date: 2012-03-05
forum: General Help
---

### Post by fleamour on 2012-03-05
How would I go about the above so as to file a bug report.  At the moment Apport will not file bug because of non standard package, I assume latest audio dev packages installed from following linky:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo add-apt-repository ppa:team-iquik/alsa; sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r) libasound2; sudo apt-get --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r)  libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```

I do get following return:

```
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-sound-base is already the newest version.
alsa-base is already the newest version.
alsa-utils is already the newest version.
gdm is already the newest version.
linux-image-2.6.32-39-generic is already the newest version.
E: Couldn't find package linux-alsa-driver-modules-2.6.32-39-generic
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-39-generic
pulseaudio: no process found
```
I am using Xubuntu 10.04 LTS.  Thank you.

---

