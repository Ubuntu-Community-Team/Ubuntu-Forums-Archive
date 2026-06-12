---
title: "mobile pre usb 200f problem"
date: 2012-07-07
forum: General Help
---

### Post by artofshred87 on 2012-07-07
i plugged all my stuff in and it seems to be working fine i can listen to music with my headphones plugged into the  mobilepre and it seems to register sound my problem is i can only hear my guitar through my headphones very faintly. Any ideas?




ok soi was following this guide and i  screwed something up the liitle speaker icon on my task bar dissappeared and when i go to system settings-sound-hardware there are no devices under hardware. what did i do? heres what i was following.


I was recently gifted a badass ["M-Audio Mobilepre" USB Pre-amp]("http://www.m-audio.com/products/en_us/MobilePreUSB.html")  by a buddy of mine so i could learn to play the bass in the comfort of  my own home. All was fine and well when we used it in Windows to record  with [Audacity]("http://audacity.sourceforge.net/"),  but when i attempted to use it on Ubuntu Linux, i couldn't hear  anything i was plugging into the Pre-amp sound card. I found some  threads regarding the older versions of this card and how to use [madfuload]("http://usb-midi-fw.sourceforge.net/") to load the appropriate firmware to support the cards. Thing is, my version is 200F and should be "plug-n-pray".
After much searching, i figured out that it was due to [Pulseaudio]("http://en.wikipedia.org/wiki/PulseAudio") yet again.
In this article, i will show you how to remove [Pulseaudio]("http://en.wikipedia.org/wiki/PulseAudio"), and replace it with [ALSA]("http://www.alsa-project.org/main/index.php/Main_Page") packages. After which, you will be able to get the mono inputs on the [M-Audio Mobilepre USB]("http://www.m-audio.com/products/en_us/MobilePreUSB.html") card to come out the stereo output on the back of the card.
1) Kill pulseaudio
# sudo killall pulseaudio
2) Uninstall pulseaudio
# sudo apt-get purge pulseaudio
3) Remove gstreamer pulseaudio support
# sudo apt-get remove gstreamer0.10-pulseaudio
4) Restart
# sudo reboot
5) Install replacement mixers (to control your sound)
# sudo apt-get install xfce4-mixer aumix-gtk
After installation, you may find them in Ubuntu Menu:
Applications -> Sound & Video -> Mixer
Applications -> Sound & Video -> aumix
6) Download Debian package "gnome-control-center" from Ubuntu 9.04 Repositories
32bit:
# wget [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_2.26.0-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_2.26.0-0ubuntu3_i386.deb)
64bit:
# wget [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_2.26.0-0ubuntu3_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_2.26.0-0ubuntu3_amd64.deb)
7) Extract both deb packages and data.tar.gz
# ar p capplets-data_2.26.0-0ubuntu3_all.deb data.tar.gz | tar zx
# ar p gnome-control-center_2.26.0-0ubuntu3_i386.deb data.tar.gz | tar zx
8) Install "gnome-sound-properties" into Ubuntu 9.10
# sudo cp usr/bin/gnome-sound-properties /usr/bin
# sudo mkdir /usr/share/gnome-control-center/glade/
# sudo cp usr/share/gnome-control-center/glade/sound-properties.glade /usr/share/gnome-control-center/glade/
9) Configure Gnome Sound Settings
# gnome-sound-properties



i only got up to step 5 because the links in step 6 did not work, i just noticed this was for an older version of ubuntu so how do i reinstall what i deleted?

---

