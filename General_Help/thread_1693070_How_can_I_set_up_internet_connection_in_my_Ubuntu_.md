---
title: "How can I set up internet connection in my Ubuntu 10.04?"
date: 2011-02-22
forum: General Help
---

### Post by MGTHEBOSS on 2011-02-22
In my Ubuntu 10.04 I can not connect to internet.When I open Mozila
Firefox it shows: Server not found ,after a long time.
I have a DSL Modem.In the same machine I have XP from which I can connect to internet.I want to connect to internet from Ubuntu.I 
have an attachment which will clearly explain the situation.

---

### Post by Quarkrad on 2011-02-22
If you right click on the network icon in the top panel (the one with two arrows) and choose *Connection Information* what does it say?

---

### Post by gandaran on 2011-02-22
> **MGTHEBOSS said:**
> In my Ubuntu 10.04 I can not connect to internet.When I open Mozila
Firefox it shows: Server not found ,after a long time.
I have a DSL Modem.In the same machine I have XP from which I can connect to internet.I want to connect to internet from Ubuntu.I 
have an attachment which will clearly explain the situation.
can you describe what you have done to get the modem working?
and how does the DSL modem work in windows? which connects to internet the modem or the XP computer with pppoe setup connection or the modem authenticates the connection? 
this is important to understand your internet setup and help you fix it for ubuntu.

---

### Post by MGTHEBOSS on 2011-02-22
> **Quarkrad said:**
> If you right click on the network icon in the top panel (the one with two arrows) and choose *Connection Information* what does it say?
Something bad happened while trying to set up internet connection
by taking help from some websites.Now I can't see the network icon in it's place.Please help.I need to set up internet connection 
immediately.

---

### Post by MGTHEBOSS on 2011-02-22
> **gandaran said:**
> can you describe what you have done to get the modem working?
and how does the DSL modem work in windows? which connects to internet the modem or the XP computer with pppoe setup connection or the modem authenticates the connection? 
this is important to understand your internet setup and help you fix it for ubuntu.
In XP:
I have connected every thing properly.I have installed Atheros
AR8121/AR8113/AR8114 PCI-E Ethernet Controller.I have set up my internet connection from XP Control Panel.Now while connecting 
to internet I take the following steps:
1.RClick on Broadband shortcut on desktop->connect
2.A dialog box appears where I type my Username and Password.
3.Connection is established.
Please help me. I need to establish an internet connection immediately from Ubuntu.
 Something bad happened while trying to set up internet connection from Ubuntu by taking help from other websites.
Now I don't see that network icon(the one with two arrows) in the top bar.How can I get that back?

---

### Post by gandaran on 2011-02-22
> **MGTHEBOSS said:**
> In XP:
I have connected every thing properly.I have installed Atheros
AR8121/AR8113/AR8114 PCI-E Ethernet Controller.I have set up my internet connection from XP Control Panel.Now while connecting 
to internet I take the following steps:
1.RClick on Broadband shortcut on desktop->connect
2.A dialog box appears where I type my Username and Password.
3.Connection is established.
Please help me. I need to establish an internet connection immediately from Ubuntu.
 Something bad happened while trying to set up internet connection from Ubuntu by taking help from other websites.
Now I don't see that network icon(the one with two arrows) in the top bar.How can I get that back?
looks like you have setup a pppoe dialing configuration in XP, you do the same on ubuntu, there are several ways but the easiest is right click the panel network icon » edit connections » DSL tab » add » fill in the ISP authentication details, username and password then you should be able to connect from the network icon.
maybe you have messed the system up now following some tutorial so I cant be sure it will work now but try, if it doesn't work there are other ways to set up a pppoe connection.
to get the panel icon back right click the panel area » add to panel » add the notification applet.

update: sometimes a computer reboot is needed for the setup to start working.

---

### Post by gandaran on 2011-02-22
another question, is the modem usb or ethernet? if ethernet doesn't it have a web based interface for setting up connections? or you really need a pppoe setup from the computer (if your internet provider uses pppoe authentication!)
you may not get the right help needed because we don't know what you are trying to do, we have to guess everything so any help could complicate things.

---

### Post by marshag63 on 2011-02-22
We really need to know the make and model of your modem to be able to help.  

From the photo you posted, up on the top panel there are arrows - one points up and one points down.  Right click on the arrows and look for the "connection information" If a network interface is configured, it will show the name of the interface, the driver, security settings and IP address, etc.  If anything shows up, please report that along with the make and model of your modem.

MDG

---

### Post by MGTHEBOSS on 2011-02-22
> **gandaran said:**
> another question, is the modem usb or ethernet? if ethernet doesn't it have a web based interface for setting up connections? or you really need a pppoe setup from the computer (if your internet provider uses pppoe authentication!)
you may not get the right help needed because we don't know what you are trying to do, we have to guess everything so any help could complicate things.
I use ethernet cable for Modem.My ISP uses pppoe authentication which I have already explained.
Thanks for your quick reply.

---

### Post by MGTHEBOSS on 2011-02-23
I have already tried your suggestion on how to get the  icon back.
That hasn't helped me.So, I have uninstalled Ubuntu and now I am reinstalling it.I have a question when I install it,it shows 
different installation sizes ranging from 10 to 30 GB.What is the meaning of this?What is the difference between 10GB installation
and 30GB installation?
 I have chosen 30GB installation size thinking that something extra will be available(because in the previous 15GB installation gfortran was not available) and I see that Ubuntu Installer is downloading lucid-desktop-i386.iso for a long time.What is this?
After installing shall I get gfortran package in Synaptic Package Manager?
Here is an attachment.

---

### Post by gandaran on 2011-02-23
> After installing shall I get gfortran package in Synaptic Package Manager?
all packages from the repositories are available ready to install from synaptic package manager after you connect ubuntu to internet,
just update the package list when you have internet "sudo apt-get update" or click the reload button in synaptic to fetch all packages

---

### Post by gandaran on 2011-02-23
> **MGTHEBOSS said:**
> I use ethernet cable for Modem.My ISP uses pppoe authentication which I have already explained.
Thanks for your quick reply.
then your modem must have a web based interface, I would forget using the computer pppoe setup to connect to internet and use the modem instead but thats up to you.
if on windows you are using a computer setup then use the same on ubuntu and if the network DSL setup option doesn't work remove it and try the command line, open terminal and type [COLOR="Teal"]sudo pppoeconf [/COLOR], check that it shows your ethernet device is detected, if not it is useless to continue, start again or reboot, then if detected all you have to do is enter the username and password and choose to connect at startup, reboot the computer you should have internet now.

---

### Post by MGTHEBOSS on 2011-02-23
> **gandaran said:**
> then your modem must have a web based interface, I would forget using the computer pppoe setup to connect to internet and use the modem instead but thats up to you.
if on windows you are using a computer setup then use the same on ubuntu and if the network DSL setup option doesn't work remove it and try the command line, open terminal and type [COLOR="Teal"]sudo pppoeconf [/COLOR], check that it shows your ethernet device is detected, if not it is useless to continue, start again or reboot, then if detected all you have to do is enter the username and password and choose to connect at startup, reboot the computer you should have internet now.
Thanks for your help.You have solved my problem.I can access internet from Ubuntu now.
But here are some questions for you:

1.when I install Ubuntu,it shows different installation sizes ranging from 10 to 30 GB.What is the meaning of this?What is the difference between 10GB installation and 30GB installation?

2.I see that Ubuntu Installer is downloading lucid-desktop-i386.iso for a long time.What is this?
In fact to install Ubuntu(30GB) quickly I had to disconnect internet.

3.While setting up internet connection I saw a dialog box where
if I clicked on Yes I was not getting internet connection.I
had to click on No to set up internet connection(See attachment
MSS please).

I am waiting for your reply.

---

### Post by gandaran on 2011-02-23
> 1.when I install Ubuntu,it shows different installation sizes ranging from 10 to 30 GB.What is the meaning of this?What is the difference between 10GB installation and 30GB installation?

2.I see that Ubuntu Installer is downloading lucid-desktop-i386.iso for a long time.What is this?
In fact to install Ubuntu(30GB) quickly I had to disconnect internet.
I don't know what you talking about here, how did you install ubuntu? dual boot separate windows and ubuntu or did you install inside windows (wubi install)?
the desktop iso is 700MG, the download time depends on internet speed, 30GB or 10GB as nothing to do with ubuntu install, if you choose to install ubuntu on separate partition you define what size the partition should be.

---

### Post by MGTHEBOSS on 2011-02-25
To gandaran:

Answer to your question: I have installed Ubuntu inside Windows.

Is that a problem for setting up internet connection inside Ubuntu?

I have sent you a private message.Give a reply as quickly as possible.

---

### Post by MGTHEBOSS on 2011-02-26
It seems that there is a huge bug in the network manager of Ubuntu
10.04.Watching that none is interested to this thread any more
I will mark this thread as SOLVED.

---

### Post by marshag63 on 2011-02-26
You might try the ubuntu IRC channel for someone who can help you with your wubi install of ubuntu.  Most like native ubuntu - either by live cd or regular install.  Sorry I don't have experience to be able to guide you further.

MDG

---

