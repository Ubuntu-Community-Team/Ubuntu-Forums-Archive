---
title: "Installing new unity on old ubuntu"
date: 2011-10-22
forum: General Help
---

### Post by Scooter_X on 2011-10-22
Hey all, I wonder how I can install the new Unity that's in Oneiric on my netbook? Thing is, I run Linux Mint on my Netbook because it's just always run smoother than Ubuntu for whatever reason. I'm running Mint 11, which is the Natty equivalent. I wanted to try Oneiric and the new Unity, but I don't really like what I'm hearing about battery life, etc with Kernel 3.0. I was thinking I would probably need to somehow use Oneiric's repos, but I don't know how to do that, and I'm concerned it might break stuff. Can anyone shed me some light on the subject? Greatly appreciated. Thanks.

---

### Post by haqking on 2011-10-22
> **Scooter_X said:**
> Hey all, I wonder how I can install the new Unity that's in Oneiric on my netbook? Thing is, I run Linux Mint on my Netbook because it's just always run smoother than Ubuntu for whatever reason. I'm running Mint 11, which is the Natty equivalent. I wanted to try Oneiric and the new Unity, but I don't really like what I'm hearing about battery life, etc with Kernel 3.0. I was thinking I would probably need to somehow use Oneiric's repos, but I don't know how to do that, and I'm concerned it might break stuff. Can anyone shed me some light on the subject? Greatly appreciated. Thanks.

if you want to try Unity and Oneiric then use a Live USB/CD/DVD or VM

---

### Post by Scooter_X on 2011-10-22
I did. It was really slow, didn't work really great off of my USB. I was tempted to install it, but don't want to have to back everything up, restore it, then find that I don't like it, then start all over again.

---

### Post by haqking on 2011-10-22
> **Scooter_X said:**
> I did. It was really slow, didn't work really great off of my USB. I was tempted to install it, but don't want to have to back everything up, restore it, then find that I don't like it, then start all over again.

well to be brutally honest doesnt sound like you really want to test it then ;-)

And you should already have everything backed up.

just take a clone, install oneiric then on you real hardware,if you dont like it or it doesnt work then clone your old system back, use clonezilla

Better to do all that than to just trash your system.

What does didnt really work well mean ? anything in particular ?

---

### Post by Scooter_X on 2011-10-22
I have the important stuff backed up using Dropbox. I never have cloned my system, I'm not sure how. Guess I'll go check it out. And yea, I don't want to trash my system. You're right. That's why I am posting here in the first place.

---

### Post by haqking on 2011-10-22
> **Scooter_X said:**
> I have the important stuff backed up using Dropbox. I never have cloned my system, I'm not sure how. Guess I'll go check it out. And yea, I don't want to trash my system. You're right. That's why I am posting here in the first place.

[www.clonezilla.org](www.clonezilla.org)

take a clone, then do as you wish to your machine and if you dont like it then clone back again and your back to where you were.

However be warned that using clonezilla requires some understanding of drives and partitioning so make sure you know what you are doing when you choose source and location

---

### Post by grahammechanical on 2011-10-22
How much hard disk space is there on a netbook? Is there not enough room for another partition of say 10GB? I always test a new release by installing it on another partition before deciding to upgrade the earlier release that I was using to do work with.

And further more I am coming around to the view that a fresh install is better than an upgrade. It is easy if you have a separate /home partition.

I am using 11.10 right now on a 10GB partition which I dual boot into. I access my files on the 11.04. So, when I next come to testing out 12.04 I do not loose any data.

Regards.

---

### Post by Utew on 2011-10-22
> **Scooter_X said:**
> I did. It was really slow, didn't work really great off of my USB. I was tempted to install it, but don't want to have to back everything up, restore it, then find that I don't like it, then start all over again.

If your netbook specs are low and and the live version (off of USB stick) was running "really slow", it sounds like it doesn't bode well for a system you'd be happy with (performance wise). Though Unity 2d, might work well for you.

But as haqking suggested and it's exactly what I do.. clone your current install with Clonezilla and if the 11.10 install doesn't please.. then you're just a few minutes away from a complete restoration of your current Mint 11 setup.  Good Luck :)

---

### Post by masgeeks on 2011-10-22
Using a live CD or usb really isn't indicative of the performance you would experience if you install the OS...  :(

I did a clean install of 11.10 - I was using 11.04 prior to that.  Afterwards I loaded all the apps I normally use, and did most all of the functions I use on a daily basis for my work, and things are faster in 11.10 than they were in 11.04.  I was surprised that there seems to be that much of a performance boost.

And I have raid 1 mirror with two 1 TB hard drives, and I had to offload 350 GB of data to do my clean install (so I could totally wipe the drives), but it was worth the effort - took me less than a day to get things to where they were before I did my clean install... and I went with gnome shell which is faster than unity, at least on my machine...  :)

---

### Post by Scooter_X on 2011-10-22
> **grahammechanical said:**
> How much hard disk space is there on a netbook? Is there not enough room for another partition of say 10GB? I always test a new release by installing it on another partition before deciding to upgrade the earlier release that I was using to do work with.

And further more I am coming around to the view that a fresh install is better than an upgrade. It is easy if you have a separate /home partition.

I am using 11.10 right now on a 10GB partition which I dual boot into. I access my files on the 11.04. So, when I next come to testing out 12.04 I do not loose any data.

Regards.

That sounds like a good idea to have a small partition for that. Then I can install it right next to the other one and not have to go back and forth cloning.

I agree that a fresh install is way better than upgrading, however I have had issues when just having a separate /home partition due to different program settings that can reside in hidden folders in /home that can mess with different things. In the past I stored my documents, pictures, music, etc in a separate partition then just mounted them each individually using  fstab to their corresponding folders in /home. Then one day somehow something got screwed up and I had to wipe the entire thing and start over. I never fixed it again. Instead I just back up on an external now and again and if needs be, just copy the important stuff back over. 


[QUOTE=masgeeks]
I went with gnome shell which is faster than unity, at least on my machine... [/QUOTE]

Netbook tho, or something bigger?

---

