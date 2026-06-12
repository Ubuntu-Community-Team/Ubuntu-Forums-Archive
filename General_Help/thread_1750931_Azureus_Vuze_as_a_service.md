---
title: "Azureus Vuze as a service"
date: 2011-05-06
forum: General Help
---

### Post by Player-X on 2011-05-06
I'm trying to set up a torrent download/file backup server with Ubuntu desktop 11.04 and so far I have SSH and VNC access, I also have samba set up and Azereus directory settings just the way I want it, however I am having trouble getting Azureus to start as a service where I don't have to manually get into VNC and start Azereus every time this PC starts up.

I tried the guide found here to get Azereus set up and it appears that it hasn't worked for me:
[http://nerdica.com/?p=30](http://nerdica.com/?p=30)
> sudo cp ~/software/azureus/azureus /etc/init.d/
sudo chmod +x /etc/init.d/azureus
sudo update-rc.d azureus defaults


Is there anything I can do to install Azereus as a service in a similar way I had Firedaemon start uTorrent as a service when I was using WHS?

---

### Post by himraj13 on 2011-12-10
I tried the same on ubuntu server 11.10 but it didnt work for me.. the post was written in 2007 and after then Azureus has change to Vuze and it has got improved and changed the way could have been installed.

unfortunately being noob, I'm higly dependent on such guides.

if anyone can share some knowledge on how to setup torrent box, i would highly appreciate.

Thanks.

---

### Post by oldtimer7777 on 2011-12-10
> **himraj13 said:**
> I tried the same on ubuntu server 11.10 but it didnt work for me.. the post was written in 2007 and after then Azureus has change to Vuze and it has got improved and changed the way could have been installed.

unfortunately being noob, I'm higly dependent on such guides.

if anyone can share some knowledge on how to setup torrent box, i would highly appreciate.

Thanks.

Use rtorrent instead. It is much much better for what you are attempting to do.

[https://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](https://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

