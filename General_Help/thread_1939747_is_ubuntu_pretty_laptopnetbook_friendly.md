---
title: "is ubuntu pretty laptop/netbook friendly?"
date: 2012-03-12
forum: General Help
---

### Post by Delsos on 2012-03-12
i used ubuntu on my desktop but since i moved here to college we dont have ethernet just wireless, and none of the network adapters i bought work with ubuntu.

but anyways i want to get a laptop, does ubuntu work good with most laptops in terms of compatibility and functionality?

---

### Post by Paqman on 2012-03-12
Yep. To get your wifi working you'll probably need to install a driver using the Hardware Drivers tool. To use that you'll probably need a connection, so you'll probably need to find somewhere you can plug in with a cable to download it. If you stick to an Intel wifi card you won't need any extra drivers, it'll just work.

---

### Post by jingaling on 2012-03-12
Hi,

In my experience the range of Hardware that bun2 works with is excellent. HOWEVER, make sure you stay away from laptops (or any other kind of machine) running an SiS (Silicone Integrated Systems) chip as SiS simply won't write Linux drivers so you will be stuck. I learned this the hard way when I bought a laptop for my grandad. Had to send it back in the end.

Also stay away from machines that run UEFI instead of BIOS as GRUB won't work with UEFI. The only machines I've seen that have UEFI enabled by default and can't be turned off is Lenovo (again, I learned this the hard way).

Apart from that, hardware support is excellent. Go for a Dell or HP and you can't go wrong :)

Kev

---

### Post by oldfred on 2012-03-12
Many new machines have UEFI/BIOS or will work in either mode. But if Windows is in UEFI mode you need to install Ubuntu in efi mode.

Grub will work in UEFI systems, but the install process is not as easy as MBR. Still a few bugs to work around. Backups are even more important, but several users have posted successful installs of UEFI booting Ubuntu.
So far, all successful installs have been where users partitioned in advance.

---

### Post by jingaling on 2012-03-12
I was posting simply from my own experiences and the research I did when I hit those problems. Personally I couldn't get it to work, I wasn't using MBR, it was a blank HDD and I did partition the drive in advance....no joy though.

Anyway, I personally couldn't get it working and it certainly isn't an easy thing to work out for someone with limited Ubuntu experience like myself (only 2 years or so coming from a Windows background).

Kev

---

### Post by Mark Phelps on 2012-03-12
If by "friendly", you mean that it will easily install, load the right drivers, and upon reboot, have all the hardware up and working -- with no manual configuration or installation work on your part ...  I would have to say NO.

I've done a half-dozen different installs, using a variety of old and new laptops, and in EVERY case, there was at least one function that could NOT be made to work.  

And while you could say those don't count because some of the failures were stuff like "special keys" such as rotation, volume, display switching -- in the end, though, that left me with stuff that did NOT work.

So to me, a YES for "friendly" means that EVERYTHING on the laptop works -- even if it takes a little bit of effort to get it working.

Laptop manufactures are INFAMOUS for using lots of customized hardware to squeeze every ounce of performance out of their machines.  This hardware often requires special drivers -- which come preloaded on MS Windows boxes.

All to often, however, even finding these drivers ends up being a LOT of work for Linux distros -- and that presumes you can even FIND them.  

This is NOT to say that there aren't success stories -- I'm sure there are.  But the only TRUE way to find out is to boot a LiveCD of the distro version you want to use on the laptop/netbook of choice and see how well it works.

---

### Post by Basher101 on 2012-03-12
i never had any major issues with Ubuntu, not on my laptop (eMachines E725) or my custom built rig (see below). I was actually really surprised that Ubuntu worked ***better*** with the hardware than windows on the custom build (espacially during installation). But anything apart from that, i must agree to what _[COLOR="Red"]Mark Phelps[/COLOR]_ said.

regards

---

### Post by Paqman on 2012-03-12
> **Mark Phelps said:**
> If by "friendly", you mean that it will easily install, load the right drivers, and upon reboot, have all the hardware up and working -- with no manual configuration or installation work on your part ...  I would have to say NO.


Sure, but you could say the same about any operating system. When was the last time you installed Windows and had everything work straight away?

---

### Post by jingaling on 2012-03-12
I must say that I disagree with what Mark Phelps has said. I've installed Ubuntu on many different machines, from many different vendors and I have never had a problem with drivers apart from the SiS and UEFI issues mentioned above.

I've reinstalled Windows literally hundreds of times and have very rarely seen it were all drivers are working out of the box, it's usually 800x600 graphics, or no wireless, or no eth...or all three! Most of the time chipset drivers are missing also. With Ubuntu you MAY have to run the additional drivers application to get a better graphics driver, or plug in with a cable to get wireless but apart from that I've never had a problem.

However I have found that printer drivers, or to be more precise, MFD drivers are thin on the ground.

Kev

---

### Post by roger_1960 on 2012-03-12
Hi

 Best advice is from Mark Phelps.  Make a live CD or USB stick, find someone (a shop) with the laptop that interests you and boot from the media and test everything.  It will be slow, but you should be able to check what works (or not)

---

### Post by polt on 2012-03-12
There are also a lot of websites that discuss successes and failures of various laptops with linux.

For example:

[http://www.linux-laptop.net/]("http://www.linux-laptop.net/")
[https://wiki.ubuntu.com/Testing/Laptop]("https://wiki.ubuntu.com/Testing/Laptop")
[http://www.ubuntu.com/certification/]("http://www.ubuntu.com/certification/")

---

