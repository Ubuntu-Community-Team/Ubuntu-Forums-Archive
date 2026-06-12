---
title: "MAJOR PROBLEM!! complete HD corruption!! take a look..."
date: 2006-04-10
forum: General Help
---

### Post by MrMojoRising on 2006-04-10
WOW!! Am i in a bind.

Here's how it happened....

I just purchased a *brand new* Acer Laptop (TravelMate 4404). I had Breezy and winXP pro setup to dual boot via GRUB. I've been using the laptop for 1 week now with no serious problems. Recently i've been trying to get my wireless card to work with my WPA protected AP. So i was messing with Ndiswrapper, Acer_acpi, and wpa_supplicant....

I had one terminal open running a wpa_supplicant command (it was activeley looking for an access point) then in a nother terminal i was issuing a iwconfig command when BAM!!!! my laptop instantly restarts. I had it plugged into power from my wall so i know the battery didn't die, and i know there wasn't a power surge as it was protected. 

The best part is when GRUB loaded up and tried to boot Ubuntu i got this B(black)SOD...
[IMG]http://www.subversivemediagroup.org/images/linux.PNG[/IMG]

There is no response from any buttons on the laptop except for the power button.....so i power it down.
Just in case i try booting into the WindowsXP partition through GRUB....and i get this B(black)SOD....
[IMG]http://www.subversivemediagroup.org/images/windows.PNG[/IMG]

crap!!! (i say to myself)

some other things to note:
1. GRUB does load fine
2. BIOS does not detect anything wrong
3. Any liveCD or MemTest attempts just result in a black screen with no prompts or anything
4. This is a brand new comp.....no changes make except for a fresh WinXP install and a fresh Breezy install with above mentioned tools put in. 

UPDATE #1 : Certain liveCDs (BackTrack, Auditor, Trinity Rescue, and others...) will load up untill the screens to enter boot parameters, but once i hit enter and get to the " Loading Vmlinuz......" part the computer just hangs and nothing happens....CD drive stops spinning....nothing happens at all.      could this be a memory issue, certain things make me think it might be :(

You can check [this post]("http://ubuntuforums.org/showthread.php?t=156516") out that i did a couple days ago asking for help with wireless to....other than the stuff mentioned in that post, nothing else has been done to system.

---

### Post by MrMojoRising on 2006-04-10
Right, 
So i'm fairly sure this is a memory issue and not a corrput HD (wish i could change the title). But seeing as MemTest86 won't run, i can't figure out any details.....and i surely don't want to buy new memory only to figure out it wasn't the memory. 
So if anyone has any ideas i'd love to know.

---

### Post by Stormbringer on 2006-04-10
[QUOTE=MrMojoRising]Right, 
So i'm fairly sure this is a memory issue and not a corrput HD[/QUOTE]

I'm no expert with notebooks, but if you are sure that the problem is related to faulty memory try downloading the latest version of [memtest86]("http://www.memtest86.com/") or [memtest86+]("http://www.memtest.org/") and run it off a floppy disk or USB stick (to avoid hdd boot).

Another option would be to borrow a memory module from another laptop (i.e. friend of yours) and see if things work out as they should.

Storm.

---

### Post by MrMojoRising on 2006-04-10
[QUOTE=Stormbringer]I'm no expert with notebooks, but if you are sure that the problem is related to faulty memory try downloading the latest version of [memtest86]("http://www.memtest86.com/") or [memtest86+]("http://www.memtest.org/") and run it off a floppy disk or USB stick (to avoid hdd boot).

Another option would be to borrow a memory module from another laptop (i.e. friend of yours) and see if things work out as they should.

Storm.[/QUOTE]


Okay, 
    Went on over to [www.memtest86.com](www.memtest86.com), burnt a boot up CD (as my laptop has no Floppy drive), stuck it in using a paper clip to open the CD drive.....Boot up...

BIOS check is fine, then the CD starts spinning and all i have is a blank screen with a flashing cursor about 5 lines down from the top. CD drive stops spinning and the cursor blinks indefinatley. Not responding to any input.

I know the CD burnt fine because i checked it on 2 others computers and it worked flawlessly.


As for checking other memory Dimms.......The screws on the back of the Acer are convienently extremley tight, , extremeley small, and made of soft metal. Trust me i am no idiot when it comes to handling hardware. I've built many systems from scratch. And i couldn't continue to losen these screws without fear of stripping the heads:(

---

### Post by Jonzo on 2006-04-10
I think it's a memory issue because everytime your computer tries to write to RAM, it freezes.  Surely the memory tester writes some data to RAM (in order to function), then it halts.  Same with when your kernel is trying to load.  It tries to throw it in RAM and instantly crashes.

I would try memory before anything else.

---

### Post by MrMojoRising on 2006-04-10
Yeah, that seems to be the general consensus. Even among the Acer Techs. I would just swap out the RAM but i'm to afraid to void the warranty by breaking those little screws :) So i'm just getting it serviced at their shops.

I would like to know though, if any one knows how messing with wireless tools and drivers could have cottupted my memory. Or could it just be that the memory was bad to begin with?

---

### Post by txgunslinger on 2006-04-10
More than likely it was just bad memory to begin with.  I sincerely doubt that wireless tools would corrupt RAM.

---

### Post by MrMojoRising on 2006-04-10
Bummer.....

Okay, for anyone wanting to get an Acer laptop to use with linux. Don't!
Their integrated Broadcom chips are a pain to setup.
And you could possibly be sending it in for bad memory and who knows what else.

---

### Post by sarhento_lobo on 2006-04-10
I would agree that it's bad memory, but I don't think it was the tinkering with the wireless that did it in -- it just so happened that you were doing stuff with it when the RAM got busted. Take advantage of the warranty ;)

---

### Post by MrMojoRising on 2006-04-10
Packaging it up for FedEx to pick it up as i type this.

me's loves the warranties.


(Let's just hope they don't care that i had linux installed and say something like..."we're sorry, seing as you weren't using Windows when the error happened we won't help you!)

---

