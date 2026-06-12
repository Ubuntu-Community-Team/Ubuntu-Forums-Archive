---
title: "Booting from usb, What brands/models work best?"
date: 2009-12-11
forum: General Help
---

### Post by miniyak on 2009-12-11
I know the that to put ubuntu on a usb stick, having more then a gig works best, so im going to have to go and buy a new thumb stick. 

I have also heard that some usb drives work better then others, so my question is 
Which brand/model thumb drives have you been successful booting from?
And which brands are a pain? 


Also if you know, What is the best performing drive you have used?

---

### Post by emigrant on 2009-12-11
i have used only Kingston to boot and for me some drives have worked successfully while others failed, on different machines.

---

### Post by Raistlin355 on 2009-12-11
hmmm, I don't think I have ever even bothered with the performance of a thumb drive, I just use whatever I have available.  ATM I have a bootable 1gb drive on my data recovery box it is pretty old.  I would imagine that any recent drives this would be negligible.  While writing it has occured to me that you might be asking on just popular brands I use mostly Crucial drives or whatever is cheap off Newegg.

---

### Post by miniyak on 2009-12-13
Im going to be using a thumb stick as the main drive on the hp tc4400 i just picked up for free, so performance matters in this case

the tablet was droped and the current hard drive is being labeled by ubuntu as having "many bad sectors"... so it will be time to replace it soon and i believe the drive is a sata with a specialized connector... regardless i figure a 16gb jump drive should be faster cheaper and better on gas...(power) 

What i mainly want to know is, if i go to staples tomorrow which flash stick is going to offer me the most bang for my buck and if the model I pick will be bootable at all?

---

### Post by rokytnji on 2009-12-15
I would just stay away from any thumb drives Like Sandisk that install non writable read only software in them like U3. There is a uninstaller for U3 offered by Sandisk but you need a Windows Operating System to run it.

That said I have also had real good results with Kingston Data Travelers. They are cheap and rugged.

---

### Post by miniyak on 2009-12-15
good to know, I just bought a 16gb pny drive, i was considering the sandisc same price on sale at a different store because of the retractable plug but i think ill stick to the pny

before i open the package, does anyone have any gripes with pny?

to give an idea of what im going to use it in place of see [here]("http://ubuntuforums.org/showthread.php?t=1355112") 

the guy at staples was try to tell me that all the drive go about the same speed... because its usb 2.0... lol, he said that the speed differences would be negligible... even though in test i saw once i recall seeing something like 12mbs vs. 30mbs in some drives. Wish i could find that article. I also heard that 30 was pushing it at the time and that maybe every thing would get up to that speed, so the guy at staples might have been right

---

### Post by jimmers on 2009-12-15
Miniyak,

Hi, I have never heard of pny drives, but I have karmic on a sandisk 16 gig retractable and it runs great, no U3.

I also have an Integral 16 gig drive, which has run Jaunty, but now just use it for backup,
also have 4 sandisk cruser 4 gig drives which have all had Linux on them running without a problem, the only trouble I have had is with LG Drives, I could install on them but they wouldnt run.

I am probably to late with this missive, but just incase your pny does'nt perform, consider Sandisk.

Good luck and have fun.


Jimmers

---

### Post by luigi_mb on 2009-12-15
> **miniyak said:**
> I know the that to put ubuntu on a usb stick, having more then a gig works best, so im going to have to go and buy a new thumb stick. 

I have also heard that some usb drives work better then others, so my question is 
Which brand/model thumb drives have you been successful booting from?
And which brands are a pain? 


Also if you know, What is the best performing drive you have used?

I have been using Rally2 (16 and 64 GB) by ocz. Compatible, very fast, very reliable.

/luigi

---

### Post by miniyak on 2009-12-15
ok, heres the current status of my adventure

16gb pny "attache" live usb install using "USB start-up disc creator"
on my hp tc4400- boots to the menu that prompts "try ubuntu without making changes to you computer" the freezes up at the black and white ubuntu logo
on my s76 panp5- same deal

Same drive using unetbootin
hp tc4400- boots to the main live menu again but this time it has different options

live
live install
check integrity 
ect.

when live install was selected, got past B&W logo to freeze at a blank screen
same with plain old live
check integrity- says no errors

Antec 2.5 hard drive enclosure w/ WD scorpio blue installed via live cd when the WD drive was in the tc4400 
Through usb on panp5= amazing, works just like real install
Through eSata= dont know antec didn't include the cable *waves fist*

dose anyone know of a way to just do the full install on the pny flash drive with out any of the live stuff? (I dont think any one who boots from usb wants to do the live stuff...)

---

### Post by miniyak on 2009-12-17
Has any one else used the 16gb pny attache drive in particular?

currently it hasn't really worked out for me, was successful once out of maybe 11 trys or so.

the one time i got it right i wasn't to impressed ether, because i'm looking to do a persistent install. Guess I was just trying to prove it was possible at that point.

maybe its just a streak of bad luck?

---

### Post by rokytnji on 2009-12-18
> dose anyone know of a way to just do the full install on the pny flash drive with out any of the live stuff? (I dont think any one who boots from usb wants to do the live stuff...)

You will need some sort of media to install whatever Linux to your PNY Flash drive whether via CDROM, USB Flash,CF Flash,SD Flash (as far as I have done it). There is a method called From Iso but I have never tried it.

Not PNY. Not Ubuntu. Not USB. But this is how I did it.
And I run Macpup on USB. And AntiX on SD. Both capable of saving changes. Both though on a Asus EEEPC 900. 

> when live install was selected, got past B&W logo to freeze at a blank screen

By your sig I see you run Linux for awhile. You don't think it might be a video issue maybe freezing instead of USB Flash drive maybe? Anyhows sorry it aint Ubuntu or PNY
[http://yatsite.blogspot.com/2009/07/install-antix-82-final-on-asus-eee-900.html](http://yatsite.blogspot.com/2009/07/install-antix-82-final-on-asus-eee-900.html)

---

### Post by miniyak on 2010-01-19
might be a video issue, but ubuntu has always said yes to my gpu before... plus it did work once

I ended up installing a distro to the drive called "super ubuntu" using unetbootin.. this almost works perfectly, apparently there is some way to keep applications/files on it but haven't really got around to really messing w/ it.

super ubuntu seems to be base on 9.04 at the moment and has alot of applications included with it that I would consider staples. Like the start-up manager for instance.

I also read on the topic on doing full installs on flash drives. The one important thing to note is doing this reduces the life of the drive. This is prob. why developers are so preoccupied w/ doing live usbs vs. regular installs.

Of course running puppy of a flash drive would be a completely different story. I might conceder trying this in the future

---

