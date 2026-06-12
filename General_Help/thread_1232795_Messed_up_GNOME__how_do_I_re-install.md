---
title: "Messed up GNOME : how do I re-install"
date: 2009-08-05
forum: General Help
---

### Post by uge on 2009-08-05
Hi guys,

Please don't tell me to look around in the forum.

I DID but I was too unsure because of linux version differences and also because of what I have done, and what I want to do... I guess it's a particular situation I've put myself in.

SO, I've got Ubuntu Deskop 8.04 LTS 64.
I don't want to reformat because it took me a while to configure
- RIBS
- LVM
and other stuff

however, I messed up GNOME.

How ? I installed a freakin audio driver that was made for SUSE by issued a SUDO ./install and now I can't login anymore.
I get the following message.
"You've been logged off less than 10 seconds after you logged in" blah blah blah and the log is about SEAHORSE-AGENT that can't open shared library because some audio file is missing.
So GNOME and even the FAILSAFE GNOME won't work.

Looking around the internet, I think I understood that SEAHORSE-AGENT is only used by GNOME.
So I hope I only messed up GNOME and not anything else (what do you think please ??)
Or maybe there's just a not-working-audio-driver floating in the kernel...

Luckily, my OpenVPN still works.

What I'd like to do, is completely removing GNOME and then reinstalling it.

Do you think it's a good idea ?

If so : how do I do that ;) ??


THANKS !!!

---

### Post by 3rdalbum on 2009-08-06
I think the more appropriate action would be to remove or blacklist the driver, and see if that helps Gnome to start up again.

---

### Post by uge on 2009-08-06
> **3rdalbum said:**
> I think the more appropriate action would be to remove or blacklist the driver, and see if that helps Gnome to start up again.

Hmm and how do I do that ?

---

### Post by lordbux on 2009-08-06
it doesnt see much serious
just a mess upa s you have said... try this.

from grub start in the recovery mode
soon you will get a blue screen with options 
NORMAL BOOT
FIX BROKEN PACKAGES
FIX X
...etc etc..or something like that.

just select fix X and keep your fingers crossed while 
the system do its job..

restart.

if still the thing wont get right and you wana try your idea 
jsut enter in recovery mode and 

enter```
 sudo apt-get install gnome
```

---

### Post by metalf8801 on 2009-08-06
> **3rdalbum said:**
> I think the more appropriate action would be to remove or blacklist the driver, and see if that helps Gnome to start up again.

From what I've found I think you need to 
Open /etc/modprobe.d/blacklist file and add drivername using following syntax:
blacklist driver-name

I think the commands would be 

cd /etc/modprobe.d/blacklist 
blacklist "the name of the suse drive" 

please post if that works or not 
I hope this helps 
Dan

---

### Post by warp99 on 2009-08-06
Can you post the link to the SuSe modules you installed? You may be able to either uninstall the modules or just overwrite them with the correct Ubuntu .deb packages.

---

### Post by slakkie on 2009-08-06
aptitude reinstall ubuntu-desktop

---

### Post by uge on 2009-08-06
> **warp99 said:**
> Can you post the link to the SuSe modules you installed? You may be able to either uninstall the modules or just overwrite them with the correct Ubuntu .deb packages.


Hey that would really rock !!

But I can't really find the exact link.

I'll tell you how I got it.

[http://support.asus.com/download/](http://support.asus.com/download/)
type in search box : P5GC-MC/1333
choose OS : LINUX
In the "Other" download there is a section called "LINUX DRIVERS"
Within this file, after extraction, there is a subdir called "AUDIO" then "SUSE" and here you go.

Keep me posted :)

---

### Post by warp99 on 2009-08-06
Those modules that you built are only alsa drivers and the utilites so you can overwrite them from the command line. Just run the following:

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-ubuntu-modules-$(uname -r) alsa-utils alsa-base libasound2 libasound2-plugins
```

Just cut and paste the string, install then reboot. You should be back to normal with sound at least.

---

### Post by uge on 2009-08-07
> **warp99 said:**
> Those modules that you built are only alsa drivers and the utilites so you can overwrite them from the command line. Just run the following:

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-ubuntu-modules-$(uname -r) alsa-utils alsa-base libasound2 libasound2-plugins
```Just cut and paste the string, install then reboot. You should be back to normal with sound at least.

Hi warp99 !

Thanks so much for the reply.

I just ran the command above from my office through SSH session.

I was wondering : did it re-install SEAHORSE or at least SEAHORSE-AGENT in the process ?

Thanks :)

---

### Post by warp99 on 2009-08-07
> **uge said:**
> I was wondering : did it re-install SEAHORSE or at least SEAHORSE-AGENT in the process ?

Thanks :)

No it didn't reinstall SEAHORSE. I believe there is an interaction between pulseaudio and SEAHORSE for authentication so when one of the files was overwritten the error occurred. Now this is just a wild guess, so don't quote me on it. ;)

---

### Post by uge on 2009-08-07
> **warp99 said:**
> No it didn't reinstall SEAHORSE. I believe there is an interaction between pulseaudio and SEAHORSE for authentication so when one of the files was overwritten the error occurred. Now this is just a wild guess, so don't quote me on it. ;)

Hey Warp99

It worked !

Thanks so much !

Just got home, and simply logged in, and no problems at all !

---

