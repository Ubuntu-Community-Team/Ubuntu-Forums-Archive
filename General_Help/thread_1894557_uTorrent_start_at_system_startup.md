---
title: "uTorrent start at system startup"
date: 2011-12-12
forum: General Help
---

### Post by JoeGoalie on 2011-12-12
I'm using Ubuntu Server 10.04 and I have got uTorrent (the linux version) working on it just fine.  I even was able to use [this guide]("http://www.webupd8.org/2011/02/start-utorrent-server-as-daemon-with.html") to make utorrent a daemon service.  However, the service still doesn't start at system boot up.  I still have to login and sudo start utorrent.   That isn't exactly an ideal situation for a server setup...  Any help would be greatly appreciated.  Thanks.

---

### Post by oldtimer7777 on 2011-12-12
> **JoeGoalie said:**
> I'm using Ubuntu Server 10.04 and I have got uTorrent (the linux version) working on it just fine.  I even was able to use [this guide]("http://www.webupd8.org/2011/02/start-utorrent-server-as-daemon-with.html") to make utorrent a daemon service.  However, the service still doesn't start at system boot up.  I still have to login and sudo start utorrent.   That isn't exactly an ideal situation for a server setup...  Any help would be greatly appreciated.  Thanks.

I recommend you use the linux native version of that exact same application instead:

```
sudo add-apt-repository ppa:hydr0g3n/ppa 
sudo apt-get update && sudo apt-get install qbittorrent
```It is essentially the same application as utorrent, but it was actually designed to be used with Linux, from my experience with both.  And you have much better results too.

After you get that installed don't forget to install moblock:

```
sudo add-apt-repository ppa:jre-phoenix/ppa 
sudo apt-get update sudo apt-get install moblock blockcontrol mobloquer
```

---

### Post by JoeGoalie on 2011-12-13
> **oldtimer7777 said:**
> I recommend you use the linux native version of that exact same application instead:

```
sudo add-apt-repository ppa:hydr0g3n/ppa 
sudo apt-get update && sudo apt-get install qbittorrent
```It is essentially the same application as utorrent, but it was actually designed to be used with Linux, from my experience with both.  And you have much better results too.

After you get that installed don't forget to install moblock:

```
sudo add-apt-repository ppa:jre-phoenix/ppa 
sudo apt-get update sudo apt-get install moblock blockcontrol mobloquer
```

The reason I want uTorrent is familiarity (I used it heavily in Windows) its nice remote app for android, and because I can import my settings.dat and my rss.dat.  I mainly use it to monitor rss feeds and download new tv shows when they come out.  I'll look into qbitorrent, but if it doesn't do rss, it's a no go.  I've noticed that about a lot of other torrent clients.

---

### Post by JoeGoalie on 2011-12-13
> **oldtimer7777 said:**
> I recommend you use the linux native version of that exact same application instead:

```
sudo add-apt-repository ppa:hydr0g3n/ppa 
sudo apt-get update && sudo apt-get install qbittorrent
```It is essentially the same application as utorrent, but it was actually designed to be used with Linux, from my experience with both.  And you have much better results too.

Ok, now that I've installed it, how can I get it to run at startup?  This still leaves me with the same issue, I have to login and start it manually.

---

### Post by papibe on 2011-12-13
Without the intention of creating more confusion... I have had excellent results using transmission-daemon. By default it is added as a service at startup.

Just a thought.
Regards.

---

### Post by JoeGoalie on 2011-12-15
Well, I got utorrent to start on bootup, sort of... I moved the utorrent directory to /use/share/utorrent and modified my /etc/init/utorrent.conf accordingly. It starts, but the webui is broke. That's when i realized it is recreating all the settings.dat and RSS.dat in the ~/ directory and that's why it can't find the webui.zip file. So, how can I get a startup .conf file to cd to the proper directory first? I tried just adding cd /use/share/utorrent to the .conf file and every time I invoke start utorrent it starts and immediately stops again. Any ideas?

---

