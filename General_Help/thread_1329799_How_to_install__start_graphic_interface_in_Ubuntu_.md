---
title: "How to install / start graphic interface in Ubuntu 9.10 server edition"
date: 2009-11-17
forum: General Help
---

### Post by dxnation on 2009-11-17
I just installed ubuntu server 9.10 on a machine and I can login with the command line interface.

However, I would like to get on a Graphic Interface and work on the internet.

Not sure how can I start graphic interface.

some help will get me started with my system :)

---

### Post by oldfred on 2009-11-17
Just like on the desktop:

startx

but of course you have to install a graphical interface first for gnome:

sudo apt-get install gdm ubuntu-desktop

I do not know the command line install for kde or any of the lightweight graphical front ends.

---

### Post by blueridgedog on 2009-11-17
sudo apt-get install ubuntu-desktop

---

### Post by fancypiper on 2009-11-17
I would start with maybe a simple window manager such as fluxbox.  Just follow the prompts when trying to start it.

sudo apt-get install fluxbox fluxconf

After that installs, command:
startx
Install the suggested programs until you can launch fluxbox.

[Fluxbox]("https://help.ubuntu.com/community/Fluxbox")

---

### Post by dxnation on 2009-11-18
whan I typed: startx
it gave me this:
The program 'startx' is currently not installed. You can install it by typing: sudo apt-get install xinit
startx: command not found.

Then I tried: sudo apt-get install xinit

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package xinit.

I tried sudo apt-get install ubuntu-desktop
It came up with

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-desktop


I have the ubuntu server 9.10 CD in my CD-ROM Drive...is there anyway I can fetch or access the package from this CD and install GNOME or KDE or any other available desktop environment

I want to use ubuntu server 9.10 as "Openbravo" ERP works on this distro.

---

### Post by Cheesemill on 2009-11-18
You need either internet access or the alternate install CD to be able to install a GUI onto the server edition (note that having a GUI on your server isn't recomended in the first place), the server CD doesn't contain any of the required packages as it's not meant to be used with a GUI.

---

### Post by dxnation on 2009-11-18
Thank you for the reply, I will try to get connected using internet and then try installing the GNOME interface.

Any ideas how can I configure my wireless using command line. My office does not have any wired connection.

---

### Post by Cheesemill on 2009-11-18
You're better off just installing the Desktop version and then installing the server kernel if that's what you want. You'll end up with an identical system to the method you're trying at the minute.

Although the question remains, why would you want a GUI on a server in the first place.....

---

### Post by scottuss on 2009-11-18
Yeah, so far from what I can tell, you just want to use this as a desktop PC to surf the web, right? If so, you want the Desktop installer CD, not the Server one.

It's way easier to get up and running with your Wireless and everything else for that matter if you use the Desktop version, you get a GUI "out of the box"

Server edition is mainly for servers that perhaps won't even have a monitor plugged in (my home server only has power and network!)

Edit: Ah, I failed to read the bit about OpenBravo! Sorry about that. Actually you can install it on the Server or Desktop edition, so maybe you could go for the Desktop install and then install your ERP system afterwards?

---

