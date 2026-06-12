---
title: "Problem with magnetic links and qbittirrent"
date: 2012-06-30
forum: General Help
---

### Post by offir on 2012-06-30
i have ubuntu 10.04 
and qbittorrent ver 2.2.5 from the ubuntu software center 
i use firefox

and magnetic link dont work 
i get an error Message in firefox

:confused:

---

### Post by ubudog on 2012-06-30
I don't think qbittorrent supports magnet links. (**edit: it does, sorry!**)  I recommend you install Transmission, as according to [this]("http://www.makeuseof.com/answers/download-magnet-links-firefox-ubuntu/"), any version after 1.9 supports magnet links.  You can use their PPA to get the latest.

```
sudo apt-add-repository ppa:transmissionbt/ppa && sudo apt-get update; sudo apt-get install transmission
```

Best,
ubudog

---

### Post by offir on 2012-07-01
i know Transmission work with magnetic links
i have it

but i prefer qbittirrent
Is there a way to add this option

---

### Post by ubudog on 2012-07-01
Could you post the error Firefox is giving you?

---

### Post by offir on 2012-07-01
"Firefox doesn't know how to open this address, because the protocol (magnet) isn't associated with any program."

---

### Post by ubudog on 2012-07-01
Try this, in a terminal, to register the magnet protocol with Firefox:
```
gconftool-2 -s /desktop/gnome/url-handlers/magnet/command '`which qbittorrent` %s' --type String
```

```
gconftool-2 -s /desktop/gnome/url-handlers/magnet/enabled --type Boolean true

```

Then open Firefox, and type 'about:config' into the address bar and press enter.  Click the "I'll be careful, I promise!" button.

Then, do:

Right-click -> New -> Boolean -> Name: network.protocol-handler.expose.magnet -> Value -> false

Then the next time you open a magnet link, you should be asked which application should be used to open it.  

- [Source]("http://kb.mozillazine.org/Register_protocol")

---

### Post by haqking on 2012-07-01
qbittorrent does support magnet links

but not with your version of 2.2.5.

Update to latest version if i was you, you can download the deb from the site at
[http://www.qbittorrent.org/download.php](http://www.qbittorrent.org/download.php)

then choose linux and ubuntu from the options at the bottom (other binary packages)

Peace

---

### Post by offir on 2012-07-01
Thank you
This solved the problem

---

### Post by haqking on 2012-07-01
> **offir said:**
> Thank you
This solved the problem

no worries you are welcome.

Remember to use the thread tools menu to mark the thread as solved.

Cheers

---

