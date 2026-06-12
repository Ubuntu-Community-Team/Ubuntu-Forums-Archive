---
title: "Ubuntu Server Virtualbox on Windows 7 PC"
date: 2011-02-14
forum: General Help
---

### Post by stangdaman on 2011-02-14
I built a new desktop with a large amount of storage space (6TB)fairly recently and tried out WHS for a little while on it. I liked the way it automatically backed up my other PCs on me network and some of the other web features but I ended up installing Windows 7 instead so that I could use the media extender features and some of the other things that were not available with WHS.

I'm pretty inexperienced with server OS but just have been kind of missing some of that functionality. Could someone maybe give me some idea of how similar, in terms of features, Ubuntu server is to WHS and could I possibly run it on something like virtualbox on my Windows 7 PC?

---

### Post by cariboo on 2011-02-14
The ubuntu server, is more of a do it yourself setup, there isn't a gui, as it is meant to run headless. During installation, you can add the services you need.

---

### Post by stangdaman on 2011-02-14
So, there would be services you could run to back up the other PCs on the network, windows, mac, linux whatever? Would it run well on something like virtualbox on a Windows 7 PC or would that cause too many complications?

---

### Post by sydbat on 2011-02-14
> **stangdaman said:**
> So, there would be services you could run to back up the other PCs on the network, windows, mac, linux whatever? Would it run well on something like virtualbox on a Windows 7 PC or would that cause too many complications?I wouldn't run a server in a virtual environment. There are too many limitations. However, if you ran Windows virtually *on a server*, you would probably be better off.

---

### Post by stangdaman on 2011-02-15
I don't know. I have a feeling that things like the extender service and mediacenter would have issues running in a virtual environment. The office stuff would run fine I'm sure. I have Windows running on Virtualbox on my Ubuntu laptop and it runs fine but in that particular case the laptop has a lot more memory and I'm not running those types of graphic intensive applications.

---

### Post by stangdaman on 2011-02-16
I don't know if I'm using the correct terminology or not. I think I am more looking for something just to manage storage and serve files to my home network not necessarily a web server. Not that having some web services wouldn't be nice but it's not primarily what I'm looking for here. Would something like Amahi or FreeNAS work better for that?

---

