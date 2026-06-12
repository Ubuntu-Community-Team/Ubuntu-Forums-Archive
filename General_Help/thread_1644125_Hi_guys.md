---
title: "Hi guys"
date: 2010-12-12
forum: General Help
---

### Post by freefixkorma on 2010-12-12
hi there i am sorry i am always asking ,i am running on ubuntu 10.10 dktop ed acer aspire 5742 64bits ,listen can i use Putty to monitor the web surfing on the desktop that i have upstairs ,so i can go ahead and check what my kids are looking from my desktop ,here is what i got i have rca modem from comcast this feeds my wireless router and this router feeds the desktop upstairs ,and gives me wireless internet in my laptop what i wanna do is from my laptop monitor the web surfing can that be possible i will appreciate ,and please name what i need i am not an expert i already Putty installed from synaptic so please be le me know how can i set it up if it is possible thanks in advance


free fix:p

---

### Post by Foxheadz on 2010-12-12
Not sure about putty but you can set up a VNC server on the other computer and then view/control it from your laptop or even and ipod touch (if you have) by using a client like remote desktop viewer which comes with ubuntu

---

### Post by 311005901 on 2010-12-12
I agree with Fozheadz. Using Remote Desktop is a lot easier than playing around with Putty.

If those computers use Ubuntu, the setup is a breeze. On their computers, look under "System>Preferences>Remote Desktop" and play with the options. 

If they are running Windows or OSX, you can download a free VNC server program for their computers. You can purchase RealVNC, but I'm sure there are a free ones available.

To view their desktops on your computer running Ubuntu, just run "Applications>Internet>Remote Desktop Viewer".

I think that would be better than messing around with Putty...

---

### Post by freefixkorma on 2010-12-12
thanks for the reply is there a guide how to set it up i will appreciate am dummy for this will appreciate how to set it up will look for it ,thanks in advance i am runing i both computer ubuntu in dktop 10.4 lucid and laptop 10.10 dktop ed thanks for the reply how do i set it up 

freefix

---

### Post by 311005901 on 2010-12-12
Sure. [This link here]("http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/") has instructions for Ubuntu (viewing and serving) and Windows (viewing). Although it is written for an earlier version of Ubuntu, the instructions still work on Ubuntu 10.10. :)

---

### Post by freefixkorma on 2010-12-12
this what i got in my laptop is this app has to be set on dktop first and than in my laptop thanks for the help

free fix

---

### Post by CharlesA on 2010-12-12
If you do enable VNC (remote desktop) be sure to give it a strong password and not allow it access to the internet (by making sure the "configure the network automagically" box is left unchecked)

---

### Post by 311005901 on 2010-12-12
> **freefixkorma said:**
> this what i got in my laptop is this app has to be set on dktop first 


This what I have on my laptop. Does this app have to be set on the desktop first and then on my laptop? ;)

You only have to set this window to the options you want on the computer you want to view.

---

### Post by Foxheadz on 2010-12-12
Kind of off topic but does anyone know how to do something like vnc but over a different network?

---

### Post by 311005901 on 2010-12-12
Foxheadz, you're going to have to mess around with a DNS server. I'm sure there is a way to do it, but it's really complicated... :p
[Maybe this link]("http://lloydpuckitt.wordpress.com/2007/11/08/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/") can help?

---

### Post by CharlesA on 2010-12-12
> **Foxheadz said:**
> Kind of off topic but does anyone know how to do something like vnc but over a different network?

You'd have to use SSH in order to connect securely.

> **311005901 said:**
> Foxheadz, you're going to have to mess around with a DNS server. I'm sure there is a way to do it, but it's really complicated... :p
[Maybe this link]("http://lloydpuckitt.wordpress.com/2007/11/08/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/") can help?

SSH has nothing to do with DNS. The only reason you'd need to use something like DynDNS is because you have a dynamic IP address.

---

### Post by 311005901 on 2010-12-13
Agreed, but who has a static IP nowadays? :)

---

### Post by CharlesA on 2010-12-13
> **311005901 said:**
> Agreed, but who has a static IP nowadays? :)

Businesses, normally.

---

