---
title: "Remote access to Ubuntu"
date: 2010-10-10
forum: General Help
---

### Post by @hJ?oS6^ on 2010-10-10
I've been using Ubuntu (along with a few other Linux distros) on and off for years. One of the things that has always stopped me for using at home on my main computer is the lack of a decent remote access method.

I have a Windows 7 laptop that I use for work. I have a Windows xP desktop that I have at home, I use remote desktop to access the XP machine from the 7 machine. This works great, I've got a full-screen interface that acts as if I'm working on the XP machine directly.

I'd like to put Ubuntu on the XP machine but would like a similar interface to remote desktop on XP. I've tried RealVNC, that can do full screen but the mouse lags horribly. I've tried FreeNX, that didn't seem to do full screen and alt-tab didn't work to cycle between applications. I've tried a few others here and there but nothing seemed to fit the bill.

Is there a combination of client & server app that will do what I'm looking for?

---

### Post by HermanAB on 2010-10-10
You have never heard of SSH?

VNC is mostly a Windows thing.  On Linux it is best avoided.  The standard way to remote control UNIX and Linux machines is via SSH.  For example:

$ ssh -X -C -c blowfish user@linuxipaddress gnome-panel

That will open a remote gnome panel on your local machine and then you can go click happy.  All applications will run transparently on the local desktop.  It works from Windows too if you install Cygwin.

So, install openssh-server and read a bit at the openssh web site.  SSH is immensely powerful and can do a lot more than just running remote applications.

---

### Post by @hJ?oS6^ on 2010-10-10
I have heard of SSH and have used it and Cygwin.  However what I'm looking for is a stand-alone application to remote to the Ubuntu machine so everything on the Ubuntu machine is self-contained within that app, not integrated with my Windows box.

---

