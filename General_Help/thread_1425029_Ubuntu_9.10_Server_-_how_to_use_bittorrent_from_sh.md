---
title: "Ubuntu 9.10 Server - how to use bittorrent from shell"
date: 2010-03-08
forum: General Help
---

### Post by gottijr on 2010-03-08
I'm new to linux and try to make a ubuntu home server.

  1.One of my concerns is that i can't figure out how to use bittorrent (or any other torrent download application) from shell.

  Do you guys know if there is any tutorial for me to read that will help me understand how it works?

  (i have the desktop package installed but i don't wanne get used with that - or should i start the downloads from there but if I close the gdm (gdm stop) will my bittorrent stop as well?)

  any kind of advice will help alot.

  p.s. tried to google the topic but couldn't find much

---

### Post by Chris Musampa on 2010-03-08
RTorrent (in conjuction with Screen) works great for me, it can be set to watch a directory (just google .rtorrentrc)so you drop the torrents in there and off it goes.  I have it running on my media server and just access it through ssh, using Screen means rtorrent carries on when you disconnect your ssh session.

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by mk1w86 on 2010-03-08
If you want a simple bit torrent client that will run in a shell or you can access it via a web interface take a look at Transmission. I think the specific package you want is the daemon package from the repos.  The GUI version is actually included by default with a Ubuntu desktop install.

[http://www.transmissionbt.com/](http://www.transmissionbt.com/)

Run:

```
aptitude search transmission
```

to see the different versions available for install. ;)

---

### Post by sisco311 on 2010-03-08
+1 for rtorrent:
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

or you can use deluge:
[http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless-RC.html](http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless-RC.html)

---

### Post by Cas07 on 2010-03-08
> **sisco311 said:**
> or you can use deluge:
[http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless-RC.html](http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless-RC.html)

I personally suggest Deluge (v1.2.1). I tried several torrent clients and Deluge was the only one I could install and run without issue.

I have it running on a headless 9.10 server (same as above) and it works great with remote access through either the GTK GUI or any web browser along with the option of the dedicated console.

---

### Post by whoop on 2010-03-08
On the server:
```

sudo bash
aptitude install transmission-daemon
/etc/init.d/transmission-daemon stop
nano /etc/transmission-daemon/settings.json

```
make optional changes in settings.json

```

/etc/init.d/transmission-daemon start

```

You now have a daemon running which will start (by default) if you turn on the machine and starts downloading/uploading unless you tell it not to.

Use a web-browser on your desktop to access transmission web interface:
serverip:9091



Note, this info was out the back of my head, so check if I forgot something :D

---

### Post by gmargo on 2010-03-09
I'm sure the newer fancier tools work better, but it's worth pointing out that the original **bittorrent** code, written in python, has a text mode client.  Install the **bittorrent** package.

---

### Post by i.r.id10t on 2010-03-09
I use btdownloadheadless and a screen session...

---

### Post by cpressland on 2010-03-09
Personally, I love transmission-daemon, amazing client once you've got it working properly, personally I've setup everything up in '/home/torrents' and even kept the settings file there '/home/torrents/setting.json'

Set it up something like this:

```
{
    "alt-speed-down": 50, 
    "alt-speed-enabled": false, 
    "alt-speed-time-begin": 540, 
    "alt-speed-time-day": 127, 
    "alt-speed-time-enabled": false, 
    "alt-speed-time-end": 1020, 
    "alt-speed-up": 50, 
    "bind-address-ipv4": "0.0.0.0", 
    "bind-address-ipv6": "::", 
    "blocklist-enabled": false, 
    "dht-enabled": true, 
    "download-dir": "\/home\/torrents\/downloads", 
    "download-limit": 100, 
    "download-limit-enabled": 0, 
    "encryption": 1, 
    "lazy-bitfield-enabled": true, 
    "max-peers-global": 200, 
    "message-level": 2, 
    "open-file-limit": 32, 
    "peer-limit-global": 240, 
    "peer-limit-per-torrent": 60, 
    "peer-port": 58075, 
    "peer-port-random-high": 65535, 
    "peer-port-random-low": 49152, 
    "peer-port-random-on-start": true, 
    "peer-socket-tos": 0, 
    "pex-enabled": true, 
    "port-forwarding-enabled": false, 
    "preallocation": 1, 
    "proxy": "", 
    "proxy-auth-enabled": false, 
    "proxy-auth-password": "", 
    "proxy-auth-username": "", 
    "proxy-enabled": false, 
    "proxy-port": 80, 
    "proxy-type": 0, 
    "ratio-limit": 2.0000, 
    "ratio-limit-enabled": false, 
    "rpc-authentication-required": true, 
    "rpc-bind-address": "0.0.0.0", 
    "rpc-enabled": true, 
    "rpc-password": "removed", 
    "rpc-port": 9091, 
    "rpc-username": "root", 
    "rpc-whitelist": "127.0.0.1", 
    "rpc-whitelist-enabled": false, 
    "speed-limit-down": 100, 
    "speed-limit-down-enabled": false, 
    "speed-limit-up": 100, 
    "speed-limit-up-enabled": false, 
    "umask": 18, 
    "upload-limit": 100, 
    "upload-limit-enabled": 0, 
    "upload-slots-per-torrent": 14
}

```Then I just open transmission-daemon like this

```
transmission-daemon -g /home/torrents
```Then you've got an awesome WebUI that even works on iPhone and Android :)

---

### Post by gottijr on 2010-03-09
you guys are amazing. I wasn't expecting someone to answer my newbie questions but this is a great response.

  great support, great community thanks

---

### Post by gottijr on 2010-03-09
> **cpressland said:**
> Personally, I love transmission-daemon, amazing client once you've got it working properly, personally I've setup everything up in '/home/torrents' and even kept the settings file there '/home/torrents/setting.json'

Set it up something like this:

```
{
    "alt-speed-down": 50, 
    "alt-speed-enabled": false, 
    "alt-speed-time-begin": 540, 
    "alt-speed-time-day": 127, 
    "alt-speed-time-enabled": false, 
    "alt-speed-time-end": 1020, 
    "alt-speed-up": 50, 
    "bind-address-ipv4": "0.0.0.0", 
    "bind-address-ipv6": "::", 
    "blocklist-enabled": false, 
    "dht-enabled": true, 
    "download-dir": "\/home\/torrents\/downloads", 
    "download-limit": 100, 
    "download-limit-enabled": 0, 
    "encryption": 1, 
    "lazy-bitfield-enabled": true, 
    "max-peers-global": 200, 
    "message-level": 2, 
    "open-file-limit": 32, 
    "peer-limit-global": 240, 
    "peer-limit-per-torrent": 60, 
    "peer-port": 58075, 
    "peer-port-random-high": 65535, 
    "peer-port-random-low": 49152, 
    "peer-port-random-on-start": true, 
    "peer-socket-tos": 0, 
    "pex-enabled": true, 
    "port-forwarding-enabled": false, 
    "preallocation": 1, 
    "proxy": "", 
    "proxy-auth-enabled": false, 
    "proxy-auth-password": "", 
    "proxy-auth-username": "", 
    "proxy-enabled": false, 
    "proxy-port": 80, 
    "proxy-type": 0, 
    "ratio-limit": 2.0000, 
    "ratio-limit-enabled": false, 
    "rpc-authentication-required": true, 
    "rpc-bind-address": "0.0.0.0", 
    "rpc-enabled": true, 
    "rpc-password": "removed", 
    "rpc-port": 9091, 
    "rpc-username": "root", 
    "rpc-whitelist": "127.0.0.1", 
    "rpc-whitelist-enabled": false, 
    "speed-limit-down": 100, 
    "speed-limit-down-enabled": false, 
    "speed-limit-up": 100, 
    "speed-limit-up-enabled": false, 
    "umask": 18, 
    "upload-limit": 100, 
    "upload-limit-enabled": 0, 
    "upload-slots-per-torrent": 14
}

```Then I just open transmission-daemon like this

```
transmission-daemon -g /home/torrents
```Then you've got an awesome WebUI that even works on iPhone and Android :)

  thanks for the advice.

  That's the one i installed and it was easy. even for a newbie like me.

  second question - are you saying that you installed the actual application in /home or u are just keeping the settings file there?

  what is that -g command doing actually?

  thanks

---

### Post by gottijr on 2010-03-09
i'm still trying to figure out what is the -g command for 

  i installed transmission and have it running but i want to understand the -g command
 
  <code>
  transmission-daemon -g /home/torrents
  </code>

  if someone can explain something like the right steps or the best steps to fallow
   
  - install, stop process, vi settings, start ... that's all?

---

### Post by gottijr on 2010-03-16
> **Caos said:**
> I personally suggest Deluge (v1.2.1). I tried several torrent clients and Deluge was the only one I could install and run without issue.

I have it running on a headless 9.10 server (same as above) and it works great with remote access through either the GTK GUI or any web browser along with the option of the dedicated console.

  Can you please advice with an tutorial for that install?

  I'm still trying to make it work.

  quite difficult for some reasons

  ...

---

### Post by whoop on 2010-03-17
> **gottijr said:**
> i'm still trying to figure out what is the -g command for 

  i installed transmission and have it running but i want to understand the -g command
 
  <code>
  transmission-daemon -g /home/torrents
  </code>

  if someone can explain something like the right steps or the best steps to fallow
   
  - install, stop process, vi settings, start ... that's all?

well,
```

man transmission-daemon

```

returns (amongst other things):
> 
-g --config-dir directory
             Where to look for configuration files.  This can be used to swap
             between using the cli, daemon, gtk, and qt clients.  See
             [http://trac.transmissionbt.com/wiki/ConfigFiles](http://trac.transmissionbt.com/wiki/ConfigFiles) for more informa&#8208;
             tion.



If you are following cpressland's tracks, he probably just installed transmission-daemon from the repo's (sudo aptitude install transmission-daemon), created a user named torrents, added transmission config files to the home of torrents, and launched the daemon pointing to the config's (that's what -g is for)

---

