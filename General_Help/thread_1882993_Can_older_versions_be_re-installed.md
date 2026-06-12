---
title: "Can older versions be re-installed?"
date: 2011-11-18
forum: General Help
---

### Post by LinuxCmx on 2011-11-18
I upgraded my Dell netbook 910 from lucid to maverick when sound anf graphic software wasn't working properly - caused, I think now, by an update. However, wireless failed to work in maverick, despite much help from folks on this forum - and upgrade to natty did not solve problem. Plus I hate natty!

So here's the question - can I re-install the original LTS lucid now? Will be done by usb. This netbook had hardy originally - which also had wireless issues.

---

### Post by Gremlinzzz on 2011-11-18
A fresh install of lucid  yes,A roll back to the old system,i don't think so.:popcorn:

---

### Post by Gremlinzzz on 2011-11-18
> **Gremlinzzz said:**
> A fresh install of lucid  yes,A roll back to the old system,i don't think so.:popcorn:

[http://distrowatch.com/?newsid=06526](http://distrowatch.com/?newsid=06526)

---

### Post by LinuxCmx on 2011-11-18
Sorry for being dumb - but would an install of the original lucid iso, booted via usb, be a fresh install? Presumably this could not be done  from the natty desktop?

---

### Post by Frogs Hair on 2011-11-18
The answer to you question is yes if you choose the installation option . After that you could choose to dual boot or use the entire disc for 10.04   
When booting directly from a live cd or usb you are not booting into an installed operating system first .

---

### Post by mörgæs on 2011-11-18
It is not only possible, I would highly recommend it. If you get into some problems you can not solve, a fresh install (not upgrade) of another release is worth trying. Never install an unsupported release, though.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by LinuxCmx on 2011-11-19
Thanks all! Did a complete re-install of Lucid LTS. Had to activate STA and B43 drivers, but am now wireless again. Lesson to anyone with a Dell 910  mini - don't upgrade! Neither maverick nor natty would allow wireless on this netbook.

One question ... how safe are the recommended updates? I have no idea what most of them are - or if I need them on this machine.  Is there a place which describes why they are issued? Want to study up on them this time.

---

### Post by mörgæs on 2011-11-19
In Update Manager you can see an explanation to each of them pointing to the relevant page in Launchpad. 

In general: Apply all updates but don't upgrade. Do a fresh install in stead.

---

### Post by snowpine on 2011-11-19
> **LinuxCmx said:**
> Thanks all! Did a complete re-install of Lucid LTS. Had to activate STA and B43 drivers, but am now wireless again. Lesson to anyone with a Dell 910  mini - don't upgrade! Neither maverick nor natty would allow wireless on this netbook.

One question ... how safe are the recommended updates? I have no idea what most of them are - or if I need them on this machine.  Is there a place which describes why they are issued? Want to study up on them this time.

I've tested every release of Ubuntu since 8.04 on my Dell Mini Inspiron 910 and never had a single wireless problem.

I think the problem in your case was activating **both** the b43 and STA drivers. They are mutually exclusive and one blacklists the other. The correct driver for our chipset is STA and the instructions to install are here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_STA_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_STA_drivers)

(edit) also check your BIOS options (press '2' at the boot screen) to make sure the wireless is enabled. Sometimes it's the simple things...

---

### Post by LinuxCmx on 2011-11-20
Thanks for the info about updates. Something went wrong with Lucid after a recent update. No audio and screensaver graphics wouldn't work. Was nothing obvious and when no patch came through, I decided to upgrade via the update mgr. I hear you about the clean install - and if I do it again, it will be via USB.

After upgrading to Maverick, my wireless wouldn't work, and I had a lot of help from this forum regarding the STA and B43 drivers. Tried every conceivable combination. No dice. So I upgraded to Natty, thinking it might solve the problem. It didn't.

Thing is, Hardy came with the mini when I bought it new, and it was buggy from the start. Sometimes the wireless worked, other times not. Keyboard froze, etc. When I did a new install from USB of Lucid, the wireless worked immediately and everything else was great too. In this re-install, both drivers had to be activated and work fine, just as before. I tried just activating just the STA - no wireless. Ditto for B43 alone. This machine apparently needs both.

I looked at the help pages on wireless issues, but after eliminating the obvious things, like the BIOS (it was correct), etc. I got lost in the technical stuff. That's when I went to the forum help. You can see my posts and the replies on the Broadcom drivers wireless issue. 

I want to understand Ubuntu Linux better. I did a Debian install from the kernel over 15 years ago when it was a picky, complicated process using command lines - on an old 286. Could have written a book about that! But it was fun.

---

