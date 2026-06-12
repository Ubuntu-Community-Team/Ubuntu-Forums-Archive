---
title: "Having trouble getting Ubuntu to work on bro's PC"
date: 2010-06-02
forum: General Help
---

### Post by Snippa on 2010-06-02
This is not the first time I've installed Ubuntu on a computer, but the first time I've run into so many issues. I have Ubuntu 10.04 64bit working perfectly on the pc I'm currently using.

My brother's pc is quite a bit older, 2.7 ghz celeron (...single core), 1gb memory, 80gb hd, 9250 radeon.
It took me forever to even gt Ubuntu installed on his hdd, I actually had to unhook it from his pc and put it in mine to be able to do it. (kept running into busybox initramfs error)

So I finally got Ubuntu installed on his pc last night after having completely wiped out windows xp (with no disc to get windows back), put the hdd back in his pc, got it up & running. Got the network settings set up, tried to open firefox - nothing, wouldn't load. went into update manager and started updating the software. The update manager got stuck on updating Grub, I left it to do it's thing while I slept hoping it would finish.

I wake up, go back to his pc and it's still stuck on grub, not really anything I could do but shut down his pc and try again, well, his pc doesn't even want to load Ubuntu now.
I tried booting up several times, then tried the restore option in the loader, but all I get is this:

[http://ubuntuone.com/p/5sX/](http://ubuntuone.com/p/5sX/)

Any help would be very welcome.
Also, if anymore information is needed, please let me know and I will do what I can to provide the info.

---

### Post by bigsmitty64 on 2010-06-02
Are you using the same live cd you used for** your** install? If so, that would pretty much rule out a bad burn. 
The next thing I would try is a complete reinstall. As this is fresh anyways and you've got nothing to lose.
Is there more than one hard drive on the p.c.?  If so, make sure the ubuntu drive is set as first boot drive in the bios. 
This is what I would do, someone else may have more insight on the subject though.

---

### Post by Snippa on 2010-06-02
I didn't think his computer could run 64bit Ubuntu, so I downloaded the latest iso off ubuntu.com.
I guess I can try reinstalling with the disk I used to install Ubuntu on this pc, but i have no clue how it will run, if I can even get to that point.

---

### Post by bigsmitty64 on 2010-06-02
How old is his pc? it may be 32 bit right? 64 bit won't run on a 32 bit, but the other way around is o.k. try downloading that (32 bit) instead maybe?  or is that what you meant when you said you downloaded the latest one?

---

### Post by TheDesertDragon on 2010-06-02
While Celeron processors are marketed to be able to run 64-bit, it often runs incredibly poorly and is not recommended.

Besides, with only 1GB of RAM and such an old graphics card, there isn't really any reason to be running 64-bit at all.

My suggestion is to use a 32-bit version.

Also, you might get one hell of a time getting a proper display driver. I wish you good luck with the legacy FGLRX drivers. (Well, one can only hope you'll find a great Open Source driver - there should be some of them around by now, eh?)

---

### Post by Snippa on 2010-06-02
Well, his graphics don't need to really be outstanding. When it was running last night, the graphics seemed fine without updating but then I only got so far lol... didn't really get to put the gfx card to the test. :)

...That is what I did last night, was install the 32 bit version, thats why I'm wary of trying my 64 bit disc.
I was wondering if I should try an older version of Ubuntu, but my friend said no.
He also thought that the hdd was fried, but it seemed to work fine (though as slow as those older ones do) when I put it in my pc. I even checked it for errors with none coming up.

I was thinking there was some other hardware problem, I'm not sure what exactly though.

---

### Post by bigsmitty64 on 2010-06-02
Its been said that an iso burn can go bad if burned at too high of a speed. Maybe try it again (burning) at the slowest speed you can. And like the previous poster said, with 1 gig of ram 64 bit is kinda gonna be useless on that old machine.

---

### Post by Snippa on 2010-06-02
Tried burning a couple new discs, and even though I didn't really plan on putting 64 bit Ubuntu on his pc, I still tried my cd I used for my pc as well.

The first of the last 3 tries was a reburn of the iso I downloaded last night, but at 8x speed. No good, froze up fairly quickly. Couldn't even hit F6 to see what it had done up to that point.

The second try was with my 64 bit disc, no surprise I'm sure, I got an error saying I should use a non-64bit version.

3rd try, I downloaded the iso from the Rochester mirror... started up ok at first, at least got to the loading bar screen, watched the blinking lights on my computer stop, hit F6 and it is completely stopped.

---

### Post by Snippa on 2010-06-03
Just tried a freshly burned cd of Xubuntu as well, same busybox/initramfs problem as the Ubuntu cd I tried.

I really don't know what to do at this point. Neither I nor my brother can afford new hardware at this point. I am absolutely amazed that I can't get this working on that computer.

---

### Post by bigsmitty64 on 2010-06-03
I just read in another post that someone went   into their BIOS and changed the SATA mode from 'IDE' to 'RAID' and that solved there problem.

[HERE'S ]("http://ubuntuforums.org/showthread.php?t=765195") the link to the thread if you want to read it. It pretty much just says what I just said. :)

---

### Post by Snippa on 2010-06-03
I read something about there before I posted, but I'm really not sure how to go about that, I don't see a setting for that in my bios

Edit: yeah, I just went through all my bios settings and theres nothing like that in there at all.

---

### Post by Snippa on 2010-06-03
Still having trouble, I went through and tried a couple more things. I tried installing from my external hard drive onto his computer, no go same problem. I tried installing to my external hard drive, but that just gave me other problems I don't feel like dealing with (grub issues). Oh, and the cds do work, theres no problem there.

I have only 1 more thing I can think of to try, but I don't see why it would work... which would be unhooking my extra cd burner & extra hard drive. (I dunno, the installer says it can't find a medium with a live file system on it right? so maybe one or both of those are causing some issue - my reasoning behind trying that, however unhelpful it may be)

---

### Post by cryptotheslow on 2010-06-03
Try using the text-based alternate installer CD from here: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

That at least should get you around any gfx related issues during the install and probably give you a better idea about the exact point the install is failing.

---

### Post by Snippa on 2010-06-03
tried that, hangs at 33% of setting up the ext4 partition. Couldn't find a solution for that either.

---

### Post by cryptotheslow on 2010-06-03
Maybe try creating just a 20GB ext3 partition - that's room enough for the install then you could move /home into the other 60GB once you get it up and running.

That does sound suspiciously like a problem with the drive or the BIOS mapping to it.

---

### Post by bigsmitty64 on 2010-06-03
" unhooking my extra cd burner & extra hard drive"

That actually might be a good idea. My roomate always unhooks every hard drive except the one he's gonna install to. I personally think it's the same as setting that drive first in the boot order in bios. But hey give it a shot bud, it may surprise you!

**EDIT**: side note, I'm stepping out for a bit but will check back in a couple hours from now. I know theres a time difference between us so its later where you are right?

---

### Post by Snippa on 2010-06-03
Not me, I'm actually in Michigan.

@cryptotheslow - that's a little bit confusing, but I'll see what I can do.

Haven't done anything yet... enjoying a nice break from all the questions running through my head about why it wont work. lol

---

### Post by bigsmitty64 on 2010-06-03
whoops! I glanced  @ cryto above me and saw UK, thinking it was you. 
I agree, it always helps to take a break sometimes and just walk away for a while.

---

### Post by cascade9 on 2010-06-03
> **Snippa said:**
> tried that, hangs at 33% of setting up the ext4 partition. Couldn't find a solution for that either.

I've had HDDs with bad sectors that will stall like that when tryign to create a partition. 

I'd try cryptotheslows advice, and try making a smaller partition (and ext3 as well, just 'to be sure'). If you have things hang again, but at a different point, you can use a bit of maths to figure out if its at the same place in the drive.

---

### Post by Snippa on 2010-06-03
Unhooked the cdrw drive, the extra hard drive and am trying the alternate install... still problems.
Also am trying a smaller partition. It doesn't hang with the smaller partition for the journaling system, but it does fail. I have tried ext4, ext3, ext2, and a couple others. Only one of them (xfs was it? i don't remember) worked, but then failed while it was attempting to install the base system.

Also, for some reason, while using the alternate install it wants network info, but then when I put in the newtwork info for my wireless network, it fails to connect. Not sure if that had something to do with the install failure of the base system. It said something about network or bad cd.

Gonna try one of the other cds again, non-alternate install, since I haven't tried them since disconnecting those drives. ...just want to see if it helped at all, you know?

---

### Post by Snippa on 2010-06-03
With the non-alternates I still get errors:
init: line 7: can't open: /dev/sdb : no medium found
init: line 7: can't open: /dev/sdb : no medium found
init: line 7: can't open: /dev/sdc : no medium found
init: line 7: can't open: /dev/sdc : no medium found
init: line 7: can't open: /dev/sdd : no medium found
init: line 7: can't open: /dev/sdd : no medium found
init: line 7: can't open: /dev/sde : no medium found
init: line 7: can't open: /dev/sde : no medium found

That's with both trying to "try first" and just straight up install.

...going to try a slow burn of the alternate install now... sigh

---

### Post by bigsmitty64 on 2010-06-04
So, to recap, you've tried different distros, Ubuntu, kubuntu, 32 bit 64 bit,  different partitioning, slow burn, fast burn. 
 Do you have an extra hard drive anywhere? Thats the only thing you haven't tried. And it was mentioned earlier in this thread that the hard drive could be toast. I think you've ruled out almost everything else at this point, I'd definately try a different hard drive if at all possible.

---

### Post by Snippa on 2010-06-04
> **bigsmitty64 said:**
> So, to recap, you've tried different distros, Ubuntu, kubuntu, 32 bit 64 bit,  different partitioning, slow burn, fast burn. 
 Do you have an extra hard drive anywhere? Thats the only thing you haven't tried. And it was mentioned earlier in this thread that the hard drive could be toast. I think you've ruled out almost everything else at this point, I'd definately try a different hard drive if at all possible.

I am replying to this message from a freshly installed copy of Ubuntu on the hard drive from my brother's computer (i disconnected my hard drive to make absolutely sure installation went as intended).
Before this installation, I had removed my dvd-rw drive from my computer, put it in his computer to see if the problem was with the cd drives, same problem with my drive.

I haven't attempted to run linux again on this hard drive in my brother's computer yet, however I'm pretty sure I will end up with the problem I ran into that led me to posting here in the first place.

I am thinking there must be a problem with the motherboard (ms 6577), memory, or the processor. Just compatibility issues is all I'm sure, as the computer worked fine for years on Windows XP.

Oh, I also brought my brother's computer into my room and plugged the ethernet cable that was in my pc into his, network worked fine during install attempts, but again as I said everything else ended up failing just the same.

For some reason something on his computer doesn't seem to want to work with ext4, ext3, or ext2 file systems.

I have found web pages that say the ms 6577 motherboard is supposed to be compatible with Linux so I'm not completely sure if that is the problem.

Edit: I have found my Windows XP disc, so if it comes to it, I guess I'll have to try and reinstall that, and pray I don't run into similar installation problems.

Edit 2: This installation was done with the alternate Ubuntu install files from a CD.

---

### Post by JigglyWiggly_ on 2010-06-04
Go install Debian, report back.

---

### Post by Snippa on 2010-06-04
Will try.

---

### Post by Snippa on 2010-06-04
Good news: The Debian installer worked perfectly, even while using the graphical installer.

Bad news: After installation was completed, the system rebooted, went to the grub menu, and then shortly after dumped these on me:

(first boot) [http://ubuntuone.com/p/60z/](http://ubuntuone.com/p/60z/)
(second boot) [http://ubuntuone.com/p/610/](http://ubuntuone.com/p/610/)

Edit: The install was 100% on my brother's computer, not using any of the hardware from my computer.
The install also used the ext3 file system. The install appeared completely flawless.

---

### Post by Dimarchi on 2010-06-04
Here goes a category "I have no idea what I'm talking about" reply...

I noticed that soft lockup thing in the first screenshot you provided. There are bug reports based on that one...I have found:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/64125](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/64125)

Making an uneducated and wild guess based on the frequency of butterfly initiated earthquakes I would say that you should try the following in no particular order:

- see what device the computer tries to boot from and whether it matches the one what ubuntu tries to boot from (bios check)
- acpi=off with grub
- floppy off in either grub or bios
- take whatever you don't need out of the computer for installation
- tweak bios (been there done that...it can be an exercise which increases male baldness patterns)
- check the installation target drive with live cd and perform repairs and perhaps initial partition/formatting

Hopefully *something* works.

Quickie edit from the oh, and another thing...d'oh...posted already dept.:

note the pci-db thing...it seems to suggest the video card...some problem related to it, perhaps.

---

### Post by Snippa on 2010-06-04
> **Dimarchi said:**
> 
note the pci-db thing...it seems to suggest the video card...some problem related to it, perhaps.

Good news: After removing both the wireless network card and the ATI Radeon 9250 card, Debian decided to boot up. (after which I readded the wifi card)

Bad news: ...Obviously it's bad news that I cannot use the video card, and have to stick with the on board video. Also, after booting into Debian, it doesn't seem to want to connect to the network over wifi. It can find the network, but when I put in my WEP it fails to connect. Not sure why.

I'm retesting all the other install CDs now... (ubuntu graphical, alternate, xubuntu alternate) just to see if the reason they didn't work had something to do with the video card as well. Not sure about that, but who knows, right?

---

### Post by Snippa on 2010-06-04
I am happy to announce that I am posting this message from a fresh install of Ubuntu 10.04 LTS 32 bit (installed from graphical cd) on my brother's computer.

It appears that indeed the problem was with my ATI Radeon 9250 video card. I'm not sure exactly why though.
Wifi is working fine on this, as should be obvious. No problems detected so far whatsoever.

Now I just need to run the update manager, and then find some essential programs that I'm sure my brother will be looking forward to using.

Thank you everyone for your input and trying to help me out with this. If any of you can think of a work around to get the video card to work as well, I'd appreciate it.

---

### Post by cryptotheslow on 2010-06-04
Well now you have a working system you could try putting the ATI card in and see what happens.

Probably best to see what fglrx packages you have installed first - apparently the open drivers do work with this card and will enable the nice desktop effects but even a quick google returns lots of problems with getting the 9250 to work right.

I'm saying "apparently" because I have never used ATI cards with Linux, always NVidia - so I'm just regurgitating what I've read, which is probably not very helpful! :D

---

### Post by Snippa on 2010-06-04
The 9250 is a piece of crap, lets just put it that way. (that's why I have the pc I use now lol)
It is however much much better than the onboard graphics on that computer.

Video (youtube) is extremely choppy on that pc right now. And I have actually had a couple freeze ups on it with the graphics going crazy in the last few minutes. I'm done working on it for the moment.

I COULD put the card back in and attempt to boot, but remember, I'm here because of the issues with booting in the first place... which removing the card solved. Something in the kernel just doesn't like it.

...I have lots of crap to clean up, screws to replace... fun fun fun.

---

### Post by Snippa on 2010-06-05
So putting the video card back in turned out to be a bad idea.
Started getting new errors (which I cannot recall at the moment) during boot.
So I removed the video card and tried booting up again... similar error, checked bios, noticed it was still set to use the PCI video card (oops) so switched it to onboard, rebooted... similar error.

Tried rebooting a few more times, similar errors. Decided to reinstall Debian, seemed fairly stable, no lag. Though Debian does have a graphic issue which would mess up my brother's eyes worse than they already are, and of course as I mentioned before it doesn't want to work with the wifi card correctly either.

Checked my cds (cuz I hadn't labeled them yet), labeled them, attempted a reinstall of ubuntu... now the system is acting really weird. screen blinking black, can see the cursor until I move it, then its gone on the next blink. ctrl+alt+del doesn't work, power button doesn't work. can only pull the cord.

Extremely annoyed at this.

---

### Post by Dimarchi on 2010-06-05
A clean reinstall after removing everything non-essential is probably the way to go...again (if you can't get it to stable condition after removing 9250).

Do not use fglrx driver with that ATI card! It is no longer supported by it. Basically, if it does not have HD in the card name, no go. Radeon or even more primitive VESA are the ones to be used.

If you can't get it to work even with those, I'm afraid the option is to be content with onboard video or buy a cheapo replacement video card.

---

### Post by Snippa on 2010-06-05
The fglrx drivers were not pre-installed, however all the others were.
I have tried several things over night. Sadly it seems even without the video card in the machine, the system is incredibly unstable with Ubuntu on it. I'm not sure if this is just an Ubuntu problem though. I tried updating the kernel at one point, hoping that would work, unfortunately of course, no go.
That did however allow me to see some errors with the card in the machine that I hadn't been able to see before. What's bad about that though is that the system went corrupt after seeing those errors and my camera wasn't cooperating with trying to take a picture of the errors . Also, after attempting to use the LiveCD to view the log files, no go. the CD cannot see the /var directory for some reason, which I believe is where the log files are (could be wrong, not sure).

...I suppose I could load up the hard drive in my machine and see what I could do from there, but I'm really getting tired of dealing with all this crap lol

I have done so much searching trying to find the exact cause of the problem... going by the error messages in the log files, it hasn't really been much help.

I'm going to try yet another different distro out, claims to be lightweight, we'll see how it compares to debian (which had less graphical lag than Ubuntu), this one is Arch Linux.

I am about 90% positive the problem with the video card is Kernel related and has nothing to do with Ubuntu or the Xorg drivers. I really don't know what to do about that though.

I guess at this point, for right now anyway, I can only pray that Arch Linux will run the way I want it to. If not, I'll probably keep digging.

Problems are unacceptable and must be dealt with. I will get this to work! ...sooner or later. o.O

---

### Post by Snippa on 2010-06-06
Just a quick FYI.

Arch Linux, wow what an experience. Nothing like doing all the setup manually. That was definitely an experience.
Computer is up & running on Arch Linux with Xfce desktop. Wifi card is up & running... and video lag is... well, he'll have to deal with it. It's not horrible, but it's not smooth. System is stable. Not much else to do from here for me except put some stuff back together and put his pc back at his desk.

I really appreciate the help you guys tried to provide. I did attempt to use the video card with this build as well, but unfortunately the computer tried to tell me that the file system was corrupted when I did.

I guess I'll have to keep my eye out for a Kernel update that fixes the problem (if that is indeed where the problem is) or something, I dunno.

I'm just happy to provide him with a stable linux system that he can use to do everything he needs to do without having to worry about the downfalls of windows.

Thanks again.

---

### Post by Snippa on 2010-06-07
The video card problem is still bugging me. So I did another google search a little while ago and saw something about blacklisting agpgart & intel_agp to possibly solve the problem. I have not attempted this since, just putting the card in the computer risks corrupting the file system.

For the people who have had no success with blacklisting those, I read through their entire threads on the problem, and they seem to dead end, not sure if they gave up or what.

Basically, the idea is to keep the system from trying to use the onboard graphics card it appears.

So here's my questions:
What does blacklisting those actually accomplish?
And what if that fails to do what it is supposed to? Is there another way?
Is it actually possible that this may be a solution to getting the video card to work in that pc?

I can see 2 scenarios where this could end miserably for me:
1. Blacklisting those works the way I think they do, however at the same time, the card still doesn't work... making it impossible for me to use even the onboard graphics past the bios.
2. The card corrupts the file system again, forcing me to reinstall linux yet again.

I don't even want to attempt this until I get some sound feedback on this. Let me know what you guys think.

---

### Post by arubislander on 2010-06-07
I'm not sure how blacklisting the on board video card drivers would help in getting the graphics card to work... but blacklisting is a reversible process.

---

### Post by Snippa on 2010-06-07
I'm not sure either, I assume it's possible theres some conflict that the kernel doesn't know how to handle and spews out those errors. But, it does appear to have worked for some people who were having issues with their video card and intel onboard graphics.

---

### Post by Snippa on 2010-06-08
Problem solved. Blacklisting those modules did indeed fix the problem with the video card.

---

### Post by arubislander on 2010-06-08
Good to hear!

---

