---
title: "How to use SSH with Remote Desktop"
date: 2010-05-23
forum: General Help
---

### Post by Axilus on 2010-05-23
Hey guys,

Recently I have setup my laptop to be able to connect to my home PC from school using Remote Desktop (By fowarding port 5900); however I would really rather be using Remote Desktop with some sort of security layer.

I have followed [this guide]("https://help.ubuntu.com/community/VNC") however nothing works, the closest I get is,'Cannot create SSH tunnel: permission denied.' I have registered a dns called axilus.ath.cx as the tutorial recommended but that didn't make a difference.

Does anyone have a simple and straight forward way to setup secure Remote Desktop?

---

### Post by CharlesA on 2010-05-23
I guess you mean you want to tunnel VNC over SSH.

Forward whatever port SSH is running on to the outside world and then see if you can SSH in. If you can, create a tunnel that points to the machine's ip address on port 5900.

I needed to install tightvnc server on the box I wanted to VNC into, since Vino (the remote desktop server for ubuntu wouldn't launch until after logon).

---

