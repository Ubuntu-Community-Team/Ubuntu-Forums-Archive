---
title: "DivX for Linux! The Ultimate Question"
date: 2005-03-17
forum: General Help
---

### Post by rudeboyskunk on 2005-03-17
I've downloaded the .tar.gz file.  I've uncompressed it.  I've gone into the created folder and did the whole chmod a+x install.sh and then ./install.sh.  It thought for a few seconds, then just came up with another prompt.  NOW, I've been told this means all is well.  However, when I start Totem and try to play .avi files, ones I know to be supported by DivX4Linux, they won't play.  Plus, there is no list of divx plugins in my about: plugins thing in mozilla or firefox.  Must I do something to Totem/Mozilla/Firefox?  Is there some small file hidden somewhere deep in /usr/bin or some other obscure place that I need to hunt down and tell Totem that that's a plugin file?  Or are there more repositories for Warty than what the installation cd gives, and some of these have access to a .deb setup for DivX4Linux that does it all?

---

### Post by bored2k on 2005-03-17
[QUOTE=rudeboyskunk]I've downloaded the .tar.gz file.  I've uncompressed it.  I've gone into the created folder and did the whole chmod a+x install.sh and then ./install.sh.  It thought for a few seconds, then just came up with another prompt.  NOW, I've been told this means all is well.  However, when I start Totem and try to play .avi files, ones I know to be supported by DivX4Linux, they won't play.  Plus, there is no list of divx plugins in my about: plugins thing in mozilla or firefox.  Must I do something to Totem/Mozilla/Firefox?  Is there some small file hidden somewhere deep in /usr/bin or some other obscure place that I need to hunt down and tell Totem that that's a plugin file?  Or are there more repositories for Warty than what the installation cd gives, and some of these have access to a .deb setup for DivX4Linux that does it all?[/QUOTE]
 add this line to your repositories:
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Update, then 
sudo apt-get install w32codecs mozilla-mplayer xine-ui totem-xine vlc-esd vlc-plugin-esd

that should get you covered.

---

### Post by rudeboyskunk on 2005-03-18
Awesome!  Thanks a bunch.

---

### Post by bored2k on 2005-03-18
[QUOTE=rudeboyskunk]Awesome!  Thanks a bunch.[/QUOTE]
 No probs . Your turn next time someone has that problem ;).

---

### Post by A-star on 2005-03-18
You can also take a look at the following page:
[http://www.ubuntuforums.org/showthread.php?t=18443](http://www.ubuntuforums.org/showthread.php?t=18443)

it explains how to install mplayer, which can play everything.

---

### Post by bored2k on 2005-03-18
[QUOTE=A-star]You can also take a look at the following page:
[http://www.ubuntuforums.org/showthread.php?t=18443](http://www.ubuntuforums.org/showthread.php?t=18443)

it explains how to install mplayer, which can play everything.[/QUOTE]
 Its a lot easier to apt-getting. And btw, mplayer is nothing without its codecs.
Now vlc DOES play everything with a single install.

---

### Post by RastaMahata on 2005-04-08
I've gotta say taht totem-xine is hell a lot better now than mplayer, and even looks better... any way I can implement it with firefox?

---

