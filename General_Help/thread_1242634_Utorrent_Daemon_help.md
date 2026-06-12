---
title: "Utorrent Daemon help"
date: 2009-08-17
forum: General Help
---

### Post by grubia on 2009-08-17
Hello all,
I'm new to ubuntu and I need help creating a daemon.
My idea is to start utorrent at startup before starting the X.
I want to use its webui among with xbmc (gnome is not started).
So i wrote a script:
sudo -u <my user> screen -d -m -t utorrent-daemon /usr/local/bin/wine /usr/local/bin/utorrent.exe

when i run the script from shell as ./script it runs perfectly and ui is working (gnome is stoped with sudo/etc/init.d/gdm stop)
but i cannot make the script to execute at system startup from init.d
So can someone please help me acomplish this?
Thanks

---

### Post by Grenage on 2009-08-17
While I don't know how to advise you on utorrent, is there any reason not to use th. Deluge daemon, or rtorrent?

---

### Post by Bradj47 on 2009-08-17
Why not just System -> Preferences -> Startup Applications?

---

### Post by karlmp on 2009-08-17
don't use utorrent

wine is not perfect

rtorrent, transmission, deluge, etc... are better than utorrent

---

### Post by Bradj47 on 2009-08-17
> **karlmp said:**
> don't use utorrent

wine is not perfect

rtorrent, transmission, deluge, etc... are better than utorrent

I agree. I use Deluge.

---

### Post by Grenage on 2009-08-17
Yup; rtorrent + rssdler = sexy.

---

### Post by grubia on 2009-08-17
I'm using deluged with deluge webui now.
The reason for using utorrent is nice webui and ability to add .torrent files from windows machines directly without having to open ui, click browse and etc ... just click on torrent and choose open with utorrent adder.
If anyone can suggest similar program or script that will autoadd torrents to deluge ui from windows i'll continue using it.

---

### Post by Grenage on 2009-08-17
Deluge likely supports folder scanning, so any torrents thrown in there will be added.  I use that in rtorrent.

---

### Post by grubia on 2009-08-17
yes, but i cannot chose destination folders if i use automatic download ...

---

### Post by Grenage on 2009-08-17
Do you have a different destination folder per torrent? Or just a handful that a handful or torrents go into?

wtorrent is a really nice front end for rtorrent, web-based and very configurable.

---

### Post by grubia on 2009-08-17
i'll check it, thank you

---

### Post by Grenage on 2009-08-17
No problem.  If you get stuck anywhere along they way, please post back; I've not much experience with wtorrent, but I've dabbled with rtorrent plenty.

---

