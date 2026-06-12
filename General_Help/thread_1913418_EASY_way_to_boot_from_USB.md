---
title: "EASY way to boot from USB?"
date: 2012-01-22
forum: General Help
---

### Post by mk5500 on 2012-01-22
I have a Pentium 3 (several actually) that don't allow USB boot in their BIOS.

I saw this "plop" ? but just too involved -- don't have the time for it.

ANY easy way or add on I can install that will allow me to run the OS from a USB drive?

Actually using Lubuntu. Using the PC as a web browser -- no apps.

---

### Post by 2F4U on 2012-01-22
If your machines don't support booting from usb, there is as far as I know no way to make it happen.

---

### Post by TeoBigusGeekus on 2012-01-22
AFAIK plop is your only chance.

---

### Post by bluexrider on 2012-01-22
> **mk5500 said:**
> I have a Pentium 3 (several actually) that don't allow USB boot in their BIOS.

I saw this "plop" ? but just too involved -- don't have the time for it.

ANY easy way or add on I can install that will allow me to run the OS from a USB drive?

Actually using Lubuntu. Using the PC as a web browser -- no apps.

I have a couple of machines that don't allow USB booting but once I had created the live USB I just inserted the Ubuntu CD and started the machine. It found the pendrive right away.

---

### Post by mk5500 on 2012-01-22
yeah ok -- saw that and just saw something about GRUB? anyone know about that?

seems I'm out of luck though.

---

### Post by mk5500 on 2012-01-22
so you had a usb drive installed then ran a live cd and it worked? after that, it would boot without the cd?

---

### Post by Double.J on 2012-01-22
Hi there, unless I'm misunderstanding, in which case please correct me, but if the bios does not support booting off of usb, then you can't do it. It's very unlikely with a pentium 3, but you mayt be able to get a bios update if you contact the manufacturer.

In terms of what you could do with USB - boot off a CD each time and auto mount the usb stick to store all data from. As you would be using such old machines, you could use a distro such as puppy, which also lets you create your own live cd, set up as you wish. then once booted mount the usb and read/write data to there.

Obviously a few problems - everytime you want to make a system change, you'd have to change the live cd, the USB is probably USB1 so slow and you'd loose your USB port and CD drive.. though as puppy loads to RAM the CD could be removed once booted.

You may also be able to use a bootloader on an internal hard drive to point to the USB partition. I mention this second as if you had an internal drive on a machine most likely using USB 1 with limited USB ports, you'd probably use the internal drive? And the motherboard itself may not be able to support this.

Hope it helps!

---

### Post by WasMeHere on 2012-01-22
Hi mk5500,

Do your P3-PCs have CD drives? In that case, is there any way for you to burn a boot CD from your iso file? (Maybe using the computer of someone else, if you have no CD-RW).

Otherwise, you can use an external CD or DVD drive attached via USB (maybe borrow one, or attach an internal box temporarily via an adapter).

... or try the fix suggested by *bluexrider*.

Have fun finding out :-)
Olle

---

### Post by snowpine on 2012-01-22
Install Lubuntu to your internal hard drive, problem solved (and you will have better performance).

---

### Post by mk5500 on 2012-01-22
are solid state hard drives still a ton of money? (I'll go and look now at newegg)

are they a direct replacement for conventional drives as far as the bios is concerned I wonder?

---

### Post by mk5500 on 2012-01-22
wow -- ebay has 64gb SS hard drives way under 100 bucks !

last time I looked at  ss drives was 3 or 4 years ago, need to start paying attention.

still wonder about the bios with these?

---

### Post by snowpine on 2012-01-22
> **mk5500 said:**
> are solid state hard drives still a ton of money? (I'll go and look now at newegg)

are they a direct replacement for conventional drives as far as the bios is concerned I wonder?

Probably a waste of money for an old Pentium 3, because faster storage cannot compensate for CPU bottlenecks or insufficient RAM. For the price of an SSD you could go on Craigslist and buy a 2nd-hand Pentium 4 with 1gb RAM (and boot-from-USB capabilities). This is my personal recommended minimum hardware specs to run desktop Linux.

---

### Post by mk5500 on 2012-01-22
thing is, I have a dozen of real nice P3 machines 733mhz -- are you saying I'll just have "redunadant" performance or actual read/write problems?

---

### Post by tea for one on 2012-01-22
> **mk5500 said:**
> I have a Pentium 3 (several actually) that don't allow USB boot in their BIOS.

I saw this "plop" ? but just too involved -- don't have the time for it.

ANY easy way or add on I can install that will allow me to run the OS from a USB drive?

Actually using Lubuntu. Using the PC as a web browser -- no apps.

A few years ago, when my brother had an old PC that would not boot from USB, I managed to create a "Boot CD" for Ubuntu using instructions from the Pendrive Linux site.

I have not had the need to use these instructions recently but, in the past, they were very useful.

There is a wealth of information on this site if you haven't come across it before.

[http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-11-10/](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-11-10/)

---

### Post by WasMeHere on 2012-01-22
I think it would work, but I agree with *snowpine*, that it is no good solution, unless you want to do it just for fun, and then 're-use' the SSD in a more powerful computer, where it can really be fully utilized.

Why not simply boot from a CD, or if you want persistence, install lubuntu onto the hard drive?

*Edit: Or are there no hard disk drives in the P3s?*

---

### Post by snowpine on 2012-01-22
> **mk5500 said:**
> thing is, I have a dozen of real nice P3 machines 733mhz -- are you saying I'll just have "redunadant" performance or actual read/write problems?

There is no such thing as a "real nice P3 machine" in 2012, I'm afraid. Personally I would sell my 12 old computers to buy 1 fast one. (Unless there is a reason you haven't explained to us why you need 12 computers simultaneously running Linux slowly? :))

But that is a tangent to your actual question; do you feel you have enough information now to run Lubuntu through its paces, using the suggestions you've been given?

---

### Post by mk5500 on 2012-01-22
tired of failing (and noisy) hard drives.

I may try one of these 64gb ssd drives on ebay.

---

### Post by CC Inc on 2012-01-22
I just put PLoP on a floppy disk and booted from that. It allowes you to boot from usb, cd, network, and all your hard drives. I think you can also put it on a CD.

---

### Post by Double.J on 2012-01-22
> **mk5500 said:**
> are solid state hard drives still a ton of money? (I'll go and look now at newegg)

are they a direct replacement for conventional drives as far as the bios is concerned I wonder?

They are coming down fast, but of course I really don't know about compatibility on old mobo's - many have limitations as to what size drive they can even see. 

If they did work, the speed advantage probably wouldn't be worth the cost - you almost definately have an IDE (PATA) Hdd interface, so you'd have to use a IDE to SATA adapter that slows communications anyway, as well as the speed limitation of the original hardware. So faster - yes, but probably not miracle fast, and this is just going to address boot times and program load times - not the whole system. 

On these machines, I'd look for cheap IDE drives with faster speeds and bigger caches... see if you can get a RAM upgrade.. that'll help a lot with modern systems. 

Personally I recommend trying some live CD's to see what performance is available - old hardware eventually reaches the point where you can't keep it going, so look at your CPU speed, upper ram limit, what video cards are they running? what video cards are you prepared to go to? its all cost/benefit at the end of the day. 

The usual suspects for older hardware are
Lubuntu (probably most commonly used)
Xubuntu (similar specs to lubuntu, less RAM, same CPU)
Crunchbang (lowest RAM usage, most minimal)
Puppy (requires 512 ram realistically, runs totally live - boot media can be removed)

As a reference point for price comparison - an ITX box for basic computing can be made for a little under £100 on a real budget if you shop around on ebay and can run windows 7 ultimate for the basic user (internet,office,music)

---

### Post by kleeh777 on 2012-01-22
Think it can be done..

All u need is 
1. grub-legacy
2. and empty fat32 or ext-partiton (and thats what u also have on ur usb)

Then copy the content of the .iso file to the empty partiton and make a menu-entry like this and edit the entries: /boot/grub/menu.lst

title Parted Magic SSD sdc6
uuid      ad85538d-e427-49b7-9e93-45eb40fd1cbd
kernel   /pmagic/bzImage root=UUID=ad85538d-e427-49b7-9e93-45eb40fd1cbd
initrd     /pmagic/initrd.img

It can be done at least withot USB nor CD and directly from harddisk. I am booting my Parted Magic from a 1gb partition on a 64 SSD with a i7 980x. Fast booting ;) 

Sometimes it need more commands to work, not an expert by any means but this has truly worked for me. Installed Linux Mint this way recently.

kernel   /pmagic/bzImage root=UUID=ad85538d-e427-49b7-9e93-45eb40fd1cbd boot=casper noprompt ro

---

