---
title: "need help getting packages.medibuntu.org karmic release to work"
date: 2009-12-13
forum: General Help
---

### Post by orin zolis on 2009-12-13
i ran this in my terminal for ubuntu karmic koala 32. **sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar**

this is what happened:[B] Kunin: 183 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) karmic-updates/multiverse Sources [1,744B]Nakakuha ng 1,190kB ng 49710d 5h 0min 0s (0B/s)
Binabasa ang Listahan ng mga Pakete...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: Ang sumusunod na mga lagda ay hindi maberipika dahil ang public key ay hindi available: NO_PUBKEY 2EBC26B60C5A2783
sudo: timestamp too far in the future: Dec 13 16:44:34 2009
[sudo] password for shaw: 
[/B]
can someone help. now im new to ubuntu and appreciate any help with this. and if u cant help can u tell me weather or not i have to keep this terminal open untill i get the problem sorted cos an error hapend when i tryed to instal it on my other computer and i lost the terminal window and had no idea how to acces it at the same point of the pakage agian. however im further this time so i dont want to screw it up again :)

---

### Post by MelDJ on 2009-12-13
try the link in my sig

---

### Post by fancypiper on 2009-12-13
# Add medibuntu sources latest release
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

---

