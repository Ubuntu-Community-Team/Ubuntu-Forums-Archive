---
title: "Getting frustrated here"
date: 2012-08-14
forum: General Help
---

### Post by bstrawt90 on 2012-08-14
I have been trying to figure this out for the past 5 hours straight and trying different things from the research I have been doing on google.

what im trying to do: is turn my old desktop into a ubuntu home server

when I plug in the thumb drive with the imagefile on it, i get "There is no bootload partition table." The desktop that I have is a compaq and it has ubuntu 11.04 on it. I have been getting to log in screen and pressing the ctrl+alt +f1+f6 to use command line because when i log in normally i just get a blank screen. spent about couple of hours on that, changing my settings to "nosetmode" actually makes it worst. I tried downloading a couple of other more ubuntu desktops to just overwrite the one i have on now. I tried 11.04 again and it says no boot partition table. I tried 12.04 and just got some nonsense.

I finally broke down and will just ask for some ones help. 
How do I create a boot partition via Terminal window?, because i can not use gpart since Im only in terminal window. and also is there anything else i need to do?
PLEASE HELP!:confused:

---

### Post by rccubed on 2012-08-14
bstrawt90,
When you say "Old Desktop" how Old are we talking about?
Is the hardware able to boot from a usb port?
I have several that can't.
rccubed

---

### Post by oscarivera9 on 2012-08-14
If it's an "old desktop", like rccubed said, the problem may be that the PC might not be able to boot from your thumb drive.  Have you tried using a Live CD instead?

Also, depending on how old the desktop is, you may encounter many, many more problems down the road if you somehow manage to install Ubuntu Server 11.04.  
It would help us much more if you were to tell us more about the hardware you're using.  Give us more than just Compaq so that we know what we're dealing with here.

So, not knowing how old your PC is, what I would recommend instead is that you use Ubuntu Server 10.04 instead.  It is older but still supported.

If you'd rather go with something new, Xubuntu 12.04 may be a good alternative.  Even though Xubuntu doesn't have a server edition, it may suit your needs with a little tweaking.

---

### Post by bstrawt90 on 2012-08-14
> **rccubed said:**
> bstrawt90,
When you say "Old Desktop" how Old are we talking about?
Is the hardware able to boot from a usb port?
I have several that can't.
rccubed

Its not as old as ya think, I would say 2005/6.  And yeahit can boot from usb, thats how I got 11.04on it. When I installes it I think I put use entire disk and did not do anything w partitioning hard drive. So I prolly deleted the boot partition

---

### Post by bstrawt90 on 2012-08-14
> **oscarivera9 said:**
> If it's an "old desktop", like rccubed said, the problem may be that the PC might not be able to boot from your thumb drive.  Have you tried using a Live CD instead?

Also, depending on how old the desktop is, you may encounter many, many more problems down the road if you somehow manage to install Ubuntu Server 11.04.  
It would help us much more if you were to tell us more about the hardware you're using.  Give us more than just Compaq so that we know what we're dealing with here.

So, not knowing how old your PC is, what I would recommend instead is that you use Ubuntu Server 10.04 instead.  It is older but still supported.

If you'd rather go with something new, Xubuntu 12.04 may be a good alternative.  Even though Xubuntu doesn't have a server edition, it may suit your needs with a little tweaking.

Ok yeah I may go with 10.04 server, and probably check out xbuntu on laptop. But the problem is getting a boot partition. I think I put on desktop, which is like 05/06, use entire disk and did not do any partitioning what so ever so I think I deleted the boot partition to allow other boot methods for. Is there any code people can walk me through that I can plug into terminal?

---

### Post by Wim Sturkenboom on 2012-08-14
> 
when I plug in the thumb drive with the imagefile on it, i get "There is no bootload partition table."

That would point to the thumb drive having a problem.

> 
The desktop that I have is a compaq and it has ubuntu 11.04 on it. I have been getting to log in screen and pressing the ctrl+alt +f1+f6 to use command line because when i log in normally i just get a blank screen. spent about couple of hours on that, changing my settings to "nosetmode" actually makes it worst.

Is that with the version that is currently installed on the HD? Or with the thumb drive (which contradicts above).

> 
I tried downloading a couple of other more ubuntu desktops to just overwrite the one i have on now. I tried 11.04 again and it says no boot partition table. I tried 12.04 and just got some nonsense.
Did you check the md5sum after download? Did you use the same thumb drive? Or another one? Or did you burn CDs? There is no such thing as 'some nonsense'; try to give the error messages that it throws at you.

I basically would think that your thumb drive is broken and hence does not have a proper image on it.

---

### Post by lisati on 2012-08-14
> **bstrawt90 said:**
> I have been trying to figure this out for the past 5 hours straight and trying different things from the research I have been doing on google.

what im trying to do: is turn my old desktop into a ubuntu home server

when I plug in the [COLOR="Red"]thumb drive with the imagefile[/COLOR] on it, i get "There is no bootload partition table." The desktop that I have is a compaq and it has ubuntu 11.04 on it. I have been getting to log in screen and pressing the ctrl+alt +f1+f6 to use command line because when i log in normally i just get a blank screen. spent about couple of hours on that, changing my settings to "nosetmode" actually makes it worst. I tried downloading a couple of other more ubuntu desktops to just overwrite the one i have on now. I tried 11.04 again and it says no boot partition table. I tried 12.04 and just got some nonsense.

I finally broke down and will just ask for some ones help. 
How do I create a boot partition via Terminal window?, because i can not use gpart since Im only in terminal window. and also is there anything else i need to do?
PLEASE HELP!:confused:

How did you copy the image file to the thumbdrive? Just copying the ISO file to the thumbdrive as if it were a regular file doesn't necessarily work too well.

---

### Post by bstrawt90 on 2012-08-14
> **lisati said:**
> How did you copy the image file to the thumbdrive? Just copying the ISO file to the thumbdrive as if it were a regular file doesn't necessarily work too well.


Ok it has been a while since I booted something with another OS, so yeah I did just basically copy and drag iso file to thumb drive.

---

### Post by bstrawt90 on 2012-08-14
> **Wim Sturkenboom said:**
> That would point to the thumb drive having a problem.


Is that with the version that is currently installed on the HD? Or with the thumb drive (which contradicts above).

Did you check the md5sum after download? Did you use the same thumb drive? Or another one? Or did you burn CDs? There is no such thing as 'some nonsense'; try to give the error messages that it throws at you.

I basically would think that your thumb drive is broken and hence does not have a proper image on it.

It is same version I had on hard drive, keep in mind that I juss clicked and dragged iso file from downloads to thumb drive. It has been awhile since I booted into new OS so I could have forgot the real way. And no I havent used any blank cds and it has been the same thumb drive most of the time. I had tried another, same way copy n drag iso file but with ubuntu12.04, different than what is installed on hdd. I till hold off on the old thu,b drive because the bottom part of it that holds the data may have gotten dust or somthing, it has been months without proper protection. Does this info help?

---

### Post by bstrawt90 on 2012-08-14
> **Wim Sturkenboom said:**
> That would point to the thumb drive having a problem.


Is that with the version that is currently installed on the HD? Or with the thumb drive (which contradicts above).

Did you check the md5sum after download? Did you use the same thumb drive? Or another one? Or did you burn CDs? There is no such thing as 'some nonsense'; try to give the error messages that it throws at you.

I basically would think that your thumb drive is broken and hence does not have a proper image on it.
I also did not check/do not know what the m5s thing is

---

### Post by drmrgd on 2012-08-14
> **bstrawt90 said:**
> Ok it has been a while since I booted something with another OS, so yeah I did just basically copy and drag iso file to thumb drive.

I've been following this (I was thinking it was an improperly created Live Disc at first and nothing hardware related, but wasn't sure I was totally following you in regard to what you've got set up at the moment).  What I'm not sure about is whether or not you have any bootable system at all.  If you do, then what you need to do is make a bootable USB image from that .iso that you downloaded (your choice which you use, although a lighter weight version may compliment your system a bit more - age is not as much a concern as speed and flexibility of the hardware).  There are a few tools available, and the Ubuntu Community Documentation covers this pretty well:

[https://help.ubuntu.com/community/Installation/FromUSBStick/](https://help.ubuntu.com/community/Installation/FromUSBStick/)

---

### Post by bstrawt90 on 2012-08-14
> **drmrgd said:**
> I've been following this (I was thinking it was an improperly created Live Disc at first and nothing hardware related, but wasn't sure I was totally following you in regard to what you've got set up at the moment).  What I'm not sure about is whether or not you have any bootable system at all.  If you do, then what you need to do is make a bootable USB image from that .iso that you downloaded (your choice which you use, although a lighter weight version may compliment your system a bit more - age is not as much a concern as speed and flexibility of the hardware).  There are a few tools available, and the Ubuntu Community Documentation covers this pretty well:
[https://help.ubuntu.com/community/Installation/FromUSBStick/](https://help.ubuntu.com/community/Installation/FromUSBStick/)

Ya thats what im thinking, I think I deleted the boot partition from my cpu when I was  setting up ubuntu awhile ago. I need to allocate memory for it(boot partition in order to actually b able to boot other OSs) thru terminal since I.cant use gpart and I will go ahead and read into how to create a live disk the right way

---

### Post by drmrgd on 2012-08-14
Unless there's a trick that I'm unaware of, I think without any bootable OS, you're sort of stuck between a rock and a hard place.  It sounds to me like you have broken your Ubuntu bootloader on your HDD by accidentally deleting the partition - is this right?  It also sounds like you didn't make a bootable USB drive and can't boot from that - is that correct?  I didn't read anywhere about Windows, and so I'm assuming this is just a single boot computer with Ubuntu - is that correct?

If all of those are true, you're going to need to find a working computer to make a repair device.  You've got a few choices:

1. You can create a Gparted Live CD that will allow you to re-partition the hard drive and remake the boot partition.  I'm not clear as to whether you deleted the partition and reallocated the space, or if you just relabeled it as something else (in other words, change the flag from /boot to something else).  A little more info might help guide you the right way.

[http://gparted.sourceforge.net/livecd.php/](http://gparted.sourceforge.net/livecd.php/)

2. You can create a Boot Repair live CD (or USB of course) that may be able to help you repair the /boot partition and get the current system booting again.  In that package, there's also Bootinfo Script that will help us determine how your drive(s) are partitioned, and what's going on with the /boot partition.  This actually might be more useful as a first step rather than Gparted, especially if you're unsure how to fix the boot partition on your drive and need guidance.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

3.  If you've got nothing to lose on the current install and just want to scrap everything, you can create a working Ubuntu live disc, which you can use to re-install the OS (which I'm thinking is what you wanted in the first place).  During the re-installation, you'll have the opportunity to repartition the drive if you choose, and certainly remake your boot partition so the system will boot normally again with the new OS.  Depending on what OS you have at your disposal now, you have a couple choices, which are outlined in the last link I sent.

I'm pretty sure that in order to get any further, you'll need a computer that is bootable to be able to create bootable media, and consequently fix your current borked computer.

---

### Post by Moif_Murphy on 2012-08-14
Have you read this guide?
 
[https://help.ubuntu.com/community/Installation/FromUSBStick/](https://help.ubuntu.com/community/Installation/FromUSBStick/)

---

### Post by bstrawt90 on 2012-08-14
> **drmrgd said:**
> Unless there's a trick that I'm unaware of, I think without any bootable OS, you're sort of stuck between a rock and a hard place.  It sounds to me like you have broken your Ubuntu bootloader on your HDD by accidentally deleting the partition - is this right?  It also sounds like you didn't make a bootable USB drive and can't boot from that - is that correct?  I didn't read anywhere about Windows, and so I'm assuming this is just a single boot computer with Ubuntu - is that correct?

If all of those are true, you're going to need to find a working computer to make a repair device.  You've got a few choices:

1. You can create a Gparted Live CD that will allow you to re-partition the hard drive and remake the boot partition.  I'm not clear as to whether you deleted the partition and reallocated the space, or if you just relabeled it as something else (in other words, change the flag from /boot to something else).  A little more info might help guide you the right way.

[http://gparted.sourceforge.net/livecd.php/](http://gparted.sourceforge.net/livecd.php/)

2. You can create a Boot Repair live CD (or USB of course) that may be able to help you repair the /boot partition and get the current system booting again.  In that package, there's also Bootinfo Script that will help us determine how your drive(s) are partitioned, and what's going on with the /boot partition.  This actually might be more useful as a first step rather than Gparted, especially if you're unsure how to fix the boot partition on your drive and need guidance.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

3.  If you've got nothing to lose on the current install and just want to scrap everything, you can create a working Ubuntu live disc, which you can use to re-install the OS (which I'm thinking is what you wanted in the first place).  During the re-installation, you'll have the opportunity to repartition the drive if you choose, and certainly remake your boot partition so the system will boot normally again with the new OS.  Depending on what OS you have at your disposal now, you have a couple choices, which are outlined in the last link I sent.

I'm pretty sure that in order to get any further, you'll need a computer that is bootable to be able to create bootable media, and consequently fix your current borked computer.

Thats exactly right the desktop is solo on ubuntu, and I think I accidently deleted that partition. I have nothing to lose, I just want to turn it into a ubuntu server so I plugged in the thumbdrive when I was done downloading the iso file of ubuntu server to it but maybe I copied file wrong. I literally just clicked n dragged from downloads tothumb drive. And I want to do option three cause I have nothing to lose but no matter what I try its always no boottable in partition. If I do option 1 would I have to download it to thumb drive and startup comp off that instead of going thru ubuntu? Because I have no gui after.i log into ubuntu, just terminal

---

