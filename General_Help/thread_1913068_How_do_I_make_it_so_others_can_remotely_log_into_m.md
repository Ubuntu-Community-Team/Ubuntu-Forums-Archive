---
title: "How do I make it so others can remotely log into my computer?"
date: 2012-01-21
forum: General Help
---

### Post by brushman on 2012-01-21
I'd like to set up my desktop so everyone in the office can log in, as if they were at the computer itself and had their own login information. What's the best way to achieve this? I am using Ubuntu 11.10 (the most updated version).

Thanks.

---

### Post by saneearth on 2012-01-21
Teamviewer may be a solution. Works cross platform also.

---

### Post by imachavel on 2012-01-21
> **saneearth said:**
> Teamviewer may be a solution. Works cross platform also.

team viewer is for windows, and I figure wouldn't work well being opened in wine. That is a very good question. You would need to give everyone rdp access and make sure port 3389 is opened on your router. You would need to set it up so that anyone could log in, rdp would be the best bet. I'm going to say I don't know but give this my best shot:

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

so if my i.p. address was 192.168.0.100 then I would rdp from windows into linux like so:

rdp 192.168.0.100:3389 if the port was opened and allowed for the i.p. address I'm trying to log into, and this is considering that rdp works the same with windows that it does with linux.

---

### Post by imachavel on 2012-01-21
> **saneearth said:**
> Teamviewer may be a solution. Works cross platform also.

I don't know am I wrong? Does team viewer work well with ubuntu? I just never thought about it, if you go team viewer web site? Is there a linux version?? If so that'd be best.

---

### Post by memristor on 2012-01-21
I have Teamviewer 6 installed on my Ubuntu and i have used it quite often to remote into other Ubuntu box or Windows Vista Box. Worked flawlessly for me.
Here is the link to Ubuntu Linux version
[http://www.teamviewer.com/en/download/index.aspx?os=linux](http://www.teamviewer.com/en/download/index.aspx?os=linux)

---

### Post by raja.genupula on 2012-01-21
yeah +1.
Team viewer also worked fine to me . you can use that .

---

### Post by aysiu on 2012-01-21
Teamviewer works well and is very cross-platform. I've used it in Ubuntu, Mac OS X, Windows, Android, and iOS. I'd highly recommend it.

---

### Post by brushman on 2012-01-22
Let me clarify: I don't want to share the same screen with other users. I want multiple people to be able to simultaneously use the computer (each person doing their own thing). Ideally I would be able to give someone their own login and password that they use to log in. I've logged into other people's computers using ssh, and I thought that would be the best solution for me. Or do you still recommend teamviewer?

Thanks.

---

### Post by WorMzy on 2012-01-22
I recommend ssh. You can run X11 applications over it, using the -X, or -Y options, assuming that X11 forwarding is enabled in sshd.

If the other users are on Windows, they can still run X11 apps, but they'll need to use something like [Xming]("http://www.straightrunning.com/XmingNotes/"), along with something like [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/").

---

### Post by Choragos on 2012-01-22
If command line is adequate, then SSH is the way to go.  The -X as stated above is great, but if you're logging in from outside the network (i.e. into a server, then ssh from that server to the computer) -X will not work (at least directly).

---

### Post by goodbye-windows(tm) on 2012-02-16
Is team viewer open sourced???? I looked on the website and find nothing about downloading the source code.

For me, if it ain't open sourced, then I don't need it::> Without the protection offered by open sourced software, using it is no better than running windows software, ie Russian Roulette.

Regarding the original post, it sounds like the op might be better off using the server version and setting up a mini server. In such a system, email between those in the office would never see the internet at all.

So, is team viewer open sourced?

GL to all.

Art

---

