---
title: "Installing Ubuntu on a Diseased Racked PC."
date: 2009-09-19
forum: General Help
---

### Post by ed5000 on 2009-09-19
I'm trying to install ubuntu on our family desktop computer after a virus that disabled both the cd rom and dvd drives and the usb ports via the bios file.  The bios file says each of these devices are non-existent.  I even tried installing another cd drive I had and the pc can't recognize it either.  

Basically, my teenage son was downloading our store bought dvds to his new iphone when everything quit working (Grrrr the dvd industry!).  The MS restore program didn't help and resetting the bios to it's original default settings didn't work either.  

 I'm trying to find a way to install Ubuntu.  If anyone has any ideas I'd appreciate it.  It's been a good computer and I'm not ready to toss it yet.


Some info:
Dell Dimension 8400 model DHM
Manf. Date 9-13-04
Pentium 4  3.0ghz
Currently windows xp home ed. (original os)

---

### Post by HappyFeet on 2009-09-19
You will have to reflash your bios. Go to the manufacturers website for more info.

---

### Post by ed5000 on 2009-09-20
Thank you happy feet!  I was able to flash the bios with the latest version.  Good learning experience!  However I still have no cd rom drives.  In asking around, I found out that it was more likely that the motherboard went bad.  I tend to agree with this because:

1)  I was able to flash the latest bios file and the version number at startup confirms this (yet still no cd drives).
2)  We used a lot of these Dell 8400 pcs at work and the IT guys had to replace motherboards on a regular basis including my pc at work.  One of the IT guys showed me how the capacitors would actually swell up indicating problems ahead.  This pc has that.

Now, should I replace the motherboard with some quad-core overclocked hotrod board or just get a whole new box?  Hmmmmm.

---

### Post by oldfred on 2009-09-20
If the Dell is 4-5 years old the power supply is probably sized to the minimum required for the system you bought to hold down costs. So you will want a new power supply for your new hot rod MB. Of course your son will want some games so you need a hot rod video card and larger hard drive(s). It sounds like you have talked yourself into to new system.:)

---

### Post by ed5000 on 2009-09-20
This is true.  I would probably suffer some performance loss if I reuse the old parts.

---

### Post by sideaway on 2009-09-20
You probably would. Have a go at putting your own system together? If you haven't done so previously :P And if you have, well then you can decide whats best for you :)

---

### Post by ed5000 on 2009-09-23
I have put one pc together about 7 or 8 years ago.  It was a lot of fun to do.  I was thinking of having my teenager doing it.  I guess one advantage is the savings on the OS.  Thanks!

---

### Post by mentalelf on 2009-09-23
Try the reset CMOS jumper on the motherboard, I've had a couple of PCs where things weren't quite right after a BIOS update until I did that.

Worth a try, can't break anything, if it's a rack PC the hardest bit will be getting into the thing.

---

### Post by ed5000 on 2009-09-23
> **mentalelf said:**
> Try the reset CMOS jumper on the motherboard, I've had a couple of PCs where things weren't quite right after a BIOS update until I did that.

Worth a try, can't break anything, if it's a rack PC the hardest bit will be getting into the thing.



What's the basic procedure for doing this?

btw, the access is easy

---

### Post by mentalelf on 2009-09-24
First of all MAKE SURE THE DAMN THING'S TURNED OFF ('scuse the shouting).  Oh & take anti-static precautions just in case.  If you don't know what I mean by that then Google it, seriously.  All that aside it's dead easy :P

Look on the motherboard, somewhere there'll be a jumper (either a set of two pins which are uncovered, or three pins with 2 of them covered with a small plastic & metal cap) marked CMOS, or clear CMOS, & usually close to it a small flat battery.  

If your motherboard has the 3-pin type (most common), move the cap from (eg) pins 1 & 2 to pins 2 & 3 briefly (ie few seconds is more than enough), if it's the 2-pin type bridge them with a paper clip or something instead. This will clear all the customisable information in the BIOS.  If you can't find the jumper but can see the battery then just take the battery out instead.

After you've done that (& put the cap back to original position if it's the three-pin type).  Boot up, go into the BIOS (hammer the right key as it's starting, usually Delete or F2, may be F10 or whatever they decided to use this week as it's a Dell box) & set the time & boot order.  While you're there see if the optical drives are detected yet.

Now boot from your Ubuntu CD, & bask in the Linuxy goodness.

Please note: if you turn the thing off & earth yourself there's *no* chance at all that you'll break anything at all doing this.

---

### Post by ed5000 on 2009-09-25
Thanks Mentalelf!  It was worth a try.  I found the "CLR CMOS" pins.  It was the 3 pin type like you mentioned.  It definitely reset something as there was a message and I had to reset the date and time, but still no CD rom or USB.  I tried to turn off and on the different drives and rebooted it several times as well.

---

### Post by Radioman991 on 2009-09-25
My 0.02

While you may have other problems, I found in my Dell, the DVD ROM drives they installed 3 or 4 years ago, out of the blue just stopped burning CDs and DVDs.  It was an issue with the cheap drives they installed.  After a while, Windows didn't even think there was a drive installed!  

You might Google the model number of the drive to see if it has some weirdness in other people's systems.

Since that time, I have replaced the drive, and now the OS too!

Good Luck

Radioman991

---

### Post by ed5000 on 2009-09-27
Thanks Radioman.  I had two cd drives in there and they both went at the same time.  I also tried another cd drive I borrowed from another computer but it didn't work either.  Time to get something a little newer.

Do you want to know something funny?  My wife just opened her laptop and found the screen cracked with big spider web cracks.  All the way though too.  Our two year old was spotted carrying it through the house.  Looks like I'll need all the computer repair skills I can get!  :^)

---

### Post by ed5000 on 2009-10-05
Here is an update on the old family Dell computer whose cd, dvd rom drives and USB ports quit working:

  Well after disassembling the Dell I found the 4 pin CPU power plug was kind of melted and burnt up where it connects to the motherboard.  I'm not sure why it took out cd rom drives but, apparently it did.

So what I did do is go out and buy (and assemble) a MSI K9N6PGM2-V2 motherboard with an AMD Athlon X2 250, 3.0 Ghz dual core processor plus 4 gigs of memory and a case and I moved over the two cd drives and the 250 gig sata drive and then installed a fresh copy of Ubuntu 9.04 and Bam!  I have a hotrod computer!  Keep me off the forum now!  

Okay, seriously I know it's not the fastest computer in the world but, after running 5 years on windows xp with clogged up registry files, it's fast!

Thanks to those that helped troubleshoot (and shoot) the old Dell PC and thanks for ideas for this new one.  All of you keep up the good work!

ed5000 :)

---

