---
title: "System restore/last known good for Ubuntu?"
date: 2010-10-04
forum: General Help
---

### Post by y2k1 on 2010-10-04
I have 2 partitions on my laptop both ubuntu and neither of them i can get to the desktop. The errors seem to be something to do with Gnome or whatever. Can someone just tell me a simple solution because its getting me f'd off. The first partition went bust like a month ago and the other yesterday.

---

### Post by searchfgold6789 on 2010-10-05
You can't just have two partitions, you need swap space, right?
Anyway.
It would be helpful if you posted the exact errors, or at least a more precise description of them :)

---

### Post by y2k1 on 2010-10-05
I've got windows memory environment  tbh i dont know what swap space is but whatever....
 
 
turn on-screen with [ok] boxes keeps flashing (see below) then....
 
 
msg
Ubuntu is running in low graphics mode-need to config youreself
 
click on reconfig graphics-use default-nothing happens 
click on enter ubuntu in low graphics mode for just 1 time-black screen with some text with [ok] boxes....nothing happens
 
Is there some easy solution to this because I thought getting Linnux would get rid of this ****.  
 
Thanks btw

---

### Post by emarkay on 2010-10-05
What a convoluted way  to address a concept.  :)

It would be nice to at least have a "rollback" method - While I never trusted that concept in Window$, (as it has no  absolute idea of any non-MS package changes that don't 100% follow the rules, and/or other third-party crappy code) I think a global "Undo" would be a nice thing - say some sepatate area on teh volume that stores the last (selectable, of course) 5 or 10 commands, actions, and disk writes.

---

### Post by emarkay on 2010-10-05
> **y2k1 said:**
> I've got windows memory environment  tbh i dont know what swap space is but whatever....
 
turn on-screen with [ok] boxes keeps flashing (see below) then....
 msg
Ubuntu is running in low graphics mode-need to config youreself
 click on reconfig graphics-use default-nothing happens 
click on enter ubuntu in low graphics mode for just 1 time-black screen with some text with [ok] boxes....nothing happens
 Is there some easy solution to this because I thought getting Linnux would get rid of this ****.  
Thanks btw

What hardware do you have???  List it all - CPU, Graphics, Graphics and RAM memory, Ubuntu Version...

Have no idea what "windows memory environment  tbh" is, but 99% sounds like a graphics card issue.

---

### Post by Mark Phelps on 2010-10-05
> **emarkay said:**
> It would be nice to at least have a "rollback" method

For what it's worth, I totally agree with you.  Every time I see a post from someone who "upgraded" to a pre-release version of Ubuntu, had their machine fail for some reason, and only THEN learned that there is no roll-back feature, I keep hoping that SOMEDAY, Canonical will implement a roll-back capability.

And yes, before all of you other folks beat me up about it, I KNOW we're supposed to take backups (which, BTW I do on a regular basis) ... but telling a new person they should have backed up their PC BEFORE they did the upgrade, and now, their only recourse is a complete re-install, is not welcome news to them.

---

### Post by Quackers on 2010-10-05
I agree with you Mark. Even if a newbie did make backups, he/she needs a second computer to access the Web to find out what to do with them when his/her system won't boot any more. It's not the best impression to leave people with imo.

---

### Post by y2k1 on 2010-10-05
It's a Toshiba laptop "equium". Duo core. Thats all I know tbh 
 
This looks like it
[http://www.amazon.co.uk/Toshiba-Equium-P200-1ED-Widescreen-TruBrite/dp/B0013LM3DM](http://www.amazon.co.uk/Toshiba-Equium-P200-1ED-Widescreen-TruBrite/dp/B0013LM3DM)
 
Am I screwed? if I am how do I atleast delete the 2 partitions

---

### Post by Quackers on 2010-10-05
Which version(s) of Ubuntu did you install? 9.10, 10.04 etc

---

### Post by turqoisehex on 2010-10-05
Try booting from the Live CD (of the same version you have installed). If the graphics have a problem there, it's likely your hardware. 

If you're able to use the live CD, copy your old home directory from the version of Ubuntu you use most frequently to a USB stick (the contents will be hidden, press CTRL+H to show hidden files) and delete everything in your home directory (/media/PARTITION/home/username). PARTITION is the partition where your OS is installed. If you're comfortable with the command line that would look something like this:

```
cp -a /media/PARTITION/home/USER /media/USBSTICK
rm -r /media/PARTITION/home/USER
mkdir /media/PARTITION/home/USER
```

While you're in the Live CD, it may be worth while to create a linux-swap partition equal to the size of your RAM by using Gparted, which can be found in system-->administration-->gparted. You'll need to tell the OS to use it in fstab, but that's a longer discussion.

Reboot, and see if you're able to get into that Ubuntu. If you can, it means you made some kind of configuration change that screwed the graphics up. Your settings are safe on your USB stick, so copy the ones you need back to your home directory (firefox, etc) I suggest **not** copying any that are system related. (.gconfd, etc.)

---

### Post by ezsit on 2010-10-05
> ... but telling a new person they should have backed up their PC BEFORE they did the upgrade, and now, their only recourse is a complete re-install, is not welcome news to them.

One thing many people forget when dealing with a newbie, is that the newbie has just made the jump from consumer/user to administrator/system builder. 

When a typical person buys a computer, they have no experience loading OSes and software, maintaining a system, and fixing problems. When a person downloads a copy of Ubuntu, they make the leap into administrator/system builder.

What I find funny, is that many people expect the Linux distribution provider to make the move from user to administrator painless and pleasant. However, the user bears most of the responsibility. 

When I first started playing with different operating systems back in 1994, it was OS/2, BeOS, FreeBSD, and Linux. Windows taught me to make regular backups just to recover from its own failings, but having those backups made recovery easier. I learned through trial and error and re-installations what worked and what did not. I no longer have pitty on those who complain that they lost all their data due to tinkering. That is the nature of the beast. It is also how to learn what not to do very quickly.

---

### Post by Quackers on 2010-10-05
So running the Update Manager is "tinkering". Hmm.

---

