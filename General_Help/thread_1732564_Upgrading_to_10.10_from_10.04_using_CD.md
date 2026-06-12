---
title: "Upgrading to 10.10 from 10.04 using CD"
date: 2011-04-18
forum: General Help
---

### Post by Dean_Grobler on 2011-04-18
Hi there,
 
I've recently done a full installation of 10.04 on my machine. Not too long after, I applied for a free 10.10 CD that Ubuntu offers instead of donwloading it due to no internet access.
 
How can I upgrade from 10.04 to 10.10 using the free CD that Ubuntu mailed to me?
 
I don't really want to consider doing a clean installation again as I have important programs and plug-ins installed on my current version.
 
Thanks in advance! :confused:

---

### Post by ~Plue on 2011-04-18
afaik, you cant upgrade using the live cd. it contains an already installed system that is just copied to the harddrive

but you could use the alternate cd which has all the necessary package files >> [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)
you'd have to download or order it because shipit has closed down

---

### Post by Dean_Grobler on 2011-04-18
NoOoOoOo!! Okay what about a clean installation? Will it work if I just boot from disc (10.10) and just do a whole new installation? I would obviously then have to back my stuff up as much as I can...

---

### Post by ~Plue on 2011-04-18
that would work out.. since you're going to reinstall, it might be a good idea to create a separate /home partition so that you don't have to backup all of it if you need to reinstall again in the future.
(/home is where you usually keep your data files and applications preferences)

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) 
the screenshots are from an older release, but the instructions would be the same

---

### Post by MartyBuntu on 2011-04-18
> **Dean_Grobler said:**
> ...I have important programs and plug-ins installed on my current version.
 


I would just leave it at 10.04, as it is a LTS version.

Unless of course, you have some compelling reason to upgrade...

---

### Post by Dean_Grobler on 2011-04-18
@Plue - thanks alot, appreciate your help! Just one more thing. Is there a way to copy the "packages" of my already installed applications on a flash disc. And then after the new installation of 10.10 is installed, just copy the packages back to my machine and install it again that way. Since I don't have an internet conenction on the Ubuntu machine it would really be great if I could.
 
@Martybuntu - You know I've actually been thinking about this myself to be honest. Since 10.10 won't be supported for very long, would it even be worth it upgrading to 10.10? What is so much better on 10.10 that is not on 10.04? (Except a cooler looking wallpaper...) If I upgrade to 10.10 I'm going to have to upgrade every 6 months, and having limited internet access. Is this really even worth it? I wonder how many people out there, only stick to the LTS versions...

---

### Post by ~Plue on 2011-04-18
maybe if you copy the apt cache and install it in the new version... but that might not be the best solution since they are different releases and might break something.

personally, i too would recommend sticking with the lts as it is generally regarded as more stable than 10.10.
the non-lts has newer version of software in the repositories but that wouldn't be a good point if you prefer stability over newer software ( this doesn't mean that the non-lts releases are unstable)
as for support, 10.04 has till april 2013 and april 2012 for 10.10

---

### Post by Spyderkid on 2011-04-18
To update to the newest version of ubuntu (10.10) run these in terminal....

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by Dean_Grobler on 2011-04-18
> **Spyderkid said:**
> To update to the newest version of ubuntu (10.10) run these in terminal....
 
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
 
That's if you have an internet connection on the machine right? :-s

---

### Post by MartyBuntu on 2011-04-18
> **Dean_Grobler said:**
> Since 10.10 won't be supported for very long, would it even be worth it upgrading to 10.10? What is so much better on 10.10 that is not on 10.04? (Except a cooler looking wallpaper...) If I upgrade to 10.10 I'm going to have to upgrade every 6 months, and having limited internet access. Is this really even worth it? I wonder how many people out there, only stick to the LTS versions...

You said you have "important programs". 

I would just wait until the next LTS and then upgrade. It makes the most sense for a production environment.

---

