---
title: "Removing Google Chrome"
date: 2010-02-23
forum: General Help
---

### Post by chome4 on 2010-02-23
I cannot resize Chrome's overall size to half/quarter screen size etc....

So how can I remove it to start all over again?

---

### Post by jobix on 2010-02-23
If you used apt-get to install it, you can use this to remove it:

> sudo apt-get remove google-chrome


By default, the files are stored in /opt/google/chrome directory. So you could try deleting that directory entirely. However, there might some other files in your home directory. Typically these are "." files. So, look for something like .google or something and remove that.

---

### Post by chome4 on 2010-02-23
After typing: sudo apt-get remove google-chrome, I get:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package google-chrome is not installed, so not removed
The following packages were automatically installed and are no longer required:
  python-crypto python-zopeinterface python-twisted-names python-twisted-core
  libqimageblitz4 dvgrab ndiswrapper-common swh-plugins kdenlive-data kdenlive
  app-runner libmlt++1 realplay sun-java6-plugin python-twisted-web
  ubuntu-tweak libqt4-test libmono-zeroconf1.0-cil python-twisted-runner
  furiusisomount libqt4-core podsleuth disable-system-beep super-os-repo
  libkcddb4 libsox1 moonlight-opera libsnack2-alsa amsn inigo skype
  python-serial libqt4-xmlpatterns python-pam python-openssl
  python-twisted-mail libkonq5 amsn-data libtaglib2.0-cil python-twisted-lore
  python-twisted-conch python-pyopenssl python-twisted-news
  python-twisted-words ffmpeg libavfilter0 libboo2.0-cil recordmydesktop
  libsox-fmt-base fuseiso tcl8.5 libsox-fmt-alsa libavahi1.0-cil tk8.5
  libkonq5-templates ndisgtk gufw kdelibs libmlt-data tcl-tls
  python-twisted-bin libmlt1 libnotify0.4-cil libavdevice52
  ndiswrapper-utils-1.9
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
========================================

I don't understand how to use the 'apt-get autoremove' command.

---

### Post by zeroseven0183 on 2010-02-23
Type ```
man apt-get
``` in the Terminal, you'll see a brief description of

> 
**autoremove** is used to remove packages that were
           automatically installed to satisfy dependencies for some
           package and that are no more needed.
> **Michael.Godawski said:**
> Have a look here:
 
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=377542](http://ubuntuforums.org/showthread.php?t=377542)
[*][http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)
[/LIST]
 
  This command removes packages that were installed by other packages and  are no longer needed.

How did you install Google Chrome? But you can go to Synaptic Package Manager and look for Chrome, then mark the item for either reinstallation or complete removal, depends on you.

---

### Post by jobix on 2010-02-23
The fourth line in your message says:
Package google-chrome is not installed, so not removed

This means you did not use apt-get to install. That's why I said if you used apt-get then use ....

How did you install chrome?

I'm guessing manually. If so, at this point, you should try the manual removal method that I described above. Check to see if there is stuff in the /opt/google/chrome directory and in your home directory, and remove them.

> sudo rm -rf /opt/google/chrome


---

### Post by wojox on 2010-02-23
To use autoremove you just run:

```
sudo apt-get autoremove
```

As far as Chromium how did you install it?

---

### Post by chome4 on 2010-02-23
Synaptic got rid of it.

Thanks.

---

