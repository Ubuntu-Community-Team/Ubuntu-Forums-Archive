---
title: "Constantly Have to reset Remote Desktop"
date: 2009-07-08
forum: General Help
---

### Post by ogboot on 2009-07-08
First of all, I would like to say hello.  I have tinkered with ubuntu several times in the past, and finally made a complete switch about a month ago.  I am dual booting ubuntu 9.04 32 bit and x64 Studio, and have been very happy with the operating system.  I feel like it is here to stay.
  my only current issue is with remote desktop.  I like to use VNCViewer to connect to my desktop from my windows machine at work.  However, I seem to be able to only get one good session out of it; for instance:  I can't connect right now, if I went home and checked it would say that I am only available locally.  If I disable remote desktop, and re-enable it, it will then tell me that I am available locally and through my ip address.  I could then go to work and login remotely.  However, tomorrow it will be the same problem all over again.
  I first thought it was my router (linksys), but ports are forwarded correctly, and I find it curious that it will allow that first time connection after the remote desktop reset but no connections afterward.  any ideas?

---

### Post by ogboot on 2009-07-08
obligatory bump as my thread was promptly pushed down to page 8 :(

---

### Post by HermanAB on 2009-07-08
Hmm, don't use VNC.  It is a serious security risk.  Your machine will get hacked eventually.  It is also hard to get to work and slow as molasses.

Rather install ssh server.  SSH is secure and cross platform and only uses a single TCP port.  You can connect to it from Windows using Xming and PuTTY.

To connect to a server do this:
$ ssh -X -C -c blowfish user@server gnome-panel

---

### Post by ogboot on 2009-07-08
i'm familiar with using putty, will I just end up with a CLI though?
NVM, just went and took a look at XMing, very interesting stuff!

---

