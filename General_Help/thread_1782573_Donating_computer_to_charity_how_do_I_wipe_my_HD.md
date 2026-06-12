---
title: "Donating computer to charity how do I wipe my HD?"
date: 2011-06-14
forum: General Help
---

### Post by sympaty on 2011-06-14
Hello

I'm donating my computer to charity but first I want to make sure there's no data left on it.

I heard about Dban but I can't get it to work is there any way I can do it? I heard about a terminal command which writes many zeros making it impossible to retrieve data, is it legit?

I'm being paranoid but I've done many baking online and I'm scared if my HD would end up in wrong hands.

Any help would be greatly appreciated.

---

### Post by ClientAlive on 2011-06-14
I've only ever used this program when on Windows; but, apparently they have it for Linux too. Maybe it's they type of program where it doesn't matter though - idk. I used it when I switched from Windows to Linux. Whiped my drive like a champ!

[http://linux.softpedia.com/get/System/Hardware/DBAN-6081.shtml](http://linux.softpedia.com/get/System/Hardware/DBAN-6081.shtml)

Useful info:

[http://www.linux.com/archive/feature/48092](http://www.linux.com/archive/feature/48092)

Comment: If you do this it will completely wipe your hd beyond all going back. Yes the bios will still be ther (it's not on the hd) and yes you, or whoever, can proceed to install an o/s after that - but it will be absolutely blank until you do.


[http://www.linux.com/archive/feature/48092](http://www.linux.com/archive/feature/48092)
--------------------------

Edit: I don't know how I missed that. My bad. I'm not sure why you would have a problem with it. If I remember right, when I used it before you burn it to disc, put the disk in the drive and then boot from that disc. I had a problem making the selections correctly the first couple times I tried; but, after reading the instructions very carefully, I figured out the right way. It took a long time to do (and this is only a 40 gig drive). I think it writes all zeros or something like that, then erases the drive - and does it like 3 times over. It's said the gov uses it for their needs. (thats what I heard somewhere anyhow).

---

### Post by ventrical on 2011-06-14
Try to identify the maker of the drive and you can most likely download a diskmanager specific for that drive, ie; MaxBlast etc. 

 These will restore all bits to Zeros.

 Using non-proprietary software can be risky always. Iv'e seen a lot of drives where people ahve told me they have been wiped clean and they are loaded with info and settings.

---

### Post by pqwoerituytrueiwoq on 2011-06-14
there are some programs that can get some data (not much) off even after a dod wipe
if you really are paranoid run it 2 times

---

### Post by SavageWolf on 2011-06-14
I'm not sure, but would "dd if=/dev/zero of=/dev/sdX" or "cat /dev/zero > /dev/sdaX" be sufficient?

---

### Post by sympaty on 2011-06-14
> **ClientAlive said:**
> I've only ever used this program when on Windows; but, apparently they have it for Linux too. Maybe it's they type of program where it doesn't matter though - idk. I used it when I switched from Windows to Linux. Whiped my drive like a champ!

[http://linux.softpedia.com/get/System/Hardware/DBAN-6081.shtml](http://linux.softpedia.com/get/System/Hardware/DBAN-6081.shtml)

Useful info:

[http://www.linux.com/archive/feature/48092](http://www.linux.com/archive/feature/48092)

Comment: If you do this it will completely wipe your hd beyond all going back. Yes the bios will still be ther (it's not on the hd) and yes you, or whoever, can proceed to install an o/s after that - but it will be absolutely blank until you do.


[http://www.linux.com/archive/feature/48092](http://www.linux.com/archive/feature/48092)
--------------------------

Edit: I don't know how I missed that. My bad. I'm not sure why you would have a problem with it. If I remember right, when I used it before you burn it to disc, put the disk in the drive and then boot from that disc. I had a problem making the selections correctly the first couple times I tried; but, after reading the instructions very carefully, I figured out the right way. It took a long time to do (and this is only a 40 gig drive). I think it writes all zeros or something like that, then erases the drive - and does it like 3 times over. It's said the gov uses it for their needs. (thats what I heard somewhere anyhow).
Thank you. I will take a look at those links, forgot to mention that I was running Dban from usb, I'll get some blank cds and try again.


> **ventrical said:**
> Try to identify the maker of the drive and you can most likely download a diskmanager specific for that drive, ie; MaxBlast etc. 

 These will restore all bits to Zeros.

 Using non-proprietary software can be risky always. Iv'e seen a lot of drives where people ahve told me they have been wiped clean and they are loaded with info and settings.
What kind of info and settings?


> **pqwoerituytrueiwoq said:**
> there are some programs that can get some data (not much) off even after a dod wipe
if you really are paranoid run it 2 times
I was thinking about PGNR 8 times.



> **SavageWolf said:**
> I'm not sure, but would "dd if=/dev/zero of=/dev/sdX" or "cat /dev/zero > /dev/sdaX" be sufficient?
That's what I was talking about "terminal command", I also wanted to know if it would be enough, I'd be glad if someone could clear that for us.

---

### Post by ClientAlive on 2011-06-15
I just happened to stumble across this. Thought the info may be of some use to you?

[http://superuser.com/questions/19326/how-to-wipe-free-disk-space-in-linux](http://superuser.com/questions/19326/how-to-wipe-free-disk-space-in-linux)


HTH

---

### Post by -kg- on 2011-06-15
Is your computer a desktop or a laptop?  If it's a desktop, I just found a 320 GB internal hard drive on the 'net for $40 and I'm sure you can probably find them even cheaper.

The absolute best way to protect your data from falling into the wrong hands is to take out the old hard drive and replace it with another.  Then either physically destroy the old drive or reuse it.

---

### Post by decoherence on 2011-06-15
I second the suggestion of taking out the current hard drive and putting a new one in. Otherwise I would go with savagewolf's suggestion of running dd if=/dev/zero of=/dev/sdX (X being whatever hard drive it is. Probably 'a' if it's the only hard drive in the machine.) Run this command from a live cd or bootable usb stick. I really don't trust proprietary software to do this properly -- the built in tools work and have worked for decades.

Another cute trick for the paranoid

```

while true
do cat /dev/urandom > randomfile
rm randomfile
done

```

this will write random junk to a file until the filesystem is full and the cat command bails out, then it will delete the file and repeat. The idea is to repeatedly write random crap to unallocated blocks, where the CIA might find your plans for world domination that you just deleted. For great justice, let this run overnight then kill it with CTRL C and delete whatever remains of randomfile. You can do all of this before or after doing a format -- doesn't really matter. 

An additional perk is that this can be safely run on a live system (as long as you aren't running a busy sql database or something when the filesystem fills up) to 'shred' unused disc space.

Of course, the above assumes that you have mounted the drive you want to operate on and your working directory is somewhere on that drive. Really, whether or not you do this depends on just how certain you are that the drive will fall in to enemy hands. After all, charities that accept computers are really just fronts for the CIA you know and those damn spooks will foil your world domination plans and rip off your grandma's jambalaya recipe.

---

### Post by decoherence on 2011-06-15
> **-kg- said:**
> Then either physically destroy the old drive or reuse it.

I'm a fan of the maraca method.

1) throw the drive on the ground as hard as you can (keeping in mind drives are hard so try to avoid your toes and maybe do it in the parking lot or on some kind of concrete)
2) repeat until the drive becomes a serviceable maraca
3) start a latin jazz band

this method of disk disposal is also effective at burning calories. Double blind tests at MIT have shown this method to be an emotionally therapeutic form of disk disposal.

---

### Post by Irihapeti on 2011-06-15
Using one pass of dban or dd is enough.

[http://computer-forensics.sans.org/blog/2009/01/15/overwriting-hard-drive-data/](http://computer-forensics.sans.org/blog/2009/01/15/overwriting-hard-drive-data/)

If you want to take the $)$% out of wannabe data recoverers, you can do this: [http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/](http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/)

---

### Post by crispy_420 on 2011-06-15
Sure you can go all out and physically destroy the hard drive by various methods including [thermite]("http://www.youtube.com/watch?v=k-ckechIqW0") but that serves the next owner no good. I would just use Darik's Boot and Nuke as mentioned by others as wipe until your heart is content. Lets just say the DoD is OK with a three pass minimum and if it secure enough for them, who am I to judge they only protect national secrets.

---

### Post by decoherence on 2011-06-15
> **Irihapeti said:**
> 
If you want to take the $)$% out of wannabe data recoverers, you can do this: [http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/](http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/)

+1!

Similar to what I posted but so much more amusing!

---

### Post by ventrical on 2011-06-15
> **sympaty said:**
> Thank you. I will take a look at those links, forgot to mention that I was running Dban from usb, I'll get some blank cds and try again.



What kind of info and settings?



I was thinking about PGNR 8 times.




That's what I was talking about "terminal command", I also wanted to know if it would be enough, I'd be glad if someone could clear that for us.


 If the hdd ever had a Windows Os on it and it was upgraded from , say Win 95 to XP or an XP hdd to Vista etc.. then it is likely that it has hidden partitions that are not always necessarily destroyed - even using Windows own tools. So , it a USER was deleted then those files are stored at the back-end of the disk. You would be surprised how much stuff still remains on hdds that are suppossedly clean.Most importantly are log-files of the destroyed oS/files.

 I know for sure that the Maxtor DM (MaxBlast) DOES and WILL restore all bits to zero. This is a 1.44MB boot floppy that can be easily downloaded from the internet.  It works mostly on Maxtor drives but has worked on some other drives.

  What is the brand name of the hdd???

---

### Post by ventrical on 2011-06-15
Here is free Maxblast bootable floppy:


[http://members.shaw.ca/rinocanada/hdutils.htm](http://members.shaw.ca/rinocanada/hdutils.htm)

You can get bootable CD also.

 Not sure if this is what you are looking for

Maxblast also covers Seagate drives now.

There might be other sites to download MaxBlast from.

---

### Post by slooksterpsv on 2011-06-15
Personally, I like Dariks Boot and Nuke. It's fast, you can burn it to a CD or get the Ultimate Boot CD (which is a collection of utilities (DOS based)).

---

### Post by Yellow Pasque on 2011-06-15
Take the hard disk out. Don't donate it. If you still want to destroy the data, wipe the drive, physically destroy it, and bury the pieces at different spots in the backyard.

---

### Post by SavageWolf on 2011-06-16
Ventrical, doing anything with /dev/sdX will erase all the partitions.

Also, I think [http://xkcd.com/538/](http://xkcd.com/538/) comes in to play, nobody will care what is on the HDD, and if they did, there's better ways of getting that information. A single write should suffice, unless you know anyone who has an electron microscope.

---

### Post by ClientAlive on 2011-06-16
> **crispy_420 said:**
> Sure you can go all out and physically destroy the hard drive by various methods including [thermite]("http://www.youtube.com/watch?v=k-ckechIqW0") but that serves the next owner no good. I would just use Darik's Boot and Nuke as mentioned by others as wipe until your heart is content. Lets just say the DoD is OK with a three pass minimum and if it secure enough for them, who am I to judge they only protect national secrets.


I'm pretty sure - if my memory serves me - that dban makes 3 passes by default. It's not like you literally have to run it 3 times. I do remember it taking a long time though. I think it was something like 2.5 hours or so form my 40 gig drive I ran it on.

---

### Post by sympaty on 2011-06-16
> **ClientAlive said:**
> I just happened to stumble across this. Thought the info may be of some use to you?

[http://superuser.com/questions/19326/how-to-wipe-free-disk-space-in-linux](http://superuser.com/questions/19326/how-to-wipe-free-disk-space-in-linux)


HTH
Hi again.

I ran this overnight

```
dd if=/dev/zero of=zero.small.file bs=1024 count=102400
dd if=/dev/zero of=zero.file bs=1024
sync ; sleep 60 ; sync
rm zero.small.file
rm zero.file
```

When I woke up I saw a warming saying that my disk was full then I thought, It worked! but when I opened gparted to format it said my hdd was not full and was only 4% used, Any ideias what did I do wrong?

Thank you again.

> **-kg- said:**
> Is your computer a desktop or a laptop?

Old laptop

> **decoherence said:**
> 
Another cute trick for the paranoid

```

while true
do cat /dev/urandom > randomfile
rm randomfile
done

```

Hi, I think I did something wrong when running that.
*Terminal
*sudo -s
*copy and paste that code into terminal

Nothing happened, did I do something wrong? Thanks

> **Irihapeti said:**
> 
If you want to take the $)$% out of wannabe data recoverers, you can do this: [http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/](http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/)

Too bad dban won't work here, Apparently that'd only destroy the empty space and not the whole drive, but I could be wrong.

> **ventrical said:**
> What is the brand name of the hdd???
SAMSUNG HM160HI, Thanks.


> **slooksterpsv said:**
> Personally, I like Dariks Boot and Nuke. It's fast, you can burn it to a CD or get the Ultimate Boot CD (which is a collection of utilities (DOS based)).
I ran ubcd but dban won't rum from it, then I used diskill not sure if that was the best option after rebooting I got a black screen saying I had no OS on it, did it work? I haven't seen good reviews about it though, thanks.

---

### Post by ClientAlive on 2011-06-16
> **sympaty said:**
> Hi again.

I ran this overnight

```
dd if=/dev/zero of=zero.small.file bs=1024 count=102400
dd if=/dev/zero of=zero.file bs=1024
sync ; sleep 60 ; sync
rm zero.small.file
rm zero.file
```

When I woke up I saw a warming saying that my disk was full then I thought, It worked! but when I opened gparted to format it said my hdd was not full and was only 4% used, Any ideias what did I do wrong?

Thank you again.



[http://superuser.com/questions/19326/how-to-wipe-free-disk-space-in-linux](http://superuser.com/questions/19326/how-to-wipe-free-disk-space-in-linux)

That link above is the one about only destroying the free space. That's the one I shared. I thought maybe the info could used if a person just modified/ tweaked what they were doing there. No biggie.


This link, however, [http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/](http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/)  contains information on at least two options (1) only the free space and (2) the entire thing. They aren't numbered like I did here but they are in that order.



This link, however, [http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/](http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/)  contains information on at least two options (1) only the free space and (2) the entire thing. They aren't numbered like I did here but they are in that order.

---

### Post by dcstar on 2011-06-17
> **pqwoerituytrueiwoq said:**
> there are some programs that can get some data (not much) off even after a dod wipe


Rubbish. I have been hearing this stuff for over 20 years (usually from people selling "Wiping" software) and have never seen anything NOT out of Hollywood that can do it. Please quote some credible sources or cease spreading myths.

If people want to "wipe" their disks, download and use a utility that uses the built-in ATAPI "Secure Erase" command that every PATA/SATA drive had had for well over a decade.

---

### Post by User3k on 2011-06-17
[http://www.dban.org/](http://www.dban.org/)

Has worked for me in the past.

---

### Post by KeyserSoze93 on 2011-06-17
I'd boot from a live disc and run "shred -n 2 /dev/sda" (or whatever your disc is.)

shred will overwrite the file/disc with random data but it's a lot faster than dd'ing from /dev/random. -n 2 means it will do it twice for added security.

---

### Post by -kg- on 2011-06-19
> **dcstar said:**
> Rubbish. I have been hearing this stuff for over 20 years (usually from people selling "Wiping" software) and have never seen anything NOT out of Hollywood that can do it. Please quote some credible sources or cease spreading myths.

If people want to "wipe" their disks, download and use a utility that uses the built-in ATAPI "Secure Erase" command that every PATA/SATA drive had had for well over a decade.

I agree with that.  The only reason you'd want to go even with DOD standards is if you had something to hide from a government or major criminal organization, who (might) have the resources.

Still, rather than go through all that bother, I'd just take the old HD out and replace it with a cheapie.  Then you'd have an extra hard drive to use on your new system.

---

### Post by ClientAlive on 2011-06-20
When I ran dban on my laptop (this laptop) it took me several attempts to get it right. The thing is odd in that, if you don't follow the instructions exactly for selecting the action to perform or item to perform it on - whatever, it will look like it is running the process but will only take a min and then you find out it didn't do it at all. This was at the time I switched over to Linux - which was only about 3 mos ago.

It was only after sitting there and being very very careful to read the instructions a couple times and about how I made my selections/ followed those instructions - that it actually ran like it should. When it did run I was surprised at how long it actually took to do the job. I have a, roughly, 40 gig drive on this thing; and, if I recall correctly, it took about 2.5 hrs to complete. When it was all said and done I was very pleased with the result though. It does exactly as it's supposed to and does a great job of it - if you set it up correctly and get the job to run at all.

dban claims to do a dod whipe if I remember right. It's said that the dod actually uses *it* for their disk whiping needs.

---

### Post by Sylslay on 2011-06-20
dd if=/dev/zero of=/dev/sdX bs=1 count=512

dd does the job!

Where sdX is Yours HDD, 
try random delete data with "dd"

---

