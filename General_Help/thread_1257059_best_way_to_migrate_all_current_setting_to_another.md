---
title: "best way to migrate all current setting to another laptop?"
date: 2009-09-03
forum: General Help
---

### Post by firsttimeuser on 2009-09-03
I got a new laptop which I just loaded ubuntu 9.04 yesterday, now the fun part starts, how can I migrate everything from my current laptop, which also runs ubuntu 9.04, to the new one?

The two laptop are not same brand so the specific are not same.

What is the quick and easy way to magically get everything over to my new one?

Thanks

---

### Post by Zoot7 on 2009-09-03
How about either clone or swap the hard drive? 
Ubuntu from what I've heard is pretty good at handling complete hardware changes, the only problem is you'll have to re-configure your video again if going from ATi to nVidia etc.

---

### Post by MoonRocketZero on 2009-09-03
I don't have an answer - but I hope someone does as I've been wondering about this too, I been toying with fully upgrading my main system and it's the one where I have 9.04 set up just the way I want it. Would be great to be able to just transfer or clone to the new system I build...if that'll work.

going to keep an eye on this thread hope there is an easy way to do, would hate to have to set things up again from scratch...

---

### Post by Zoot7 on 2009-09-03
> **MoonRocketZero said:**
> I don't have an answer - but I hope someone does as I've been wondering about this too, I been toying with fully upgrading my main system and it's the one where I have 9.04 set up just the way I want it. Would be great to be able to just transfer or clone to the new system I build...if that'll work.
I'll be doing something similar tomorrow night. I've to re-install Ubuntu on my desktop, but I already have a perfectly functional install of Hardy on my laptop. So I plan to clone the hard drive of my laptop onto a 750GB SATA HD via an enclosure, and pop it into the desktop to see what the end result is.

The specs of both are as follows:
Laptop - Dell XPS M1530 | T7500 | 2GB | 8600M GT
Desktop - Phenom II 955 | Gigabyte MA790FXT-UD5P | HD4870 | X-Fi

I'll post back the result here. :)

---

### Post by aeiah on 2009-09-03
install on the new with the same username as the prior one. put them both on the network and scp over all the stuff in your home directory. you could compliment this with apt-on-cd, but be sure to get it from the site as i hear the repos hold a buggy copy

---

### Post by MoonRocketZero on 2009-09-03
> **Zoot7 said:**
> I'll be doing something similar tomorrow night. I've to re-install Ubuntu on my desktop, but I already have a perfectly functional install of Hardy on my laptop. So I plan to clone the hard drive of my laptop onto a 750GB SATA HD via an enclosure, and pop it into the desktop to see what the end result is.

The specs of both are as follows:
Laptop - Dell XPS M1530 | T7500 | 2GB | 8600M GT
Desktop - Phenom II 955 | Gigabyte MA790FXT-UD5P | HD4870 | X-Fi

I'll post back the result here. :)
I'll be interested to see if that works

---

### Post by firsttimeuser on 2009-09-03
last time i coped over everything, including the hidden directories, under my home dir to the new box and ubuntu refuse to enter the gnome on the new box.


> **aeiah said:**
> install on the new with the same username as the prior one. put them both on the network and scp over all the stuff in your home directory. you could compliment this with apt-on-cd, but be sure to get it from the site as i hear the repos hold a buggy copy

---

### Post by Zoot7 on 2009-09-04
well you know what? It worked! :)

I had a small bit of work with the video driver, uninstall the nVidia driver, uninstall envy and then install the ATi driver manually, and then to upgrade ALSA to 1.0.21 so I could sound through my X-Fi. Ubuntu detected all the hardware no problem. :)

So based on my experience I'd recommend just swapping out the hard drive, saves lots of time. ;)
The only thing to watch for is the video driver, but I'd reckon going to the same type of Video card should be okay.

---

### Post by Scotty Bones on 2009-09-04
I use [Remastersys]("http://www.geekconnection.org/remastersys/ubuntu.html") to create a live-cd backup of my OS. 


  Remastersys is a tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation.

   1. It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
   2. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it.

---

### Post by MoonRocketZero on 2009-09-05
> **Zoot7 said:**
> well you know what? It worked! :)

I had a small bit of work with the video driver, uninstall the nVidia driver, uninstall envy and then install the ATi driver manually, and then to upgrade ALSA to 1.0.21 so I could sound through my X-Fi. Ubuntu detected all the hardware no problem. :)

So based on my experience I'd recommend just swapping out the hard drive, saves lots of time. ;)
The only thing to watch for is the video driver, but I'd reckon going to the same type of Video card should be okay.
Good to hear it worked - I think I will give that a shot soon (when I get my new hardware) :).

---

### Post by jobst on 2009-09-06
> **firsttimeuser said:**
> I got a new laptop which I just loaded ubuntu 9.04 yesterday, now the fun part starts, how can I migrate everything from my current laptop, which also runs ubuntu 9.04, to the new one?

The two laptop are not same brand so the specific are not same.

What is the quick and easy way to magically get everything over to my new one?

Thanks

Number of ways to do this, one way is to use a PC that has a number of free drive slots (ide/sata).
put the two drives of your laptops in there, go and get clonezilla and copy the soucre drive to the target drive, does not take long to do.

jobst

---

