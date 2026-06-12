---
title: "Best Ubuntu RDP?"
date: 2011-02-28
forum: General Help
---

### Post by Mr. ViC on 2011-02-28
Hey there.

I have a VPS I use frequently, but there's this problem that when I use it on Ubuntu it **gets damn slow, and crashes frequently**.

I thought it was because of the VPS specs, so, I bought an upgrade.

Still the same.

Today, I tried to connect it using a Virtual Machine with Windows XP in there. It worked out great.

I used to use Remmina to connect, but it keeps crashing the VPS now. Both on my Desktop PC and laptop. Also using others like Remote Desktop Viewer and Gnome-RDP, they both crash the VPS making it slow as hell and freezing.

It gets pretty anoying have to use my VM in order to use the VPS (it's Windows XP, by the way).

Is there any other software I can use to connect to the VPS using Ubuntu?

Thanks!

---

### Post by doas777 on 2011-02-28
well, what OS is on your VPS? windows or linux?
if it is a linux host, then FreeNX/NeatX are the best remote desktop-ish tools I have used. nice and responsive, but ssh based so nice and secure too. and clients for windows mac and linux.

---

### Post by Mr. ViC on 2011-02-28
Hey there. Thanks for replying.

The OS of the VPS is Windows Server 2003.

I had one before ( Windows Server 2008 ), and used it with Remmina and worked great. I don't know why this one keeps crashing.

I'll try the ones you mentioned, thank you.

---

### Post by Mr. ViC on 2011-02-28
Hey.

Just to say I got my problem solved. I've installed KRDC from Software Center, and works great!

Thanks again guys. :)

---

### Post by beercz on 2011-03-07
I user gnome-rdp alot for remote desktops - works very well for me

---

### Post by W1zz on 2012-12-18
Just to post a possible solution for people.

I found Remmina started crashing at start-up and there was no obvious cause from searching the net.

I was able to trace the issue as being a problem with the config files in ~/.remmina/.  A couple of these files were empty (0 bytes). When I deleted these Remmina started normally again.

HTH

Alan

---

