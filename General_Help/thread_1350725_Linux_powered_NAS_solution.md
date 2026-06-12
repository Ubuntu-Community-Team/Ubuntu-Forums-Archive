---
title: "Linux powered NAS solution"
date: 2009-12-09
forum: General Help
---

### Post by peedeeramone on 2009-12-09
I am looking into getting a NAS for home use to be able to host media for streaming, file hosting, and possibly a low use webserver. I have been looking into the Linksys NSLU2. There is a strong community of modders who have put unslung (a specially modded linux) on it and have configured it to work well running ftp servers, daap servers, apache, and even databases. i will probably go with this route as they are relatively inexpensive (though discontinued) and perform well for a low power device.

the only problem with this solution is that I would need to have an external hard drive attached to function properly. while this is not really a big deal, i was wondering if there was a cheap NAS unit that is equally moddable (or at least has the same features) that can house drives inside itself. I would prefer if it came without drives preinsalled so i could purchase one separately to lower the cost. Linksys also has a device that is essentially this, but it apparently has very poor performance. 

just wondering if anyone has any suggestions. thanks

---

### Post by doas777 on 2009-12-09
I picked up a Synology DS209 for about 3 bills last week (no disks though; have to supply them yourself). 
comes with 3 usb ports for extra media, so i have about 5 TB on it now.
it is a linux system underneath the web-guis, and I have had some luck messing with the mounting and samba config and whatnot.

overall I'm pretty happy with it, except that usb drives are treated as externals, so it's hard to create perpetual named shares on them. instead I just created a symlink to one of the internal drives and voila, now I have a 3TB volume. most kewl.

---

### Post by memilanuk on 2009-12-09
I happened across [this link]("http://wiki.dns323.info/") a while back... installing Debian on a D-Link DNS-323, which seems kinda cool.

---

### Post by peedeeramone on 2009-12-09
yeah ive been looking at the dns-323. i just found it and think it might be exactly what im looking for.

thanks for the replies

---

### Post by michaelzap on 2009-12-09
I have a Buffalo LinkStation and an HP MediaVault. There are hacking possibilities for both of them, although the specific models that I have aren't ideal for running proper servers (they're both kind of old and limited). At some point I'll probably get a newer NAS that can be hacked to run Debian and use full-disk encryption.

---

### Post by SeeGo on 2009-12-10
Hi,

I'm very new to Ubuntu/Linux, but as a longer term project I'm going to build a small server initially for NAS/Squeezebox server and later for who knows what.  I currently have an older LinkStation which is modded (I just followed instructions) for Slimserver (Squeezebox server), but it's underpowered and difficult to update.  I decided that for me it might be better to have a small linux PC that can also do NAS instead of trying to shoehorn PC tasks onto a NAS.

Anyhow, I'm going to try using an MSI Wind Nettop (Atom 330) barebone system ($150 at Newegg).  Just need to add RAM (200-pin notebook style which I happen to have on hand) and a hard drive.  They also have an MSI Wind PC (Atom 230) barebone system for $120 after rebate.  Both systems have one 3.5" and one 5.25" bay (Newegg reviewers state that they've used adapters to install a 2nd hard drive in the 5.25" bay, but apparently neither system supports hardware RAID and some have done software RAID instead). 

Just thought I'd throw that out as another option.

- Chuck

---

### Post by michaelzap on 2009-12-10
@SeeGo: I may do pretty much the same thing with my Eee PC 701 and an external hard drive. To me the most important factors are strong encryption of data, low power usage, and the ability to serve mp3s and videos over the LAN. I think Eeebuntu or Debian would do all of this very well.

---

### Post by paxmark1 on 2009-12-27
Hopefully the prices will fall after xmas.  Staples in Canada had the dns-323 for about $150 once, I did not think twice.  With the funplug script to ssh into, it is sweet.

---

