---
title: "teamviewer does not launch on Ubuntu 12.04 Precise Pangolin 32bit pae"
date: 2012-09-27
forum: General Help
---

### Post by VitasLoWang on 2012-09-27
Hello, just installed TeamViewer and sadly I cannot start it. Does nothing and does not even seem to spawn any new process. There is no related message in /var/log/syslog nor in dmesg, so I have no idea what goes wrong. When I attempt to start it it shows this:
TeamViewer: 7.0.9360
Profile: /home/vitas (root)
Desktop: 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
 TeamViewer: 7.0.9360
Profile: /home/vitas (root)
Desktop: 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
 
Checking setup...
Launching c:\Program Files\TeamViewer\Version7\TeamViewer.exe...

Checking setup...
Launching c:\Program Files\TeamViewer\Version7\TeamViewer.exe...

and that is all. It worked OK on Ubuntu 11.10. Do you think I shall install wine and make TV somehow use it instead of its own bundled in /opt/teamviewer/teamviewer/7/wine/ which seems to not work with Ubuntu 12.04...?

---

### Post by HiImTye on 2012-09-27
what do you use Team Viewer for? I would use an alternative

---

### Post by VitasLoWang on 2012-09-27
Well, what would YOU use it for? :) I use it to remote control and do some file transfers between the computers I use obviously ;)
Please be so kind and tell me about those alternatives which are as easy to use as TV. Thanks

---

### Post by HiImTye on 2012-09-27
if by 'remote control' you mean 'use the other computer remotely' then you can use anything from VNC, NX, X11 over SSH, etc.
if you want to copy files from one computer to another then NX and X11 are likely your best bets

---

### Post by daslinkard on 2012-09-27
I started out by going to this [website]("http://www.teamviewer.com/en/download/dyngate.aspx") and downloading the appropriate Linux OS for me in which I chose the [TeamViewer deb v6.0.9366]("http://www.teamviewer.com/download/version_6x/teamviewer_linux.deb") Debian, Ubuntu (32-Bit) [multilanguage].

It took less than 45 seconds to download the file and once I clicked on the download file it immediately brought up the Ubuntu Software Center in which I was able to select the install button for the program.

After installed I went to my Dash Home and typed in Teamviewer, found what I just downloaded...selected it and immediately saw the WINE configuration come up, then I was agreeing to the terms.

Are you for certain that you downloaded the Linux version for Teamviewer?

---

### Post by stepking2 on 2012-09-28
TeamViewer has worked flawless on my laptop with 12.04. So I am not sure what you have done wrong.

---

### Post by VitasLoWang on 2012-09-28
> **stepking2 said:**
> TeamViewer has worked flawless on my laptop with 12.04. So I am not sure what you have done wrong.
great, very helpfull :D I have no idea either and that is why I ask here.

HiImTye I would like to use TeamViewer because it has a nice "contact list" where you see all your pcs and their status and you can easily use it to connect to your work computer even behind corporate firewall without any port forwarding and tunneling hassle which I would probably have to cope with when using VNC or those other tools right? It also works flawlessly between linux and windows without any special configuration (until Ubuntu 12.04 :-]. I think I would have to setup some ssh server if I wanted to use NX or VNC to connect to windows which is not that simple IMHO and it would probably not work if I cannot forward any port at my workplace for example right?
I think maybe Hamachi could be an easy to setup alternative in this case...?

---

### Post by bubbajunk on 2012-09-28
I am using the latest version of TeamViewer 7.0.9360 on my laptop with 12.04.1 pae install. In fact, I was using it last night between my Win7 laptop and my Ubuntu laptop to remote control and transfer files just as you mentioned. 
 
I had no problem with the install or with the startup and use of the TV application. Like other posts have mentioned above, TeamViewer does not require a separate install of Wine. It comes packages with the Wine components it needs. Not sure what you might have done during the install. Just wonder if it has something to do with your particular hardware, e.g. graphics card. Just a guess.

---

### Post by VitasLoWang on 2012-09-28
It worked on the same notebook with Ubuntu 11.10 just before I screwed something badly and rather reinstalled it freshly to 12.04. Is there some logfile in teamviewer embedded wine maybe which I can check?...

---

### Post by EkiLibRiuM on 2012-09-28
team viwer is a virtualsing tool so you can try to install virtualbox as well or go to the ubuntu software cengter and choose a virtual appliance who work's well on ubuntu...did you check al the verion off the program ??..

---

