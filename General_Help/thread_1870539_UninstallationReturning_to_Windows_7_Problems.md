---
title: "Uninstallation/Returning to Windows 7 Problems"
date: 2011-10-27
forum: General Help
---

### Post by LostForever on 2011-10-27
I'm in way over my head by this point, so I'm very sorry if I seem like I'm asking stupid questions. I may as well start from the beginning.

I originally had Vista on my machine, and through the promo at the time I bought my laptop, I got a Windows 7 upgrade disc. My laptop now runs Windows 7, though the recovery partition is still Vista.

A few months ago I installed Ubuntu 10.04 LTS as a dual boot system. More recently, I tried to remove it. I followed this guide: [http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/) using EasyBCD. At the point where it says 

[LIST]
[*]Try to boot your system just to make sure that it’s going  directly to Windows without any interference from GRUB. If everything is  OK, let’s continue to the next step.
[/LIST]
I did so. And it didn't work. It wouldn't boot anything. I've since played around with a host of options, and as far as I can gather, I have the following;
SDA1 is Vista (Loader), but accessing it does nothing, or rather, it starts cycling through the process of loading Vista without managing to do anything.
SDA2 is also called Vista (Loader), but is my main 200GB piece of hard drive with Win 7 on. I can't access this.
SDA3-8 I think are various Ubuntu bits. I reinstalled it once today to get GRUB running again, but without any luck in solving my problem. My most recent action was to run lilo, but that didn't work either.

Literally any help would be appreciated. I never had an original Vista disc, and my Win 7 upgrade disc is far, far away. I'll try to provide as many details as possible (I currently have it running ubuntu through a USB), and I may be able to access someone else's laptop with Windows 7, and possibly a stack of DVD-R's if they would be of any use.

Thanks for reading this.

---

### Post by oldtimer7777 on 2011-10-27
You need to buy the Full OEM disc of Windows from the electronics/software store.

Borrowing it and installing your friend's copy would be illegal, so I can't recommend you doing something like that. 

Then you are going to need to wipe all your Ubuntu partitions clean with gparted. You will need to create a Live USB stick of Ubuntu to boot from in order to run gparted.

After you wipe your devices and reformat your harddrives to NTFS, you should be ready to install Windows 7. 

If you can't handle this job yourselves, you should take it to Geek Squad, or the computer repair guy and have give them those instructions.

There is no alternative to buying Windows if you need Windows. 

"Not all who wander are lost"


> **LostForever said:**
> I'm in way over my head by this point, so I'm very sorry if I seem like I'm asking stupid questions. I may as well start from the beginning.

I originally had Vista on my machine, and through the promo at the time I bought my laptop, I got a Windows 7 upgrade disc. My laptop now runs Windows 7, though the recovery partition is still Vista.

A few months ago I installed Ubuntu 10.04 LTS as a dual boot system. More recently, I tried to remove it. I followed this guide: [http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/) using EasyBCD. At the point where it says 

[LIST]
[*]Try to boot your system just to make sure that it&#8217;s going  directly to Windows without any interference from GRUB. If everything is  OK, let&#8217;s continue to the next step.
[/LIST]
I did so. And it didn't work. It wouldn't boot anything. I've since played around with a host of options, and as far as I can gather, I have the following;
SDA1 is Vista (Loader), but accessing it does nothing, or rather, it starts cycling through the process of loading Vista without managing to do anything.
SDA2 is also called Vista (Loader), but is my main 200GB piece of hard drive with Win 7 on. I can't access this.
SDA3-8 I think are various Ubuntu bits. I reinstalled it once today to get GRUB running again, but without any luck in solving my problem. My most recent action was to run lilo, but that didn't work either.

Literally any help would be appreciated. I never had an original Vista disc, and my Win 7 upgrade disc is far, far away. I'll try to provide as many details as possible (I currently have it running ubuntu through a USB), and I may be able to access someone else's laptop with Windows 7, and possibly a stack of DVD-R's if they would be of any use.

Thanks for reading this.

---

### Post by satanselbow on 2011-10-27
> **oldtimer7777 said:**
> You need to buy the Full OEM disc of Windows from the electronics/software store.

Borrowing it and installing your friend's copy would be illegal, so I can't recommend you doing something like that. 


If the OP has his own "unique" key for the w7 upgrade - the source of the media (assuming it provides the w7 for which he has a valid key) is immaterial and it is in no way illegal to use other media. You pay for the key - not for the disc.

---

### Post by oldtimer7777 on 2011-10-27
> **satanselbow said:**
> If the OP has his own "unique" key for the w7 upgrade - the source of the media (assuming it provides the w7 for which he has a valid key) is immaterial and it is in no way illegal to use other media. You pay for the key - not for the disc.

That is correct, however you are only able to use MS keys a limited number of times, and after that you are required to repurchase a new key.
They said that they had Vista originally, that means they don't have an OEM key for Windows 7 on the bottom of that Laptop right now. So they are going to naturally need to purchase a OEM Windows 7 if they wants to use Windows 7. They can easily go back to Vista and use the key for Vista on the bottom of her laptop, and without breaking any software piracy laws.

---

### Post by sgage on 2011-10-27
> **oldtimer7777 said:**
> That is correct, however you are only able to use MS keys a limited number of times, and after that you are required to repurchase a new key.

This is simply not true. 

What the OP should do is download a Win7 Rescue Disk image (they are available from MS and various torrent sites), burn a CD, and boot with it to try a recovery that way first.

But he may have to reinstall - if he has a valid key he can download an appropriate Win7 install image and start over.

---

### Post by LostForever on 2011-10-27
I have a valid key for Vista, and a genuine CD that will update it to 7. I'm not sure if the key would work directly with 7 though.

---

### Post by satanselbow on 2011-10-27
> **oldtimer7777 said:**
> That is correct, however you are only able to use MS keys a limited number of times, and after that you are required to repurchase a new key.


Sign... FUD...

Obviously if a key is repeatedly used an exceptional number of times it may/will ultimately be blacklisted by MS. Any key made public by way of blog / website etc will very quickly join the list.

If the OP can reinstall vista from his recovery partition the key on the machine will be valid. The key for the W7 would then be valid for AN UPGRADE ONLY - regardless of upgrade disc/download source.

Keys on the bottom of laptops etc get rejected by the web authentication all the time when they entirely valid (multiple failed installation attempts / registry corruption etc) - whether 6 days or 6 years old - use the telephone system to authenticate in this case.

---

### Post by oldtimer7777 on 2011-10-27
> **LostForever said:**
> I have a valid key for Vista, and a genuine CD that will update it to 7. I'm not sure if the key would work directly with 7 though.

Then you have discovered the Order of Operations to reinstall Windows, in systems engineering.  First install Vista. Then upgrade to Windows 7 with the upgrade disc.  There is no way around it.

---

### Post by satanselbow on 2011-10-27
> **LostForever said:**
> I have a valid key for Vista, and a genuine CD that will update it to 7. I'm not sure if the key would work directly with 7 though.

That is correct - Upgrade, OEM and Retail keys are separately distributed and not interchangeable 

Your upgrade key will not therefore be will for a full oem/retail install ;)

Glad you got all your bits together :D

---

### Post by oldtimer7777 on 2011-10-27
> **satanselbow said:**
> Sign... FUD...

Obviously if a key is repeatedly used an exceptional number of times it may/will ultimately be blacklisted by MS. Any key made public by way of blog / website etc will very quickly join the list..

You need to contact the vendor on how many times it is allowed to reuse a key.. For example, when I contacted my vendor years ago, about Windows XP, they said it was 11 times. Period. I have no idea now with Vista or 7 because I stopped using MS completely, because of stuff like that.

---

### Post by LostForever on 2011-10-27
Thanks to everyone who is helping.

> **oldtimer7777 said:**
> They said that they had Vista originally, that means they don't have an OEM key for Windows 7 on the bottom of that Laptop right now. So they are going to naturally need to purchase a OEM Windows 7 if they wants to use Windows 7. They can easily go back to Vista and use the key for Vista on the bottom of her laptop, and without breaking any software piracy laws.

I'm in the UK if that makes any difference, and there was some form of promotion ran through the manufacturers that if you bought a laptop within about 6 months before the release of Windows 7, you would be given a free upgrade to Windows 7.

> **sgage said:**
> What the OP should do is download a Win7 Rescue  Disk image (they are available from MS and various torrent sites), burn a  CD, and boot with it to try a recovery that way first.

I'd seen this suggested a few times with the startup recovery option (or something similar). How would I burn the CD?

> **oldtimer7777 said:**
> Then you have discovered the Order of Operations to reinstall Windows, in systems engineering.  First install Vista. Then upgrade to Windows 7 with the upgrade disc.  There is no way around it.

I'm kinda hoping that's the last resort.

> **oldtimer7777 said:**
> You need to contact the vendor on how many times it is allowed to reuse a key.. For example, when I contacted my vendor years ago, about Windows XP, they said it was 11 times. Period. I have no idea now with Vista or 7 because I stopped using MS completely, because of stuff like that.

I've not used it more than twice over however many years, so it should be OK.

---

### Post by oldtimer7777 on 2011-10-27
I'm in the UK if that makes any difference, and there was some form of promotion ran through the manufacturers that if you bought a laptop within about 6 months before the release of Windows 7, you would be given a free upgrade to Windows 7.

**You would probably need to buy the Windows 7 upgrade package to have that option.**

I'd seen this suggested a few times with the startup recovery option (or something similar). How would I burn the CD?

**I don't think you can burn Windows like that to installation Disc.  The only windows you can burn to a disc is Windows Server 2008 from the Microsoft web site. If you want to wipe Ubuntu off your system you will need to create an Ubuntu live dvd/usb flash drive to boot from. Boot from that device and run gparted from the Ubuntu desktop to remove the Ubuntu partitions, and repartition and format to NTFS to install Windows.**

I'm kinda hoping that's the last resort.

** Well there is only one correct legal way to do it.**

I've not used it more than twice over however many years, so it should be OK.

**You should be fine, but you are going to need a Vista install disc, and then a Win7 upgrade disc w/Win7 key.**

:popcorn:

---

### Post by BillyBoa on 2011-10-27
I had the same problem and I did something else. I re installed Ubuntu but creating a separate boot directory with a size of 100mb. Afterwards I installed startup manager and set it to boot first on Windows and the time to wait to 0. Then from Windows I delete the ubuntu partitions apart from the boot of 100mb and that's it.

---

### Post by Mark Phelps on 2011-10-27
Starting with Windows 7, MS made the media essentially the same.  That means, you can use a Win7 Professional DVD to install Win7 Home Premium.  However, you may have to do some tweaking to a config file to allow it to install a version different than the one shown on the box.

Also, you CAN do an install of Win7 using ONLY an Upgrade disk.  But, since MS doesn't really want you to do this, there are some tricks involved.

For answers to these and other questions, you should really go to the Windows 7 forums: sevenforums.com.

They have tutorials there that will walk you through doing both of these.

---

### Post by LostForever on 2011-10-27
OK, so on a slightly different problem...

I have almost everything backed up anyway, but by the sheer number of failed methods of recovery, I appear to have lost the ability to access my files through ubuntu to back them up ready for a fresh install.

Everything is on SDA2. This isn't listed on 'Computer'. Is there a way of circumnavigating in order to access my stuff?

---

