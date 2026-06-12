---
title: "Ubuntu will not boot from my external hard drive and it was installed by another pc"
date: 2012-05-20
forum: General Help
---

### Post by feature pro on 2012-05-20
I installed Ubuntu into my external hard drive using AMD A8 laptop.
it was full installation of Ubuntu into external hard drive.

I just try to boot from my other Toshiba Satellite (intel i5)laptop and external hard drive is not even recognized by Toshiba Satellite laptop.  

Boot grub is all installed correctly what can be an issue of this?

I would appreciate any help on it. thanks

---

### Post by wilee-nilee on 2012-05-21
> **feature pro said:**
> I installed Ubuntu into my external hard drive using AMD A8 laptop.
it was full installation of Ubuntu into external hard drive.

I just try to boot from my other Toshiba Satellite (intel i5)laptop and external hard drive is not even recognized by Toshiba Satellite laptop.  

Boot grub is all installed correctly what can be an issue of this?

I would appreciate any help on it. thanks

Can you be more detailed in what OS's are on the toshiba, and if any are linux do they see the external in gparted or in a partitioner, is the usb drive seen in the home of a linux install on the toshiba.

Is it that you see no usb drive in the toshiba bios, could itbe  being read as another read and listed differently.

Do you know the per-session boot menu key prompt on my toshiba it is f12 at powering on at the bios flash not the actual bios.

So we can assume the external boots on the AMD.

---

### Post by feature pro on 2012-05-21
> **wilee-nilee said:**
> Can you be more detailed in what OS's are on the toshiba, and if any are linux do they see the external in gparted or in a partitioner, is the usb drive seen in the home of a linux install on the toshiba.

Is it that you see no usb drive in the toshiba bios, could itbe  being read as another read and listed differently.

Do you know the per-session boot menu key prompt on my toshiba it is f12 at powering on at the bios flash not the actual bios.

So we can assume the external boots on the AMD.

I have used F12 to boot from my external hard drive, but my hard drive didn't even show up on boot drive list.  
 
Toshiba laptop OS is windows 7 premium and also installer OS is windows 7 also.

I originally installed my Ubuntu on my external hard drive so I will be able to boot from my business trip, but is this not a possible option?

---

### Post by wilee-nilee on 2012-05-21
Was this a install from a windows environment, a wubi install?

---

### Post by feature pro on 2012-05-21
> **wilee-nilee said:**
> Was this a install from a windows environment, a wubi install?

I used live ubuntu from usb to install into external drive.  
I did create live ubuntu on windows.  
thanks for help.

---

### Post by wilee-nilee on 2012-05-21
> **feature pro said:**
> I used live ubuntu from usb to install into external drive.  
I did create live ubuntu on windows.  
thanks for help.

Take a lok in the bios to see if there are any locks on a usb or anything really, and look to see if the usb shows there as well.

You could boot a live cd on the toshiba and see if it will see the usb drive.

So can this usb hd boot from the amd?

---

### Post by feature pro on 2012-05-21
> **wilee-nilee said:**
> Take a lok in the bios to see if there are any locks on a usb or anything really, and look to see if the usb shows there as well.

You could boot a live cd on the toshiba and see if it will see the usb drive.

So can this usb hd boot from the amd?

live USB boots fine on my toshiba and I have looked over on BIOS and there are no locks on it.  
This External Hard Drive works like its new on AMD laptop.  
What else can be wrong on it?  

I checked grub etc I still am not able to come up with an answer for it.

I have faith on wilee help me!

---

### Post by wilee-nilee on 2012-05-21
> **feature pro said:**
> live USB boots fine on my toshiba and I have looked over on BIOS and there are no locks on it.  
This External Hard Drive works like its new on AMD laptop.  
What else can be wrong on it?  

I checked grub etc I still am not able to come up with an answer for it.

Wish I new probably something fairly simple. You could try a reinstall booting the live cd/thumb from the Toshiba and re-installing.

A amd has a special install disc, I would use a regular one if that is what you used before.

Just guessing here though really.

---

### Post by feature pro on 2012-05-21
> **wilee-nilee said:**
> Wish I new probably something fairly simple. You could try a reinstall booting the live cd/thumb from the Toshiba and re-installing.

A amd has a special install disc, I would use a regular one if that is what you used before.

Just guessing here though really.

So let me get this straight.
I should reinstall on Toshiba onto external hard drive right?
Would I be able to use that hard drive on AMD laptop?
I really thought Ubuntu is able to boot from anywhere, but I guess I was wrong. 
I really would hate to use Windows 8 again if I can help it.  I just hate them blue screen error.

---

### Post by wilee-nilee on 2012-05-21
> **feature pro said:**
> So let me get this straight.
I should reinstall on Toshiba onto external hard drive right?
Would I be able to use that hard drive on AMD laptop?
I really thought Ubuntu is able to boot from anywhere, but I guess I was wrong. 
I really would hate to use Windows 8 again if I can help it.  I just hate them blue screen error.

I'm not sure to be honest I would see if others chime in. If it was me I would use a large enough usb flash drive with a full install. I have assumed this is a actual HD.

The not being seen is the strange part, the install is loaded with the drivers needed to run on the amd I would think you at worse would just be getting a black screen if you actual were able to boot it from the grub at worst.

---

### Post by feature pro on 2012-05-21
I have installed Ubuntu into external hard drive using my AMD A8 laptop.

I am trying to boot my external hard drive from Toshiba Satellite(Intel i5) laptop, but in Toshiba BIOS external hard drive is not recognized as a hard drive. 

I tested back on my AMD laptop and it works fine. 

what can be a problem here?  
I have updated my grub already.

---

### Post by darkod on 2012-05-21
That depends on the computer whether it can boot from usb or not. But most newer computers can do that.

Also, some of them are not detecting usb disks fast enough to boot from them. That could be an issue on some computers.

---

### Post by feature pro on 2012-05-21
> **darkod said:**
> That depends on the computer whether it can boot from usb or not. But most newer computers can do that.

Also, some of them are not detecting usb disks fast enough to boot from them. That could be an issue on some computers.

I was able to boot live Ubuntu on Toshiba, but external hard drive was not recognized as a hard drive in BIOS.

Is there way to fix this?

---

### Post by darkod on 2012-05-21
Not sure. You need to google around for that toshiba model and whether it can see ext hdds. Maybe you need to update the BIOS or something.

---

### Post by overdrank on 2012-05-21
Hi and welcome, please do not create multiple threads on the same issue. Threads merged.

---

### Post by black veils on 2012-05-21
this may be useless, but what Ubuntu image did you download?   is one laptop 64-bit and the other 32-bit?  in terms of installing onto an *internal*  hard drive, you would use an amd image for 64-bit, and an i386 image for 32-bit. you can use i386 for both types of computers, but you cant use amd for both types, only 64-bit.

this may be irrelevant, i dont know.

---

### Post by feature pro on 2012-05-21
> **black veils said:**
> this may be useless, but what Ubuntu image did you download?   is one laptop 64-bit and the other 32-bit?  in terms of installing onto an *internal*  hard drive, you would use an amd image for 64-bit, and an i386 image for 32-bit. you can use i386 for both types of computers, but you cant use amd for both types, only 64-bit.

this may be irrelevant, i dont know.

I did install 64 bit version and I have installed 64 bit version on my Toshiba laptop before and it booted just fine before.  

Any other possible solutions?

---

### Post by GreatDanton on 2012-05-21
I tried something like you years ago with Windows. I wanted to install Win xp on hard disk on 1 computer and then use the same hard disk on the other computer. However this wasn't possible. Even if I installed operating system on the second computer and then switch disk to the first computer I wasn't able to boot from hard disk.  I think you have the same issue with Ubuntu, and I am not sure if your problem can be solved (in Windows it's not possible to do that).

Good luck with solving your problem!

---

### Post by feature pro on 2012-05-21
> **GreatDanton said:**
> I tried something like you years ago with Windows. I wanted to install Win xp on hard disk on 1 computer and then use the same hard disk on the other computer. However this wasn't possible. Even if I installed operating system on the second computer and then switch disk to the first computer I wasn't able to boot from hard disk.  I think you have the same issue with Ubuntu, and I am not sure if your problem can be solved (in Windows it's not possible to do that).

Good luck with solving your problem!

I bet there is a way to do it with Ubuntu, but I can't find right information for it online it. 

Windows are just harsh license OS and closed source with lots bug so I fully expect that out come from Windows tho. 

I hope Ubuntu is as flexible as Chrome OS

---

### Post by black veils on 2012-05-21
perhaps you would be best with a *persistent*  live usb, allowing you to save settings and things on the usb flash drive. but you should keep a back-up for important data, in the cloud (somewhere like *dropbox *), just in case.

---

### Post by feature pro on 2012-05-21
> **black veils said:**
> perhaps you would be best with a *persistent*  live usb, allowing you to save settings and things on the usb flash drive. but you should keep a back-up for important data, in the cloud (somewhere like *dropbox *), just in case.

If there are no other solution to this I guess I will have to do your live USB and cloud option.  thanks for suggestion.

please keep me informed if you come cross some other possible way
thanks

---

### Post by oldfred on 2012-05-21
Did you install to a large / (root) partition (over 137GB)?. Some older computers cannot boot from partitions beyond 137GB.

There are some BIOS settings that can make a difference on booting. Not sure if any change USB boot or not.

BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size

---

### Post by black veils on 2012-05-22
if you are really desperate, try this:

[www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/]("www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/")


obviously it refers to allowing to boot from usb flash drive, but it can allow booting from other devices too, you could try it!  but it would mean always using a usb flash drive or cd first to boot you into the hard drive, though i have used the method myself and it is very fast.

---

### Post by feature pro on 2012-05-22
> **oldfred said:**
> Did you install to a large / (root) partition (over 137GB)?. Some older computers cannot boot from partitions beyond 137GB.

There are some BIOS settings that can make a difference on booting. Not sure if any change USB boot or not.

BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size

What you said make sense so I will try to install to smaller drive and see if this will work and I will keep you updated when I get a time to do so. thanks for very nice info.

---

### Post by feature pro on 2012-05-22
> **black veils said:**
> if you are really desperate, try this:

[www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/]("www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/")


obviously it refers to allowing to boot from usb flash drive, but it can allow booting from other devices too, you could try it!  but it would mean always using a usb flash drive or cd first to boot you into the hard drive, though i have used the method myself and it is very fast.

I will also try this too thanks for a tip.

---

### Post by roelforg on 2012-05-22
> **feature pro said:**
> I will also try this too thanks for a tip.
 
Plop boot manager is always useful for stuff like this.

---

