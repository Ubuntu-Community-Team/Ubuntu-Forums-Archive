---
title: "Cannot update Video Driver for advanced effects"
date: 2010-07-11
forum: General Help
---

### Post by himmelr on 2010-07-11
Hello, I just installed linux Mint 9, although I was having the same exact problem with ubuntu 10.04. Just testing mint out for a bit. I am running on the 64 bit OS. When I got to select advanced visual effects, It goes to enable the drivers but then I get this message. 

"SystemError: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_195.36.15-0ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_195.36.15-0ubuntu3_amd64.deb) 404  Not Found [IP: 91.189.88.45 80]"

It used to work before but then just stopped one day when I booted up. I use Docky, and it won't work without the drivers because it requires compositing to work properly. I am using a Nvidia GTX 260 video card if that has anything to do with it. Thank you.

Sorry if this is in the wrong place, I didn't know where else to put it.

---

### Post by yetiman64 on 2010-07-11
Just did a lookup on that address and the IP should be 67.215.65.132. Your ISP may be using an outdated DNS lookup list. You could consider changing to another DNS provider for example openDNS. Or alternatively add the line,
> 67.215.65.132 [archive.ubuntu.com]("http://archive.ubuntu.com/") to your hosts list.

with

```
gksudo gedit /etc/hosts
```and add in the above line just below your local machine entries (127.0.x.x). Format the new line added just like the lines above it.

If that doesn't work on the next attempt, remember to remove the extra line added to your hosts file.

---

### Post by himmelr on 2010-07-11
Thanks, I tried it but It still isn't working. Do I have to reboot? This is what my hosts file now says..

"127.0.0.1	localhost
127.0.1.1	ryan-desktop
67.215.65.132   [http://archive.ubuntu.com/](http://archive.ubuntu.com/)

> # The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts"

Thanks

---

### Post by yetiman64 on 2010-07-11
> **himmelr said:**
> Thanks, I tried it but It still isn't working. Do I have to reboot? This is what my hosts file now says.... I didn't think about having to reboot etc. Maybe you could try logout/login first, then maybe a reboot if that fails. Let us know how it goes as I can successfully ping the archive.ubuntu server at that IP address, whereas the original address gets no response at all.

[B]Also try removing the http first to leave only

> 67.215.65.132   archive.ubuntu.com if that works I'll edit the first post of mine to correct it.[/B]

---

### Post by himmelr on 2010-07-11
I rebooted and now my resolution is 600x800 i think. I tried your new post and it still didn't do anything. I am having trouble with installing the drivers. Im going straight to that and still getting the error.

---

### Post by yetiman64 on 2010-07-11
> **himmelr said:**
> I rebooted and now my resolution is 600x800 i think. I tried your new post and it still didn't do anything. I am having trouble with installing the drivers. Im going straight to that and still getting the error.

Sounds like to get hold of the drivers you will need to sort out some network issue first.
Unfortunately if changing to archive.ubuntu.com didn't work, you may have to wait for someone more experienced in networking to help, sorry.

Good luck.

---

### Post by himmelr on 2010-07-11
I my networking stuff is working great. I have downloaded many thing and I'm getting both the wireless and ethernet to work fine. The only problem is when trying to install the Nvidia drivers.

---

### Post by yetiman64 on 2010-07-11
> **himmelr said:**
> I my networking stuff is working great. I have downloaded many thing and I'm getting both the wireless and ethernet to work fine. The only problem is when trying to install the Nvidia drivers.

Try using System > Administration > Network Tools and ping the original IP in the error of yours, then do a lookup on [http://archive.ubuntu.com/](http://archive.ubuntu.com/) and note the IP address and then ping it.

You seem to have a DNS related error for the archive that is giving the error (the NVidia drivers), which is what I was trying to rectify with the hosts file. If you can't get it working just remove the line added to hosts and all is back how it was. 

Note your networking hardware is fine and not affected by such errors, also other archives/ servers can still work fine. Cheers, yetiman64.

---

