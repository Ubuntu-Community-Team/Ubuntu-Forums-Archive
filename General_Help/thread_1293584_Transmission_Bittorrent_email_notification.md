---
title: "Transmission Bittorrent email notification"
date: 2009-10-17
forum: General Help
---

### Post by conorgriffin on 2009-10-17
Hi guys, has anyone got any links or ideas on how I can get Transmission to send me an email when it completes a torrent?  I'm running it on the server version of Ubuntu so there's no GUI

---

### Post by lovinglinux on 2009-10-17
I'm not sure Transmission has this functionality, but you could do it with some workarounds.

Does Transmission allow to move the downloaded content once is completed? If yes then you could [install Specto](apt:specto), which is a little application capable of monitoring folder or file changes (web sites too). Set Specto to watch the folder where the completed torrents will be moved to by Transmission. Specto also allows you to specify a command to be executed when it detects changes inside the folder.

You can use a [sendemail](apt:sendemail) command, so whenever Specto detects changes in the folder it will send an e-mail. You could even create a script to list the contents of the folder and pipe it through sendemail.

Another option would be using Deluge BitTorrent client. You can run the daemon on the headless server and connect to it through cli, webui or even a gtk interface, which means you can see and manage your torrent list as if you were downloading locally.

I'm almost sure Transmission also has a webui, but Deluge gtk interface is way much better.

---

### Post by nikgare on 2009-10-17
Why not use the Transmission web interface?

---

### Post by Charles Kerr on 2009-10-21
> **lovinglinux said:**
> Does Transmission allow to move the downloaded content once is completed?
This feature is in the nightlies for 1.80, but is not in Karmic's 1.75.

---

### Post by Charles Kerr on 2009-10-21
> **conorgriffin said:**
> Hi guys, has anyone got any links or ideas on how I can get Transmission to send me an email when it completes a torrent?  I'm running it on the server version of Ubuntu so there's no GUI
I haven't used this myself, but in the wiki there's a script to do that: [http://trac.transmissionbt.com/wiki/Scripts/EmailNotifier](http://trac.transmissionbt.com/wiki/Scripts/EmailNotifier)

---

