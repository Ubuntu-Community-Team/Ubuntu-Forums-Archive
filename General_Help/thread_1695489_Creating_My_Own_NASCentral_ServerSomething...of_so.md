---
title: "Creating My Own NAS/Central Server/Something...of sorts"
date: 2011-02-26
forum: General Help
---

### Post by Fid3lisV3rnula on 2011-02-26
Hi everyone,

First off, I hope I posted this in the right spot...couldn't decide if this was a general help or networking.

Anyways, I'm new to the forums, and semi-new to Linux, and I have a question:

I was gifted an older Dell Dimension 1100 for fixing a friend's computer, and I have an idea of what I want to do with it. The HDD bit the dust, so I'm replacing it with a 250 right now, with probably Ubuntu 10.10 desktop unless advised differently, and hopefully another 500-750 soon.  I want to be able to create a central server that I can offload most of my media onto (that I don't use frequently...since I do quite a bit of graphics work/videos/etc for a local organization and most isn't used often) and then be able to pull it back to my computers over my local network and hopefully over the internet (when necessary).  I have a few simple ideas on how to do this (most involve Windows programs so I'm not 100% on Ubuntu), but I would really like some expert opinions on this, and anything would definitely lead me in the right direction.

Thanks!

---

### Post by cackles on 2011-02-26
Here's one I made earlier ...

[http://ubuntuforums.org/showthread.php?t=799712](http://ubuntuforums.org/showthread.php?t=799712)

---

### Post by prshah on 2011-02-26
> **Fid3lisV3rnula said:**
> I have an idea of what I want to do with it. The HDD bit the dust, so I'm replacing it with a 250 right now, <..> I want to be able to create a central server that I can offload most of my media onto

While you can definitely do this with Ubuntu (or whatever platform of choice), I would suggest that you sell away the system and buy a cheap atom-based system. Such usage as you are targeting will usually be powered on 24/7, and you will take a hit in electricity charges when compared to the Atom. (Eg, and old P4 uses about 4-5 times more power even at idle, when compared to the atom processor - see [http://www.tomshardware.com/reviews/atom-d510-pentium-4-nettop,2649-10.html](http://www.tomshardware.com/reviews/atom-d510-pentium-4-nettop,2649-10.html) )

You could also go in for a NAS, but these are relatively expensive.

I'd suggest you go in for a cheapie, home-built atom computer without keyboard, mouse and monitor.

However, if you still feel you need to use machine you have got, then you can easily have such a setup with Ubuntu.

---

### Post by metalf8801 on 2011-02-26
> **prshah said:**
> While you can definitely do this with Ubuntu (or whatever platform of choice), I would suggest that you sell away the system and buy a cheap atom-based system. Such usage as you are targeting will usually be powered on 24/7, and you will take a hit in electricity charges when compared to the Atom. (Eg, and old P4 uses about 4-5 times more power even at idle, when compared to the atom processor - see [http://www.tomshardware.com/reviews/atom-d510-pentium-4-nettop,2649-10.html](http://www.tomshardware.com/reviews/atom-d510-pentium-4-nettop,2649-10.html) )

You could also go in for a NAS, but these are relatively expensive.

I'd suggest you go in for a cheapie, home-built atom computer without keyboard, mouse and monitor.

However, if you still feel you need to use machine you have got, then you can easily have such a setup with Ubuntu.

Very true that a P4 uses significantly more power than an atom but I think it's about 10 times more power. My parents P4 CPU uses 80 watts (that's just the CPU) and my dual core Atom uses 8 watts (again just the CPU). 

While my Atom server isn't very powerful it only doesn't take long to turn on because it doesn't have a desktop. So I don't leave it on 24/7 when I need it I use the wakeonlan command and then I ssh in or I use Webmin to access it. 

My point use Ubuntu Server not Ubuntu desktop. Which you can download here [http://www.ubuntu.com/server/get-ubuntu/download](http://www.ubuntu.com/server/get-ubuntu/download) 
and here is some documentation on it [https://help.ubuntu.com/10.10/serverguide/C/index.html](https://help.ubuntu.com/10.10/serverguide/C/index.html)
I use the 32Bit version because my little Atom board only has 2GB of RAM and because there are a few programs that I use that work better on 32bit systems. 

When installing Ubuntu server make sure to install Samba and SSH (these are options when you install use the space bar to check them then press enter don't press enter first) 

After you have installed Ubuntu server with SSH and Samba install Webmin here's a how to [http://ubuntuforums.org/showthread.php?t=1686705](http://ubuntuforums.org/showthread.php?t=1686705)

Then make sure Wake On Lan is enabled in your BIOS [http://en.community.dell.com/support-forums/desktop/f/3514/p/19326625/19674580.aspx](http://en.community.dell.com/support-forums/desktop/f/3514/p/19326625/19674580.aspx)

I haven't been using WOL from Windows but this looks like a good program 
[http://download.cnet.com/EMCO-WakeOnLan-Free/3000-2085_4-75335257.html?tag=mncol;2](http://download.cnet.com/EMCO-WakeOnLan-Free/3000-2085_4-75335257.html?tag=mncol;2)

I hope this helps 
Dan

---

### Post by Fid3lisV3rnula on 2011-04-10
Thanks for the answers everyone!

Sorry I didn't reply sooner, I've been really busy with school and my side project has taken a backseat.

Some updates in my project:
My modem and router have been moved to a closer side of the house, so it's now going to be hardwired, so WOL seems to be a good possibility; however, I recently upgraded laptops, so now I don't have to worry about having my media in a central location.  Since I can carry everything around, I'm not exactly sure what is going to come of my project.
I have to work with what I have for the time being, though I really like the idea of an Atom over a P4.

I'll keep everyone posted, and if you have any more suggestions, I'm completely open to them.

---

