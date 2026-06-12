---
title: "Login to another Ubuntu PC over lan?"
date: 2010-02-05
forum: General Help
---

### Post by mahela007 on 2010-02-05
I'm very new when it comes to networking under Linux AND windows. I've learned that linux is a fundamentally 'multiuser ' operating system and I also found the other virtual terminals in ubuntu. (Ctrl + Fn keys) So how can I log into an Ubuntu PC while another user is working on it? I'll try to use an example to make this clear. 
There are two computers called A and B. There is a user already working on PC B. I want to be able to login and use PC B via PC A over a LAN.

---

### Post by r_s on 2010-02-05
If they are connected using a LAN , you can ssh into that account, but there are other considerations for this too , probably you can look into them.

---

### Post by mahela007 on 2010-02-05
what's ssh and how do I do that? I've also read about something called XDMCP (is that right?).

---

### Post by audiomick on 2010-02-05
> **mahela007 said:**
> what's ssh and how do I do that? I've also read about something called XDMCP (is that right?).
There is an extensive explanation of what ssh is here
[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

I don't know exactly how to set it up, but it is not that difficult, I believe.

What you want to do is definitely possible on Ubuntu. Linux, like Unix that it is derived from, is conceived as a multi user system from the ground up. This means that things like what you want to do are, in a sense, "built in".

---

### Post by ushills on 2010-02-05
> **mahela007 said:**
> what's ssh and how do I do that? I've also read about something called XDMCP (is that right?).

xdmcp is what thin clients use and is built into ubuntu, there is a guide just google xdmcp ubuntu.  you will be able to login even as the same user on both machines on use the resources on the server.

---

### Post by mahela007 on 2010-02-05
> **ushills said:**
> xdmcp is what thin clients use and is built into ubuntu, there is a guide just google xdmcp ubuntu.  you will be able to login even as the same user on both machines on use the resources on the server.
 
It seems that this has been removed from Ubuntu 9.10. most of the guides I find by googling tell me to select 'remote login via xdmcp' at the login screen. However, there is no such option in ubunti 9.10

---

### Post by 2hot6ft2 on 2010-02-05
> **mahela007 said:**
> what's ssh and how do I do that? I've also read about something called XDMCP (is that right?).

About SSH and how to install it
[Installing Open-SSH]("http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html")

You'll want stronger keys so follow this for the keys
[Stronger SSH Keys than in the above guide]("http://help.ubuntu.com/community/SSH/OpenSSH/Keys")

And if you want a secure remote desktop using ssh
[Installing FreeNX]("http://help.ubuntu.com/community/FreeNX")

Attached is a pic of me using FreeNX and SSH to Securely Remote Desktop into my other pc and run a bit torrent client (Deluge) on it while at the same time transferring a file from the SSH server to the client using nautilus. Doing all this using g band WiFi adapters, and playing on the Internet at the same time, so it's not going real fast but it works flawlessly.

To put it the way you are: I am on PC A, running Deluge on PC B, and transferring a file from PC B to PC A.
There could be someone else using PC B at the same time but there isn't at the moment.

I can also do this from the Internet not just on the local network (LAN) as long as PC B is running and has SSH and FreeNX running.

Is that the kind of thing you have in mind?
:guitar:

---

### Post by VcDeveloper on 2010-02-05
[2hot6ft2]("http://ubuntuforums.org/member.php?u=568708"), I'm trying to set-up a Bazaar Version Control Server where my developers can collaborate.  Will these links also show me the best way to set-up this type of server?  This will not only be for LAN but also far a WAN.

---

### Post by mahela007 on 2010-02-06
> **2hot6ft2 said:**
> About SSH and how to install it
[Installing Open-SSH]("http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html")

You'll want stronger keys so follow this for the keys
[Stronger SSH Keys than in the above guide]("http://help.ubuntu.com/community/SSH/OpenSSH/Keys")

And if you want a secure remote desktop using ssh
[Installing FreeNX]("http://help.ubuntu.com/community/FreeNX")

Attached is a pic of me using FreeNX and SSH to Securely Remote Desktop into my other pc and run a bit torrent client (Deluge) on it while at the same time transferring a file from the SSH server to the client using nautilus. Doing all this using g band WiFi adapters, and playing on the Internet at the same time, so it's not going real fast but it works flawlessly.

To put it the way you are: I am on PC A, running Deluge on PC B, and transferring a file from PC B to PC A.
There could be someone else using PC B at the same time but there isn't at the moment.

I can also do this from the Internet not just on the local network (LAN) as long as PC B is running and has SSH and FreeNX running.

Is that the kind of thing you have in mind?
:guitar:
yes.. this is what I want. However, I'm not that concerned about security as there are only two computers on my LAN and I don't mind disconnecting from the internet. can't I just use this xdmcp thing?

---

### Post by Andreas1 on 2010-02-06
```
aptitude install ssh
``` (this installs the ssh server, the client is usually already installed, so do this at least at the computer you want to log in to)
```
ssh username@ip_of_computer
```
or
```
ssh username@hostname_of_computer.local
```


EDIT: if you want to run graphical applications, you can do
```
ssh -X [email]username@hostname.local[/email]
```
For more information, type ```
man ssh
```
and if you want to share the entire desktop, try System > Preferences > Remote Desktop and Applications > Internet > Remote Desktop Viewer (NOTE: this is not ssh and is not secure for it is not encrypted, assuming security is a concern).

This xdmcp also looks interesting, i have not used it yet though.

---

### Post by mahela007 on 2010-02-06
Could you please explain what ssh connects to? Does it act as a kind of 'encrypter' between the x client and server to add security? If this is the case, how will it allow me to log into the other Ubuntu PC as another user?

---

### Post by Andreas1 on 2010-02-06
> **mahela007 said:**
> Could you please explain what ssh connects to? Does it act as a kind of 'encrypter' between the x client and server to add security? If this is the case, how will it allow me to log into the other Ubuntu PC as another user?

when you try to connect to your "server" computer for the first time, ssh keys will be generated to identify the computers to each other. all further communication between your computers will be encrypted by these. then it will prompt for the password of the user on the server computer. example:

computer1 is "aspire", user is andreas
computer2 is "travelmate", user is andi

now i (andreas) open a terminal on aspire and type ```
ssh andi@travelmate.local
```

then ssh asks me to verify that the other computer is in fact travelmate. then i enter andi's password.
that's my naive understanding of what's going on, if i'm wrong, someone please correct me...

---

### Post by noway2 on 2010-02-06
SSH stands for Secure Shell.  It gives you remote access, via a terminal, to your remote PC.  It is designed with security in mind and all traffic between the two systems, including the authentication and login is handled via an encrypted link.  As SSH is a terminal program, often times it is convenient to have remote GUI / desktop access.  There are several ways to accomplish this.  Currently, the best option is FreeNX, which was suggested in one of the earlier responses.  FreeNX is reliable and secure and it compresses data for better response.  VNC used to be a popular choice, but it is also one of the most common ways that systems get cracked.   

In an earlier post you mentioned "not being concerned about security".  With all do respect, this would be a grave mistake.  It takes very little effort to keep things secure and the consequences of not can be painful.  Take a look in the security forum if you would like to get an idea of what others have gone through after their systems were cracked.

Installing SSH is as simple as issuing a sudo apt-get install command and then performing a little bit of setup.  Usually it works right out of the box.  To connect to another PC you will either need to know its network name or IP address.  You then connect to it with the command ssh user@remotepc, where user is the account you wish to log on as and remote pc is the name or IP of the remote device.

If you are running only under a LAN that should be all you need to do.  If you wish to access the PC from a WAN or the internet, you will need to open a port in your router / firewall.  SSH typically runs under port 22.  Some will advocate moving this to an obscure port claiming security by obscurity.  In actuality this offers little to no protection as a port scan will reveal the true location.  Instead you should use key based authentication (and turn off passwords) and install a program such as deny-hosts or fail2ban which blocks attempts to break into your system.

Again, all of this takes very little effort.  Both the security and server platforms here will provide you all the information you need.  A google search will also bring up plenty of ubuntu wiki pages that are excellent how to documents.

---

### Post by mahela007 on 2010-02-06
Thanks.. great post (specially the part about not ignoring security). Thanks to Andreas1 as well. 
I'm trying to get a little background on this subject and I'd like to ask you about xdmcp. Do you know anything about that? I heard it's insecure and that by default its disabled in the Ubuntu 9.10. What's the difference between using ssh and XDMCP?
Also, I was reading up about ssh in Linux and I saw that X11 server-client communications (I don't know the technical term for messages between X servers and clients) can be sent over ssh allowing the user to have graphical applications. Is this correct?

---

### Post by mahela007 on 2010-02-06
well guys.. I finally got it.. I got ssh up and running. Everyones' post were useful.. (I mean that).
Any advice on running a graphical application will be greatly appreciated. I have tried
```
ssh -X username@hostname.local
```but that doesn't seem to be enough. I know I have to start the X server on that machine.. but I don't know how to do it..

---

### Post by Andreas1 on 2010-02-06
> **mahela007 said:**
> well guys.. I finally got it.. I got ssh up and running. Everyones' post were useful.. (I mean that).
Any advice on running a graphical application will be greatly appreciated. I have tried
```
ssh -X username@hostname.local
```but that doesn't seem to be enough. I know I have to start the X server on that machine.. but I don't know how to do it..

if you have a desktop environment like gnome or kde or something on that machine then you should not have to do anything. do you mean the x server or the ssh server?

EDIT: i have a standard desktop install on both machines, i am not sure how it works if that is not the case.

---

### Post by mahela007 on 2010-02-06
I have a standard desktop installation on both machines as well. I meant that the X server doesn't run by default on all vitrual terminals. I though that when one logs into to a new terminal the X server must be started. ( This is because the terminals you can access by using the Ctrl + Fn keys are text based and don't have graphics. )
EDIT : Never mind.. I figured this one out with some tutorials.

---

