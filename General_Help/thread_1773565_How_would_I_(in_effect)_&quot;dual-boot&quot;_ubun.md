---
title: "How would I (in effect) &quot;dual-boot&quot; ubuntu &amp; lubuntu?"
date: 2011-06-02
forum: General Help
---

### Post by gopherofdoom on 2011-06-02
Hi all,

This might be a stupid question (but I'd rather ask it anyway!)

I'm just getting a new netbook, and when considering what to put on it, I thought since I like 'standard' ubuntu for all its handy-for-my-workflow bits and bobs I've got used to -- but also sometimes want to be able to use the leaner, faster lubuntu for some tasks or just for fun -- it'd be nice to in effect dual-boot it.

I realise that's not an accurate term since they're both linux and hence the same OS, but you get what I mean, I hope. How would I go about it?

Or do I have a completely wrong understanding of the backstage operations of linux, and differences between ubuntu flavours, and all I need to do is install LXDE...?

**TL;DR:** Installing ubuntu and lubuntu on the same netbook -- please educate me!

Cheers!

--

FYI, the netbook is the PCSpecialist.co.uk "Axino II", with an 80GB SSD and minus Windows!
[http://www.pcspecialist.co.uk/notebooks/axinoII/](http://www.pcspecialist.co.uk/notebooks/axinoII/)

---

### Post by Laforge129 on 2011-06-02
> **gopherofdoom said:**
> Hi all,

This might be a stupid question (but I'd rather ask it anyway!)

I'm just getting a new netbook, and when considering what to put on it, I thought since I like 'standard' ubuntu for all its handy-for-my-workflow bits and bobs I've got used to -- but also sometimes want to be able to use the leaner, faster lubuntu for some tasks or just for fun -- it'd be nice to in effect dual-boot it.

I realise that's not an accurate term since they're both linux and hence the same OS, but you get what I mean, I hope. How would I go about it?

Or do I have a completely wrong understanding of the backstage operations of linux, and differences between ubuntu flavours, and all I need to do is install LXDE...?

**TL;DR:** Installing ubuntu and lubuntu on the same netbook -- please educate me!


I believe this article is related and should help your journey:

[http://ubuntuforums.org/showthread.php?t=752270](http://ubuntuforums.org/showthread.php?t=752270)

---

### Post by Joe of loath on 2011-06-02
Basically, install one, leave a partition for the other, and install the other to that one. The second one will detect the first, and allow you to dual boot. However, it might call both 'Ubuntu 11.04', so it might take a bit of trial and error editing grub ;)

---

### Post by Canime on 2011-06-02
You have to be able to make the partitioning system work for you in a way that is satisfactory. When you make it partitioned you are in effect breaking up hard disk space to account for the files that you will be adding later. Load the system so that one feeds from the other, or have them completely separated for testing purposes, you might want to destroy or delete lubuntu! I've got no need for two systems, but I need to hard drives now that space is becoming scarce, so I rely on an external drive to attempt to give me more space. Uh, that being said I really need more space on my primary drive and have that first sector completely attached to a windows system, something I cannot get rid of.

---

### Post by ratcheer on 2011-06-02
Note that both installations can use the same swap partition.

Tim

---

### Post by hhh on 2011-06-02
Whoa whoa whoa whoa... "all I need to do is install LXDE...?" THIS!!! Either...```
sudo apt-get install lxde
```[http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

Or maybe better...```
sudo apt-get install lubuntu-desktop
```[http://packages.ubuntu.com/search?keywords=lubuntu-desktop&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=lubuntu-desktop&searchon=names&suite=all&section=all)

Then choose LXDE from the available sessions in the login manager...
[http://wiki.lxde.org/en/Ubuntu#GDM_or_KDM](http://wiki.lxde.org/en/Ubuntu#GDM_or_KDM)

To return to pure Ubuntu (remove Lubuntu)...
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Hope that helps.

---

### Post by FuturePilot on 2011-06-02
> **hhh said:**
> Whoa whoa whoa whoa... "all I need to do is install LXDE...?" THIS!!! Either...```
sudo apt-get install lxde
```[http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

Or maybe better...```
sudo apt-get install lubuntu-desktop
```[http://packages.ubuntu.com/search?keywords=lubuntu-desktop&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=lubuntu-desktop&searchon=names&suite=all&section=all)

Then choose LXDE from the available sessions in the login manager...
[http://wiki.lxde.org/en/Ubuntu#GDM_or_KDM](http://wiki.lxde.org/en/Ubuntu#GDM_or_KDM)

To return to pure Ubuntu (remove Lubuntu)...
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Hope that helps.

This

---

### Post by 3Miro on 2011-06-02
In this case you have two options:

Option 1: Install LXDE along side Gnome and then select between the two at boot time. This is incredibly easy.

Option 2: Get separate partitions (can share swap) for both Ubuntu and Lubuntu and then select between the two at boot time (like you would do with Windows and Linux).

The difference between Ubuntu and Lubuntu is the desktop environment. If this is all that you wish to try, then just go with Option 1.

---

### Post by Rudra Brahm on 2011-06-02
That's easy if you install each of them in separate hard drives. but make sure you have different user names on the two installations otherwise it will mingle up with each other. make sure to update your grub.
OR
I think you can just install the two environment in a single ubuntu installation and choose the session when you log in.

I have ubuntu 11.04 and mint 10 but on separate hard drives and they work well.

---

### Post by gopherofdoom on 2011-06-03
Thanks for all the info g/g/o*!

I'll probably do what hhh and FuturePilot suggested, I've given it a go on my current computer and am now writing this from the lubuntu desktop. :) Nice and simple.

But thanks also for the info on partitioning, I may be needing that when I put together a desktop later in the year!

Cheers,
Goph


* = guys/girls/other (you can tell I've taken the recent gender-assumptions thread in the Cafe to heart)

---

### Post by Joe of loath on 2011-06-03
> **gopherofdoom said:**
> 
* = guys/girls/**other** (you can tell I've taken the recent gender-assumptions thread in the Cafe to heart)

Yey, for once someone included me :D

---

### Post by flemur13013 on 2011-06-03
I did what you're proposing; here's some notes for if you install two complete linux OSs, rather than two window managers on one linux OS: 

The lubuntu installer doesn't have os-probe (mine didn't - depends on version?), so it won't see the ubuntu install; install lubuntu first, or if the lubuntu install hides the existing ubuntu, go back afterwards and fix the dual-boot prob (not hard).

Make /home a separate partition and you can use it in both OSs - they'll have the same ~/Pictures, ~/Downloads, etc.

---

