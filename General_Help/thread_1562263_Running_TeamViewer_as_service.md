---
title: "Running TeamViewer as service"
date: 2010-08-27
forum: General Help
---

### Post by prroots on 2010-08-27
I wish to start TeamViewer as a service in Ubuntu. In Windows I can load it as a service and remotely enter password at login screen. Is it possible with Ubuntu? Thanks
Pete

---

### Post by prroots on 2010-09-05
I wrote the same question to TeamViewer and have now received a response. They are very responsive even to users of the free version!

---

### Post by HermanAB on 2010-09-05
Got to wonder why?

The standard way to remotely manage a machine is with SSH.

---

### Post by prroots on 2010-09-05
> **HermanAB said:**
> Got to wonder why?

The standard way to remotely manage a machine is with SSH.
Thanks for the reply. I'm an Ubuntu newbie. Could you possibly refer me to a good (spelled easy) tutorial of some sort on how to do this. I will give it a try.
Pete

---

### Post by prroots on 2010-09-05
I just got SSH working with puTTY running on my wife's Windows laptop to log onto my laptop running SSH. The real purpose of this exercise is to connect my Unbuntu laptop before login. Is that possible? 

Edit: I am able to connect to my Ubuntu laptop prior to logging in running PuTTY on my wife's Window computer. Of course, I'm presented with a terminal window. How do I get to see the GUI (ie, desktop) from her computer? Basically, I want full access to the Ubuntu desktop. Basically, I'm asking what is the best and most recommended way of accessing the Ubuntu desktop from another computer?
Thanks
Pete

---

### Post by msmx5s on 2010-10-13
> **prroots said:**
> I wrote the same question to TeamViewer and have now received a response. They are very responsive even to users of the free version!

So what was their response? lol

---

### Post by peejay1977 on 2010-10-24
I've found a workaround for this, there's several topics out there about this and I understand SSH is the "Linux way" of accessing a remote machine but like you I wanted to use Teamviewer for the graphical side of things.

Using OpenVPN I can access my machine from anywhere and use SSH without having to open up my machine to all and sundry but it still wasn't straightforward enough. Plus I didn't want to have to mess about with convoluted workarounds.

1 workaround mentioned using auto-login on your account but my PC is used by my wife and son so don't want them getting into the PC as me.

What works for me is the following (on 10.10) :

System - Administraton - Login Screen - Set my account to login on machine startup.

System - Preferences - Startup Applications - I added both "xdm-screensaver lock" and "/usr/bin/teamviewer" as startup applications.

It seems the above hasn't always worked in the past for people so I can only assume on 10.10 something is more user friendly.

Now, everytime my machine boots it goes straight from the Ubuntu startup screen to the screensaver, I wiggle the mouse and it states its already logged in as me, but locked which is perfect for what I want.

I can then access my machine remotely and my wife can switch users and logon as her without causing me any issues (as long as I dont logon while shes using it) but this at least means I can reboot my machine without fear of losing Teamviewer connectivity.

Paul.

---

### Post by kuvanito on 2010-10-24
I have Teamviewer fully working on my desktop with Ubuntu 10.10
go to the website and download latest version,they now have a full version not the Beta any more.
I use this app in win and now in ubu

---

### Post by peejay1977 on 2010-10-24
> **kuvanito said:**
> I have Teamviewer fully working on my desktop with Ubuntu 10.10
go to the website and download latest version,they now have a full version not the Beta any more.
I use this app in win and now in ubu

So do I but it still doesn't start as a service, you have to logon to be able to start it under normal circumstances, unlike the Windows version.

---

### Post by ingber on 2010-10-24
I tried installing the latest teamviewer on Ubuntu 10.10 x64 remotely with
dpkg -i teamviewer_linux_x64.deb
but I got:


Selecting previously deselected package teamviewer5.
(Reading database ... 94135 files and directories currently installed.)
Unpacking teamviewer5 (from teamviewer_linux_x64.deb) ...
dpkg: dependency problems prevent configuration of teamviewer5:
 teamviewer5 depends on libc6-i386 (>= 2.2); however:
  Package libc6-i386 is not installed.
 teamviewer5 depends on ia32-libs; however:
  Package ia32-libs is not installed.
 teamviewer5 depends on lib32asound2; however:
  Package lib32asound2 is not installed.
 teamviewer5 depends on lib32z1; however:
  Package lib32z1 is not installed.
dpkg: error processing teamviewer5 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 teamviewer5

So, I did

# apt-get purge teamviewer_linux_x64
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package teamviewer_linux_x64
root@lin:/tmp# apt-get purge teamviewer
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package teamviewer
root@lin:/tmp# apt-get purge teamviewer5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl libgsasl7 libdbi-perl guile-1.8-libs
  mysql-server-core-5.1 mysql-client-core-5.1 libmailutils2 libdbd-mysql-perl
  libntlm0 libplrpc-perl mysql-server-5.1 mysql-client-5.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  teamviewer5*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 63.8MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 94601 files and directories currently installed.)
Removing teamviewer5 ...
Purging configuration files for teamviewer5 ...

---

### Post by peejay1977 on 2010-10-25
> **ingber said:**
> I tried installing the latest teamviewer on Ubuntu 10.10 x64 remotely with
dpkg -i teamviewer_linux_x64.deb
but I got:


Selecting previously deselected package teamviewer5.
(Reading database ... 94135 files and directories currently installed.)
Unpacking teamviewer5 (from teamviewer_linux_x64.deb) ...
dpkg: dependency problems prevent configuration of teamviewer5:
 teamviewer5 depends on libc6-i386 (>= 2.2); however:
  Package libc6-i386 is not installed.
 teamviewer5 depends on ia32-libs; however:
  Package ia32-libs is not installed.
 teamviewer5 depends on lib32asound2; however:
  Package lib32asound2 is not installed.
 teamviewer5 depends on lib32z1; however:
  Package lib32z1 is not installed.
dpkg: error processing teamviewer5 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 teamviewer5

So, I did

# apt-get purge teamviewer_linux_x64
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package teamviewer_linux_x64
root@lin:/tmp# apt-get purge teamviewer
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package teamviewer
root@lin:/tmp# apt-get purge teamviewer5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl libgsasl7 libdbi-perl guile-1.8-libs
  mysql-server-core-5.1 mysql-client-core-5.1 libmailutils2 libdbd-mysql-perl
  libntlm0 libplrpc-perl mysql-server-5.1 mysql-client-5.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  teamviewer5*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 63.8MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 94601 files and directories currently installed.)
Removing teamviewer5 ...
Purging configuration files for teamviewer5 ...

Have you tried launching the .deb file through the Ubuntu Software Studio and seeing if you have any more success? What about if you manually install those dependancies first?

---

### Post by ab8a on 2010-11-17
This is how I got mine to work for me.
Please note that i have auto login since this is a headless machine acting as a file server.
1. Setup permanent access on TeamViewer
2.Go to: system>preferences>startup applications
3. Drag your TeamViewer launcher to this
4. Done
Hope this helps someone.

---

