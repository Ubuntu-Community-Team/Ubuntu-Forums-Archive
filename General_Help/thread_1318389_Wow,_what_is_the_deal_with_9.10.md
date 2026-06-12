---
title: "Wow, what is the deal with 9.10?"
date: 2009-11-07
forum: General Help
---

### Post by EM man on 2009-11-07
I just upgraded from 9.04, which was essentially trouble-free, to 9.10, and it has frozen on me a couple times in the last 12 hours.  The first time, it at least let me restart, but the second time, I had to unplug it and pull out the battery! [it's a laptop] 

Also, Evolution is having a hard time.  A lot of times, when I start it, it will simply crash.

Will there be patches forthcoming?

---

### Post by Olav on 2009-11-07
> **EM man said:**
> I had to unplug it and pull out the battery! [it's a laptop]
Probably could have just pressed the "Fn" key together with the power button. Works on many laptops.

I am not sure what the problem is with your setup. I hear 9.10 runs just fine on most computers. Perhaps try a fresh install instead of an upgrade?

---

### Post by EM man on 2009-11-07
> **Olav said:**
> Probably could have just pressed the "Fn" key together with the power button. Works on many laptops.

I am not sure what the problem is with your setup. I hear 9.10 runs just fine on most computers. Perhaps try a fresh install instead of an upgrade?

Isn't it too late for that?

---

### Post by Olav on 2009-11-07
I'd say it's never too late for that. You do have your data backed up or at least in a separate partition, right? 8)

---

### Post by EM man on 2009-11-07
> **Olav said:**
> I'd say it's never too late for that. You do have your data backed up or at least in a separate partition, right? 8)

No, and my girlfriend has my 4 "Gigabyte" thumbdrive and is out of town, and I really don't feel like buying another one, although maybe I have no choice, because this windows-like behavior is really frustrating me.  So I have to back up:

1)  regular files
2)  all of my Evolution mail folders
3)  my bookmarks
4)  my cookie settings (I don't know if this is possible but I would really like to do it)

Can you think of anything else?

---

### Post by falconindy on 2009-11-07
/home
/etc

whatever other data you have outside /home.

---

### Post by Plumtreed on 2009-11-07
Are you being a bit impetuous? Perhaps you should try to find the source of your problem since you have already done the upgrade. You may go to all this 'backup' effort and do the install only to find the problem persists.

I did an upgrade and after sorting a rather simple glitch have found the upgrade to be perfect. From what I read it appears that a great many people have done successful up grades.

Perhaps you could describe your equipment and how the problem developed.

---

### Post by Olav on 2009-11-07
> **Plumtreed said:**
> Are you being a bit impetuous? Perhaps you should try to find the source of your problem since you have already done the upgrade. You may go to all this 'backup' effort and do the install only to find the problem persists.
You're not saying he doesn't have to have a backup of all his data, are you? It astounds me frankly that someone would dare upgrade an operating system without having backed up his valuable files. Then again I'm a freak who has a server in the attic for backups...

You are of course right that the freezes that he experiences could perhaps be solved without re-installing. Could be a video problem, or who knows what.

---

### Post by EM man on 2009-11-07
It might have nothing to do with the upgrade, but the timing is a bit suspicious.

---

### Post by NuclearStr1der on 2009-11-07
I've heard a lot of reports of Upgrading from 9.04 to 9.10 causing problems, as well as a lot of successful upgrades.

It's still safest to do a clean install after a new version is released it seems.

---

### Post by EM man on 2009-11-07
> **NuclearStr1der said:**
> I've heard a lot of reports of Upgrading from 9.04 to 9.10 causing problems, as well as a lot of successful upgrades.

It's still safest to do a clean install after a new version is released it seems.

Are the people with problems up excrement creek?

---

### Post by NuclearStr1der on 2009-11-07
Not really.

Just a lot of compatibility problems. Although the moaning is coming from people on Twitter and Facebook.

---

### Post by EM man on 2009-11-07
So does anyone have any idea what can be done about the problem wherein I can move the mouse pointer wherever I want, but it suddenly is unable to interact with anything on screen (e.g., unable to click on a selection, drag an item, highlight, etc.)?

---

### Post by Plumtreed on 2009-11-07
One thing that has been causing problems with the upgrade is the business about Grub & Grub2.

Use the system monitor to verify that you are booting into the correct kernel, it may look like Karmic but the actual kernel may be the old 9.04.
It should be 2.6.31-14

Whether you back-up or not is not relevant to the matter at hand. You have upgraded and an upgrade should work for most people. If you ran a straightforward 9.04 you should be able to upgrade seamlessly.

The early upgrades continued with ext3 and legacy Grub. You could then, if desired, change to Grub2.

---

### Post by Cybie257 on 2009-11-07
In the past couple of days I've had a few lock ups. No way out of them except hard reset. It seems to have began after the updates about last Wednesday. 

Kind of strange since all the way through Alpha 3 (Installed 1st time, Karmic), up to the RC, I had Zero issues. now that the official release it out, bugs are showing up. :(

-Cybie

---

### Post by graphius on 2009-11-10
Is it just me, or are some people getting very defensive about Karmic? 
I much prefer Ubuntu to the alternives (Microsoft is so kludgy...) but I too have been having problems, especially with Evolution, ocassionally with Firefox.
I am not a programmer, but it seems to me to be an issue with networking. And from the volume of complaints it seems to be real (and I have been having the same problems so it is real for me!!)
I know the devs are aware something is happeing, and I trust they are working on a solution, so please have sympathy with those of us suffering from this problem.

BTW I am using a new Toshiba laptop 
Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
Intel Corporation Wireless WiFi Link 5100

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
try [url=http://kember.net/articles/231/reisub-the-gentle-linux-restart]this[/[url] before performing a hard reboot. FWIW, I can never get the emergency reboot to work, but the emergency shutdown always has.

---

### Post by diskmaster23 on 2009-11-10
I personally haven't had more than a few small problems with 9.10. I would look into to find out why it isn't working, if that seems like a bit much. I would just backup your data and do a clean install. 

9.10 is a good OS and provides plenty of good features. It certainly has made leaps and bounds since 8.04.

---

