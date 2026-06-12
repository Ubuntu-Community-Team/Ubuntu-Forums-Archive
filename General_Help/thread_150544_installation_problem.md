---
title: "installation problem"
date: 2006-03-26
forum: General Help
---

### Post by dotal on 2006-03-26
when trying to install packeges with aptitude or dselect it requires 
superuser privilege.how do i get superuser privilege?
more details - tried to run install kubuntu-desktop which got stuck with a disk error of some kind.
now im geting the message - dpkg was interrupted run dpkg --configure -a

---

### Post by lupine_nickt on 2006-03-26
Prefix your terminal command with sudo (e.g. 'sudo dselect') - or run in a root terminal.

xF,
...Nick

---

### Post by eriefisher on 2006-03-26
Well I don't use either of those. Instead, I use Synaptic or Apt-get in the command line. 

In Synaptic, when you open it, it asks you for your password. This is the password you set up when you installed.

For apt-get, you type ina terminal-sudo apt-get update- and you will be asked for your password. Then type sudo apt-get install (package name).

Hope this is what you wanted.

eriefisher

---

### Post by dotal on 2006-03-26
[QUOTE=lupine_nickt]Prefix your terminal command with sudo (e.g. 'sudo dselect') - or run in a root terminal.

xF,
...Nick[/QUOTE]
how do you run in root terminal

---

### Post by lupine_nickt on 2006-03-26
Open Konsole (KDE Menu->System->Konsole), then choose Session->New Root Shell. The background goes ugly yellow to remind you that you're running as root.It'll ask you for your usual sudo password, so stick that in. 

From there, you'll be running as the root user in that shell - meaning you can screw up your installation any which way you please. Example: I accidentally deleted almost all my fonts last night, playing with getting a 32-bit chroot set up.

In general, sudo is a better method for running commands than running as root. But YMMV. I always end up having to type the commands twice, because I forget the sudo, which is a pain. 

xF,

...Nick

---

### Post by dotal on 2006-03-26
[QUOTE=lupine_nickt]Open Konsole (KDE Menu->System->Konsole), then choose Session->New Root Shell. The background goes ugly yellow to remind you that you're running as root.It'll ask you for your usual sudo password, so stick that in. 

From there, you'll be running as the root user in that shell - meaning you can screw up your installation any which way you please. Example: I accidentally deleted almost all my fonts last night, playing with getting a 32-bit chroot set up.

In general, sudo is a better method for running commands than running as root. But YMMV. I always end up having to type the commands twice, because I forget the sudo, which is a pain. 

xF,

...Nick[/QUOTE]
forgive me i didnt mention the fact im in server instalation now and trying to
install the gui interface.so i log in into the sever command line

---

### Post by lupine_nickt on 2006-03-26
Ah. Gotcha. 

Assuming that you haven't already set a root password...

Login to the server as your normal user, and type 'sudo passwd'. Enter your normal sudo password, then enter & re-enter whatever you want your root password to be. Having it the same as your normal password is easy but naughty - your best bet is to keep them different.

From console, to switch from normal user to super-user, just type 'su', then enter your newly-acquired root password when asked. If your prompt changes from a '$' to a '#', then you're in root mode. 

All the previously-mentioned caveats still apply, of course...

xF,

...Nick

---

### Post by dotal on 2006-03-26
o.k this worked but i keep geting errors in different stages so im gona try the
instalation from the beginning & will see if i have better luck.
thanks for the tips.

---

### Post by Barrakketh on 2006-03-26
Try using apt-get or Adept.

---

