---
title: "Transmission port forward/ everything using internet slowed"
date: 2010-05-16
forum: General Help
---

### Post by winchendonsprings on 2010-05-16
While I have Transmission running, whether it be up/downloading or just open with one thing unpaused and no activity, all other computer functions that need internet access are unusable.

Transmission says my port is closed in its preferences.

1. How do I find and open port?
2. Will finding an open port solve the problem of all things internet not working while Transmission is?
3. Do I need to create a static ip in order to forward a port through my router?
4. Will creating a static ip and forwarding that port solve my problem of only being able to use the internet while Transmission is on?

---

### Post by interceptorV8 on 2010-05-16
mine's been doing the exact same thing for the past few days.  i limit the up/down speeds so i can web surf without any lag in speed, however just simply having transmission open, everything requiring internet suffers.  pidgin frequently disconnects my accounts, web pages "cannot be displayed" thus requiring constant reloading, etc.  any ideas anyone?

---

### Post by 3rdalbum on 2010-05-16
Edit > Preferences > Network

Use UPnP port forwarding from my router

And then access your router's web-based configuration screen and make sure that UPnP is turned on there. You might need to restart the router afterwards, by turning it off and then on again.

I don't know if that will solve any problems regarding slow internet while Transmission is running, but you can try it anyway. It'll make your torrents faster at least.

---

### Post by scouser73 on 2010-05-16
+1 for UPnP on the router, the best advice for bit torrent.

---

### Post by warfacegod on 2010-05-16
All torrent clients will slow other Internet apps to one degree or another. Transmission is especially fond of this. I suggest Ktorrent or Deluge.

Here's a bit torrent guide: [http://ubuntuforums.org/showthread.php?t=1259923]("http://ubuntuforums.org/showthread.php?t=1259923")

---

### Post by Dessicus on 2010-05-16
I haven't had any noticeable slowdowns with Deluge yet.

---

### Post by interceptorV8 on 2010-05-16
it's just odd because i've been using transmission for the past year on 9.04 and 9.10 and it worked great.  actually i was using deluge before transmission and i was very fond of it until it started acting weird one day.  so i switched to transmission... it was flawlessly for until a few days ago (after i made the switch to 10.04), it starts slowing everything down even after restricting the up/down speeds.  

oh, and i checked my linksys router settings. Upnp was/is enabled.

---

### Post by winchendonsprings on 2010-05-16
same here. upnp was already on. 

can anyone answer my questions about port forwarding and static ip? it seems as though setting up a static ip is kind of strange since you can't have network-manager installed. 

am I right?

---

### Post by -humanaut- on 2010-05-16
sudo apt-get install deluge 

Solves all torrent related problems.

---

### Post by winchendonsprings on 2010-05-16
bump

---

### Post by interceptorV8 on 2010-05-16
winchendonsprings, i'm sorry that you haven't gotten the answers you wanted yet.  it may or may not help you to know that after checking my router settings, i restarted the router and the modem and so far transmission seems to be working fine at the moment.  it's no longer kicking me off pidgin or causing pages to not load.  <shrug>  but you've probably already thought of that...

---

### Post by Dessicus on 2010-05-17
Follow the link; select your router from the list, and then choose BitTorrent from the B section for a general guide to port forwarding with your router. When you set up port forwarding you can turn off UPnP.

[http://portforward.com/english/routers/port_forwarding/routerindex.htm]("http://portforward.com/english/routers/port_forwarding/routerindex.htm")

Here is an excellent guide for optimizing your torrents.

[http://ubuntuforums.org/showpost.php?p=7909527&postcount=1]("http://ubuntuforums.org/showpost.php?p=7909527&postcount=1")

---

### Post by warfacegod on 2010-05-17
I generally prefer KTorrent to Deluge. They are both relatively comparable in getting the job done and they are both ususally fairly faster than Transmission because of DHT. What counts for me is that KTorrent has more options and its much easier to setup DHT. Although Deluge has a nicer, more refined look to it. I *believe* they both have Automatic Port Forwarding. I know KTorrent does, at least, and that seems to be the simplest way to alleviate your Port issues.

Whatever you decide to do, I still suggest taking a good look at the link I posted in my first reply.

---

### Post by Dessicus on 2010-05-17
I like to use Deluge b/c its similar to uTorrent in design and functionality. When I followed the guide in my last post I was able to almost double my speeds. Your mileage may vary though.

---

### Post by warfacegod on 2010-05-17
Yeah, that's the same one I posted earlier.

---

### Post by winchendonsprings on 2010-05-17
Transmission says my port (default 51413) is closed.I cannot set up port forwarding on my router without a static ip says portforward.com. I cannot use my local ip (192.168.1.5) in the portforward settings.  I can see on my router page that I have set up other portforwarding from years ago with utorrent and azureus on a windows machine.


To enable Port forwarding I need to have a static ip, yes? 

I cannot have a static ip with network-manager installed, yes?

Can someone point me to a guide to set up a static ip? I have googled and searched but it seems you need to uninstall network-manager.

---

### Post by Dessicus on 2010-05-18
The static IP is set on the router for your computer's specific MAC address. Just set network manager to automatic in the IPv4 settings and then give your computer a static IP with your router.

---

### Post by winchendonsprings on 2010-05-18
I know this is very specific but maybe someone can help.

[http://farm5.static.flickr.com/4033/...aefcbe87_o.png]("http://farm5.static.flickr.com/4033/4618020982_3faefcbe87_o.png")

Here on my router I set my computer to 192.168.1.3 under Address  Reservation under LAN IP setup (Netgear smart wizard). I looked at  documentation and though all the menus and didn't see something for  static ip or fixed ip.

I set transmission to port 51416. and closed Transmission

With Ubuntu Network Tools it says that port is open as you can see.

I forwarded the port on the router for my ip i set up a second ago.

I reopen Transmission and check to see if the port is open  . . .  nah

---

### Post by warfacegod on 2010-05-18
It's possible that Transmission just isn't seeing that its open when it is.

---

### Post by Dessicus on 2010-05-18
Doing some google searching it looks like there might be a problem with the service name. I don't see why that would be a problem but it wouldn't hurt to change it.

Also you could try letting transmission find an open port automatically and then set your router to that port.

---

### Post by winchendonsprings on 2010-05-18
Even though I have tried and deleted other ports I cannot use the same service name again. Like Trans, Transmission, Tran, whenever I try to create a new port and name it Trans it says "**Service name already in use, and cannot be used twice." **Is there a way to clear the cache on a router? I don't know.

How would I go about letting Transmission find an open port? Choose random port on opening? I tried that and it found a closed port.

also, thanks for helping

---

### Post by Dessicus on 2010-05-18
In Transmission I tested the first port that showed up (51413) and it was closed. I then checked the port I'm using in Deluge (60730) and it was open. Maybe you should try that port. I'm not sure about the router cache so maybe you should change the name to BitTorrent or something. I noticed that in Deluge I have UPnP and NAT-PMP unchecked so try unchecking that in Transmission as well.

---

### Post by winchendonsprings on 2010-05-18
both 51413 and 60730  are closed according to transmission. with and without upnp ann natpmp checked.

blah

I like the simplicity and really simple gui of transmission.

---

### Post by Dessicus on 2010-05-18
Other than installing the latest release from the PPA (1.93) I don't know what else to try.

[https://edge.launchpad.net/~transmissionbt/+archive/ppa]("https://edge.launchpad.net/~transmissionbt/+archive/ppa")

---

### Post by SPARTAN-118 on 2010-05-22
Sorry, I can't help you very much, except to say that you should try forwarding (opening) your port in your router. 

The funny thing is, though I opened my port that Transmission uses using [this guide]("https://trac.transmissionbt.com/wiki/PortForwardingGuide"), DL speeds are still much slower than direct downloads (~50kb/s compared to +100kb/s).

But perhaps this is just the lack of seeders for some torrents?

---

### Post by Charles Kerr on 2010-05-30
If your router is still getting overloaded when running Transmission, try disabling DHT.  DHT is notoriously unforgiving to some routers. :/

---

