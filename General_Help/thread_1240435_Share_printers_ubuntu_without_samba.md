---
title: "Share printers ubuntu without samba"
date: 2009-08-14
forum: General Help
---

### Post by Sashin on 2009-08-14
Anyone know how to do this, I have three windows free computers two desktops and a laptop. The desktops are connected to the router and the laptop connects wirelessly. They are not networked (I have no idea how).

Anyone know how to share the printer between them.

---

### Post by lykwydchykyn on 2009-08-14
> **Sashin said:**
> Anyone know how to do this, I have three windows free computers two desktops and a laptop. The desktops are connected to the router and the laptop connects wirelessly. They are not networked (I have no idea how).

Anyone know how to share the printer between them.

What are your "windows free computers" running?  Ubuntu? DOS? HaikuOS?

And what do you mean that they are not "networked"?  Are they all connected to the router and able to access the internet?

Is the printer connected directly to the network or to one of the computers?  What kind of printer is it?

---

### Post by Sashin on 2009-08-14
I'm not an advanced linux user, they all run ubuntu 9.04. The printer is connected normally to one of the computers, all computers access internet through the same router/modem the desktops are both connected via ethernet cablle whereas the laptop does so wireless.

What I mean by them not being network is that they can't share files (I don't know how). I'd like to do that but it's not essential, what is though is being able to print from all three.

I have a Xerox workstation PE220 that's running on the samsung unified driver.

---

### Post by perce on 2009-08-14
I assume all run a Unix-like system (Linux/OS X). You should connect the printer to one of them, which will be the print server, and configure CUPS on the server to share the printer on the network, and CUPS on all other computers to detect network printers. In Ubuntu you do this by going to
system > administration > printing, then in the "printer configuration" windows: server > settings. In the server (the one the printer is attached to) you should check the boxes: "publish shared printers connected to this system" and "allow printing from the Internet". On the clients (the other computers) you should check the box "show printers shared by other systems".
A reboot of all machines (starting from the server) may or may not be needed; not sure about this.

For this to work, of course, the printer must be properly configured on the computer it is connected to.

---

### Post by juancarlospaco on 2009-08-14
just go here:

**[http://remote-ip-with-installed-printer:631/printers/](http://remote-ip-with-installed-printer:631/printers/)**

---

### Post by perce on 2009-08-14
> **Sashin said:**
> 

What I mean by them not being network is that they can't share files (I don't know how). I'd like to do that but it's not essential, 

In order to share files, you have two option: you can either use NFS, configure one as server, and allow the other ones to mount a partition of the server (never done this, I can't help you), or you can use ssh. As a first step, you should install an ssh server on all computer which contain files you want to share (an ssh server is not in the standard Ubuntu installation), then go to Places > connect to server, choose "ssh" as service type", and fill the relevant information; it is quite intuitive what you have to fill.

---

### Post by Old_Grey_Wolf on 2009-08-14
Edit:  Perce answered first. What he said above.

To slow at typing :)

---

### Post by Sashin on 2009-08-14
It works, perfectly now I can print from wherever. This is awesome. 
I still can't share files though. 
But I suspect that will be harder a task to accomplish. Dropbox might just be the easiest way, and when its matured Ubuntu one can take its place.

---

### Post by perce on 2009-08-14
> **Sashin said:**
> It works, perfectly now I can print from wherever. This is awesome. 
I still can't share files though. 
But I suspect that will be harder a task to accomplish. Dropbox might just be the easiest way, and when its matured Ubuntu one can take its place.

What did you try to share files? (a caveat: for both methods I suggested every must always have the same local ip address)

---

### Post by Old_Grey_Wolf on 2009-08-14
Using the Places menu, select the folder or file you want to share; then, select the file or folder (left click), next right click. You will get a pop up display, select sharing options. Check the box to share the file or folder.

---

