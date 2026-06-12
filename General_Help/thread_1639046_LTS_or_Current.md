---
title: "LTS or Current ?"
date: 2010-12-06
forum: General Help
---

### Post by rectagonal on 2010-12-06
I am about to build an Ubuntu Machine for a friend as a gift who is in desperate need of a new  computer. I will be providing the vast majority of technical support (and have been doing so in the past for her Mac). 

I am having trouble deciding which version to load. The latest LTS or the current version. Has anybody been in my shoes before, what did you pick and why?

I would like to set it up with the oem install option so they get to pick their user name and all that jazz, but I assume that is available on both.

Thanks

P.S. I typically use Debian proper so I have no personal preference.

---

### Post by Zzl1xndd on 2010-12-06
When I configure systems for new Linux users I normally go with the LTS. 

I find most of them will want to avoid upgrading as long as they can, and the LTS's tend to be a little more stable.

---

### Post by madjr on 2010-12-06
> **rectagonal said:**
> I am about to build an Ubuntu Machine for a friend as a gift who is in desperate need of a new  computer. I will be providing the vast majority of technical support (and have been doing so in the past for her Mac). 

I am having trouble deciding which version to load. The latest LTS or the current version. Has anybody been in my shoes before, what did you pick and why?

I would like to set it up with the oem install option so they get to pick their user name and all that jazz, but I assume that is available on both.

Thanks

P.S. I typically use Debian proper so I have no personal preference.

if its a new user i would consider linuxmint first, because it also comes loaded with everything preinstalled, thus less support.

mac users will find it easy to use and the looks are similar (in version 10), just move the panel to the top, so they feel more at home :p

also pinguyOS is a nice mac clone and easy transition:

[http://freekko.blogspot.com/2010/11/2-great-looking-distros-released.html](http://freekko.blogspot.com/2010/11/2-great-looking-distros-released.html)

If she has used linux before and dont mind some extra software installations her self, then i would probably use normal ubuntu 10.10. I have both installed 10.04 / 10.10 and both are stable. But 10.10 has some software that is more up to date.

---

### Post by 3Miro on 2010-12-06
LTS in this case. This will be way less hassle for you. Don't touch it until it goes to 12.04.1

Current is for more adventurous people or if you absolutely need a newer feature that you cannot get from a PPA.

---

### Post by NightwishFan on 2010-12-06
As a long time Ubuntu administrator, I advise you to go with the LTS edition. Way fewer question marks. Set up the updates to come once a week and automatically. The process to upgrade to the next LTS is easy enough to do every three years and the user can probably handle it themselves.

---

### Post by madjr on 2010-12-06
> **NightwishFan said:**
> As a long time Ubuntu administrator, I advise you to go with the LTS edition. Way fewer question marks. Set up the updates to come once a week and automatically. The process to upgrade to the next LTS is easy enough to do every three years and the user can probably handle it themselves.

i dont think am too comfortable letting users upgrade themselves.

Things usually break. Some have better luck, but it can be a gamble.

i prefer taking 20 mins to install to a fresh partition and avoid possible hours / days of headaches and then resorting to install to the new partition anyway...

---

### Post by NightwishFan on 2010-12-06
I can understand. Though to be honest I have had only a successful experience with upgrades, the biggest issue I had was GDM still showing the lucid background on Maverick.

My recommendation that they could "do it themselves" comes from a friend who had a blank computer (and could not afford a new windows) he installed ubuntu 9.10 himself, and upgraded since then to 10.04 and 10.10. He said he has had no problems, and did the upgrade without even me prompting him. :D

He is not a "computer admin" either. He is just a normal guy that browses email.

---

### Post by philinux on 2010-12-06
Moved to General Help.

---

### Post by uRock on 2010-12-06
I agree with using the LTS version, so that your friend doesn't get upset with having to upgrade in little more than 12 months.

---

### Post by Slim Odds on 2010-12-06
> **NightwishFan said:**
> As a long time Ubuntu administrator, I advise you to go with the LTS edition. Way fewer question marks. _**Set up the updates to come once a week and automatically.**_ The process to upgrade to the next LTS is easy enough to do every three years and the user can probably handle it themselves.

Just curious how you handle updates that require a reboot.

---

### Post by matt_symes on 2010-12-06
Hi

I would also suggest 10.04 LTS. Make sure you install the restricted  extras packages for the codecs, DVD and the flash plugin.

Kind regards

---

### Post by madjr on 2010-12-06
> **NightwishFan said:**
> I can understand. Though to be honest I have had only a successful experience with upgrades, the biggest issue I had was GDM still showing the lucid background on Maverick.

My recommendation that they could "do it themselves" comes from a friend who had a blank computer (and could not afford a new windows) he installed ubuntu 9.10 himself, and upgraded since then to 10.04 and 10.10. He said he has had no problems, and did the upgrade without even me prompting him. :D

He is not a "computer admin" either. He is just a normal guy that browses email.


it would be the best thing if full ubuntu upgrades gave a "safe option" to keep a **snapshot** / backup (maybe even keep a partition) of the old one.

Then after you dont need it anymore it would just delete it and free up the space.

am not sure how it would be done, but that is probably the only way for an upgrade to be **fail-proof** (or at least "fail-safe" by allowing one to revert back.).

People have huge drives these days, so if you have tons of unused space, using a few gb temporarily that you wont even notice to make something fail-safe is more than welcome.

---

### Post by NightwishFan on 2010-12-06
> **Slim Odds said:**
> Just curious how you handle updates that require a reboot.

They will take effect whenever the user chooses to reboot.

> **madjr said:**
> it would be the best thing if full ubuntu upgrades gave a "safe option" to keep a **snapshot** / backup (or even a partition) of the old one.

Hey help the op not me! I know what I am doing. :) They have never had any issues for almost a year now. Though I do agree. However trust me. On my particular case, helping them close a tab in Firefox is a big issue I deal with. So worrying about system backups for them to do is out of the question. I would have to do it myself anyway.

---

### Post by uRock on 2010-12-06
> **madjr said:**
> it would be the best thing if full ubuntu upgrades gave a "safe option" to keep a **snapshot** / backup (maybe even keep a partition) of the old one.

Then after you dont need it anymore it would just delete it and free up the space.

am not sure how it would be done, but that is probably the only way for an upgrade to be **fail-proof** (or at least "fail-safe" by allowing one to revert back.).

People have huge drives these days, so if you have tons of unused space, using a few gb temporarily that you wont even notice to make something fail-proof is more than welcome.
I recommend clean installs over upgrades just because there is no easy-to-use defrag software for EXT4.

From what I have read BRTFS will make it possible to take snapshots, which may help with upgrades in the future. I haven't read to see if there is a defrag tool for BRTFS yet.

---

### Post by madjr on 2010-12-06
> **uRock said:**
> I recommend clean installs over upgrades just because there is no easy-to-use defrag software for EXT4.

From what I have read BRTFS will make it possible to take snapshots, which may help with upgrades in the future. I haven't read to see if there is a defrag tool for BRTFS yet.

I hope BTRFS can help solve one of the oldest problem. Support threads could be cut down like 30% :o

many more reviews would be positive and OEMs happy :p

---

### Post by searchfgold6789 on 2010-12-06
Problems with upgrading usually result from people doing a fresh install, and then changing their system in such a way that installing all of the new software on top of it will make their system ... not good.
If your friend plans on doing a fresh install of Ubuntu, usually using the main software that comes with it, and not doing any major hacking, in other words just *using* it, then I can guarantee that the upgrade will go just fine. So, in this case where it is just an everyday user that is not trying to get too fancy (e.g. fooling with hardware drivers) then the current release will be just perfect.
Also remember that you do not have to upgrade from a non-LTS release if you do not want to.
The real question is what *type* of ubuntu you want to install, and you know the computer better than I do, so have at it.
 - search

---

### Post by rectagonal on 2010-12-07
Well thanks for all the comments. Will probably be loading LTS on it, I had suspected that was the way to go, but suspected there might be a good case to be made for it to be running something more current. However the over whelming number of folks recommending LTS has convinced me my initial instinct was probably correct.

Thanks.

---

