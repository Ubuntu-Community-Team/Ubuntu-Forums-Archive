---
title: "utorrent remote"
date: 2012-02-28
forum: General Help
---

### Post by chimeradeimos on 2012-02-28
Hi

I want to completeley ove over to linux in my office, but over weekends i Use utorrent to download
and i use the remote login to add torrents from home and manage my downloads.

What i want to know, what client for ubuntu 11.10 is the easiest to configure like this and also I do not have
access to the router so i cant use a dyn-dns/no-ip account...

i allready tried vuze but the plugins dont work...

here is the web link to the utorrent remote where you just use a username and password to log into utorrent...

[https://remote.utorrent.com/](https://remote.utorrent.com/)

Thanks is advance

---

### Post by charlescarroll1 on 2012-03-13
I've never used it, but qBittorrent offers remote control through a web user interface. It can be found in the Software Center.

---

### Post by LewisTM on 2012-03-13
+1
I use the no-GUI qbittorrent-nox server and it works perfectly. You can also just enable the Web interface inside qbittorrent if it's already running. This requires that you open a port on the router that would lead to the web interface, typically 8081.

I use a complicated SSH approach to spawn and access the server which allows encrypted communication and authentication but you may not need this, at least not to try it out.

Cheers!

EDIT: Just looked at your link and saw that utorrent actually provides its own web service so you don't have to host your own server. Don't think anything in the Software center offers that. However, you can run utorrent under Wine.

---

### Post by chimeradeimos on 2012-03-14
Hi

I have tried running it in WINE, but the program launces but then i get no network access... =(

Going to reload my box to get rid of windows then going to try again with wine, Id have liked to use qtorrent but i dont have access to the router, as its a compane router...

---

### Post by trevolio on 2012-08-15
I would say the easiest way to start downloads would, if you have drop box, set your utorrent to auto add and start torrents from the drop box folder, then all you have to do it add torrent files into your dropbox from any computer or phone, and it will auto detect then and start the download.

---

