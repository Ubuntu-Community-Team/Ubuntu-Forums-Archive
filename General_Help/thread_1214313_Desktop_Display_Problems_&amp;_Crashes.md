---
title: "Desktop Display Problems &amp; Crashes"
date: 2009-07-15
forum: General Help
---

### Post by Alan Jack on 2009-07-15
Hi.

I've been really looking forward to working under Linux, and I'm really frustrated - every time I try to install Ubuntu, I get the same problems.

1: Desktop doesn't display.

I basically get a mess of STUFF where the desktop should be - shapes, colours, bits that look like they've dumped from a buffer somewhere.  Changes as I'm using things - most often, when a new window opens, part or some of the desktop is filled in with part of the window, stretched and distorted.

2: Crashes under odd circumstances.

So far I've only found 2 things that trigger it - one is clicking the "quick start" firefox link at the top, and another is when I enter the password for the update manager (which sucks, because I thought maybe problem #1 was a graphics driver issue that the update manager might fix!).  Each time is the same - it drops out to the command prompt, then quickly fires back to the Ubuntu login screen.

Both issues have plagued me since I started (with a Live CD installation using the latest build (Jaunty?)) and have been with me no matter what I do (complete HD scrub, windows reinstalled, booted from Live CD, same problem, made new Live CD, same problem, now installed through Wubi).

Help me, Ubuntu forums users, you're my only hope!

---

### Post by HiImTye on 2009-07-15
have you tried

system>administration>hardware drivers?

if that yields no results you can also use

system>preferences>display

to change the refresh rate/screen resolution and see if that helps your display issues. lastly use

system>administration>update manager

to try and update your system. it is likely that whatever issues you are experiencing will go away once you do that (enabling you to use synaptic). alternatively you can go to

accessories>terminal

and type in

'sudo apt-get update && sudo apt-get check && sudo apt-get update'

this will refresh your repository lists, check to make sure you aren't missing dependencies and finally update your packages to the latest

---

### Post by Alan Jack on 2009-07-16
> **Alan Jack said:**
> Hi.
2: Crashes under odd circumstances.

So far I've only found 2 things that trigger it -  another is when I enter the password for the update manager 

Yeah, I can't use the Update Manager.

I have checked the hardware drivers, and received the message "No Proprietary Drivers Are In Use On This System".  I'm going to try and find some, but I'm doubtful - Everything else on top of the desktop displays perfectly, I don't think that would happen if it was a driver issue, would it?  Surely its more likely to be an issue with the GNOME desktop?

[IMG]http://i26.tinypic.com/3004kmf.png[/IMG]

Here's a picture, if it helps.

Have also discovered that if I maximise windows, they become distorted too, so will look into drivers.

---

### Post by HiImTye on 2009-07-16
> **HiImTye said:**
> alternatively you can go to

accessories>terminal

and type in

'sudo apt-get update && sudo apt-get check && sudo apt-get update'

this will refresh your repository lists, check to make sure you aren't missing dependencies and finally update your packages to the latest

did you try this?

---

### Post by HiImTye on 2009-07-16
whoops, should be:

sudo apt-get update && sudo apt-get check && sudo apt-get upgrade

heh, guess I got ahead a meself

---

### Post by Alan Jack on 2009-07-16
> **HiImTye said:**
> whoops, should be:

sudo apt-get update && sudo apt-get check && sudo apt-get upgrade

heh, guess I got ahead a meself

Alas, I did.  To no avail.  :(

It punted out a list of repositories twice, and said something to the effect of everything being up to date.

Am attempting to get Wubi to install Kubuntu to determine if its a GNOME issue (really wanted GNOME though!)

---

### Post by Alan Jack on 2009-07-17
Interesting ... no problems running Kubuntu (other than the fact I don't like it).  So its a problem with the GNOME desktop application.  Anyone else got any idea why this might be happening?

---

