---
title: "Network Manager ignores eth0"
date: 2011-10-25
forum: General Help
---

### Post by arodulfo on 2011-10-25
Dear all,

After upgrading from XUbuntu 11.04 to 11.10, I can no longer browse the web.
It took me half an hour (I'm close to a newbie) to see something was happening to NetworkManager and its manoeuvres.

I have no NetworkManager icon in the notifications area of the upper panel and *Applications / System / Network connections* simply ignores *eth0*, even after trying to include it in the list of interface it shows. No way!

I temporarily solved the matter by manually editing */etc/resolv.conf* and including two DNS addresses there. That's how I have been able to get here and leave this post.

However, as soon as I reboot the system, NetworkManager wipes that file out and there we go, right to the first box.

Does anybody have any hint?
Thanks in advance.

---

### Post by garvinrick4 on 2011-10-25
Try this and see if helps get you a network manager.

```
sudo apt-get install --reinstall network-manager
```
```
sudo /etc/init.d/network-manager restart
```

---

### Post by arodulfo on 2011-10-25
Dear **garvinrick4**,

Thanks for being there.

I have just done it, according to your hints.

As soon as network-manager restarts, once it has been reinstalled (no errors or other claims here), it wipes out */etc/resolv.conf* and makes the browser unable to do its job.

I'm quite sorry it didn't work.

Any other idea?

---

### Post by arodulfo on 2011-10-25
Dear **garvinrick4**,

In fact, there's been a change: Now I have an icon in the upper panel, but the changes do end there.

What a pity!

UPDATE: After a reboot, the icon is out again, and /etc/resolv.conf is empty again.
I'm not happy!

---

### Post by BeRA on 2011-10-25
now this may be a bit illogical, but something similar happened to me on 100% fresh ubuntu 11.10 install (I had an icon, but it couldn't connect to anything). I managed to connect using pppoeconf and after I tried many things to fix my Network Manager and failed - I simply decided to reinstall everything and it worked :S Don't ask me how :) Maybe if everything else fails it could be worth trying...

---

### Post by garvinrick4 on 2011-10-25
If you manually install your isp manually it works. Then it runs until your reboot and you
lose connection. So you need to figure out why you are not getting info from isp to your
computer. Cable must be good because you can stay online. I will be back I have to go 
look at a cabled system in another room. Will be something simple I am sure. A setting
will be wrong.

---

### Post by garvinrick4 on 2011-10-25
So you have can go to Edit connections in network manager. Then click on tab
wired connection then highlight auto etho and edit connections and box is checked that says
automatic and then in ipv4 it is set at automatic DHCP.

---

### Post by arodulfo on 2011-10-26
Dear **garvinrick4**,

As per the beginning of the thread, I said I already was browsing, uploading and downloading files, emailing and so on.

Given the fact this is a desktop PC, I set up a static IP for it in */etc/network/interfaces*:
```

auto lo
iface lo inet loopback

#ethernet static details
auto eth0
iface eth0 inet static 
    address 192.168.1.3 
    netmask 255.255.255.0 
    gateway 192.168.1.1
    network 192.168.1.0
    broadcast 192.168.1.255


```

As I already said, even if I manually edit */etc/resolv.conf* to include the *nameserver* addresses, as soon as I reboot the system or restart network-manager, it wipes those addresses out.

To make things even funnier, I can state some things:

[LIST]
[*]the icon in the right side of the upper panel appears when (and only when) I go to a terminal and restart the service; of course, it claims the interface is not connected and so on
[*]no matter if I use *Auto DHCP* or *Manual* for the IPv4 settings (I triple-checked that the details I enter in *Manual* are correct and complete), Network Manager keeps claiming there's no connection and the interface I set up with it is never used
[*]as long as NM is saying its bla-bla, if I use a console and ping the router, or another PC in my LAN, or whatever web in the net, I have no problems to reach them, provided the namerserver addresses are in *resolv.conf*
[/LIST]
I have even restarted the router itself. Sometimes in the past, I have noticed some problems (glitches or conflicts) affect its DHCP capabilities. No way! After having it back to life and checking everything again, the problem is still there.

Thanks for all your help

---

### Post by garvinrick4 on 2011-10-26
```
lspci -nnk | grep -iA2 net
```
Lets look at card and driver.
Everytime network manager go's down for reboot it makes a new connection and gets its
default route and such. You are obviously not getting them. So lets see if has happened before you to card and driver. Got to be something going on does just not work for no
good reason. Would like to find out why?

---

### Post by arodulfo on 2011-10-26
Dear garvinrick4,

> Would like to find out why?
I completely agree on that with you. In fact, given the fact linux sessions can be quite lengthy (in terms of weeks or even months) before a reboot is needed, I could simply apply that temporary solution and forget about the question or, even better, uninstall network manager and get rid of the problem. However, by doing so I would never go beyond the problem and would miss a very good chance to learn.

Following your instructions:

```
~$ lspci -nnk | grep -iA2 net

01:04.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
    Subsystem: Hewlett-Packard Company Device [103c:1246]
    Kernel driver in use: 3c59x

```Does it pour any light on the problem for you?
I deeply hope so!

BR.

---

### Post by arodulfo on 2011-10-30
Does anybody have anything to say about it?
I am seriously thinking of installing the system from scratch, since the upgrade doesn't seem to be as stable as it should.

Regards.

---

### Post by grahammechanical on 2011-10-30
May I add something to the mix? People can and no doubt will, correct me if I am wrong but I do not think that Network manager uses the /etc/network/interfaces file. Putting anything in it other than

auto lo
iface lo inet loopback

will prevent Network manager from doing its stuff.

Remove the additional stuff. Reboot and use network manager to set things up the way you want.

Regards.

---

### Post by cbowman57 on 2011-10-30
[FONT=monospace]Try setting managed=true in your /etc/NetworkManager/NetworkManager.conf[/FONT]

---

### Post by arodulfo on 2011-10-30
Dear grahammechanical,

Even if I tend to disagree with you at first, what you say makes sense.
My disagreement comes from the fact the whole thing has been working perfectly to the moment I upgraded from 11.04 to 11.10.

I'm spending a couple of days far from the "problem" PC. As soon as I get back, I'll try your suggestion and report the results over here.

Kind regards,:P

---

### Post by arodulfo on 2011-10-31
Dear cbowman57,

As soon as I'm back home, I'll try your hint as well.

THX:P

---

### Post by arodulfo on 2011-11-16
Dear all,

After several useless experiments, trying to explore whatever hints you gave to me, I decided to boldly attack the problem: I have reinstalled XUbuntu 11.10.

Now, the problem is out, along with some other minor ones that seemed to be plaguing the upgraded system.

Now, all the notification icons are in place, the Network Manager window reports the network interface quite precisely, and I have all my samba shares up and running.

I'm afraid I did it the wrong way, but I consider the problem SOLVED.

Kind regards to everyone.

---

### Post by cbowman57 on 2011-11-16
Sometimes a fresh installation is best. :)

---

