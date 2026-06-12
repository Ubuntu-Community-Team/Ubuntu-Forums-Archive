---
title: "how to install flash player on ubuntu 9.10 64 bit"
date: 2010-04-17
forum: General Help
---

### Post by mjsilverstri on 2010-04-17
Hi,

I have installed ubuntu 9.10 64 bit. 
Can you please tell me how can I install flash player? I only find ones for 32 bit.

Thank you.

---

### Post by blueridgedog on 2010-04-17
If you want a 64 bit version for Linux, there is a "alpha" release from Adobe:

[http://ubuntuforums.org/showthread.php?t=1435710](http://ubuntuforums.org/showthread.php?t=1435710)

---

### Post by oldos2er on 2010-04-17
[http://www.carleedolphinaura.co.cc/programming/adobe-flash-player-installer-uninstaller/adobe-flash-plugin-installer-uninstaller-linux](http://www.carleedolphinaura.co.cc/programming/adobe-flash-player-installer-uninstaller/adobe-flash-plugin-installer-uninstaller-linux)

---

### Post by chris.jericho on 2010-04-17
go into the ubuntu software center and type in flash and you will get an option.... click and install it

---

### Post by darolu on 2010-04-17
Well the Release Candidate is out now:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Download the tar.gz file.
If you have the 32 bits installed (the one you install with software centre, synaptic or aptitude) you will need to uninstall it first, open Synaptic, search for flashplugin and uninstall it, after that extract the tar.gz file and copy the .so file to /usr/lib/mozilla/plugins/

After that run:
```
$ /usr/lib/nspluginwrapper/x86_64/linux/npconfig -i /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by dcstar on 2010-04-17
> **darolu said:**
> Well the Release Candidate is out now:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
.........

That is **not** for 64-bit.

The only 64-bit plugin is still the prerelease at:

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

---

### Post by wojox on 2010-04-17
Just download from where dcstar's link and open a terminal:

```
cd to/where you/downloaded
```

```
sudo tar xzf libflashplayer*
```

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```

---

### Post by Yellow Pasque on 2010-04-17
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by Native Dialect on 2010-04-17
best way to get flash capability for your system is to enter the following commands in the terminal. 

First command:

sudo apt-get remove flashplugin-*--purge

Second command:

sudo apt-get install flashplugin-nonfree

Just make sure you are online (obviously). Alternatively, you can go to Applications>Add/Remove

Search for "Adobe Flash" and you can get the actual Adobe Flash. It is a bit problematic though when it comes to GNU/Linux functionality. The choice is yours.

---

### Post by oldos2er on 2010-04-17
"sudo apt-get install flashplugin-nonfree" unfortunately only gets you 32-bit flash; 64-bit flash is not yet in the repositories.

---

### Post by WinterRain on 2010-04-18
> **oldos2er said:**
> "sudo apt-get install flashplugin-nonfree" unfortunately only gets you 32-bit flash; 64-bit flash is not yet in the repositories.

I don't know why it is not in the repos. It works better than the 32bit version for us 64 users.

---

### Post by blueridgedog on 2010-04-18
I am curious to know when Ubuntu will embrace the 64 bit flash from Adobe so we can drop these various how-to's regarding their test releases.

---

