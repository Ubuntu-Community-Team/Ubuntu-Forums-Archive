---
title: "Assistance with 3 monitors and new sound card"
date: 2010-06-27
forum: General Help
---

### Post by benjamingr on 2010-06-27
Hello,

My tech level is intermediate (I know my way around basic bash and such)

I'm a somewhat long time ubuntu user (since 6.06) and I've run into a problem I can't really get around.

I have an intel on-board video card as well as an nvidia geforce 8400. I'm using the nvidia (binary) drivers. 

I'd like to be able to use all three monitors (2 connected to the geforce, 1 to the onboard). I'd like to just say this worked flawlessly on windows so it is not a bios/hardware issue. I'm pretty clueless on how to get this done...

Also, I got a new EMU 1212m sound card and I'd like to know if there is a way other than compiling alsa from source in order to get this sound card working, this is the only option I found when searching the forums.

I asked on the IRC channel and they were no help. Thanks in addition for any help.

---

### Post by Spr0k3t on 2010-06-27
> **benjamingr said:**
> I have an intel on-board video card as well as an nvidia geforce 8400. I'm using the nvidia (binary) drivers. 

I'd like to be able to use all three monitors (2 connected to the geforce, 1 to the onboard). I'd like to just say this worked flawlessly on windows so it is not a bios/hardware issue. I'm pretty clueless on how to get this done...

To do this you have to start a separate X11 session on the intel or the nvidia card.  You will not be able to access all three screens from the same session.  This is a hardware/kernel restriction.  Will it ever be possible to mix graphic chipsets for one single session... sure, who knows.

---

### Post by benjamingr on 2010-06-27
So it is impossible to use 3 monitors on one (graphics accelerated) X session in linux?

---

### Post by Spr0k3t on 2010-06-27
Impossible, no.  There are people who have done it without any problems... however, the setups used did not have a deviation in the graphics processor.  Example of one user's claim with 4 monitors: [http://ohioloco.ubuntuforums.org/showthread.php?p=6363363](http://ohioloco.ubuntuforums.org/showthread.php?p=6363363)

Every other googled question of "more than two monitors" (sic Linux encompasium) comes back with either successful configurations in xorg.conf on identical graphics cards or people pulling their hair out trying to get an xsession to work across two completely different chipsets from the same manufacturer with no hard/fast solution.

One of the reasons why Xfire (ATI) and SLI (nVidia) require the same cards is due to arbitrary communication at the machine level.  Most of these chips from one revision to the next can't communicate with each other.  Part of that explination I'm sure has something to do with why it's nearly impossible with mixed chipsets in Linux.  Now, why is it possible for this to work in Windows when it can't for Linux... I have no clue.

---

### Post by dino99 on 2010-06-27
some cards with "lucid hydra" chipset are able to mix different chips

[http://www.iopanel.net/forum/thread31404.html](http://www.iopanel.net/forum/thread31404.html)

---

### Post by Spr0k3t on 2010-06-27
> **dino99 said:**
> some cards with "lucid hydra" chipset are able to mix different chips

[http://www.iopanel.net/forum/thread31404.html](http://www.iopanel.net/forum/thread31404.html)

Sweet!  A graphics translation chip... I hope a better solution will eventually become available though.  I'm sure something like that is possible through software, albeit slower.

---

### Post by benjamingr on 2010-06-27
> **Spr0k3t said:**
> 
One of the reasons why Xfire (ATI) and SLI (nVidia) require the same cards is due to arbitrary communication at the machine level.

Now the difference between crossfire or sli and what I'm trying to accomplish is that I don't need the cards to process together, I just need them to output what the OS wants to the screen. In SLI (or crossfire) all cards process the same output (this is good for games for example), I do not need this fonctionality. 

This is why this is completely doable on the theoretic level, and why it is easily possible with windows. 

I really want to continue using ubuntu but this is a real dealbreaker for me...

I found out how I might be able to enable the third monitor but that means no hardware accel on anything on any screen which hardly solves anything because a lot of programs use the GPU for a lot of stuff today...

I just find it hard to believe that a big distro like ubuntu that has a studio edition aimed at artists (which use 3 monitors frequently) and that its normal edition targets programmers (among others) (which also like to use multiple monitors) doesn't have a simple solution to this problem...

---

