---
title: "Dual-Head &quot;Big Desktop&quot; on 10.04 &quot;Lucid Lynx&quot; with ATI Radeon HD 2400 Pro?"
date: 2012-03-10
forum: General Help
---

### Post by JSeymour on 2012-03-10
I'm *finally* preparing to upgrade from 9.10 ("Karmic Koala") to 10.04 LTS ("Lucid Lynx") on my Dell PowerEdge 1600SC.  I have an ATI Radeon HD 2400 Pro 256MB PCI, running dual-head in "big desktop" mode.

What's taken me so long is that it works well and I really haven't been anxious to fix something that isn't broken.  But I can't get critical updates anymore, and the upgrade of my work laptop from Mandriva 2009 Spring to Ubuntu 10.04 LTS went so smoothly, that I figured I'd go for it.

I *assumed* that all the grief I had getting big desktop to work under 9.10 with the proprietary ATI drivers would've been a Thing Of The Past.  From my searches, apparently that's not the case.

So, before I wipe out a perfectly functioning system, can somebody tell me what I'm in for and what I have to do to get big desktop back after I over-write my 9.10 install with 10.04 LTS?

Thanks,
Jim

---

### Post by winh8r on 2012-03-10
You might like to have a read through this for starters:#

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Hope this helps

---

### Post by josephmills on 2012-03-10
BACK UP BACK UP BACK UP 1st. 

then check out the command 
sudo apt-get install update-manager-core
sudo apt-get update
sudo do-release upgrade -d

this will update for you and will ask. works great for me. I even had a computer overheat and shut off half way done with sudo do-release upgrade -d   and I was still able to fix and upgrade from 11.10 to 12.04. to bad that dont fix that overheating issue thou (needs fan)
when you run do-release it will stop all old repos and will also kill any driver that is 3rd party installed (there are work around )

well Hope that this help have a good one

---

### Post by JSeymour on 2012-03-10
> **winh8r said:**
> You might like to have a read through this for starters:#

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Hope this helps
Ahhh!  Thanks! :)  I searched and searched and could not, for the life of me, find references.

Jim

---

### Post by JSeymour on 2012-03-10
> **josephmills said:**
> BACK UP BACK UP BACK UP 1st. 
I've got an rsync-based backup that runs every night :)

I also have an unused partition that's exactly the same size as my boot partition.  I'm thinking of "dd"ing the boot partition into it, Just In Case.

> **josephmills said:**
> then check out the command 
sudo apt-get install update-manager-core
sudo apt-get update
sudo do-release upgrade -d

this will update for you and will ask. works great for me.
I'll look into those.  Thanks.

I was simply going to re-install over the top of my current install, retaining my current /var, /tmp, /usr/local and /home filesystems and contents.  I've never had much luck with upgrades of operating systems across major revisions in the past.

But, of course, if I go the re-install-over-the-top route, I'll have to subsequently manually restore/re-configure all the server services.  My desktop is also the family server, supplying DHCP, BIND, internal and external web, mail server, DLNA server, etc., etc.

Jim

---

### Post by JSeymour on 2012-03-10
> **josephmills said:**
> 
...
sudo do-release upgrade -d
...
Hmmm... manual page says it's "do-release-upgrade" (note add'l hyphen), that it upgrades to the latest release (I want 10.04 LTS, nothing later) and that "-d" specifies "development release," which I likewise do not want.

Looks like update-manager, which has been prompting me to update to 10.04.3 LTS for some time :p is the way to go?

Jim

---

### Post by JSeymour on 2012-03-12
> **josephmills said:**
> BACK UP BACK UP BACK UP 1st. 

then check out the command 
sudo apt-get install update-manager-core
sudo apt-get update
sudo do-release upgrade -d

this will update for you and will ask. works great for me.
For starters: Not blaming you.  Definitely not blaming you.  I should have known better.  Been doing systems and networks for... well, longer than I care to remember, and I've *never* had a major upgrade actually work.  Not. Once.  Nor have any of my colleagues.

But I tried it anyway.

Massive Fail: [Upgrade Ubuntu 9.10 (Karmic) -> 10.04 LTS (Lucid): Never Again!]("http://ubuntuforums.org/showthread.php?t=1939761")

I'll get back to y'all when I finally get to the point of getting back to the original question.

Jim

---

### Post by JSeymour on 2012-03-19
Ok... reinstalled from scratch on Saturday.  A lot of work, but it's all up and running.

It was worth the headache for the new Radeon driver alone.  Don't have  to wire-frame on window moves anymore and no more herky-jerky videos :smile:

The "big desktop" thing?  Too easy!  Preferences -> Monitors, uncheck "Same image in all monitors" and done.

---

