---
title: "Multiple video cards, ATI and NVidia, plus a bit of RAID problems"
date: 2010-10-08
forum: General Help
---

### Post by megaspel on 2010-10-08
Hello there, I've recently started getting into Linux, installed it onto a memory stick so I can take it wherever I want.

Let's get my first, biggest problem out of that way. I have an NVidia Geforce 8600GT, and a ATI Radeon 4770, both of these are connected to seperate monitors. Ubuntu detects them both, but only lets me use one driver at a time, saying that they are different versions of each other, my second screen plugged into my NVidia card remains blank.

Now what confuses me is that [my xorg file](http://pastebin.com/0fSmncgA) has no mention of ATI, even though I'm using only my ATI card, and it just has NVidia everywhere, even though my NVidia card doesn't work. When I enable the NVidia card and restart, it uses the NVidia driver on the ATI card, so the second monitor still doesn't light up and the resolution is wrong and all that.

My second, somewhat less important, problem is that I can't boot up Linux while my computer is in RAID mode. I have a url=http://www.asrock.com/mb/overview.asp?Model=M3A770DE]ASRock M3AA70DE[/url] motherboard running 2 1TB hard drives in RAID 0. (I know raid 0 is terrible, but I'm waiting for an external hard drive to back it up before changing it to JBOD or something.) While it's in RAID mode, when I boot into Linux I get a grub recovery error saying disk could not be found, and no commands work. However, when I set it to IDE OR AHCI, I can boot into Ubuntu fine, but I can't leave it in those modes otherwise I can't boot into my Windows 7 partition on my RAID hard drives. This happens whether I boot into my Ubuntu installation on my 16GB USB drive, or when I boot into the installation on the 20GB IDE drive inside my computer.

Any help would be appreciated and actually helpful help will be rewarded with fabulous prizes! I will draw the person who helps me the most a picture of any subject. You can see my portfolio of previous drawings and whatnot here: [http://melior.bioviral.net](http://melior.bioviral.net)

---

### Post by formaldehyde_spoon on 2010-10-10
Sorry, I don't know enough about Linux gpu drivers be be of much help, but I'm surprised you have that problem with an nvidia + an ati -  I thought you could install both their drivers side by side.

I had a similar problem with 2 nvidia cards that used different drivers - I had to replace one of the cards with another nvidia card that used the same driver as the third card - couldn't have 2 different nvidia drivers installed.

---

### Post by P4man on 2010-10-10
I didnt even know it was possible; but if it is, you might have a better chance with the opensource drivers than the proprietary ones. Does it work without proprietary drivers? 

Thing is, I cant imagine nvidia did a lot of testing their drivers side by side with an ATI driver or vice versa. Im sure both will happily overwrite each other settings in xorg.conf; though this file is no longer needed, at least the catalyst driver still seems to create one. I doubt it would generate an entry for the nvidia card. Perhaps manually adding it could help?

Second thought; why do you set it up like that? Why not connect both monitors to a single card?

Last thought; many laptops today have 2 videocards (one integrated low power, and one discrete for performance). Though they share a single screen and framebuffer, so its clearly a different setup than yours, they do require a newer kernel to work properly. You could try this one:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/)
Its for maverick (10.10), but you didnt say which version of ubuntu you you are using. 

As for the RAID issue; have you tried booting ubuntu with the nodmraid option? Just add it to your kernel line, see if that helps.

---

