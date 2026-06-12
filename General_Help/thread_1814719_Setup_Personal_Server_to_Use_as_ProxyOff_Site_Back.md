---
title: "Setup Personal Server to Use as Proxy/Off Site Backup"
date: 2011-07-30
forum: General Help
---

### Post by emagine on 2011-07-30
Hello all,

I have a simple issue that I think can be solved with several different methods.  I basically want to create a personal server solution that allows me to do two things:

1.) I want to be able to remotely backup data to my server.

2.) I want to be able to pass traffic through it and use it as a proxy.

I am off to college next year and I want to leave a computer/server back home to do the two things stated above.  I was thinking of using an Asus Eee Box PC like this:
[http://www.amazon.com/ASUS-EB1007-B0410-EeeBox-Mini-Desktop/dp/B004GVWJ44/ref=sr_1_3?ie=UTF8&qid=1312000374&sr=8-3](http://www.amazon.com/ASUS-EB1007-B0410-EeeBox-Mini-Desktop/dp/B004GVWJ44/ref=sr_1_3?ie=UTF8&qid=1312000374&sr=8-3)

I want a low power reliable machine that will only be used as a remote solution.  I won't be hooking up a monitor to it (that is, after I set it up).

It will be on 24/7 for easy access.

I will be accessing this server from a Windows 7 based machine.

I do not mind at all installing Linux on my server, but I am not an experienced coder so I will need software with a GUI that can help me set this all up.

All help is greatly appreciated!

---

### Post by 2F4U on 2011-07-30
As far as I can see there is no need for coding. You could get the Ubuntu Server edition (I would prefer the 10.04 LTS) and setup your server. I would suggest to do the setup without GUI, since you probably never need it. Then install Samba, the configuration for a home server is not that difficult. Windows works pretty good with Samba. If Samba is too much for you, you could also use just a ssh connection.

---

### Post by emagine on 2011-07-30
> **2F4U said:**
> As far as I can see there is no need for coding. You could get the Ubuntu Server edition (I would prefer the 10.04 LTS) and setup your server. I would suggest to do the setup without GUI, since you probably never need it. Then install Samba, the configuration for a home server is not that difficult. Windows works pretty good with Samba. If Samba is too much for you, you could also use just a ssh connection.
Will Samba allow me to pass traffic through it, using it as a proxy?

---

### Post by michaelb28 on 2011-09-01
Samba will allow you to access files that you store on your server.  But it is generally used within LANs, not over the internet. You might try tunneling Samba through OpenVPN with the bridged mode.  I've tried tunneling Samba through OpenVPN in the past though and the performance was rather slow.  I believe I was using routed mode instead of bridged, which might have slowed it down.

You can also setup OpenVPN to work as a proxy for web traffic. Of course there are other web proxy solutions out there, but OpenVPN has the benefit of encrypting the traffic as well. There's a few changes you have to make to the configuration file to get this to work, but it is certainly possible.

Personally, I prefer to access my files over SSH. It'll encrypt the traffic. Once you have SSH setup, you can access files on your server with Gui programs like WinSCP.

There's a program called Webmin that allows you to manage your Linux server through a web-browser interface.  I've never tried it. Basically, your server would have a certain web page that you'd access to manage your settings. But you can tunnel this traffic through OpenVPN or SSH if you want for security purposes.

There's still probably stuff you'd need to do on the command line, at least initially.

---

