---
title: "Remote Ubuntu 10.10 Server CLI VNC install"
date: 2011-02-09
forum: General Help
---

### Post by xlilcasper on 2011-02-09
Did the title make sense? I thought not.

I just got a remote ubuntu server online running 10.10 server. Ordered it from a host and it's all setup and running. I thought, great, a box I can throw maybe a game server on, have something I can log in remotely too when needed and something to just generally play around with.

I would like to VNC into it instead of always using the CLI to get things done. I like pretty pictures, they give me warm fuzzes inside. So I set about setting up a VNC server. 

I looked for about two days trying to find a guide or information on it as this is a very bare bones server and I haven't had any luck. The I know I'm doing something wrong and my newbieness is showing but I just can't seem to figure it out.

I know I need to have an xserver up and going and I know I need the vnc server to connect to that. All the guides I've been finding seem to start with changing a setting for xdmcp by clicking on .... see my problem? no gui to start with. As of right now I have reinstalled the OS and the only command I have run so far is 

apt-get update
apt-get install gnome-core

Any help at all where I should go from here would be greatly appreciated. I'm at a loss and am pulling my hair out.

---

### Post by xlilcasper on 2011-02-09
Fixed it by following this guide.

[http://havetheknowhow.com/Configure-the-server/Install-VNC.html](http://havetheknowhow.com/Configure-the-server/Install-VNC.html)

Worked great.

---

