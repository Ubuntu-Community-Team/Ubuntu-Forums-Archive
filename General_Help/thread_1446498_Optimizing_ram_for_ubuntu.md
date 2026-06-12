---
title: "Optimizing ram for ubuntu"
date: 2010-04-04
forum: General Help
---

### Post by TurtleJuice on 2010-04-04
I have a dell precision 350 desktop with only 512 mb of ram.  I want to optimize this and was wondering if theres a free program i can use or a site anyone can recomend.  Thanks for any help.

---

### Post by TurtleJuice on 2010-04-04
oh and 2.4 ghz if that matters it seemed like it was running faster the first time i put ubuntu on..  I have 2 hard drives the one i'm using is 40 gb but has a couple errors on it.  the other 20gb i tried to install ubuntu on it cause it has no errors but it wouldnt boot right an error came up.  So i'm trying to optimize this.  I would like to get a program that optimizes what ram i have if anyone has any ideas............

---

### Post by TurtleJuice on 2010-04-04
....

---

### Post by HPD2 on 2010-04-04
You cant optimize RAM, you can however run memtest86 to check the ram for errors.

What you may want is a lighter version of Ubuntu or a derivative like Crunch Bang.

---

### Post by TurtleJuice on 2010-04-04
ok what about the hard drive i seen a walkthrough for speeding up your hard drive somehow but it was for a diferent version.  Anyone else have anything they can add?

---

### Post by TurtleJuice on 2010-04-04
it had this sudo............[COLOR=#000000][COLOR=#0000BB]sudo gedit [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]etc[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]fstab ........then you had to change some things but they were different cause i'm using a diff version
[/COLOR][/COLOR]

---

### Post by NightwishFan on 2010-04-04
Until you know your way around please do not follow any such tutorials. ;)

Trust me, there is no way to optimize RAM (No way I would recommend). It is used by the kernel in a very efficient manner. I am able to run a full Gnome desktop and browse with Firefox on a mere 256mb of RAM. A lighter type of system would even perform better. Your 512mb of RAM is enough to run a speedy Ubuntu session. If you are really interested in a faster experience you need to use a lighter variant of GNU/Linux or Ubuntu. I will list a few and you. Here are lighter alternatives, if you have any questions about them please ask.
[http://en.wikipedia.org/wiki/Puppy_Linux](http://en.wikipedia.org/wiki/Puppy_Linux)
[http://en.wikipedia.org/wiki/Xubuntu](http://en.wikipedia.org/wiki/Xubuntu)
[http://en.wikipedia.org/wiki/Crunchbang](http://en.wikipedia.org/wiki/Crunchbang)

I know one tweak to optimize RAM for desktops but it might reduce battery life on a laptop. Some will disagree but on a system light on memory, increasing the tendency to swap memory out of RAM will actually improve performance. The machine might actually *feel* a bit slower when switching between applications. If you desire perceived responsiveness then do not use this tweak.

Press alt+f2 and a run dialog box should open. Type the following and push enter:
```
gksudo gedit /etc/sysctl.conf
```
The text editor should show a file. Scroll down the bottom and create a new empty line and type this:
```
vm.swappiness = 100
```
Save the file and reboot.

To revert to the default behavior simply open this file again and delete that line, and then reboot. This tweak will cause your actively running application to have more available ram at any time. This is good considering RAM is much faster than the disk. Also fetching pages from the swap file is faster than a cold read off the disk. It accomplishes this by telling the kernel to remove older inactive applications in RAM very often. If this happens to be something you switch back to, there will be a slight pause while it calls the program back into memory from swap. This will happen normally no matter what if you are low on RAM, however this tweaks causes it to happen in a much more conservative way.


Secondly, as for any disk tweaks the only one I would recommend is tuning your i/o scheduler to your workload. This is not relevant to a new user so it will not gain you added performance. The default I/O scheduler is already the best suited to desktop use. It is a very good choice.

The tweak using fstab I am sure is to use noatime. Ubuntu already uses relatime, and that is quite sufficient. In my experience the only thing adding noatime has done was cause problems.

Trust me, Ubuntu is tuned and optimized to be quite good on performance. It is a modern operating system and is a bit stricter on requirements than one made in 2001. Consider the current edition of that certain operating system on 64-bit architecture recommends 2000mb of ram and not just a mere 400mb.

---

### Post by 3rdalbum on 2010-04-04
By default, Ubuntu uses the correct settings for your hard drive. If you have the less efficient settings in /etc/fstab (as I did once when manually editing it), then the Computer Janitor program will tell you about it.

---

### Post by warfacegod on 2010-04-04
@NightwishFan

I'm not necessarily disagreeing, because all systems will behave differently.

@everybody

Aside from Solid State Drives, the speed at which data is handled will almost always be much faster with RAM than a HDD. Setting swappiness to 100 will force the OS to put as much as possible to swap/HDD before ever using the RAM. Without knowing the swap size or the HDD speed, doing this could be unwise. With a smaller swap,say under 1 GB, 100 swapiness *could* make all the difference in the world (or none). With a big swap, however, say 4 or 5 GB, it is almost certain to slow things to a crawl.

---

### Post by TurtleJuice on 2010-04-04
Thank you that was very informative.  As far as the lighter programs what are they lacking that the ubuntu i downloaded from the site has.

---

### Post by TurtleJuice on 2010-04-04
The r eason i'm trying to do all this is mainly for a java ran game called runescape.  are there any plugins at all that will make java run better.  And is wine useable with this.  I downloaded it but i dont know how to use it.

---

### Post by NightwishFan on 2010-04-04
You can install java from the Software Center. I am not sure any specific runescape tweaks because I never played it.

---

### Post by ronnielsen1 on 2010-04-04
One of my boxes is very similar. I'm running xfce with full compiz with no problems. If I had 512 M of RAM it would be slow. I'm running 1.5 G Ram but I'd like to update to the 3 it's capable of. Memory is very important to speed in linux. I'd buy another stick if I were you

---

### Post by cascade9 on 2010-04-04
> **warfacegod said:**
> Aside from Solid State Drives, the speed at which data is handled will almost always be much faster with RAM than a HDD. 

Even the fastest SSD will be slower than good DDR ;) By a long shot. SSDs might be faster than SDRAM, but anyone who has a SDRAM box with an SSD has...er....an interesting setup to say the least.

> **ronnielsen1 said:**
> One of my boxes is very similar. I'm running xfce with full compiz with no problems. If I had 512 M of RAM it would be slow. I'm running 1.5 G Ram but I'd like to update to the 3 it's capable of. Memory is very important to speed in linux. I'd buy another stick if I were you

dell precision 350s use RDRAM. That stuff is really, really expensive...

---

### Post by NightwishFan on 2010-04-04
On a low memory system you do not need random mb of an application floating out there in RAM when the system could use it for buffer or more active programs.

---

### Post by warfacegod on 2010-04-04
> **cascade9 said:**
> Even the fastest SSD will be slower than good DDR ;) By a long shot. SSDs might be faster than SDRAM, but anyone who has a SDRAM box with an SSD has...er....an interesting setup to say the least.

I excluded solid state because I have no experience with them. I didn't mean to imply that an SSD could keep up with RAM (would certainly do better than an HDD).

We see "interesting" setups here all the time.:lolflag: I'd be willing to bet somebody's got an SSD with SDRAM. Why? I'm sure I don't want to know.

---

### Post by ronnielsen1 on 2010-04-05
> dell precision 350s use RDRAM. That stuff is really, really expensive...
I don't recognize that one. In between sdram and ddr1?

---

### Post by cascade9 on 2010-04-05
> **warfacegod said:**
> I excluded solid state because I have no experience with them. I didn't mean to imply that an SSD could keep up with RAM (would certainly do better than an HDD).

We see "interesting" setups here all the time.:lolflag: I'd be willing to bet somebody's got an SSD with SDRAM. Why? I'm sure I don't want to know.

Because they cant afford hyperos/gigabyte iram for total insanity. :D I wouldnt be suprised if somebody had a SSD/SDRAMsetup- probably an old laptop, drive died, shoved in a cheapish SSD to 'give it as much go as possible and no need for big HDD'. 

> **ronnielsen1 said:**
> I don't recognize that one. In between sdram and ddr1?

Sort of. It was quite different to either of them, but appeared well after SDRAM, and before DDR, made by a company called Rambus. Intel bought into the Rambus comany, then used it for the abortive mess of the i820/820e/840 Pentuim 3/Xeon chipsets, then on the P4 850/850e and Xeon 860 chipsets. 

On the P3s, it was, well, pointless (its also part of teh reason why the i810/815 SDRam chipsets have the very low 512M max RAM, they were meant to be 'low end' chipsets- the 820 went to 2GB, and the 840 4GB). The P4 architechturewas originally designed to take advantage of RDRAM, but DDR ended up being cheaper, and faster so they dropped it- the last RDRAM P4 chipset was for the 533FSB models, there was never a 800FSB RDRAM chipset. 

here was talk of using RDRAM on video cards, but I cant recall ever seeing one. RDRAM was in the playstation2, and the last place that it even appears now is in the PS3. 

It might have been more successfull, but Rambus went around sueing all its potential fab partners and quickly got a very bad name. So very few places ended up making it, there was always a shortage of RDRAM, and it was always more expensive than SDRAM, even when SDRAM/DDR prices went very high (2001-2003). It probably would have been quite a bit more expensive then SDRAM even if they had the fab partners... 

Even now, 512MB RDRAM (2x256 MB, P4s used paired sticks of RDRAM) would be about $150. If you can find any. For 1GB, $300 or so, it would be cheaper to just get a new CPU/motherboard/RAM setup.

---

### Post by warfacegod on 2010-04-05
> Because they cant afford hyperos/gigabyte iram for total insanity.  I wouldnt be suprised if somebody had a SSD/SDRAMsetup- probably an old laptop, drive died, shoved in a cheapish SSD to 'give it as much go as possible and no need for big HDD'.

Samsung has had a 256 GB SSD for some time now. Falcon Nothwest has them as an option for their gaming laptops. $$$

---

### Post by cascade9 on 2010-04-05
> **warfacegod said:**
> Samsung has had a 256 GB SSD for some time now. Falcon Nothwest has them as an option for their gaming laptops. $$$

They arent cheap, but the OCZ 1TB SSD was about $3000(IIRC) when newegg had them. 

[http://www.newegg.com/product/product.aspx?item=n82e16820227502](http://www.newegg.com/product/product.aspx?item=n82e16820227502)

Hyper OS looks cheap in comparison, untill you lok at the 64GB limit (and you need 8x8GB DDR2 sticks to get that). 

Base Hyper OS- $400.  
32GB DDR2 (8x4GB)- about $1000-$1200. 

[http://www.hyperossystems.co.uk/07042003/products.htm](http://www.hyperossystems.co.uk/07042003/products.htm)

---

### Post by warfacegod on 2010-04-05
That hyperdrive is basically a hard drive made out of RAM! There is no way in hell I'd ever put an OS on it! If your house loses power for more than a few hours, you're S.O.L. Great idea in theory though.

I think the Samsung 256's where around $700 US.

---

### Post by cascade9 on 2010-04-05
Agreed (BTW, same thing with the iRam). I dont like the idea of another external power brick as well, there are enough power bricks in this world already IMO. 

I've always thought that hyperOS could make a great swap file for people who really use a lot of RAM (3D work and rendering particular).

---

