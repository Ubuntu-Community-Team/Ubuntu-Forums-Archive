---
title: "Ubuntu Installations keep crashing."
date: 2010-12-09
forum: General Help
---

### Post by buellboy on 2010-12-09
Hello folks, just :popcorn:ping my posting cherry on this forum, yes that's right I'm a n00b (sorta).
 
I'm trying to build a server which will allow users of the network to save their files on it and will also provide some users with the ability to save to an encrypted drive (for my dad's business)
 
Let me cut to the chase: my server becomes unresponsive very very often (at least 2/3 times every 10 minutes), most common symptoms are a stuck mouse and no scroll lock response. This happens when running on the following (i tried them all):
 
- Ubuntu 10.04, 10.06 both live and HDD installs
- Fedora (latest) both live and HDD installs
- Mepis (latest) both live and HDD installs
 
And crashes often (once an hour) on:
- Ubuntu minimal install with gnome front end (a outlined in a guide somewhere here).
 
You may think: Hardware! RAM! Raid Controller! Board! Graphics Card!, over-Heating! however I have done the following:
- Memtest for a total of 24 hours (I have ECC memory anyway)
- Low level format (or rather zero-fill) of all drives
- Ran Knoppix, DSL, Knoppix DVD version,
- Used an infra-red thermometer to measure critical chips temp
 
All the above test returned negative and Knoppix has been up for now close to 36 hours.
 
I have read several articles about turning Compiz off and turning on swap files but I've had no luck.
 
The reason why I want to run Ubuntu is because Samba works great on it unlike Knoppix, where no actual Samba is installed (not the one I want anyhow).
 
My specs are as follows:
 
1. Rioworks HDAMA motherboard with 2x AMD opteron 250
2. 1GB of IBM ECC memory
3. 1x Intel SSD Sata drive 40GB
4. 4x 500GB SATA Seagate all attached to a 3Ware RAID 9500S-4LP, in Raid 1 so effectively OS sees 2x 500GB
5. On-board ATI Rage 8mb VGA card(or so I'm led to believe)
 
Now the crash CAN be re-created by me moving the mouse or a window up and down at speed.
 
I have observed the memory usage meter and nothing looked weird next thing....bam un-responsive.
 
The only other thing I can think of is the screen saver or the login manager but really I'm at a loss! I just want a simple install with Encryption, Samba and a gui for the random check on things once in a blue moon!
 
Any help is appreciated!

---

### Post by pricetech on 2010-12-09
sounds like you have an incompatible system, though I can't explain why knoppix works when others don't.

Did you try keeping the Ubuntu live CD up for a period of time to see how that worked ??

I'd run diags on the drives and RAID controller as well.  Check with the vendor so see what they offer in the way of diagnostic tools.

I'd also check the hardware compatibility list to see how your hardware stacks up.

---

### Post by buellboy on 2010-12-10
I think my problem was a mix of hardware/power/software problems.

First of all my drives were set do cache. Secondly mid-way through installing the server the electrical line seemed to faulter...it never did cut out but was flickering at times, possibly during a disk format.

Secondly there was a problem with crypto tools making the encrypted drive a bit shaky on top of the power cuts or even worse during installation (rendering the CD rom a bit useless as its powered by an external power supply and not within the UPS of the system)

Somewhere in between operating systems and trial and error, it must have been fixed, by a fresh re-format and removal of encryption + new installation of Ubuntu desktop.

It's only been running 24hours so early days yet but hopefully this won't come back!

---

