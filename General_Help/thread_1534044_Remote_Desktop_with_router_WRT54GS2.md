---
title: "Remote Desktop with router WRT54GS2"
date: 2010-07-18
forum: General Help
---

### Post by SpenceMakesSense on 2010-07-18
I recently got a new router (and new isp). On my old isp and router it seemed quite simple to remote desktop to my linux box from any of my windows xp  machines using vnc. 

After I got my new router(WRT54GS2) and pretty much at the same time upgraded to 10.04 I had went back to reconfigure it. I simply cannot find a way to make this work. On the old version of ubuntu the remote desktop settings had a choice to change the port which seemed like the key ingredient to make it work when I was having troubles before. This new version seems verrry dumbed down to me and I can't seem to get anything to work. :confused::confused:

I read some tutorials and all I've seen is to change port forwarding settings on my router(i'll include a picture of what that looks like) If anyone has gotten this to work and can give me some tips I would GREATLY appreciate it.

---

### Post by SpenceMakesSense on 2010-07-19
bump

---

### Post by SpenceMakesSense on 2010-07-20
bumpin

---

### Post by Sam Lars on 2010-07-21
Are you sure that you can access your computer from the outside, maybe on other ports? Last time I had an ISP change I was no longer able to do that (I'm evdently behind a second router).
I'll look at the VNC settings...

---

### Post by SpenceMakesSense on 2010-07-22
When I go to my remote desktop settings it says its only available through local. So I only assumed I couldn't connect from a different connection. I can try a different port but I saw no setting with ubuntu to access from a different port. It was there on previous versions but this one doesn't seem to let me.

---

### Post by Sam Lars on 2010-07-22
What exactly are you using for the VNC server?

---

### Post by pricetech on 2010-07-22
If you're offering a VNC connection to the Internet, it's best if you don't make it work.  VNC is big security risk.

SSH is your better choice.  NX Client, Node, Server from NoMachine dot com will let you remote in with a fully functional GUI and still have the security of Secure Shell.

---

### Post by SpenceMakesSense on 2010-07-22
> **Sam Lars said:**
> What exactly are you using for the VNC server?

On the windows machine all I'm using is VNC lite. This has worked with no problem before with barely any setup on the ubuntu or windows machine. It seemed like mostly router work before.  
Btw right now this is all me trying to connect locally. If not previously understood

---

### Post by pricetech on 2010-07-22
> **SpenceMakesSense said:**
>  right now this is all me trying to connect locally. If not previously understood

I wasn't sure, that's why I brought up the security.  I think you'll find that NX will give you better performance as well.

Terminal Server Client works to control windows boxen from Linux quite well too.

I use both on a regular basis.  I also use VNC on a couple of "servers" because the software they "serve" requires they stay logged in all the time, not an option with RDP.

---

