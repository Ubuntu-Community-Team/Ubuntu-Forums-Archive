---
title: "Routing and Switching wiki/instructions not working and 2+ days been working on this"
date: 2011-10-02
forum: General Help
---

### Post by black07z51 on 2011-10-02
I'm running Ubuntu Server 10.4.3 with Gnome. I'm trying to build a replacement for a Linksys WRT54G basically.

Basically its been a bad week. 2 of my OpenWRT routers blew up and I can't afford to replace even that cheap of an object X( One literally started smoking so I have this pentium 4 @ 2.4GHz with 2 gigs of ram I was convinced would be easy to turn into a router/switch a couple days ago. It hasn't been. Its sporting 4 PCI NIC cards and a PCI Linksys Wifi card. I'm gaming here so I was thinking I might get more out of this thing than these POS Cisco devices I have been through 20+ of. I'll ghost this setup to a solid state even if I can get a solid foundation for something stable. I've played with the whole Ipcop, smoothwall, vyatta, etc. but configuration won't even work for those. I'm not some 01 idiot either but I'm 2+ days into this project and baffled (I can program in FORTRAN, Java, C++, Visual Basic, etc. etc. to give you an idea that I need basic instructions not necessarily spell it out for me since every instruction I have found is far outdated)

What I need:
-at the very least 2 NIC cards and the wifi all on a local network with a 3rd NIC outside my DMZ zone. I have one NIC working for internet but every time I mess with trying to setup serving the other computers IPs even the router/computer loses internet (I know I'm not picking on that interface but its not working like every tutorial I can find)

-a stable OS that I can leave on for at least a month without it crashing and preferably one that I can boot without a password needed, etc. to have my router working

 -I am hoping for some code to straight up copy and paste into my terminal to make it work. eth0 being the internet, eth2 being my main computer and eth4 being my other computer that holds a mirror of my files on eth2. Wifi is my Linux laptop. I can't get this working after 2 days and I am so stumped despite how much I have googled, how much I have searched these forums and the wikis on every site I can find... even an idea someone? It would be awesome if I could actually use all 4 NICs and the built in one to hook up all of my components again (xbox360 and some file servers that run stuff like Tivo, etc.) I just could really use getting my LAN for video games going again :-/

---

### Post by bodhi.zazen on 2011-10-02
First, you should not be running gnome, let alone X on a router.

Second, just use any of the firewall based distros, ip cop, google will give you a list.

---

### Post by black07z51 on 2011-10-02
Thanks for actually reading how Ipcop, etc. didn't work... I burned a whole spindle of CDs trying other distros and I know Ubuntu so I'd rather use it

---

### Post by bodhi.zazen on 2011-10-02
Well then all you need to do is learn iptables, in particular how to NAT.

Hard to give you specific advice without more details. What have you done ? What is your current set of rules on iptables ?

It really has noting to do with Ubuntu vs Fedora Vs ipcop, you still use iptables on all os.

---

### Post by dave01945 on 2011-10-02
have you tried this

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by Dangertux on 2011-10-03
As was stated already if you want to post your iptables script we might be able to help you better. If you have been following multiple tutorials, there is a good chance they are a big mess. There is also a chance you're probably just missing a rule or two, or your rules are out of order in the chain. If you want better help we need to see what the script you're using is.

If I understand correctly you're saying that when you activate dhcp you're losing internet connectivity. That leads me to believe your dhcp and or iptables configurations are probably borked.

The tutorial posted above is pretty decent, I would recommend starting with a fresh script, and instead of just copy and paste (not saying you did) but if you were, try to understand what each rule is doing, this will help you troubleshoot your issue a little better as well.

Also, as far as X if you're running X or Gnome just for the automatic login factor, all the necessary services for routing can be started at system run levels, so a user doesn't have to be logged in for them to run. You can safely ditch X and gnome unless you want it for some reason, other then the login.

Hope that helps.

---

