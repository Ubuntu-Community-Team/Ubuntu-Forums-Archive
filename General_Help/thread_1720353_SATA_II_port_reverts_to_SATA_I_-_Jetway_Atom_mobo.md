---
title: "SATA II port reverts to SATA I - Jetway Atom mobo"
date: 2011-04-03
forum: General Help
---

### Post by kansasnoob on 2011-04-03
As with many hardware problems this was caused by the dufus between the chair and the keyboard - me :(

I agreed to try and rescue the data off of a laptop that was pulled out of a burned motor-home. I even succeeded, yay :D

Only one problem, but it's got me a bit stumped. My motherboard is SATA II and the laptops hard drive was SATA I. I've generally found that SATA I drives are reverse compatible with SATA II mobos, although the opposite requires actual knowledge of the drive (sometimes a specific jumper setting is required on the drive, etc).

Anyway this is the mobo info:

[http://www.jetwaycomputer.com/Atom-GM.html](http://www.jetwaycomputer.com/Atom-GM.html)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153143](http://www.newegg.com/Product/Product.aspx?Item=N82E16813153143)

Normal setup is 500GB SATA II hard drive connected to SATA port #1, SATA CD/DVD multi-drive connected to SATA port #2, and one 80GB IDE drive connected to the IDE header.

What I did was disconnect the CD/DVD optical drive and connected the SATA I laptop drive in it's place. Of course I powered off, followed static safety procedures, etc. And I was able to basically clone that drives data partitions to a USB drive so the data can later be copied to another computer.

The problem appeared after putting my box back in it's normal configuration. The #2 SATA port seems to refuse to return to a SATA II status, and sometimes at reboot the system freezes at BIOS - I can see that it takes a very, very long time to "find" the connected drives - then it just freezes with the last line in BIOS just displaying the BIOS version.

Things I've tried so far:

* Resetting both standard and optimized defaults in BIOS.

* Clearing the CMOS a couple of times. In fact, when I gave up for the night, I disconnected the power cable to the mobo, removed the CMOS battery, moved the CMOS jumper to clear position - and then this AM I put the jumper back on pins 1 & 2, put the battery back in, and reconnected the power cable.

* The "drive detection" options in BIOS include auto, manual, and none. Default is auto. There is also an option to "detect drive" and I've tried that a few times but POST still always shows SATA port #2 reverting to SATA I :(

Any thoughts anyone?

I'm always reluctant to flash a BIOS but that may be my only option. I've also never done so using Ubuntu but I found this guide:

[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

I could connect a floppy drive but I'd prefer using a CD, although I'm quite familiar with grub (both legacy and grub2) and I could easily set my machine up to boot using legacy grub.

Any thoughts before I totally blow things up :P

---

### Post by LowSky on 2011-04-03
You shouldn't need to flash the BIOS. it should clear properly when you remove the CMOS battery.

I'm confused of your problem though. You said the Optical drive was SATA. All DVD drives are SATA, none I have come across are SATA2, there is no need they are not fast enough to require SATA2.

The BIOS freezes can be a number of things. You could have mishandled the cables and it is causing errors at boot. I suggest you look over ever cable and connector to make sure they are seated correctly and not coming off the motherboard.

---

### Post by kansasnoob on 2011-04-03
> **LowSky said:**
> You shouldn't need to flash the BIOS. it should clear properly when you remove the CMOS battery.

I'm confused of your problem though. You said the Optical drive was SATA. All DVD drives are SATA, none I have come across are SATA2, there is no need they are not fast enough to require SATA2.

The BIOS freezes can be a number of things. You could have mishandled the cables and it is causing errors at boot. I suggest you look over ever cable and connector to make sure they are seated correctly and not coming off the motherboard.

I appreciate your response :)

I've had the box running now since about 4AM so that's about 8 hours and I haven't had a problem, then again I haven't rebooted :)

Something I left out, and shouldn't have. I was using Gparted to copy the two partitions that contained user data from the drive out of that torched laptop to a USB drive.

Once the procedure was well under way and everything on my box looked happy I went to bed, this was night before last. When I woke up yesterday morning my puter "woke up" when I moved the mouse and I could see that Gparted was done.

So I closed Gparted, safely removed the USB drive, and then started doing what I normally do every day, responding to stuff in my mail. In this case it was a bug report I'd filed during Natty Beta 1 iso-testing.

After only about 30 seconds of typing things almost totally froze up. I could still move the mouse pointer and even click on apps but nothing would open. I couldn't even access a tty to investigate further, and the typical Alt>SysReq>'whatever' keys wouldn't work so I used the reset button.

Then came the first failed reboot with things stalling at BIOS - very slow detection of drives, and an ultimate failure to boot. Of course I removed that SATA I drive while I was down and plugged the CD/DVD back in.

The rest of the day was very rocky, keyboard freezes and such, but the most troubling thing was the slow loading BIOS - sometimes resulting in a failed boot altogether :(

ATM all seems well. Did leaving it sit with the CMOS jumper on pins 1 & 3 and the CMOS battery removed w/ the mobo power disconnected help?

I think it's too early to say. Regarding the POST showing SATA port #1 as SATA II and SATA port #2 as SATA I maybe that's not a problem with SATA port #2 connected to an optical drive.

To be honest the only things I normally watch closely during POST are fan speeds and temps.

I do know I'm able to read CD's and DVD's although I've not yet tried booting a live disc.

One thing, slightly OT, why would I put my hardware at risk? Well first of all I tried this drive out with a spare power supply to be sure it wouldn't totally fry everything, but the answer is:

The guy I'm doing this for is a really decent guy. Due to the economic downturn he lost his job, then his home, then his wife, and he was living in his uninsured motor home when lightning struck it! 

And his dog was in the motor home! So several of us got together and we're trying to give the guy a reason to wake up every morning :)

---

### Post by kansasnoob on 2011-04-05
@ LowSky,

That was a good call on cables. I was out of new SATA cables so I had to wait until yesterday morning to pick one up at the brick-n-mortar store. About 26 hours later and no problems :)

I could see nothing physically wrong with the old cable but this box gets used for all kinds of testing so cables get disconnected and reconnected frequently. Many thanks.

---

