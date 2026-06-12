---
title: "After updating Nvidia drivers, Ubuntu boots into text-mode"
date: 2010-12-12
forum: General Help
---

### Post by anthony62490 on 2010-12-12
DISCLAIMER: My install is less than 2 hours old. Other than installing my accessories, I have messed with nothing.

The final step in installing Ubuntu 10.10 was going to be installing the NVidia drivers. So I tried:
```
sudo apt-get install nvidia-current
```
followed by
```
sudo nvidia-xconfig
```
followed by a reset. Now Ubuntu boots up in text mode. Great.
NVidia has apparently gone downhill since I last updated.

The only thing that google gives me is a bunch of people complaining that their splash screen is in text mode.
I can't be the only person who has been having this problem.

---

### Post by sikander3786 on 2010-12-12
Which graphics card is there?

```
lspci | grep VGA
```

---

### Post by cascade9 on 2010-12-12
If you're running the video card in your sig (GeForce4 MX 420) then nvidia-current wont work. It needs 96.xx drivers, not the 260.xx drivers that nvidia-current in 101.10 gives you. 

AFAIK, they still havent fixed the 96.xx driver problem with 10.10. IIRC there is a PPA you can add to get the 96.xx drivers working on 10.10.

---

### Post by anthony62490 on 2010-12-12
> **cascade9 said:**
> AFAIK, they still haven't fixed the 96.xx driver problem with 10.10. IIRC there is a PPA you can add to get the 96.xx drivers working on 10.10.

Okay, I did some searching and found [this]("https://wiki.ubuntu.com/Testing/EnableProposed") website that appears to be what I'm looking for.
```
deb http://archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
```
I could also probably use [this]("https://launchpad.net/~dajhorn/+archive/nvidia-96/") even though it's apparently obsolete.

Is this what you were talking about?

---

### Post by cascade9 on 2010-12-12
I have no idea what the 1st link is, the 2nd says that they have fixed the 96.xx driver issue on 10.10. So you should be able to get the drivers via jockey, software centre, etc. Just make sure that you get the 96.xx drivers if you use synaptic etc ;)

---

### Post by anthony62490 on 2010-12-15
Ok, well I'm sure I'll find the driver eventually, but can I undo the changes that the driver made? I'd really like to get my GUI back with or without video drivers.

---

### Post by cascade9 on 2010-12-15
I'm not 100% sure this will work, but I'd try- 

sudo apt-get --purge remove nvidia-current 


> **anthony62490 said:**
> Ok, well I'm sure I'll find the driver eventually, but can I undo the changes that the driver made? I'd really like to get my GUI back with or without video drivers.

It's a lot easier to get nvidia drivers from 

system-> administration-> addional drivers.

---

### Post by anthony62490 on 2010-12-15
> **cascade9 said:**
> I'm not 100% sure this will work, but I'd try- 
sudo apt-get --purge remove nvidia-current 
Okay, that seemed like it worked at first since it started to boot up in graphic mode. Turns out that it froze on the bootloader. So I decided to reinstall and start from scratch.

This time, I followed the advice of [[COLOR="RoyalBlue"]_this_[/COLOR]]("https://launchpad.net/~dajhorn/+archive/nvidia-96/") website that says that the 96.xx drivers are kept in the maverick-proposed repository. So I enabled the repository and checked Synaptic for "nvidia 96".

I got this:
```
[ ]nvidia-glx-96
[ ]nvidia-96-kernel-source
[ ]nvidia-glx-96-dev
[ ]nvidia-96-dev
[ ]nvidia-96
[!]nvidia-96-modaliases
```

"nvidia-96" sure does look like what I need. Not sure what's up with the last one. Maybe it wasn't upgraded.


> **cascade9 said:**
> It's a lot easier to get nvidia drivers from 
system-> administration-> additional drivers.

About that.
[IMG]http://i55.tinypic.com/2ir2qf9.jpg[/IMG]
I got nothing.

---

### Post by cascade9 on 2010-12-16
Gah!

So adding 'maverick-proposed' didnt let you getthe drivers....wow, what a %&#%$-up the 96.xx drivers have been with 10.10. I wish that they would get fixed, they should be in the normal repo by now. 

I'm temped to have a nice rant now, but thats not going to be productive, so I'm going to have a shower instead :|

---

### Post by anthony62490 on 2010-12-19
> **cascade9 said:**
> Gah!

So adding 'maverick-proposed' didnt let you getthe drivers....wow, what a %&#%$-up the 96.xx drivers have been with 10.10. I wish that they would get fixed, they should be in the normal repo by now.

Well, installing nvidia-96 let me keep my GUI and let me play movies, but it did not enable OpenGL, so games are out of the question. Regardless, its nice to have music again. I just need to get a new video card. Time to let go of the old hardware.

---

### Post by BicyclerBoy on 2010-12-19
You need more than the video card replacing.
That is a likely an AGP card so the whole mobo will need getting replaced.
The processor is well passed it too.

So the whole box is best donated to another cause.

---

### Post by cascade9 on 2010-12-19
> **anthony62490 said:**
> Well, installing nvidia-96 let me keep my GUI and let me play movies, but it did not enable OpenGL, so games are out of the question. Regardless, its nice to have music again. I just need to get a new video card. Time to let go of the old hardware.

Or you could try a different distro. Most of them should run with 96.xx drviers with no issue. If you wanted to stay with ubuntu, sooner or later the 96.xx drivers should work out of the box again. Though that might not be untill 11.04 with the foot dragging on the 96.xx drivers.

Theres got to be some PPA for the 96.xx drivers, I'm just to lazy to install a ubuntu variant and play around till I can get the drivers works then post back. 

> **BicyclerBoy said:**
> You need more than the video card replacing.
That is a likely an AGP card so the whole mobo will need getting replaced.
The processor is well passed it too.

So the whole box is best donated to another cause.

Why? The whole box is running fine, it seems a waste to trash something just because ubuntu cant seem to get the 96.xx drivers fixed. 

There are newer AGP cards as well, Geforce 5/FX (173.xx drivers) and 6XXX/7XXX cards (nvidia-current). I dont know if I would bother getting one, the last of the nvidia AGP cards are overpriced. 

BTW, I've got a very similar setup as a media box (P4-2.53, 1GB, 6600GT) and its running stong. Not with a *buntu though.

---

