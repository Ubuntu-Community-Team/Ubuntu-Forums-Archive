---
title: "Mozilla Flashplayer Plug-in/Upgrade Problems"
date: 2011-10-07
forum: General Help
---

### Post by ricarpe on 2011-10-07
Mozilla Firefox has disabled Flash plug-in.  I am using Firefox version 3.6.23 Mozilla Firefox for Ubuntu canonical - 1.0. I'm running Ubuntu Linux 10.04.

I have searched this forum and several other sites.  I've removed, copied, uninstalled, reinstalled, installed, deleted, and copied and moved again the libflashplayer.so file.  I've downloaded the Flash file from Adobe about 6 times.  I've tried using the terminal window, the Update Manager, Synaptic, and just updating through Firefox.  

I'm at a loss.  I use my laptop to watch my grad classes -- I'm an online student.

Can anyone help me with updating/upgrading Flash on Firefox.

PS: Updating is not an option for me since my version came with Linux, so I have to wait for a special update.

---

### Post by Frogs Hair on 2011-10-07
The first thing I would do is install a newer version of Firefox , see the link. [http://palupix.blogspot.com/2011/10/how-to-install-firefox-7-in-ubuntu-1004.html](http://palupix.blogspot.com/2011/10/how-to-install-firefox-7-in-ubuntu-1004.html)
Next , install Flash Aid and use it to install the latest version of flash .[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by ricarpe on 2011-10-07
@ Frogs Hair: I was able to update Firefox to 7.0.1, which is an amazing improvement over the older version I was stuck with.   I also added the Flash-Aid plug-in, which will hopefully prove a nifty tool in the future.

However, still no joy on using Flashplayer.  As a test, I went to YouTube.com and clicked on a video. Nothing loads up in the Player's screen area except for the message:

You need to upgrade your Adobe Flash Player to watch this video. 
 [Download it from Adobe.]("http://get.adobe.com/flashplayer/")

I go to the link, which gives me only one option: APT for Linux 10.04.  I go through the process but have nothing.

Thank you for your help, though.  It is appreciated! :)

Rich

---

### Post by Xiph on 2011-10-08
I've also got the same problem as you describe. Since the last update flash stopped working. Though I'm using Kubuntu, but it shouldn't be a difference right?

I've tried using the following browsers with the same result:
[LIST]
[*]Chrome 14.0.835.202
[*]Chromium 12.0.742.112 (90304) Ubuntu 11.04
[*]Firefox 7.0.1 for Ubuntu canonical 1.0
[*]Rekonq 0.7.0
[/LIST]

I've hade this problem once before, happend when I updated to Natty I belive. But it started working after a while when there was a new update for flash. Now it stopped working with the newest update. Seems to work with every second update :-s

---

### Post by Xiph on 2011-10-08
Yay, got it working. Just removed flash and installed it again:
Just do following (maybe you don't have both installed)

```
apt-get remove flashplugin-nonfree
apt-get remove flashplugin-installer

apt-get install flashplugin-nonfree
```

---

