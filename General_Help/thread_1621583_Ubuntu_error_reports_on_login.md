---
title: "Ubuntu error reports on login"
date: 2010-11-14
forum: General Help
---

### Post by Ferto on 2010-11-14
A couple of days again, I enabled the option "don't ask password on login" on my laptop, which has been running on a full install of Ubuntu for months. The usual loading screen appears and the normal login menu pops up. I select my username and login automatically proceeds. Normally, I hear a sound, the brown background changes into my desktop and my desktop items and the control bar appears. However, currently while booting, the brown screen on the background doesn't even change and a couple of error reports appear.

> Could not update ICEauthority file home/lennard/.ICEauthority
X Close 

I hit Close and another screen appears.

> There is a problem with the configuration server.
(usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
x Close

I hit Close again and another error appears. This one looks more like the layout my computer usually have, unlike the previous two, which look grey and more simple. Around this time, a popup in the top right corner of the screen appears telling me I don't have much battery power left. This was usually the first thing that appears when logging in before all this happened.

> Nautilus could not create the following required folders:
/home/lennard/desktop, /home/lennard/.nautilus

Before running Nautilus, please create these folders or set permissions such that Nautilus can create them.

As I'm typing this, another screen appears and I have not seen it before. It say Update Information and Information available. It tells me about a security passphrase and it also features the button "Run this now". I run this, enter my password and receive a passphrase I have received earlier when I encrypted my home file. Nothing else happens so I hit the other button "Close". I also hit the Close button on the window about Nautilus. Nothing else happens for minutes, so I hit the power button and the usual screen pops up that offers me the usual choices (hibernate, restart, shut down etc.) I press suspend and wait for it to suspend. I hit spacebar and the normal screen appears that tells me Lennard Mysurname is logged in and it asks for my password. Also, the options switch user, leave message etc. are present. I enter my password and press enter. The screen becomes grey and tells me "Checking..." This usually takes a few seconds, but now, it goes on for minutes so I perform a hard reboot.

Please help me. I'm pretty much a big tool in Linux and I don't know what to do now. I can't use my computer at all at the moment.
Thanks a lot in advance.

Lennard

---

### Post by Ferto on 2010-11-14
Sorry for bumping this up, but help would be really, really apreciated right now. My exams are coming up and I really need my files right now. :P

---

### Post by Metaxa on 2010-11-14
I am also receiving the first error.

I can log in as normal, but I have no volume controls. I still have sound though, just can't control the volume.



Metaxa

---

### Post by Ferto on 2010-11-15
Strange. So the problem with my GUI probably has to do with something in the other two error reports. Can anybody tell us more about this? I think their might be an easy way to solve this problem because my computer still boots, only when logging in do I have trouble. I have had this before on the same computer, when there were still multiple user accounts, and I could normally log in to the other accounts, if I remember correctly.
Anyway, I can still enter the white on black text thingy. :P So could it be that I just have to change a setting and create the two folders mentioned using that? I know this can be done but I don't know how and I don't know if that is really the solution. Can anyone tell me more about this?

---

### Post by Ferto on 2010-11-16
Can no-one help me?
Can anyone even tell me if I can retrieve my files and reinstall the entire thing?

---

### Post by trivialpackets on 2010-11-22
sudo chown -R user:user /home/user/.*

user being your username each time may help.  Then reboot.  Did you install Veetle player for streaming video?

---

### Post by nostoq on 2010-11-22
-

---

### Post by nostoq on 2010-11-22
-

---

### Post by nostoq on 2010-11-22
[SIZE=2]-
[/SIZE]

---

