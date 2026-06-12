---
title: "wget and lynx proxy problems"
date: 2011-02-06
forum: General Help
---

### Post by daniel.jimenez on 2011-02-06
I have just installed the lynx web browser since i will be having to work on a very small bandwidth connection in the following months, probably through a vpn, and it just seemed like a good idea.

however, i encountered a problem when trying to test drive it. No matter what setting I choose on 'System/Preferences/Network Proxy' it always tries to connect to the proxy server i have configured. That is, it appears to be ignoring the selected proxy setting even after i click on 'Apply System Wide'.

If I connect to the vpn which actually requieres the proxy settings it connects without a problem, as it should. The problem also happens on wget and it doesn't happen on chrome, firefox, synaptic or apt-get, which i find strange.

Any help would be really appreciated.

---

### Post by runeh76 on 2011-02-06
You cannot connect to a remote server for a command session via lynx - you should be looking towards ssh.

---

### Post by daniel.jimenez on 2011-02-06
thanks for the quick reply.

I actually use ssh a lot to connect to the server at work. This problem, however, is quite different.

Right now, at home, with the proxy settings set to direct internet connection, lynx *still* tries to connect through the proxy settings.

wget seems to do the same thing.

Any ideas as to why or how to fix it?

If I VPN to work, it connects correctly even if I don't select the proper system proxy settings. i.e. the rest of the programs can't connect (since they shouldn't) and lynx can (but it should not).

---

### Post by runeh76 on 2011-02-06
Does this help? [https://help.ubuntu.com/community/SSH_VPN]("https://help.ubuntu.com/community/SSH_VPN")

---

### Post by runeh76 on 2011-02-06
Try to make a new direct connection and delete that proxy one..?

---

### Post by daniel.jimenez on 2011-02-06
Not really, but I really appreciate your help.

I'll try to be really clear here, be sure to ask any thing that isn't perfectly clear from my writings please.


--I'm not using a proxy or a VPN right now, altough I do it regularly.

--Every other program I use (chrome, firefox, apt-get, etc), *except* from wget and lynx, works and respects the settings from the Network Proxy app.

--The problem with lynx (and wget, apparently) is that they try to connect through a proxy *even if the network proxy settings are turned off*.

in other words, it should just try to connect to the internet, and it tries to use a proxy. Since there is no proxy server on my home network, it can never connect.

Does the above make any sense?

Again, many thanks.

---

### Post by daniel.jimenez on 2011-02-06
> **runeh76 said:**
> Try to make a new direct connection and delete that proxy one..?

I just tried that, it still tries to connect through the proxy.

It seems as though there is a variable that should change when you choose a given setting in the gnome Network Proxy app that somehow isn't.

---

### Post by runeh76 on 2011-02-06
Do u have network-manager?

---

### Post by daniel.jimenez on 2011-02-06
At the top bar of my screen there is an applet called NetworkManager Applet 0.8.1. Did you mean that?

If I just write network-manager at the command line it just mentions that the command was not found and it doesn't recommend any packages.

---

### Post by runeh76 on 2011-02-06
Yes! Use that to create direct connection, and remove that gnome Network Proxy app

---

### Post by daniel.jimenez on 2011-02-06
I was looking at this bug report
[https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469](https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469)

Which seems to be related, as my problem also arises on wget, and I noticed some people saying they only had the problem when running the command with sudo (which I wasn't). I tried to run Lynx with sudo and ir worked correctly.

Still can't tell whats wrong... maybe something in .bashrc or some other configuration file?

anyone knows about the HTTP_PROXY environmental variable? could it be related?

I really don't know enough at that part of the linux system.. I'm only a fortran programmer looking for help and i'm glad to be getting it.

---

### Post by runeh76 on 2011-02-06
Did u tryed that network-manager?

U have created in the wrong place ur connection.

---

### Post by daniel.jimenez on 2011-02-06
I currently have ubuntu 10.10

the network proxy setting is located on the menu "System/Preferences/Network Proxy" on my computer.

The bug i previously linked talks about a syntax problem or something like that on /etc/environment... seems kind of obscure, but i'll have a look anyway.

---

### Post by runeh76 on 2011-02-06
Yeah u shouldnt use that. Use network-manager!

---

### Post by runeh76 on 2011-02-06
Check what u get from terminal

```
gksudo gedit /etc/network/interfaces
```

There should be only this:

auto lo
iface lo inet loopback

---

### Post by daniel.jimenez on 2011-02-06
yes, that's exactly what i get.

I'll try to find a way to reset my network config. right now lynx works if i run it as sudo but i'd rather not have to.

---

### Post by runeh76 on 2011-02-06
Okey good. I dont know anymore other tricks, so i wait curiously  result :)

reset all network settings:
[http://ubuntuforums.org/archive/index.php/t-441480.html]("http://ubuntuforums.org/archive/index.php/t-441480.html")

---

### Post by daniel.jimenez on 2011-02-06
alright i thing i got it working.

I followed directions at the bugreport I previously posted. Had to run sudo visudo and add some defaults (it's all explained there) to make run correctly.

Even then, changing the network config once and then changing back to default means I have to log off to reset some environmental variables. But it works now!

thanks a lot.

---

### Post by daniel.jimenez on 2011-02-06
> **runeh76 said:**
> Okey good. I dont know anymore other tricks, so i wait curiously  result :)

reset all network settings:
[http://ubuntuforums.org/archive/index.php/t-441480.html]("http://ubuntuforums.org/archive/index.php/t-441480.html")

wow, that's a pretty elegant way to reset!

i'll be doing that tomorrow and see if that helps with the need to log off and on when I disconnect from vpn. it's not really a big problem as i only do it twice a week, but it'd be nice.

keep up the good work!!!

---

### Post by runeh76 on 2011-02-06
Nah i didnt do nothing, just google assistant  :)

I just havent never used that network proxy app to connect net, and just thought that might be the problem, if that app leaves some "hidden"settings even if u dont want them, like proxy.

Yeah try network-manager and let us know if that was a solution.
Its good to learn new things, and im trying my best to help what i know.

Cheers and have a nice day!  :)

---

