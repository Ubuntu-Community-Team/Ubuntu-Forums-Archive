---
title: "Windows to Ubuntu RDP"
date: 2010-11-18
forum: General Help
---

### Post by Kocrachon on 2010-11-18
Sp I am looking for a free/cheap software that will allow for a remote desktop connection from my works Windows XP machine to my home Ubuntu machine. Right now to connect from Windows to Windows I use logmein. I want something with a similar setup.

I want to be able to install a server application onto my linux machine and either use a client or a web based connection so I can remote into my machine with a true remote connection where I have a visual of my "desktop" so to speak, and full mouse/keyboard control of my machine.

Does anyone know of anything like this that is cheap/free? I really would prefer to spend less than 20 dollars because its not something so urgent I need to spend 60 dollars on.

---

### Post by alienprdkt on 2010-11-18
Could use [nomachine]("http://www.nomachine.com/download-package.php?Prod_Id=2249") its fast, easy, and ssh secure!

DEB version
Download the DEBs
Change your working directory to the location where you saved the package and install it by running from a console:

  # sudo dpkg -i nxclient_3.4.0-7_i386.deb 
  # sudo dpkg -i nxnode_3.4.0-14_i386.deb 
  # sudo dpkg -i nxserver_3.4.0-14_i386.deb
If you don't have the sudo utility installed, log on as superuser ("root") and run the commands without sudo.

or you can install them in that order just by double clicking and your software manager should install it for you. You may get some kind of warning but just ignore and works great!

If you want to control it via work hope you have secure vpn if not simply open port 22 for ssh.

---

### Post by Kocrachon on 2010-11-18
Sounds good, i will give it a shot, thanks!

---

### Post by Habitual on 2010-11-18
Have a look also at [http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by Fire_Chief on 2010-11-18
Since you mentioned LogMeIn, I thought you might want to also look at TeamViewer. It's free and works on Linux as well.

[http://www.teamviewer.com/index.aspx]("http://www.teamviewer.com/index.aspx")

Cheers!

---

