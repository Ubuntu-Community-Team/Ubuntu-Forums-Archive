---
title: "Video Problem?"
date: 2006-06-10
forum: General Help
---

### Post by SPlutard on 2006-06-10
When I try to play video in Totem, it says it cannot play the file because: "There were no decoders found to handle the stream, you might need to install the corresponding plugins". I assume this should be a relatively easy problem to fix, but I have no idea how. If I do, indeed, need some plugins, where do I get them and what do I do with them, 

Alternatively, I also got the VLC Media Player, which will open files, but will not show any video for some reason. It'll play the audio perfectly, but no picture is displayed. I've fiddled with the menus & settings all I dare, but to no avail. 

Any help (with either one)? All I want to do is be able to play videos....

Thanks
SP

---

### Post by zugu on 2006-06-10
Totem is a movie player. In the Linux world, behind players are the platforms. By default in Ubuntu, gstreamer stands behind Totem.
For almost any type of file, gstreamer has a plugin. So if you have let's say a swf plugin for gstreamer, Totem can play swf (Flash) files.

For further information about getting gstreamer to work, visit this link:

[http://help.ubuntu.com/ubuntu/desktopguide/C/codecs.html](http://help.ubuntu.com/ubuntu/desktopguide/C/codecs.html)

However, you might give xine, vlc or mplayer a try. You can find these movie players in the repositories. Note that vlc has no need for external codecs - it has them built in, so it should be able to play everything out of the box.

Note that some video files that use proprietary codecs might need the w32codecs package.

Go [here]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restrictedformats%29#head-68524fab57e2285050069d6845f95415f8ec8404") for more information.

---

### Post by SPlutard on 2006-06-10
These were not in the Synaptic Package Manager:
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

I searched but didn't fine them. I did find, however, that I have current versions of every "gstreamer0.8" installed already. 

I took your advie about the restricted codecs & entered:
wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb) 
sudo dpkg -i w32codecs_20050412-0.4_i386.deb

in a terminal, but it doesn't seem to have helped.

Also, as far as VLC Media Player goes, here's how it looks when I open a video in it:

---

### Post by taurus on 2006-06-10
I recommand you use Automatix to install codecs, plugins, media players for your Dapper.  You can find the link that explains everything here...

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

---

### Post by zugu on 2006-06-10
If you have the 0.8 version of gstreamer, it might be because you use Ubuntu 5.10, a.k.a. Breezy Badger. You posted in a Dapper Drake forum (this is the latest release of Ubuntu linux) so I assumed you use Dapper.

For Breezy Badger, use this link: [http://help.ubuntu.com/5.10/ubuntu/faq/C/sect-music-and-movies.html#codecs](http://help.ubuntu.com/5.10/ubuntu/faq/C/sect-music-and-movies.html#codecs)
I hope this helps.

As for VLC, I have no idea why is it working like that.

---

### Post by SPlutard on 2006-06-10
Oh, I feel like an idiot; sorry. Thanks again for the help both of you.

On another note: is there an easy way to upgrade to the newest realease, Dapper Drake? Or would that involve saving all my data externally & installing to new release, effectively starting from scratch?

---

### Post by zugu on 2006-06-10
You shouldn't feel like an idiot, because there's no reason to.
Try opening a thread for each problem you have. This way it's easyer to get help.

My guess is that though the Ubuntu developers have designed an upgrading system that works very well, nothing is to be taken for sure. You should ALWAYS backup your work, data and/or sensitive information, or otherwise be prepared to lose it. You never know what can happen. So, after you backed up your files, try this:```
apt-get update
apt-get dist-upgrade
```Depending on your internet connection, it may take from 30 minutes to an hour. Afterwards, you'll have a nice shiny Dapper. Post on these forums if you encounter problems during the upgrade.

---

### Post by taurus on 2006-06-10
[QUOTE=zugu]You shouldn't feel like an idiot, because there's no reason to.
Try opening a thread for each problem you have. This way it's easyer to get help.

My guess is that though the Ubuntu developers have designed an upgrading system that works very well, nothing is to be taken for sure. You should ALWAYS backup your work, data and/or sensitive information, or otherwise be prepared to lose it. You never know what can happen. So, after you backed up your files, try this:```
apt-get update
apt-get dist-upgrade
```Depending on your internet connection, it may take from 30 minutes to an hour. Afterwards, you'll have a nice shiny Dapper. Post on these forums if you encounter problems during the upgrade.[/QUOTE]
Before you run those two commands from a terminal, you need to edit your /etc/apt/sources.list and replace breezy with dapper.  Then, update and upgrade...

---

### Post by SPlutard on 2006-06-11
Man, zugu: you're awesome! I really really appreciate all of your help and patience. I managed to get that long list downloaded, and now I can play video fine  (*knock on wood*). Again: you're awesome.

One last quick question: if I do upgrade to DD, will I be undoing all my work? That would kinda suck, but I guess DD is worth it. If I can't play videos again after, I'll just follow the instructions you gave in the first place.

Thanks a lot!
Sturgis

---

### Post by SPlutard on 2006-06-11
[QUOTE=taurus]Before you run those two commands from a terminal, you need to edit your /etc/apt/sources.list and replace breezy with dapper.  Then, update and upgrade...[/QUOTE]

Forgive me, but how? Terminal code/link?

---

### Post by Chris03 on 2006-06-11
sudo gedit /etc/apt/sources.list

Then change all breezy to dapper.

sudo apt-get update
sudo apt-get dist-upgrade

:)

---

### Post by maddbaron on 2006-06-11
did u manage to get the vlc player to work? i have the same exact problem as u. audio fine. video not showing. 

anyone else know how to get it fixed?

---

### Post by blackjack6.21.91 on 2006-06-11
After you update to Dapper Drake, your work should not be lost, you should just be running newer versions of everything (with your configuration the same).

> Originally Posted by taurus
Before you run those two commands from a terminal, you need to edit your /etc/apt/sources.list and replace breezy with dapper. Then, update and upgrade...

I have heard more recently that that is the more correct method to take.  To edit your sources.list, use this command (change gedit to kate if you use kde)

> sudo gedit /etc/apt/sources.list

That will open a file with your current sources.list.  You can make a new one [here.]("http://www.ubuntulinux.nl/source-o-matic")

---

