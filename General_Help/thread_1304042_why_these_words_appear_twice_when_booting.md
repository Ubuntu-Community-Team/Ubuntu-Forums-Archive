---
title: "why these words appear twice when booting"
date: 2009-10-28
forum: General Help
---

### Post by dribuu on 2009-10-28
[B]Doing wacom setup
Doing wacom setup

Starting powernowed...
Starting powernowed...

Starting up ALSA
Starting up ALSA

fglrx(8543)
fglrx(8543)[/B]


and so on

it need 3min to boot my dell laptop

why? thanks for your help.
----------------

---

### Post by andrewabc on 2009-10-28
Sadly no idea. Is this a fresh install of 9.04? Is it waiting between text (extra time for text on screen?).

If so you may want to wait a day or two and get ubuntu 9.10 and test to see if it works better.

---

### Post by dribuu on 2009-10-28
> **andrewabc said:**
> Sadly no idea. Is this a fresh install of 9.04? Is it waiting between text (extra time for text on screen?).

If so you may want to wait a day or two and get ubuntu 9.10 and test to see if it works better.


Thanks for your help

login window--------------->about 1 min--------------->desktop

my ubuntu version is ubuntu 8.10.

How to boot more quickly?

---

### Post by fluffman86 on 2009-10-28
Oh yeah, definitely backup your data and do a fresh install with 9.10.  That should help your boot times significantly.

---

### Post by andrewabc on 2009-10-29
Yes, definitely download/burn to CD Ubuntu 9.10 when it is released (today/tomorrow), and test to make sure all the basic stuff works for you (internet/audio/video)

9.10 should start faster, and all the software and drivers are much newer.

Make sure to backup any important information.

Can you give some information about your computer specifications? (ghz, video card, ram, laptop/desktop etc).

Are you dualbooting?

---

### Post by dribuu on 2009-10-29
> **andrewabc said:**
> Yes, definitely download/burn to CD Ubuntu 9.10 when it is released (today/tomorrow), and test to make sure all the basic stuff works for you (internet/audio/video)

9.10 should start faster, and all the software and drivers are much newer.

Make sure to backup any important information.

Can you give some information about your computer specifications? (ghz, video card, ram, laptop/desktop etc).

Are you dualbooting?

I am not sure what is the matter, 
I am unfamiliar with UBUNTU, but it is attractive.

There are so many softwares and configurations in my system, how can I retain them when I reinstall my system?


I hope you can give me some commands to deal my question.

Thanks very much!

---

### Post by andrewabc on 2009-10-29
To keep your settings and installed software, you'd have to update to 9.04, then to 9.10

Which you could do through update manager (it should tell you 9.04 is available).

But I'd really recommend backing up anything important, and formating/installing clean 9.10 instead of upgrading 8.10->9.04->9.10. You will have less problems doing a clean install than upgrading twice. Also with clean install you will get ext4 instead of ext3 filesystem, and GRUB2 instead of GRUB1 bootloader.

One first step no matter what you decide to do, is to download ubuntu 9.10 when released, burn the .iso to a CD, then put CD into your cd-rom and make sure everything works. You don't have to install it if you don't want to, but you can at least see if everything works fine and whether to bother updating to newest version.

I don't have much time to help right now, have to go to work. Should be back in 6 hours or so. Post as much info as you can about your computer and what you want to achieve.

EDIT:
There are many guides to installing ubuntu. Within a week you should see guides for 9.10

[Installing Ubuntu 9.04](http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml)
Is a guide for 9.04, and should be similar to 9.10

Several important questions are do you dualboot? Or is it just ubuntu on your computer?

I would not rush into installing a new operating system if you are not sure how to do it. Take time to read as much guides and tutorials as possible, then install when you are comfortable. Wait a week before deciding on anything. The servers are slow now because everyone wants the new OS.

---

