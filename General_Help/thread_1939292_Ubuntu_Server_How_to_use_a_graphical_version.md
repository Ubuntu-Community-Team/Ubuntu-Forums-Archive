---
title: "Ubuntu Server: How to use a graphical version?"
date: 2012-03-11
forum: General Help
---

### Post by Bruno81 on 2012-03-11
Hi.

I'd like to know if it's possible to add a graphical version to the Ubuntu Server (and also what to choose - for example lxde-).
Tnx so much for the answers!!!!!!
Best Regards.

---

### Post by oldfred on 2012-03-11
You can install the full desktop enviroments, but may not want all that.

The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)

sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
sudo service gdm start

But it looks like you can just install lxde which is just the desktop without all the extra applications.

From synaptic on my Ubuntu:
sudo apt-get install lxde

```

LXDE (the Lightweight X11 Desktop Environment) is a new project aimed
to provide a new desktop environment which is lightweight and fast.

This package is a metapackage depends on the core components and
recommended components of the LXDE. It includes lxde-core, lxappearance,
lxinput, lxsession-edit, lxshortcut, gpicview, lxterminal, lxmusic,
leafpad and xarchiver.

```

---

### Post by mcduck on 2012-03-11
> **Bruno81 said:**
> Hi.

I'd like to know if it's possible to add a graphical version to the Ubuntu Server (and also what to choose - for example lxde-).
Tnx so much for the answers!!!!!!
Best Regards.

Sure, all Ubuntu versions are one and the same operating system, the only difference is what's included by default. No matter which CD you use to make the install, you are free to run any server software or graphical environments and programs you want.

What desktop environment or window manager you should to use is pretty much a question of what you like, but if it's an actual production server then one of the more lightweight ones would probably be a good option. LXDE would sure be a decent one with fairly small footprint.

I recommend checking the different desktop environments (and window mansgers if you feel brave enough to configure your graphical environment by hand), and then just installing the one that you think you'd feel msot comfortable with.

---

### Post by TheFu on 2012-03-11
Ubuntu Server is extremely stable - many months of uptime.
However, if I install and use the desktop packages, the total stability is reduced to about 1 week and there are times when the OS simply locks up entirely.  Video playback is the chief issue with this stability that I see, but any X/Windows use negatively impacts server stability.

Having desktop "stuff" on a server is fine, as long as you understand the trade-offs.  I do it this way for non-production systems myself.  For servers that need to stay up, I do not install any desktop apps.

If you have a server that requires X/Windows libraries, there is a virtual X frame buffer tool, xvfb, that can simulate X for you on a server. This is handy if you need the server to have LibreOffice for file conversions, but don't want all the X/Windows instability issues.

---

### Post by mcduck on 2012-03-11
> **TheFu said:**
> Ubuntu Server is extremely stable - many months of uptime.
However, if I install and use the desktop packages, the total stability is reduced to about 1 week and there are times when the OS simply locks up entirely.  Video playback is the chief issue with this stability that I see, but any X/Windows use negatively impacts server stability.

Having desktop "stuff" on a server is fine, as long as you understand the trade-offs.  I do it this way for non-production systems myself.  For servers that need to stay up, I do not install any desktop apps.

If you have a server that requires X/Windows libraries, there is a virtual X frame buffer tool, xvfb, that can simulate X for you on a server. This is handy if you need the server to have LibreOffice for file conversions, but don't want all the X/Windows instability issues.
That doesn't really sound like it would be having the X or desktop stuff installed that is your problem. :D It's playing back videos (in which case it's a video card/driver problem instead, something that people don't usually need to consider that much on server machines..)

---

### Post by vikjon0 on 2012-03-11
Do not install the the -desktop packages they contain the full ubuntu application suite.
lxde is fine but if you want gnome you need to be more careful.
in 10.04 and earlier gnome-core is a great package but it got screwed up. Now you can use gnome-shell for gnome3 or gnome-session-fallback --no-install-recommends for gnome2.

---

### Post by drdos2006 on 2012-03-11
I would suggest you load Webmin on your server.

Logon to your server and download from your server with :
sudo wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb)

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000) to edit files, create shares, startup daemons, change permissions etc..

regards

---

### Post by Bruno81 on 2012-03-13
Hi again and tnx so much for this info that I found very interesting and usefull for me that I'm a newbie.

I'll set this topic as "solved" because the topic and my requests were too much various.....

So I'll open new threads during my learning process.....

Tnx again to everybody for the answers.

Best Regards.

---

### Post by Paqman on 2012-03-13
> **drdos2006 said:**
> I would suggest you load Webmin on your server.


This.

The desktop packages will give you a graphical environment, but they don't include many of the tools you need to administer a server. Webmin does.

---

