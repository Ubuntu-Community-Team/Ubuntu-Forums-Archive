---
title: "OS for Server: Ubuntu Desktop or Server?"
date: 2009-09-14
forum: General Help
---

### Post by n0an on 2009-09-14
Hello,

I am planning to buy a new server which will be shared between me amd my two friends. Now my confusion is whether to go for Ubuntu Desktop or the Server edition. I am somewhat familiar with Ubuntu Desktop, but the questions are:

1) Does Ubuntu Desktop have the feature of setting up FTP so that all three of us can have different FTP access to our files?

2) This might be a newbie question, but is Ubuntu Server operated from a command line(SSH) or has a UI like the Desktop version?

3) I might even want to setup a domain and put a website on it. Is it possible to do such things and also have Control Panels in the Desktop version? If not, then will Control Panels be compatible with Ubuntu server edition?

4) Will either editions of Ubuntu work well on 576MB RAM or is 1024MB preferred?

Will post here if I have any further questions.

Thanks,

n0an

---

### Post by Woody1987 on 2009-09-15
1. Not initially but you can install ftp software. I dont use it so i cant give any suggestions on the particulars.

2. Server is command line, but a gui can be installed. Just run sudo apt-get install ubuntu-desktop.

3. Not sure.

4. They will both work fine on 576MB of ram.


The main difference between the two is the pre-installed software, but the exact same software is available to be downloaded and installed from the repositories on both the server and desktop editions. 

If your not comfortable using the command line i recommend you use the desktop edition, and use remote desktop or ssh to administor it, or even webmin. Or you could try the server edition and if you find it hard, do as i said above and install a gui.

---

### Post by n0an on 2009-09-15
The main requirement is FTP. If a Desktop-like GUI can be installed for the server edition, then it would be the best solution. So, I can get a GUI for the server edition by "sudo apt-get install ubuntu-desktop". I hope this won't re-install or replace the server edition with the Desktop edition.

---

### Post by egalvan on 2009-09-15
> **n0an said:**
> The main requirement is FTP. If a Desktop-like GUI can be installed for the server edition, then it would be the best solution. So, I can get a GUI for the server edition by "sudo apt-get install ubuntu-desktop". I hope this won't re-install or replace the server edition with the Desktop edition.

The main difference between Server and Desktop is the kernel.
the server kernel has some optimizations for server use,
mainly in the scheduler and memory management.
The 32bit Server has PAE enabled, and the 64bit Server of course has large memory support natively.
This is changing, from what I have heard...
32bit Karmic appears to have PAE as an optional kernel.
The scheduler is set up for maximum throughput from the drives and RAM.

Under VERY heavy load, the Server kernel *may* show a *slight* decrease in responsiveness.
 I have never felt this in over 18 months of running a Server version with Gnome/KDE DE.


The next difference is the software that is installed by default.
The Server has no GUI (desktop), it is command-line.
A DE can be easily installed as others have stated

```
sudo apt=get ubuntu-core
```

will install a minimal Gnome desktop...
choose your favorite...

Gnome
KDE
xfce
LXDE
(sorta-in-order of "heavy" to "lightweight")

all will work.

and no, it will not remove any Server edition.

As for how much RAM, well, this depends on your pocket-book,
but more is always better...
server functions are more RAM sensitive than desktop functions.
I max out RAM (if possible) on any server I set up.

And in the end, unless you are going to have heavy-duty server duties, 
setting up a Desktop as a server is usually quite OK.
You will probably need to install more software if you go this route.

Of course, doing everything from the command-line is very much a learning process,
 nothing better for learning the inner workings of Linux. :)

---

### Post by 3rdalbum on 2009-09-15
Ubuntu Server is the same as Ubuntu Desktop except that the kernel is slightly different, and there is no gui by default in Server.

You can use Ubuntu Desktop as a server by installing server packages from the repositories - remember, they are exactly the same as what is available in Server. You can use Ubuntu Server as a desktop by installing Xorg and a desktop environment.

Ubuntu Desktop runs fine on 512mb of RAM, but if you're buying a new machine it might as well have 1 gig, especially if two people are using it. My netbook runs Desktop as a desktop, with 512mb of RAM. My home server runs Desktop as a server, with 1 gig.

---

### Post by n0an on 2009-09-17
Could you guys suggest me the ideal application to create ftp accounts on the Desktop edition? Or a Control Panel for the server edition.

---

### Post by jm2 on 2009-10-07
If you are looking for the ability to have separate logins for ftp so you can each have your own directories that is available under VSFTPD, as it is easy to set up.
 
sudo apt-get vsftpd

---

