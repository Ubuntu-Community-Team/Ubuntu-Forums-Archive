---
title: "PC Build Question - onboard graphics"
date: 2012-07-12
forum: General Help
---

### Post by mike acker on 2012-07-12
I've decided to "take the plunge" and build a desktop PC for myself.

Q: If the motherboard I select does not have on-board graphics does that mean I will need to add a video card to my parts list?

I haven't got a Ubuntu bean yet but I do have my first Ubuntu system running* so please forgive me if I'm asking in the wrong area

*It's on an old Dell 4550 that the kids brought back loaded with malware. I purged XP and reformatted the drives and loaded Ubuntu. It runs rather well :D

uh-oh! I see I've now been awarded my first bean yea

---

### Post by cool110 on 2012-07-12
Yes. A motherboard without some form of on-board graphics will not have a VGA port or any other way of connecting a monitor.

---

### Post by ds5v50 on 2012-07-12
If you already wiped XP and installed ubuntu on it.. it must have some form of video card. If your talking about building the pc using the Dell 4550. If I'm mis-reading the post then yes what the other person said...

---

### Post by Redblade20XX on 2012-07-12
> **cool110 said:**
> Yes. A motherboard without some form of on-board graphics will not have a VGA port or any other way of connecting a monitor.

Technically you can have a computer without a gpu. The cpu will have to over compensate for it though thus making it slow. :p

- Ree

---

### Post by habana on 2012-07-12
Unless you are intending to play video games, integrated graphics will be pefectly adequate for your new PC. It will also require a smaller power supply and run cooler. Install Ubuntu on a SSD and it will be very fast! Install plenty of RAM as the the graphics chip shares it with the CPU.

My recent build:

Gigabyte B75M-D3H
Intel i5-2400
8GB RAM
OCZ Vertex 3 60G (Ubuntu)
2 x old 160GB HDD (data}
Antec 380W PSU (80+)


Good luck!

---

### Post by mike acker on 2012-10-04
> **habana said:**
> Unless you are intending to play video games, integrated graphics will be pefectly adequate for your new PC. It will also require a smaller power supply and run cooler. Install Ubuntu on a SSD and it will be very fast! Install plenty of RAM as the the graphics chip shares it with the CPU.

My recent build:

Gigabyte B75M-D3H
Intel i5-2400
8GB RAM
OCZ Vertex 3 60G (Ubuntu)
2 x old 160GB HDD (data}
Antec 380W PSU (80+)


Good luck!

~~~
I bought 12GB ram but the motherboard instructions advise installing either 8GB or 16.  I'm going to power up with 8GB later today and order the other 4GB chip. I still need another SATA cable too.  I'm hoping to bring this up with RAID0 as I think RAID0 is the best solution to the annoying constant "backup yer computer" problem.   RAID0 would change that from something I put off more than I should to something that the system does for me all the time.

---

### Post by windscape on 2012-10-04
Hi,

According to many sites like this one: [http://duncandavidson.com/blog/2011/07/raid_is_not_backup]("http://duncandavidson.com/blog/2011/07/raid_is_not_backup") RAID is NOT a backup! Especially RAID 0! RAID 0 is striping, so that means that if either drive fails, it takes ALL of your data on the RAID array with it.

Please, backup your important files to another system or offsite.

I personally manually copy important files to my file server, backup the file server to external drives using rsnapshot scheduled by cron, and use Ubuntu One to store the frequently needed important files.

---

### Post by mike acker on 2012-10-04
> **windscape said:**
> Hi,

According to many sites like this one: [http://duncandavidson.com/blog/2011/07/raid_is_not_backup](http://duncandavidson.com/blog/2011/07/raid_is_not_backup) RAID is NOT a backup! Especially RAID 0! RAID 0 is striping, so that means that if either drive fails, it takes ALL of your data on the RAID array with it.

Please, backup your important files to another system or offsite.

I personally manually copy important files to my file server, backup the file server to external drives using rsnapshot scheduled by cron, and use Ubuntu One to store the frequently needed important files.

yep, I already got corrected on this ( yea !! ) .  It's RAID1 that I want (mirrored disks ) .

---

### Post by pqwoerituytrueiwoq on 2012-10-04
if you motherboard has no vga/dvi/hdmi/display ports you will need a discrete GPU
if the mother board has some of these post and has no integrated gpu chipset you will need a cpu with a integrated gpu (amd's APUs are a good example of this)
some of intels CPU have a GPU in them (amd makes better GPUs than intel and intel makes better CPUs than amd)
if you get a cpu with no gpu in it and a motherboard with no gpu chipset you will need a discrete GPU
you dont need over 4gb ram for everyday stuff, 8gb for gaming (you could get by with 4gb), anything more is for media editing

---

### Post by mike acker on 2012-10-05
> **pqwoerituytrueiwoq said:**
> if you motherboard has no vga/dvi/hdmi/display ports you will need a discrete GPU
if the mother board has some of these post and has no integrated gpu chipset you will need a cpu with a integrated gpu (amd's APUs are a good example of this)
some of intels CPU have a GPU in them (amd makes better GPUs than intel and intel makes better CPUs than amd)
if you get a cpu with no gpu in it and a motherboard with no gpu chipset you will need a discrete GPU
you dont need over 4gb ram for everyday stuff, 8gb for gaming (you could get by with 4gb), anything more is for media editing
~~~~~

thanks

I selected a motherboard that has onboard graphics and audio

I had to kinda pick thru the catalog to find one i liked!! most seem to expect me to install a GPU but I don't think i need it.  the old Dell box I was experimenting on was not enough machine -- single core 2.4 ghz cpu and only 1GB ram

i will probably have to plead guilty to over-kill on my new  box, but oh well.
ps it runs great!!  the M5A88-M even allows me to overclock the CPU but I see no need to do that.  what I'm interested in is the RAID1 option

---

