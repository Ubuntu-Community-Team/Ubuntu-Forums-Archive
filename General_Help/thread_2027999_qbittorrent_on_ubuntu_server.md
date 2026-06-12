---
title: "qbittorrent on ubuntu server"
date: 2012-07-17
forum: General Help
---

### Post by elliotbeken on 2012-07-17
Hi all,

I have a ubuntu server running 11.04 server (cli) 64-bit and i would like to know if i am able to run qbittorrent on a server install !

I would like to access the interface over the webui only...

Does anyone know how i have has a quick google with no luck

thanks

---

### Post by LewisTM on 2012-07-17
Install qbittorrent-nox, which provides the WebUI only. Both flavors share the same configuration and can be installed on the same machine but cannot run at the same time.

qbittorrent-nox is not a daemon, you have to run it at startup or in GNU screen session; it will listen on the designated port for incoming connections.

Cheers!

---

