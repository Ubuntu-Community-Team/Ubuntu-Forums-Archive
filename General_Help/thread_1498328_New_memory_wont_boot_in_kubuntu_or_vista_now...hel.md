---
title: "New memory wont boot in kubuntu or vista now...help!"
date: 2010-05-31
forum: General Help
---

### Post by grandkodiak on 2010-05-31
p5w dh deluxe board, newest driverset and bios 3001
vista 64 ultimate and kubuntu 9.something
750w ps
twin 250gb raid vista ultimate
1tb, 750gb storage, 250gb part for kubuntu
twin radeon x1950 crossfire cards 
 
i just bought some ocz pc2 6400 5-5-5 2gb moduels, 4 total and it wont boot to windows if i have all 4 in. it will boot fine with 1, 2 or 3 of them in, but not 4. i swapped them around, all the moduals seem ok so i dont think its the ram.
 
i was running 4x 1gb oc 1gb 4-5-4-15 modules before hand.
 
what am i missing? it starts to boot normal, gets past raid screen, then right before it normally has first windows splash logo, it just reboots immediatly. i dont see any dump or blue screen or anything like that.
 
if i try safemode, the last thing it tries to load right before it reboots is crcdisk.sys.
 
i also tried booting from a usb live kubuntu and the copy of it i have already on my other harddrive but it too wont work unless its 2,4 or 6gb...never 8gb.
 
i dont really use the linux partition except when vista fails or i feel like being different... but i was able to to use the memtest program before the kubuntu main boot screen with the 8gb in and it took 15 hours scanning before i quit out of frustration, its just too goddamn slow but it doesnt seem to be a hardware issue with the ram modules as far as i can tell.
 
i would appreciate help in windows terms though as i dont know how to work with hardware under linux yet, its far to archaic :D

---

### Post by ajgreeny on 2010-05-31
> but i was able to to use the memtest program before the kubuntu main  boot screen with the 8gb in and it took 15 hours scanning before i quit  out of frustration, its just too goddamn slow but it doesnt seem to be a  hardware issue with the ram modules as far as i can tell.
I can't help with your problem specifically about the memory, but thought it worth saying that the memtest will never actually finish on its own but will just start again at the beginning and as it goes will report errors it finds as a simple number.   It will not stop if anything is wrong, just show a number in the  "errors" line.

To see whether or not you do have a problem you need to run it again for as long as possible and look to see if any errors are reported.

---

### Post by sdennie on 2010-05-31
It sounds like your BIOS doesn't actually support 8GB of memory.  If memtest works with 8GB of memory, that might confirm that.  Memtest isn't asking your BIOS for a mapping of where other devices should live in memory and is just looking at the memory.  An OS will ask the BIOS about what the memory configuration, including other hardware, looks like and act on it.  If the BIOS returns something non-sensical, it will fail.  I'm going to go out on a limb and guess you have a motherboard based on the Intel 965 chipset and so the max RAM is 8GB but, your motherboard doesn't necessarily support that.

The same thing happened to me a few years ago when I had a motherboard with a chipset that supported 4GB of RAM but no OS would boot with 4GB of RAM installed because of the BIOS.

---

### Post by grandkodiak on 2010-05-31
975x according to the site... here are the specs, it says 8gb :-/
 
[http://www.asus.com/product.aspx?P_ID=m4cR4iaPdABNLtQa&content=download](http://www.asus.com/product.aspx?P_ID=m4cR4iaPdABNLtQa&content=download)
 
any other ideas?

---

### Post by sdennie on 2010-05-31
If no operating system will boot with 8GB of memory, I would contact Asus.  It certainly wouldn't be the first time that a motherboard manufacturer has said, "Supports up to X amount of RAM" and when DIMMS finally showed up that allowed you to install X amount of RAM, it didn't work.

---

### Post by grandkodiak on 2010-06-01
pdates.
ok to find where i could edit voltages i had to uncheck auto overclock mode 20% to manual.
Once I did that I just reset as normal, and my cpu speed went back to 2.6ghz down from 3.2 :'( but...
now it boots into windows fine, reads all 8gb.
the catch:
now i notice it displays the ram as PC2 3200... where i just noticed if i run 6gb with overclock mode, it comes up PC2 5300. BUT, the memory itself is PC2 6400???
i'd be happy at the momment now at 5300 8gb and running, because it benchmarked a good percentage above 6gb, and considerably better then my old 4gb, BUT heres the other catch, i benched almost 20% lower in cpu because its running back at stock speed of 2.66ghz... and i cant seem to find where i can change it back in manual page to meet where it was stable 20% over! it wont let me change clock ratio obviously, and there doesnt seem to be an option for FSB. there is a vcore speed or somethin to that such but its locked at 255 i think? should have written it down.
ug.

---

### Post by sdennie on 2010-06-01
Ahhhh.  You didn't mention the machine was overclocked.  Changing hardware on an overclocked machine can mean you might have to re-evaluate your overclock settings.

---

### Post by HereInOz on 2010-06-01
This is not the first MB which I have seen unable to boot with 4 x 2BG RAM installed.  Some Gigabyte boards (P45 chipset) have the same issue.  I would suggest looking for a forum dealing with the specific motherboard or range of motherboards and perhaps there will be some tweaks you can do to get the thing booting.

The Gigabyte boards will often boot if you increase the RAM and processor voltage a little, and I mean a little - too much and you smoke it - because their supply to the chips drops off when you load up 4 x 2 GB pieces of RAM.

Almost definitely this is a motherboard problem, so search the forums of the relevant motherboard and you might find a way out.

---

