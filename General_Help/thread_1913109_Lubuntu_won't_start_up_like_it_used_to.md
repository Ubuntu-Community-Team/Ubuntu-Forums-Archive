---
title: "Lubuntu won't start up like it used to"
date: 2012-01-21
forum: General Help
---

### Post by Micropox on 2012-01-21
Hello everybody!
Well Lubuntu is amazing! Blows windows away.
I really want to never use windows again.
I have  bunch of veriton3900pro's: 
Pentium(r) D CPU 3ghz 2.99ghz
.97gb of ram (i could add more)

I got lubuntu 10.10 working but now it wont boot up all of a sudden.
It does this instead:

[http://oi44.tinypic.com/rh1ibm.jpg]("http://oi44.tinypic.com/rh1ibm.jpg")
Then whatever option i choose i get this:
[http://oi44.tinypic.com/nwbgk7.jpg]("http://oi44.tinypic.com/nwbgk7.jpg")

I did do some things in terminal but can't remember what. Nothing that seemed like it would cause this though, i don't think.

I also don't seem to be able install ANY kind of lubuntu (or ubuntu)on any of my other comps (which are all the same machines)but that's probably a different thread.

---

### Post by memristor on 2012-01-21
I have personally never run into any such problems but i searched for this issue and seems like most people had it when :

1)They installed for the first time and the installation CD was based on corrupted ISO image 
2)There was a problem during upgrade and that messed up their file system
3) Hard disk is on its last few breaths

Can you burn a new live cd and check your file system and disk health for starters?

---

### Post by Micropox on 2012-01-21
i'll give it a go

---

### Post by Micropox on 2012-01-21
did check disc from original live cd:
errors found in 1 files!

Also,  Iv'e been using the !386 isos. should i be using those for these machines?

---

### Post by Micropox on 2012-01-21
Wow what an unfortunate typo

---

### Post by Micropox on 2012-01-21
Tried check disk a second time. this time it dosn't even start the check and says 'error reading boot cd'

---

### Post by marinara on 2012-01-22
did it say that when booting off the cd?  Could it be your cd is dirty?

---

### Post by Micropox on 2012-01-22
i can run off the cd and access my files no problem

---

### Post by Micropox on 2012-01-22
> **marinara said:**
> did it say that when booting off the cd?  Could it be your cd is dirty?
i think it might have had some problems, i'll check again.

---

### Post by Micropox on 2012-01-22
> **marinara said:**
> did it say that when booting off the cd?  Could it be your cd is dirty?

just before it's done i get [http://oi41.tinypic.com/furfbo.jpg]("http://oi41.tinypic.com/furfbo.jpg")
Sorry about the blurry pic

---

### Post by Micropox on 2012-01-22
thanks people.
ok re burnt the iso on sombody elses nice new comp and check found 1 error again.
i guess i need another iso

can anyone think of any reason why 11.10 wouldn't work with these machines?
I think ill keep trying that one until i get one without errors.

---

### Post by marinara on 2012-01-22
the vertirons have a crappy intel chipset.  I have a old pc with a crappy intel chipset.  11.10 doesn't work on it either, but 10.04 does.  Try that.

also keep trying with the cd.  I'm pretty sure it's just a bad cd.

---

### Post by Micropox on 2012-01-22
> **marinara said:**
> the vertirons have a crappy intel chipset.  I have a old pc with a crappy intel chipset.  11.10 doesn't work on it either, but 10.04 does.  Try that.

also keep trying with the cd.  I'm pretty sure it's just a bad cd.

ah, cheers, i think i might have come to the same conclusion a while ago but i never got 10.04 to work either.
odd that i got 10.10 installed once on one machine

---

### Post by MG&amp;TL on 2012-01-22
If you have problems with CD/.iso integrity, you can try the [ubuntu wiki guide to md5summing]("https://help.ubuntu.com/community/HowToMD5SUM") then see is if works.

Other than that, I can't tell you why. As it says on the tin, a file is missing, probably the one reported by your filesystem check. I can't say whether or not the thing will boot without it. My advice would be to backup your files and try reinstalling. 

The i386 isos are fine.

You could also try booting from USB, if you BIOS supports it. USBs don't get scratched or dirty, and I've never yet had a corrupted one.

---

### Post by Micropox on 2012-01-22
> **MG&TL said:**
> If you have problems with CD/.iso integrity, you can try the [ubuntu wiki guide to md5summing]("https://help.ubuntu.com/community/HowToMD5SUM") then see is if works.

Other than that, I can't tell you why. As it says on the tin, a file is missing, probably the one reported by your filesystem check. I can't say whether or not the thing will boot without it. My advice would be to backup your files and try reinstalling. 

The i386 isos are fine.

You could also try booting from USB, if you BIOS supports it. USBs don't get scratched or dirty, and I've never yet had a corrupted one.

ah, good i have the right isos, cheers.
i really should have said iv'e tried usb too and the md5sum checks out.

---

### Post by MG&amp;TL on 2012-01-22
Well, I suggest backing up your home folder by booting the CD, then starting to debug.

---

### Post by Micropox on 2012-01-22
> **MG&TL said:**
> Well, I suggest backing up your home folder by booting the CD, then starting to debug.

Ah.. That sounds complicated..

---

### Post by MG&amp;TL on 2012-01-22
> **Micropox said:**
> Ah.. That sounds complicated..

Well...the backing up isn't. Debugging might be.

Simply boot the CD, then find your home folder, through "XYZ GB filesystem", then /home/micropox/

Then just copy that onto a USB or whatever.

---

### Post by Micropox on 2012-01-22
> **MG&TL said:**
> Well...the backing up isn't. Debugging might be.

Simply boot the CD, then find your home folder, through "XYZ GB filesystem", then /home/micropox/

Then just copy that onto a USB or whatever.

just the debugging. i have no idea where to start with that.

The major problem i have with installing seems to be getting he kernel off the cd or usb
or connecting to the net while running off the device
ubiquity crashes. sometimes other things crash too.

---

### Post by marinara on 2012-01-22
[http://www.linuxtested.com/results/acer_3900pro.html](http://www.linuxtested.com/results/acer_3900pro.html)

supposedly red hat enterprise workstation 4.0 is compatible with your acer

---

### Post by Micropox on 2012-01-22
> **marinara said:**
> the vertirons have a crappy intel chipset.  I have a old pc with a crappy intel chipset.  11.10 doesn't work on it either, but 10.04 does.  Try that.

also keep trying with the cd.  I'm pretty sure it's just a bad cd.

10.04 gives me this: gib warning     getpwuid-r(): failed due to unknown user id (0)
and nothing else.
md5sum checked out fine.

---

### Post by Micropox on 2012-01-22
> **marinara said:**
> [http://www.linuxtested.com/results/acer_3900pro.html](http://www.linuxtested.com/results/acer_3900pro.html)

supposedly red hat enterprise workstation 4.0 is compatible with your acer

really? ill check it out. 
debian worked but Lubuntu was AWESOME, for a week before it did this

---

### Post by nothingspecial on 2012-01-22
> **Micropox said:**
> Wow what an unfortunate typo

fixed :)

By the way it is possible to edit your own posts after you have posted.

---

### Post by Micropox on 2012-01-22
> **nothingspecial said:**
> fixed :)

By the way it is possible to edit your own posts after you have posted.

Yeah i could have edited it.
i was quite amused to see it was censored before i realised!

---

### Post by Micropox on 2012-01-22
Huh? I have an rss feed? I have a website?
Is this spam? right here on the ubuntu foums?

---

### Post by Micropox on 2012-01-22
A ha, did 10.10 support my architecture at one time?
now it doesn't?

because the only disk that worked was 10.10 which i downloaded about mid last year.

---

### Post by nothingspecial on 2012-01-22
> **Micropox said:**
> Huh? I have an rss feed? I have a website?
Is this spam? right here on the ubuntu foums?



It was. When you see it, please use the report abuse button at the side of it to alert the staff and we will remove it.

---

### Post by Micropox on 2012-01-22
Hmmm.. Wow! Today the comp with 10.10 just started up. No problems.
Erm... problem solved?....
I wonder if i had a virus.
This is odd.
Also my desktop background dissappeared and went blank. Don't know if that means anything?

I tried running a 10.04. cd on another machine but All i get is the 'gib warning getpwuid-r(): failed due to unknown user id (0)'   message. Just like with 11.10

---

### Post by Micropox on 2012-01-23
avgscan finds the virus worm/delf.CXJ in the one of the folders of the recycler folder.

---

### Post by MG&amp;TL on 2012-01-23
That is very unusual...Perhaps you should post again in the security forum? I've never had any form of intrusive virus (worm, virus) in linux...

---

### Post by cryptotheslow on 2012-01-23
> **Micropox said:**
> avgscan finds the virus worm/delf.CXJ in the one of the folders of the recycler folder.


The closest I can find is - according to BitDefender that is, a windows virus (Win32.Worm.Delf.NCZ) :
[http://www.bitdefender.com/VIRUS-1000224-en--Win32-Worm-Delf-NCZ.html](http://www.bitdefender.com/VIRUS-1000224-en--Win32-Worm-Delf-NCZ.html)

Not sure what the CXJ means as opposed to NCZ :confused:

Anyway that one adds a registry entry and drops an exe and a dll file. Doesn't sound like a threat to a Linux box.

Have you checked the S.M.A.R.T. status for your hard drive?

---

