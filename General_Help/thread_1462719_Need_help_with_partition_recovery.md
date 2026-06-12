---
title: "Need help with partition recovery"
date: 2010-04-26
forum: General Help
---

### Post by carlihland on 2010-04-26
Hi.

I've been using Ubuntu for a few years now and I'm completely blown away by the OS. Big thumbs up to everybody in the community.

Sadly I have a problem using the Disk utility that comes with gnome. Here's the story behind it:

I built an external drive using an Intel X25 SSD drive in a eSATA cabinet because I couldnt get one ready made from any known manufacturer. After using it to speed up my VMWare images that reside on the external drive (usb 2.0 was a drag), I decided to implement this very same drive in my Alienware m15x with a standard SATA 500Gb disk based drive. This drive contains a dual boot setup with Ubuntu 9.10 x64 and Windows 7 Ultimate x64. So I split open the Alien and swapped drives. Here's the catch. I booted the computer using the Live CD with both drives connected. SATA 500 gb disk spinner now in an external cabinet. I transferred my VMWare images from the now internal ssd drive and onto the 500Gb external drive. Sweet. Rebooted and installed Ubuntu on the ssd. Now the computer is getting crazy fast. So then I wanted to boot Windows from the external drive using Grub. So I ran an update-grub with both drives connected. It did detect my external Windows 7 but gave me the drive map error. I looked it up here and I saw a suggestion on checking the boot flag. Oh well? I fired up Disk Utility and quite rightly, no boot flag on the external Win7. I applied the boot flag and thought to myself, all I need to do now is run update-grub again and I'm honky dory. No ball. The Disk Utility gave me the Ugh something error message and froze the Disk utility. After this I had some inconcistent feedback from Disk Utility and I decided to install and fire up gParted. So I did. My Windows 7 is now an unrecognizable partition type.

It seems the demo version of Acronis Partition Expert Pro 64 bit for Windows after 2 hours of reading the disk can restore my data somehow.

But is there any way I can go about changing the partition table from my now sweet-as-my-grandmas-butt-on-barstool 64 bit ssd driven superfast Ubuntu desktop? I've been reading that messing about with these things can result in a faulty length of the partition resulting in the unknown type. Some savvy dudes do this by uploading a new table to disk or something. But there ends my savvyness I'm afraid. ;)

Big ups from Norway and suggestions greatly appreciated. It will save me countless hours of modding and tuning my flightsim, restore some psd files I need and some bangin loops I got goin in Fruitystudio. :-D

---

