---
title: "&quot;boot error&quot; message on boot from usb created with &quot;USB startup disk Creator &quot;"
date: 2012-03-30
forum: General Help
---

### Post by boyofford on 2012-03-30
Hi all,

I have tried creating a bootable usb with ubuntu on using the defualt usb creator software included and when I attempt to boot off the usb I get a "boot error" message.

I get the same problem when using [unetbootin]("http://unetbootin.sourceforge.net/") and  [Live USB Creator]("http://www.pendrivelinux.com/liveusb-install-live-usb-creator/").

I also get the same problem using some other computers, I've tried the usb on a dell inspiron 530s, vostro 410 and a vostro 210 with same result!

However it/they work on a dell dimension 4700!!
[B]
Is this a common problem? [/B]

I've read about some computers not bening able to boot usb hard drives and only zip format usbs or something( sorry for vagueness!:confused:)and the bios on all the computers that it does not work on say something like zip-usb as the boot option where as the old dell dimension 4700 just says usb!

[B]Is their a way i can make a usb that will just work on any computer that has the option to boot from usb?

I have tried [plop boot manager]("http://www.plop.at/en/bootmanager/index.html") which does enable booting of the usb, but needs me to take a CD with me! so not ideal[/B]

---

### Post by Bill Z on 2012-03-30
Hay!! I have an Acer Aspire One NetBook that I have loaded both Ubuntu 11.10 and 11.4 using USB. 

I had seen on the forums that there are times when using USB drives (like SanDisk and Kingston) there are problems. The problems seem to be around any logic in the USB drive that never gets overwritten by the USB Creator.  Some programs in the drive to help speed up transfers.

I used a micro SD by Kingston in as USB adapter. Seems these don't have the logic in them. Worked just fine. Maybe was just a little slow but it did work.

Find a cheap USB drive. One without any special speed packages in it and I bet it will work.

---

### Post by boyofford on 2012-03-30
Thanks mate, but don't think thats the problem.
Have just tried to boot from a acer aspire one funnily enough and boots fine, but still not on the above computers.
I have had the problem with three different usbs now.
will post when get chance to check but think the problem may be with these dells, they all have identical looking bios.

---

### Post by boyofford on 2012-03-30
Think may have found a post over at pendrive linux that explains the problem[(link)]("http://www.pendrivelinux.com/usb-bios-boot-options/")

Basically the boot option on the machines that do not work is **USB-ZIP** which it says may or may not work!

Should be **USB-HDD** on newer machines, but not on the dell inspiron 530s, vostro 410 and vostro 210 aparently!!!

Still curious how widespread this problem is on newer machines?
Might have to get a mini cd for carrying plop with me!

---

### Post by AgentZ86 on 2012-06-26
Dell Vostro same problem where

Created a ubuntu live flash drive works on everything I have except these Dell Vostro's I just got in

I can hit F12 and get the boot option screen, select the removable USB drive and even change the bios to first drive = removable

But same problem tries to boot and gets Boot Error

Hit enter and:
Boot Error
Boot Error
Boot Error

evertime I hit enter

So there would seem to be some problem with Vostro booting to usb driver perhaps some security issue, but anyhow it's not my drive I've tried with several different USB drives including my phone Nokia S60 and they all boot to anything I have except the Dell Vostros I have here

I have no idea why ???:confused:

---

### Post by AgentZ86 on 2012-06-26
> **boyofford said:**
> Think may have found a post over at pendrive linux that explains the problem[(link)]("http://www.pendrivelinux.com/usb-bios-boot-options/")

Basically the boot option on the machines that do not work is **USB-ZIP** which it says may or may not work!

Should be **USB-HDD** on newer machines, but not on the dell inspiron 530s, vostro 410 and vostro 210 aparently!!!

Still curious how widespread this problem is on newer machines?
Might have to get a mini cd for carrying plop with me!


Basically the boot option on the machines that do not work is USB-ZIP which it says may or may not work!

This seems to be the case for me too it calls it USB-Zip so I guess I could try to figure out how to format the usb as some sort of zip drive if possible ????

---

### Post by efflandt on 2012-06-26
Check CMOS (BIOS) settings for USB.  I think you may need Auto or Legacy for USB.  Anyway try a different setting and see if that works.  Some will say in BIOS help that you need a specific USB setting to boot from USB.

I have generally found that on Dell computers you still have to press F12 during BIOS splash to select USB even if you earlier set USB before hard drive in boot order.  On those computers the only time it "might" work without pressing F12 is if that USB device has always been connected and booted from since you set BIOS boot order.

---

### Post by GreatDanton on 2012-06-26
Did you guys tried to format usb drives with Gparted?
OR just right click on unity launcher and click format. 
Also you can click format in startup disk creator-maybe will this solve your problem

---

### Post by sembagdod on 2012-08-09
I have the same error, however i notice that the issue is not related to the USB type, because i tried on many of them and still the same, it is booting with some computers and getting "boot error" for others.

then i tried to change some options on the BIOS and issue was solved ! 

The option was "USB Mass Storage Emulation Type" was set to "All Removable" I change it to "Auto" 

And now it's working fine.. 

Enjoy

---

### Post by krackersk on 2012-09-02
This thread my help put, they had the same problem and fixed it by changing some usb settings in the BIOS:

[http://ubuntuforums.org/showthread.php?t=1042487](http://ubuntuforums.org/showthread.php?t=1042487)

See below for the fix that worked for them:

Prob: When I created Live Usb and restart my pc with all bios settings  done right I get a "Boot Error" ...thats it...No number...

Solution: The problem is not in Ubuntu or Live USB creator softwares...the problem is in ur bios settings...

go to Bios Boot Menu...
Search for ' USB Mass Storage Emulation type'
Default:<Auto>
Change it to:<All Fixed Disc>
or something similar

---

### Post by dpepe on 2012-12-31
+1 for pendrive type problem.

I have tried to boot up an Acer Aspire One Happy from USB. Boot disk was created with both of the built-in usb-creator and Unetbootin. I got "Boot error...load error" with them.
Type of the pendrive was "General USB Flash Disk" - I got it as a promotion...

When I repeated the process with Kingston Data Traveller (1GB) it worked well. 

Otherwise, I had no options in the BIOS were mentioned before.

Regards,
Peter

---

### Post by ElBjorno on 2013-01-16
I had the same problem. Most solutions I found on the internet tended to blame the BIOS, but in my case it seemed to have been the filesystem on the USB drive. Most sources suggest to format the partition to fat32, but that didn't work for me, so I changed it to ext4 and now it works perfectly!
Part of the problem may still lie in the BIOS. Make sure you try all of the different USB boot options, even illogical seeming ones like USB-ZIP.

---

