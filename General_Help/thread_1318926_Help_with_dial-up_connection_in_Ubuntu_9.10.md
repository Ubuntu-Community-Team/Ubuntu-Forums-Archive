---
title: "Help with dial-up connection in Ubuntu 9.10"
date: 2009-11-08
forum: General Help
---

### Post by AlexsAntidote on 2009-11-08
I've been using Ubuntu since 7.04, but never had a need to use a dial-up connection so this is new ground to me.

I gave a copy of 9.10 to a friend of mine who is completely new to Linux who likes Ubuntu quite well, however he only has access to the Internet through dial-up due to the lack of availability of anything better in the locality where he lives.

I did some searching about setting up dial-up connections in Ubuntu and from what I gather it appears that dial-up is a very touchy subject when it comes to Ubuntu. It seems this is a weak area indeed.

One thing that comes to mind concerning my friend's particular situation is the fact that he is unable to connect to the Internet from Ubuntu in order to install any apps (be it through apt, synaptic, or the software center), and he only has desktops so it's highly unlikely he would be able to seek alternative connection any time soon. He can connect through Windows though.

I would greatly appreciate it if someone can point me in the right direction here.

It seems to me that there is no simple option "out of the box" for Ubuntu 9.10 and dial-up... Please correct me if I am wrong.

I love Ubuntu and want my friend to love it too...


Thanks again!

---

### Post by nathanernest on 2009-11-08
Install virtualhub on his windows machine and bridge the connection there... Sounds like he simply wants to try ubuntu a bit more forst maybe. 

There are plenty of tools for Dialup (Gnome PPP is popular from what i hear). Without an internet connection, Tell him to get his walking boots on :-) and go to another connection :-)

---

### Post by AlexsAntidote on 2009-11-08
I don't think he's about to pack up his desktop and start hiking with it to find an alternate connection.

I'm trying to encourage him to use Ubuntu, not get him to completely dispel the idea...

Bridging the connection from one computer to another isn't really a useful long-term solution. You're correct that he wants to try it first, but it should be a little easier than that...

I'm thinking he will need to use Windows to download the deb packages for gnome-ppp and wvdial, then boot up in Ubuntu and install them and use gnome-ppp to connect...

But I don't know if that is enough. Anyone else know?

---

### Post by klemes on 2009-11-08
This is really a hustle because you don't only have to download only the desired debs but their dependencies as well.
Let me ask you what type of modem does he have?
If it is a winmodem (aka software modem) it will not work in Linux unless it is supported by sl-modem-daemon(download it from their website or sourceforge.net because I dont't know lately but back then in Gutsy times the Ubuntu package lacked the slamr0 module).
But the best option for him I think is buy an external 56k hardware modem (any external serial modem actually) and proceed to connect to the Internet as you know already.
At first you will have available only pppd and pon/poff commands to establish a connection so that means a little tinkering about with configuration files but there are plenty good guides on the net and even the man page for pppd is very helpful in itself,and afterwards you will be hopefully be able to download kppp and wvdial. 
I wish you success on your endeavours.

---

### Post by AlexsAntidote on 2009-11-08
Thanks Klemes! I'm not sure what kind of modem he has, but I do appreciate the advice and clarification. At least I know where to start in helping him.

Thanks again.

---

### Post by Minsky on 2009-11-08
I second Klemes, I was in a similar situation as your friend with the only way to connect to the internet was using an external serial modem. The way I did it, after connecting the modem, was to open a terminal window and type in **sudo pppconfig**, which is a configuration program included in Ubuntu that sets up an internet connection, and followed the instructions from there. During the configuration process you get the option to give a name to your internet connection such as ***myISP***. Connecting to the internet is by typing **sudo pon *myISP*** in the terminal window, and **poff** to disconnect. With a connection established, you can then download a GUI frontend such as **gnome-ppp** if you're using a Gnome desktop, or **kppp** if you're using KDE.

---

### Post by deckeeper on 2009-11-08
I think 8.4 was the last version to have that handy little helper that got dial up on line. Everyone has to agree pon/poff is not a good way to show off 9.10 to a windows user that has no choice but dial up. I'm still using 8.4 to avoid that hassle myself

---

### Post by ranch hand on 2009-11-08
Make sure t oget a hardware modem.  they do not require drivers and Ubuntu should recognize any external hardware modem.

A hardware modem has all it needs built in and works on its own.  Software, or "winmodmens" use the cpu for their power.

The modem "negotiates" with the modem at the ISP for connection.  A software modem is kind of wimpy and your connection is likely lost more often when the server is busy.  Hardware modems negotiate with a club.  With a nail in it.

Your friends connection will be better under Win JerryLewis Pro than it is now.  You probably need to pull the present modem from the box for MS to recognize the new one.  Shouldn't be a problem with Ubuntu because it won't "see" the winmodem (I figure it is a winmodem - most are anymore).

---

### Post by Raghavan48 on 2009-11-15
Hi guys,
 
Even I have the same problem with my DSL. Unable to connect to the internet. I tried using pon and poff. My ISP name is huawei. The farthest I got in this road was this:
I type pon huawei, the next line the prompt comes up and nothing happens. 
 
When I tried to get a plog, this was what I got.
 
 
Nov 17 11:39:44 ubuntu pppd[1811]: pppd 2.4.5 started by root, uid 0
Nov 17 11:39:45 ubuntu 
chat[1813]: Can't get terminal parameters: Input/output error
Nov 17 11:39:45 ubuntu pppd[1811]: 
Script /usr/sbin/chat -v -f /etc/chatscripts/huawei finished (pid 1812), status = 0x2
Nov 17 
11:39:45 ubuntu pppd[1811]: Connect script failed
Nov 17 11:39:46 ubuntu pppd[1811]: Exit.
Nov 17 11:40:50 ubuntu pppd[1817]: pppd 2.4.5 started by root, uid 0
Nov 17 11:40:51 ubuntu 
chat[1819]: Can't get terminal parameters: Input/output error

Please help. I have been a Windows user all this while but have started liking Ubuntu and want to adopt the same. 
 
Thanks in advance.
Raghavan

---

