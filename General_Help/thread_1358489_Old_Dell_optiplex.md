---
title: "Old Dell optiplex"
date: 2009-12-18
forum: General Help
---

### Post by psychovampire85 on 2009-12-18
I came across a old dell optiplex and I am wondering what linux distro to put on it. 

Specs:
256 mb RAM
20 gb HDD
everything on board which means graphics and sound and all the other stuff
Intel Pentium 4 processor

Thanks for any and all help in advanced

---

### Post by jerrrys on 2009-12-18
regular ubuntu should work, but would require the alternate install cd

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by psychovampire85 on 2009-12-18
I am using xubuntu  on it right now but it still seems to run slow.

---

### Post by jerrrys on 2009-12-18
time tested and generally accepted

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

or maybe uncharted water

[http://u-lite.org/](http://u-lite.org/)

you may even find a performance increase by just switching to Debian

---

### Post by pricetech on 2009-12-18
Puppy.

What model Optiplex ??

---

### Post by psychovampire85 on 2009-12-18
> **pricetech said:**
> Puppy.

What model Optiplex ??

Yeah thats what it is I don't have the exact model numbers on me i got it gave to me form a school.

---

### Post by ubudog on 2009-12-18
Maybe the light version of crunchbang.  [http://www.crunchbanglinux.org/wiki/downloads#lite_edition_-_32-bit]("http://www.crunchbanglinux.org/wiki/downloads#lite_edition_-_32-bit")

---

### Post by lykwydchykyn on 2009-12-18
> **psychovampire85 said:**
> Yeah thats what it is I don't have the exact model numbers on me i got it gave to me form a school.

I've tried Debian and Ubuntu on various models from that era, Gx240, GX260, and GX270 among others.  It generally works great, except some of them have intel 845 chipsets which seem to be buggy depending on which release of what distro you use. 

make sure the BIOS is fully upgraded (you can actually do this with Synaptic, Dell has a firmware APT repository) and that mitigates most problems.


As for what distro, that really shouldn't be dictated solely by the hardware.  The question is, what do you want to do with it, and how do you prefer to interact with it?

---

### Post by psychovampire85 on 2009-12-19
> **lykwydchykyn said:**
> I've tried Debian and Ubuntu on various models from that era, Gx240, GX260, and GX270 among others.  It generally works great, except some of them have intel 845 chipsets which seem to be buggy depending on which release of what distro you use. 

make sure the BIOS is fully upgraded (you can actually do this with Synaptic, Dell has a firmware APT repository) and that mitigates most problems.


As for what distro, that really shouldn't be dictated solely by the hardware.  The question is, what do you want to do with it, and how do you prefer to interact with it?

Me personaly I just want it for a computer for people to just mes around on. I mean I like to download animes and watch them on my tv which I am running it on. That is pretty much what it will be used for is a just a downloading machine and surfing the web


Edit: the version of the optiplex is a gx260

---

### Post by jerrrys on 2009-12-19
DSL has my vote, but any lite weight that has ties to ubuntu would probably get my vote too...

---

### Post by lykwydchykyn on 2009-12-19
> **psychovampire85 said:**
> Me personaly I just want it for a computer for people to just mes around on. I mean I like to download animes and watch them on my tv which I am running it on. That is pretty much what it will be used for is a just a downloading machine and surfing the web


Edit: the version of the optiplex is a gx260

Ah, that's the one with the 845 chipset.  Definitely upgrade the BIOS to the latest version (A09, I think) because early versions will cause problems with the display resolution.  

If it's just a surf machine pretty much anything will do.  I'd probably just put debian stable with LXDE for the desktop, but that's me.

---

### Post by psychovampire85 on 2009-12-19
> **lykwydchykyn said:**
> Ah, that's the one with the 845 chipset.  Definitely upgrade the BIOS to the latest version (A09, I think) because early versions will cause problems with the display resolution.  

If it's just a surf machine pretty much anything will do.  I'd probably just put debian stable with LXDE for the desktop, but that's me.

How would I go about updating the bios with it.

---

### Post by ram2500 on 2009-12-19
Zenwalk is a great, "almost" full-featured distribution for lightweight PCs. I don't recall the exact name of the web browser, but I think it's a clone of Firefox. From my experience, Internet was just plug and play (my ISP is Qwest) and everything ran like a top. However, this was just a machine I set up for my 10-year-old nephew. It had everything he needed (word processing, media player, graphics program, web browser) and ran decent on a 350Mhz K6 w/ 256 MB RAM. As far as I know, the machine works great to this day.

If you have Pentium 4 and above, go ahead with Ubuntu, just add more memory, especially if  you want a little more than web browsing (printer/wireless support, etc).

---

### Post by lykwydchykyn on 2009-12-20
> **psychovampire85 said:**
> How would I go about updating the bios with it.

If it still has windows on it, go to [http://support.dell.com](http://support.dell.com) and download the BIOS update from the drivers area.  I believe the gx260 BIOS can be updated in Windows without a floppy disk.

If you put Ubuntu, Fedora, or Centos on it you can install the BIOS using instructions here:
[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

If you put some other Linux on it, or don't have an OS yet, then you'll probably have to follow instructions on Dell's support site for creating a BIOS floppy.

---

### Post by jerrrys on 2009-12-20
i just did some looking around and it seems that latest bios upgrade was A10, came out in 2006.

can you look at your bios and see what it is?

---

### Post by psychovampire85 on 2009-12-20
> **jerrrys said:**
> i just did some looking around and it seems that latest bios upgrade was A10, came out in 2006.

can you look at your bios and see what it is?
I know the bios isn't up to date because it was a colleges computer they used for teaching purposes.

---

### Post by psychovampire85 on 2009-12-20
> **lykwydchykyn said:**
> If it still has windows on it, go to [http://support.dell.com](http://support.dell.com) and download the BIOS update from the drivers area.  I believe the gx260 BIOS can be updated in Windows without a floppy disk.

If you put Ubuntu, Fedora, or Centos on it you can install the BIOS using instructions here:
[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

If you put some other Linux on it, or don't have an OS yet, then you'll probably have to follow instructions on Dell's support site for creating a BIOS floppy.

It has Xubuntu on it currently so would the ubuntu way work?

---

### Post by lostinxlation on 2009-12-20
In my view, if Xubuntu is too slow, the next stop would be Vector Light. If vector light is too heavy, then give Puppy or DSL a chance.

---

### Post by lykwydchykyn on 2009-12-20
> **psychovampire85 said:**
> It has Xubuntu on it currently so would the ubuntu way work?

Yes, any "flavor" of Ubuntu should work with the Dell repos.

---

### Post by pricetech on 2009-12-21
I believe the GX260 will support up to 2 gigs, but only has 2 memory slots so you'd have to use 2  1gig sticks to make that happen.  Hardy ran just fine on the GX260s here with 1gig of RAM.  I know you said it only has 256, but it might be worth putting some RAM into it if you can scrounge.

The BIOS for that one is an executable, not a floppy image.  You'll have to make your own DOS boot disk to use it should you want or need to go about it that way.  And yes it would run under XP as well.

---

