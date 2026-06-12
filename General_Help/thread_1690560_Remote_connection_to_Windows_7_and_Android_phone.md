---
title: "Remote connection to Windows 7 and Android phone"
date: 2011-02-18
forum: General Help
---

### Post by Hubster on 2011-02-18
Hi, 

I'd like to connect to my Ubuntu via my Android Nexus S phone, and ideally using something works similar on Windows 7 as well. I realize that this topic must of been covered a hundred times before, but given I'm not confident even in the basic theory please stay with me; even a few links to relevant (up to date) previous posts would be appreciated ;)

As I understand it:

I need to connect via SSL (installing something like open SSL server on the desk top machines) and a suitable app on the phone (like Connectbot for example)

And then a VNC client on the phone as well as my Ubuntu and window 7 machines (?)

Can anyone recommend GUI interfaces, good practice tutorials, that they've found helpful. I'm starting on the OpenSSL docs, but an overview just to make sure that I'm looking along the right lines would be cool.  

Thanks

---

### Post by trozamon on 2011-02-18
How do you want to connect? Command Line or Visually?

If you want to connect visually, I'd recommend TeamViewer: [http://www.teamviewer.com](http://www.teamviewer.com)
TeamViewer has a client for Android, and it's very easy to set up.

If you'd rather use VNC, I personally like the built in VNC: System>Preferences>Remote Desktop

For command line, just open a terminal and type:
```

sudo apt-get install openssh-server
```Hope that helps. Feel free to ask any questions.

---

### Post by Hubster on 2011-02-18
Thanks! :D

Given the security risks I'll probably go visually and take a look at the Team Viewer thing, at least until I'm confident that I'm not making my desktops incredibly insecure. At least if I'm right in the theory of what I'm trying to do.

Am I right in thinking though that this has a built in 'SSL' or something that can be considered as good as, and I don't need to run a separate SSL prog first?

---

### Post by trozamon on 2011-02-18
TeamViewer has built-in SSL encryption, so it's pretty secure.

> **Hubster said:**
> Am I right in thinking though that this has a built in 'SSL' or something that can be considered as good as, and I don't need to run a separate SSL prog first?

As far as I know, you can not just run a "separate SSL prog" and encrypt a connection because the device on the other end will not be able to un-encrypt it.

---

### Post by gordintoronto on 2011-02-18
> **Hubster said:**
> Hi, 

I'd like to connect to my Ubuntu via my Android Nexus S phone...


What do you actually want to do? Run your desktop computer from your phone? Share files? "Connect" doesn't mean much.

---

