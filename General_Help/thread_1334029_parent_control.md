---
title: "parent control"
date: 2009-11-22
forum: General Help
---

### Post by kennethtb on 2009-11-22
Hi I have a young daughter just starting to use internet sites for her favorite Disney shows,games and children's educationial exercises etc and as before with Windows I could easily find quite a number of parent control softwares so that all one had to do is to select any area that you as a parent feels is unsafe (such as porn sites which could be entered unknowingly just by entering Barbi for instance)  
I have looked in Synaptic/Ubuntu 9.10 but could not find anything that allows custom settings for parents... an  example would be the free K9 Web Protection software.

---

### Post by chillicampari on 2009-11-22
I've never used it, but I see a lot of posts here about [http://dansguardian.org/](http://dansguardian.org/)

It should be in the repos too (or at least is on Jaunty).

---

### Post by MelDJ on 2009-11-22
you could use firefox add ons like WOT: [https://addons.mozilla.org/en-US/firefox/addon/3456](https://addons.mozilla.org/en-US/firefox/addon/3456). look for others ff add ons here: [https://addons.mozilla.org/en-US/firefox/browse/type:1/cat:12](https://addons.mozilla.org/en-US/firefox/browse/type:1/cat:12)


+1 for dansguardian. 

this may seem quite cheap but see the link in sig. its a tutorial made by me for parents to stop their kids watching porn .

regards

---

### Post by kennethtb on 2009-11-23
I have tried Dansguardian ..but cannot find it after installing???  Ubuntu 9.10 - have tried Webcontentcontrol but its in beta and unstable and blocks Firefox in default settings. I tried to uninstall it afterwards but cannot (symantec or terminal) its totally blocked! Gchildcare is the next possibility but this software is incomplete and not yet available and the suggested Firefox option is not a parent control ..its for emails around the family with children .. none of the well known 3rd party parent control softwares have a version written for Linux!
This situation should be taken more seriously by Linux in order to support families with children so I reluctantly now am being forced to go back to Windows

---

### Post by Treeh on 2009-11-23
> **kennethtb said:**
> I have tried Dansguardian ..but cannot find it after installing???  Ubuntu 9.10 - have tried Webcontentcontrol but its in beta and unstable and blocks Firefox in default settings. I tried to uninstall it afterwards but cannot (symantec or terminal) its totally blocked! Gchildcare is the next possibility but this software is incomplete and not yet available and the suggested Firefox option is not a parent control ..its for emails around the family with children .. none of the well known 3rd party parent control softwares have a version written for Linux!
This situation should be taken more seriously by Linux in order to support families with children so I reluctantly now am being forced to go back to Windows

Did you try launching Dansguardian via the run command dialogue (Alt + F2 --> type in "dansguardian" --> enter)?

I've never used it, but I presume this will work.

---

### Post by kennethtb on 2009-11-23
HI  yes thanks I tried this alt+f2 but no luck.. dansguardian is showing as installed in Synaptic but I cannot find it it anywhere .. under search or terminal it says no such file exists.

---

### Post by mgol on 2009-11-23
Maybe You made a mistake? If You installed it should be there. You can also try:
```
locate dansguardian
```
to find a location of the file and execute it directly.

I don't know this app but if it should show in menus beware that menus often refresh too rarely, I filed a bug here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/473383](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/473383)
If You want to make sure if it's refreshed, invoke:
```
killall gnome-panel
```
It will restart all panels and menus.

---

### Post by kennethtb on 2009-11-23
Hi again no luck ...entering "locate dansguardian" in the terminal does nothing yet its still showing as installed in synaptic? I tried the synaptic reinstall option - it ran and reinstalled  but again same problem ... where is it???
I must say that this new 9.10 seems full of small problems, for instance using the Janitor removal for highlighted items returns a message that there was nothing to clean??
I asked an apple question the other day on the Macworld forum which was answered fully and correctly and yet even after several days my thread was STILL  showing on the first page ... does that tell you something??

---

### Post by 3rdalbum on 2009-11-23
dansguardian works in conjunction with squid or some other proxy program. It's not something you launch from the Applications menu - if it was, then it would be too easy for the child to circumvent. It launches automatically on startup.

The configuration file for dansguardian is at /etc/dansguardian/dansguardian.conf; alternatively I believe there are a few graphical frontends to it, try doing a web search. There's one in Ubuntu Christian Edition; if you can get a Debian package of it, then you can install it in Ubuntu.

> I asked an apple question the other day on the Macworld forum which was answered fully and correctly and yet even after several days my thread was STILL showing on the first page ... does that tell you something??

On the official Apple forum, you get buried in five minutes by people complaining that all their iPhone apps have stopped working or that they can't log into their WEP wireless networks.

---

