---
title: "Okay... so what now?"
date: 2009-07-06
forum: General Help
---

### Post by Wyvernoid on 2009-07-06
Hello there. I, a linux noobie, am learning the ropes about linux things related to web hosting, and probably trying to build a small site where I could practice my PHP skills and such. So here I am, having installed (successfully, I guess) an Ubuntu Jaunty Server onto a VMware virtual machine, with everything like apache2 and php5 ready thanks to something called LAMP. I even got a small hello world PHP page up.

But the problem is, what do I do now? I mean, even if I build up a big site, how am I going to view it? Is it even possible to utilize a web browser in the command-prompt server Ubuntu? Anyway, I also have Ubuntu the desktop version installed on another VMware virtual machine, and I was wondering if there was a way that I could access the website in the server VM from the Firefox in the desktop VM. Does anyone have any idea how this might work?

---

### Post by LMZKJ on 2009-07-06
>>I mean, even if I build up a big site, how am I going to view it?

When you put in your virtual server, did you happen to setup networking?  If so, you should be able to reach the website from the host computers browser.

---

### Post by wojox on 2009-07-06
I don't run VM but as far as a server web browser enter

```
w3m
```

---

### Post by indytim on 2009-07-06
You are aware of the fact that you can run a LAMP installation effectively in Gnome, KDE etc. also?

```

$sudo tasksel

```

IndyTim

---

### Post by aromo on 2009-07-06
> **LMZKJ said:**
> >>I mean, even if I build up a big site, how am I going to view it?

When you put in your virtual server, did you happen to setup networking?  If so, you should be able to reach the website from the host computers browser.

Right, if you set up bridged networking, you should be able to browse your web server as if it were a physical machine plugged in to your LAN.

---

### Post by Wyvernoid on 2009-07-06
> **LMZKJ said:**
> When you put in your virtual server, did you happen to setup networking?  If so, you should be able to reach the website from the host computers browser.
> **aromo said:**
> Right, if you set up bridged networking, you should be able to browse your web server as if it were a physical machine plugged in to your LAN.
[IMG]http://i100.photobucket.com/albums/m25/Wyvernoid/network.png[/IMG]
Currently I have "NAT". Should I choose "Bridged" in this dialog and then go to the host computer to browse the site? Say the name of the server machine (set up during installation) is ubuserver, what should I type into the address box to browse the site that lies under /var/www?

---

### Post by Wyvernoid on 2009-07-07
*bump* Help anyone?

---

### Post by 3rdalbum on 2009-07-07
> **Wyvernoid said:**
> [IMG]http://i100.photobucket.com/albums/m25/Wyvernoid/network.png[/IMG]
Currently I have "NAT". Should I choose "Bridged" in this dialog and then go to the host computer to browse the site? Say the name of the server machine (set up during installation) is ubuserver, what should I type into the address box to browse the site that lies under /var/www?

From the description given on the screenshot, the NAT option should be fine.

In your Windows host, in your web browser, you can type:

```
http://localhost
```

and your page should come up, served from the virtual machine instance. If you want others to be able to see your page, they will need to type your external IP address like so:

```
http://210.50.105.151
```

You can find your external IP address from [www.whatismyip.com](www.whatismyip.com).

If your broadband router contains a firewall, you will need to set up port forwarding, so that incoming connections on port 80 will be routed to your computer. If you run a personal firewall, you need to set port 80 incoming to "allow".

---

### Post by Wyvernoid on 2009-07-07
I tried it, and the attempt to access [http://localhost/](http://localhost/) in the host computer (WinXP) resulted in the common "Can't connect to server" error. Using w3m in the server edition VM to access [http://localhost/](http://localhost/) turned out just fine. I even tried it on the Ubuntu desktop VM (with the same settings about NAT), still no luck. Any ideas why this is happening?

---

