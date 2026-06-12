---
title: "New nvidia drivers in PPA?"
date: 2010-10-15
forum: General Help
---

### Post by spoon_ on 2010-10-15
Nvidia released some new drivers 2 days ago (260.19.12). Does anyone know if the nvidia-current package in Maverick, which currently has version 260.19.06 (beta), will be updated with the new drivers?

I'm experiencing some video-related funkiness and I'd like to try the new drivers to see if they'll fix it. So my question is will the PPA drivers eventually be updated or should I uninstall them and install the new ones manually?

---

### Post by Quackers on 2010-10-15
260.19.12 was in my updates tonight. I've run it and all is well with it here :-)

---

### Post by spoon_ on 2010-10-15
Strange, what server do you use? I'm not seeing it.

---

### Post by Quackers on 2010-10-15
Server for United Kingdom

---

### Post by Quackers on 2010-10-15
I'm on 64 bit, if that makes any difference.

---

### Post by spoon_ on 2010-10-15
Oh yeah I'm on 64-bit too. I'm just trying to figure out which of the UK servers is shown to UK people as "Server for United Kingdom". So now I'm trying a bunch of UK servers! But thanks for the tip.

---

### Post by Quackers on 2010-10-15
You're welcome :-)
Sorry but I can't offer any advice about the specific server.

---

### Post by spoon_ on 2010-10-15
Oh maybe you can see it when you do "sudo apt-get update"? When I do that, I see the server I chose. For example, the last line is

```
Hit http://ubuntu.positive-internet.com maverick-backports/universe amd64 Packages

```

Thanks.

---

### Post by Quackers on 2010-10-15
Heres my last line 
```
Hit http://gb.archive.ubuntu.com maverick-backports/universe amd64 Packages
```

---

### Post by spoon_ on 2010-10-16
Ah, that's not one of the ones listed under UK, and I don't know how to enter a new server manually. I guess I'll just wait for the update to propagate to all the other servers. Thanks for your help.

---

### Post by Quackers on 2010-10-16
Me neither :-(
I'm sure it won't be long though.

---

### Post by spoon_ on 2010-10-16
Actually is it possible that you got it from some third-party PPA? Do you subscribe to this one, for example? [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+build/2003978](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+build/2003978)

---

### Post by Quackers on 2010-10-16
It'll be this one
X Updates ([http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) maverick)

---

### Post by spoon_ on 2010-10-16
Yep, got it, thanks.

---

