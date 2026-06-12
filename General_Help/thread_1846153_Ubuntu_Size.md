---
title: "Ubuntu Size?"
date: 2011-09-18
forum: General Help
---

### Post by galacticaboy on 2011-09-18
How much space does Ubuntu 11.04 take up once it is freshly installed? I have a 6GB HDD and I would like to play around with it, would 6GB be enough to install it and do the updates? I don't install anything except flash and AssaultCube, but I can hold off on AssaultCube...

---

### Post by amhainen on 2011-09-18
I just checked my 11.04 install which is pretty small (I haven't made many changes) and it said 22GB! I googled and found [this article]("http://www.pcworld.com/businesscenter/article/227265/how_to_install_ubuntu_1104_natty_narwhal_with_wubi.html") suggesting 17GB was the install size.

Maybe others could confirm/verify?

---

### Post by Lars Noodén on 2011-09-18
I have a freshly installed instance of Xubuntu and it takes 2.6 GB.  Nothing beyond the basic installation has been added yet.  6GB will be plenty if you are careful.

---

### Post by galacticaboy on 2011-09-18
I don't even care if it is 5GB, I just want to try it out and play with it, I am running Lubuntu right now. My RAM is not the problem, it is the HDD, I cannot find anything on how big it is once it is installed FRESH.

---

### Post by galacticaboy on 2011-09-18
> **Lars Noodén said:**
> I have a freshly installed instance of Xubuntu and it takes 2.6 GB.  Nothing beyond the basic installation has been added yet.  6GB will be plenty if you are careful.

How about my 756MB of RAM, will that run Unity 3d?

---

### Post by garvinrick4 on 2011-09-18
One install of mine that I feel is configured with most all essentials is 4.1 gig with 287 meg
in /home. 
Though if older computer with short Ram going to need swap space (scratch disk for virtual memory) of twice the size of Ram installed if got say 500 meg. might need 1 gig swap.

---

### Post by dniMretsaM on 2011-09-18
Ubuntu 11.04 fresh install size is 4.6 GiB.

---

### Post by garvinrick4 on 2011-09-18
```
/usr/lib/nux/unity_support_test -p
```Above is line of code to see if your machine will support 3D if not have to run 2D unity.
I imagine you are going to try it out so let us know how you run with 756 meg of Ram and if you support 3d or 2d and what kind of machine
you have? If you got time give it a whirl. You have a install cd run it in a live cd (try ubuntu in the install cd) if not download one and burn a disk.
Instructions in link.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by Lars Noodén on 2011-09-18
> **galacticaboy said:**
> How about my 756MB of RAM, will that run Unity 3d?

Yes, I have another machine with standard desktop Ubuntu and it uses only 600KB of RAM.  So you should be fine.

FWIW It has a few apps installed but weighs in at about 3.4 GB on the hard disk.

---

### Post by howefield on 2011-09-18
> The Recommended Minimum System Requirements, here, should allow even an inexperienced user to easily install a usable system with enough room to be comfortable.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

5 gig is the minimum recommended hard disk size. My install with all that I use plus updates (the packages for which are still in /var/cache/apt/archives) is a touch over 4gig.

---

### Post by galacticaboy on 2011-09-18
Okay I will install here in a little bit and report back what happens!

---

### Post by zero2xiii on 2011-09-18
Hay,

I have installed ubuntu on a 4GB flash drive, without swap. And it ran fine on systems with 1GB+ ram.. (havent tested or run on less ram).

Only a hand full of packages installed after the fresh install. Airocrack-ng (or what ever the repro name is) and ubuntu restricted extras. Have no idea what the actual disk usage was though.. 

Cherz

---

### Post by howefield on 2011-09-18
Try the File Systems tab in System Monitor.

---

### Post by galacticaboy on 2011-09-18
I installed Ubuntu 11.04 on my 6GB HDD, I cannot use Unity 3D, thats ok, I am using Unity 2D though. I have uninstalled all of the crap I don't need like LibreOffice and the games and such, I installed Ubuntu Tweak, BleachBit and the BleachBit Bonus Pack, I have also done all updates and upgrades. After doing all of that, I have 3.0GB of HDD space left! I am ecstatic, that is more that I had with Lubuntu and Xubuntu, with them I had 2.1 GB of HDD space left after a fresh install. Awesome!

---

### Post by Blasphemist on 2011-09-18
I've got a bunch of distros installed on small partitions, just not as small as you want. I do have a few that aren't taking up much as you can see from the screen shot. If you're careful about installing much and keeping things clean most distros will work.

---

