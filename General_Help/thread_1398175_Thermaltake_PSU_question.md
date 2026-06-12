---
title: "Thermaltake PSU question"
date: 2010-02-04
forum: General Help
---

### Post by Rayve on 2010-02-04
Folks,

Sorry for the post here, not sure where else to ask right now... I just put together my new computer - which will be Ubuntu 9.10 as soon as I get it working, and either I did something wrong or I've got a bad PSU.  Everything is plugged in (power to the PSU and all other connectors connected) and I see the red light turn on on the PSU power switch, but I've got nothing.  I can't even hear any fan from the PSU kick in, and no other case fans or anything else turns on.

Any thoughts?

PSU is a Thermaltake 1200W, I can give details of the rest if needed.

Thanks!

---

### Post by Ordes on 2010-02-04
with the red light u mean the mobo power control light? or a light on your psu?

When the mobo has power there should be a control led turned on.

I dont think its the psu. Check if the Power on/ off; Reset switches from your case are connected in the right way to your mobo. Otherwise the mobo wont receive a power on statement.

---

### Post by 3rdalbum on 2010-02-04
More probably, the switch on your case is either not plugged in correctly or it's broken. You see the two little pins where the case's power switch connects to the motherboard? Try shorting those out with a ballpoint pen and see if the computer turns on. Don't worry, it's not dangerous - there's almost no power running through there, and all you're doing is replicating what the switch does.

If shorting out those pins doesn't work, then you know that the case isn't necessarily at fault. If shorting out the pins works, then the case needs to be taken back to the shop.

---

### Post by Rayve on 2010-02-04
You guys are awesome. I put the three tiny little plugs for the Power LED, Power switch, and reset switch into the small converter-type-pin that came with the motherboard (which I didn't think I needed) which put them all into a big single plug I could put right into the JFP1 slot and it started right up!  I may have had +/- reversed on one or something...

Next question though: I booted and saw the POST, but it said CMOS Checksum Bad.  Should I be worried?  Also, I downloaded a few BIOS updates for my mobo, should I upgrade the BIOS, or only if I run into trouble?  

Thanks so much!

EDIT: Okay, I only actually saw the POST once... now it won't come up anymore, and neither my front USB port nor my mobo back USB port are registering my keyboard, I don't think.  :(

EDIT2: I plugged in my old PS/2 keyboard and the caps/num lock lights come on and work as they're supposed to, so at least the back ports on my mobo are working somewhat.  Still just a blank screen with a blinking underscore about two lines down the screen, though.  /sigh

---

### Post by Ordes on 2010-02-04
CMOS is a type of memory; on the mobo to save your time settings, etc; which will be stored during power off by the battery...

As it was the first time to boot your mobo it couldnt find any data and therefore probably resulted in the error. Specially with now the error not showing anymore. 

About the usb, check if they are connected properly. Sometimes you put a usb in the wrong place and the whole mobo goes nuts. Check that you didnt put it in the IEEEE 1394 port, which has the same connectors as USB, but is a firewire.

Flashing a mobo. You can. But i have had more bad experiences than good ones. There is nothing you can do wrong. Put the file on a usb, select and flash. But it still happens that your mobo get fried....So i dont really trust in it anymore...

Edit:
after reading edit2:
check your USBs. sometimes a broken usb can halt the whole mobo.One of my older cases had a broken front usb, which was still connected to the mobo. The pc would just show me a blank screen until i disconnected the broken usb. Same can happen if USBs are connected wrong.

---

### Post by Rayve on 2010-02-04
Ordes,

Thanks for the heads-up... but I can't even get to the "CMOS Checksum Bad" text anymore.  It starts up, splash screen for MSI comes up, but then I get a black screen.  No POST, no beeps, nothing.  

The things I'm seeing while Googling make me sad.  Any clues?

---

### Post by Ordes on 2010-02-04
disconnect everything, take out the ram etc. Just keep the monitor, and your cpu if u want to, plugged in. And check if u can load up the mobo. If u can get into the bios, than your wiring is wrong.

If the bios wont load try without the cpu, if you still cannot load up the BIOS, than its probably time to send in the mobo... :(

edit:
of course you have to keep the psu connected...

>> u can still try hard reseting the mobo with jumpers and cleaning out the mobo memory. Did u already flash it? I would first wait with it

---

### Post by Rayve on 2010-02-04
Brand new mobo, just put this comp together a few hours ago, hoping it's not bad...

Do I even unplug the power/reset switch little plugs?

How do I hard reset?  Is that the "JBAT" thing I read?  It has 1/2 on now, and it said to put 2/3 to reset, while comp is off, and then back to 1/2.  So I don't turn it on when 2/3 is chosen, it will still clear it even if it's off when I do that?
EDIT: In case it helps, I have the MSI NF980-G65 mobo.

EDIT2: I haven't "flashed" the mobo or anything, at least I don't think... the only thing I did was boot up once, see the POST, then have to reset it because it didn't register my keystrokes.  When I reset it, I tried to put the MSI Driver disk in but nothing happened, and I've gotten nothing since.

---

### Post by Ordes on 2010-02-04
Ah ok..

1) You mean the driver disk that came with your mobo? You dont need to put that in. It wont boot. You normally install these drivers inside the OS (> Windows). 

2) For the hard reset you have to check your manual. Its normally a jumper.

3) You can keep the power plugs. If you unplug those too, you need to do what 3rdalbum said. Using a ballpoint, or key, to circuit the power. Just try it with the power plugs first, and check if you can get into the bios. Dont put any CDs Boot disc etc in it.

>> u know u have to hit del, or f2, or sth similar to get into your bios.. normally when the mobo splash screen shows up

---

### Post by Rayve on 2010-02-04
Okay, when I did the hard reset on the JBAT on the mobo, and then moved it back, I was able to boot up and see the "Press F2 to enter setup" screen... except pressing F2 doesn't do anything, I go to the black screen I had earlier.

Also, I don't have any OS on here yet - new HDD, was going to use GParted and then put Ubuntu 9.10 on it, but not sure how to get that working at this point...

Thanks again.

---

### Post by Ordes on 2010-02-04
which keyboard did u use? perhaps try the PS/2 first. It might not be the mobo but the usb keyboard. 

That the screen is blank after the mobo splash screen passed by is normal. As there is nothing for the mobo to boot from.

---

### Post by Rayve on 2010-02-04
So... I can't read, heh.  The PS/2 keyboard works, that's what I've been using, but I was hitting F2 for "load defaults and run" instead of F1 for "enter setup"... oops.

I entered the setup and adjusted the time on the clock, everything else looks good, it's reading all my RAM, etc.

Only thing right now is, I have to hard reset with the little JBAT every time.  Whenever I reset or power off and back on, I get the splash screen and then the black screen, no POST unless I just did a hard reset.

This can't be normal... what am I missing?

Thank you so much.

---

### Post by Ordes on 2010-02-04
What u mean with splash screen? The mobo splash screen? What u mean with POST?

When i hear splash, i think of the mobo splash from which you can choose to load BIOS or boot system. As there is no system to boot your screen is blank. 
Or do u mean that you cannot even enter BIOS after a normal reset?

----

Did u try to disconnect everything? Its easier to find it that way if something is connected in the wrong way. Also check your jumper settings.

---

### Post by Rayve on 2010-02-04
I meant the mobo splash screen that says "MSI" and everything... but I got the main issue fixed, I was able to power on, go to BIOS setup and change the boot order and then have it load GParted from CD, but without a functioning USB I can't use my mouse, so I may just read up on GParted command-line and go from there.

Out to breakfast for a bit now since I at least know my computer is functioning!  It's my fiancee's birthday, and she must love me since she's letting me build and work on my computer today and use her Mac to post on the forums.  :P  Will check back in a few hours and update, see if I can't get things working.

---

### Post by Ordes on 2010-02-04
;) 

check if USB is enabled..
load up a ubuntu Live and check if usb is working..

---

### Post by realzippy on 2010-02-04
...can you replace the CMOS battery by a new one?

---

### Post by Rayve on 2010-02-05
Actually, everything is up and running now. :)  I'm writing this post on my new now-functioning computer.  I unconnected and reconnected the USB Front port connections and they ran just fine.  My IDE DVD-ROM drive didn't like the Ubuntu LiveCD and would fail at 53% through the install, but I put it into my SATA DVD-RW drive and it installed perfectly.  Not sure if it was an IDE/SATA thing or what.  Thanks for your help, everyone!  :)

---

### Post by Ordes on 2010-02-05
:popcorn:

---

