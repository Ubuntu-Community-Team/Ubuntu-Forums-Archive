---
title: "The Never Ending Login Loop Of Doom"
date: 2011-04-04
forum: General Help
---

### Post by nickTaylor1181 on 2011-04-04
Ok, so yesterday I saved something to the desktop... then found I couldn't click on the desktop.

Then found I couldn't start any file-browser windows at all, unless I killed the desktop nautilus.

Bit of a hassle. Reinstalled Nautilus... rebooted...


... and 24 hours of hell later, I still haven't managed to get past this screen

[http://www.weirdsky.com/miscImages/login.jpg](http://www.weirdsky.com/miscImages/login.jpg)

It accepts the password... sputters for a bit, then asks for the password again. And again, and again, and again.

So.

Ubuntu 9.10 which has been running/updating on an AMD64 quad laptop without problems for a year

Dual booting with Windows 7 using Grub2 - both of which appear to work fine.


I've tried 24 hours worth of suggestions from other threads in these forums and elsewhere - during which, I've removed Nautilus completely, and can't get it back... because when I try to do the apt-get install nautilus thing from recovery-mode (with networking) it shows messages like these

[http://www.weirdsky.com/miscImages/login2.jpg](http://www.weirdsky.com/miscImages/login2.jpg)

for an eternity without actually doing anything. I've tried apt-get update, which looked like it was working, but who knows. I can post photos of that as well if need be.

I'm getting nowhere with this - probably have 2 problems... something that's stopping apt-get install from working and something that's causing the login loop.

I really really really don't want to wipe it and start again - it takes about a week to set a new system up.



Any ideas?

---

### Post by nickTaylor1181 on 2011-04-04
ok - .xsession-errors said something about not being able to access ~/.profile - although it was clearly there.

I renamed it - and now I don't get the login loop, just a black screen with a (correctly scaled) mouse pointer - and nothing that can be done in the way of key-strokes or left/right-clicks.

The .xsession-errors talk about not being able to create directories in ~/ - things like "Movies", "Pictures" etc. Stuff I do't use.

So... it's looking like the entire desktop has gone - which leaves me (I think) with the inability to update it using apt-get (even though I do have a connection (can ping google etc)) - I just get this - after about 20 minutes of waiting

[http://www.weirdsky.com/miscImages/login2.jpg](http://www.weirdsky.com/miscImages/login2.jpg)

Is there some way of installing/updating/repairing the desktop using a .deb file. 


Any ideas? This is seriously doing my head in.

---

### Post by nickTaylor1181 on 2011-04-04
Ok - that's sorted.


I booted from a Ubuntu Live CD... and did this

1) open terminal 

2) sudo mount /dev/hda1 /mnt 

(look in system->admin->disk utility for location of the main file-system. Mine was actually /dev/sda5 rather than /dev/hda1)

3) sudo chroot /mnt 

4) apt-get update 

5) apt-get upgrade

6) apt-get install ubuntu-desktop

--

I did all of this from the wifi connection rather than the LAN cable - which for some reason wasn't resolving the repositry addresses... or it was, but it was being really really ******* slow. Dunno.


So there you go. For the record, if anyone else needs to do this.

---

