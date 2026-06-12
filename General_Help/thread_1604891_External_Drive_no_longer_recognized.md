---
title: "External Drive no longer recognized"
date: 2010-10-24
forum: General Help
---

### Post by plantboy1 on 2010-10-24
This may or may not be an Ubuntu problem.  Anyways, here's my problem:
I have a salvaged Western Digital 1tb drive, it's of the MyBook type.  It was badly corrupted due to being dropped when I got it; I formatted it to EXT4, ran a SMART test, everything checked out and it worked fine.
Now, it's been a few weeks since the last time I plugged it into my laptop to use it, and when I did...nothing.  Having just updated Ubuntu, I rebooted with an older kernel; still nothing.  I booted back into the newest kernel I had.  Again, nothing.
GParted doesn't see the drive.  Disk Utility shows a 2.2tb, unformatted drive with a clearly bogus serial number and gives me a "Daemon Inhibited" error if I try to eject it, format it, benchmark it, or anything else.  lsusb shows a "Western Digital Technologies" device.  I tried power cycling it, different cables, and same thing every time.

I know for a fact that the drive hasn't moved since the last time I used it because it's sitting on my bookshelf, so nothing physically happened to it.

I'm stuck here; did the drive just...spontaneously combust on me, do I have an Ubuntu problem, or what?  I tested it with a virtual Windows 7, which told me it was an empty CD drive, and with a virtual Mac OS X which opened disk utility, also telling me I had a 2.2tb drive.

I'm worried because this is the second USB device to fail on me within the past week, the other being a flash drive, although I'm fairly certain that one failed because it froze while I was camping.  I'd like to get this drive working again if I can and especially I need to know if it's Ubuntu or my laptop causing me problems.

---

### Post by sikander3786 on 2010-10-24
If Windows 7 and Mac OSX can't recongize it, how can Ubuntu do that?

Obviously, if it is not working on any of the OS, the hardware itself is faulty.

Is the warranty period over?

It might be worthy to check the manufacturer's website for some diagnostic tools and test with them.

I am using Ubuntu now for almost 3 years and it has never burnt my hardware :-) In fact it can't ever.

It might be the laptop's USB port, some problem with the power. I think there was some diagnostic tool for it, I'll search and post if I am able to find it.

---

### Post by plantboy1 on 2010-10-24
I wasn't expecting them to, it was just out of general curiosity that I tried them.  I don't have another system (that's not physically part of my laptop) to test it on to see if it's my hardware.  It just seems to me that it's very unlikely that the drive itself just...died for no reason while it was turned off.  

Having been using Ubuntu for five years, I've never had a problem with it, but hey, stranger things have happened.

---

### Post by coffeecat on 2010-10-24
I'm curious that Gparted doesn't see the drive yet Disk Utility...

> **plantboy1 said:**
> shows a 2.2tb, unformatted drive with a clearly bogus serial number and gives me a "Daemon Inhibited" error if I try to eject it, format it, benchmark it, or anything else.

What do you mean by clearly bogus?

Anyway. Some part of the system must be seeing it if Disk utility sees something. Try plugging it in and posting the output of:

```
dmesg | tail
```and...

```
sudo fdisk -lu
```It could be that the hardware is irretrievably damaged from being dropped, but I wonder if you zero out the partition table that you might be able to do something with it in Gparted.

---

### Post by plantboy1 on 2010-10-24
Being dropped seemed, according to the SMART diagnostic and the fact that it worked fine, to not have had an effect on it other than corrupting the drive.  Worth saying, since I wasn't clear on it before, was that I'd been using the drive for several weeks without a problem after I got and reformatted it.

And by bogus, I mean it told me the serial number was "202020202020202020" (though it went on longer)

> dmesg /dev/sdc | tail
[ 9399.655016] end_request: I/O error, dev sdc, sector 0
[ 9399.655020] Buffer I/O error on device sdc, logical block 0
[ 9399.655026] Buffer I/O error on device sdc, logical block 1
[ 9399.655030] Buffer I/O error on device sdc, logical block 2
[ 9399.656485] sd 15:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9399.656491] sd 15:0:0:0: [sdc] Sense Key : Illegal Request [current] 
[ 9399.656496] Info fld=0x0
[ 9399.656499] sd 15:0:0:0: [sdc] Add. Sense: Logical block address out of range
[ 9399.656505] sd 15:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 9399.656517] end_request: I/O error, dev sdc, sector 0
and fdisk -lu doesn't give me anything on it.  Looking at the dmesg it looks like a FAT problem, but I don't know that much about drives so I could be wrong, so I'll let someone else take that.
The disk doesn't spin up when I plug it into my laptop, which may or may not mean anything, although it used to, but I figure that was because Ubuntu was mounting it.

---

### Post by coffeecat on 2010-10-24
> **plantboy1 said:**
> Being dropped seemed, according to the SMART diagnostic and the fact that it worked fine, to not have had an effect on it other than corrupting the drive.  Worth saying, since I wasn't clear on it before, was that I'd been using the drive for several weeks without a problem after I got and reformatted it.

No, I understood that, but I agree that it is odd to spontaneously autobork itself on the shelf, so to speak.

> **plantboy1 said:**
>  And by bogus, I mean it told me the serial number was "202020202020202020" (though it went on longer)

Got it. I stand to be corrected here, but I believe the serial number would be held in firmware, not on the writable surface of the discs. Which, if I'm right, means something serious has gone awry.

> **plantboy1 said:**
>  and fdisk -lu doesn't give me anything on it.

Worrying. Even with a corrupted or non-existent partition table, it should give something.

> **plantboy1 said:**
>  Looking at the dmesg it looks like a FAT problem, but I don't know that much about drives so I could be wrong, so I'll let someone else take that.
The disk doesn't spin up when I plug it into my laptop, which may or may not mean anything, although it used to, but I figure that was because Ubuntu was mounting it.

It should spin up as soon as it gets power I believe. And that dmesg output looks bad, but I'll happily defer to someone else.

---

### Post by plantboy1 on 2010-10-24
Yeah, nothing seems good about it, something borked while it was on the shelf.  I plugged the drive into a power supply I salvaged from an old computer and it spun up fine as far as I could tell, no clicking or anything like that (unfortunately I don't have a computer that takes SATA drives to test it in- it's what I get for buying old surplus stuff on the cheap).

It seems that it *could* be the enclosure, in which case I can just run out and buy another one relatively cheaply.  I don't have the money for a terabyte drive, so if it's the drive...well...ouch.

---

### Post by coffeecat on 2010-10-24
> **plantboy1 said:**
> It seems that it *could* be the enclosure, in which case I can just run out and buy another one relatively cheaply.

Well - that's a thought and my apologies for not thinking of it.

You mentioned a laptop earlier, but do you have a desktop machine with a spare SATA header on the motherboard? You'd also need another SATA data cable for what I'm going to suggest. Simply remove the suspect drive from the enclosure, open your desktop case and plug the bare drive in to the motherboard. You'll need to find a spare power connector from the power supply as well.

That way you can test the integrity of the bare drive without the enclosure firmware getting in the way. Won't cost you anything either.

---

### Post by plantboy1 on 2010-10-24
Unfortunately no, I can't test it in any of my other computers.  I do have one that will take both SATA and IDE but...there's no SATA cables in it and I don't happen to have any around.

---

### Post by choochoousmc on 2010-10-25
> **plantboy1 said:**
> Unfortunately no, I can't test it in any of my other computers.  I do have one that will take both SATA and IDE but...there's no SATA cables in it and I don't happen to have any around.

Newbie here, to linux, so can't help much. But couple things.
as soon as power is applied it should spin up and the OS should start trying to read it once connected directly to the "sata"  or IDE connector on mother board, once the computer is up and running.

I have a windows machine that has been sitting for several months turned off. Went to turn it on and it reported critical hard drive failure. I suspect a power surge, but doubt it.
More likely the motor is not spinning up. Hey it happens, it's man made and a motor can fail at any time.

One thing I have noticed especially in linux. It doesn't like to operate USB devices through a hub. It prefers a direct connect.  So is the USB drive plugged straight in
to the computer  via the usb port?
I have had a couple usb items Linux / ubuntu refused to recognize properly when I used the hub. Plugged straight in worked fine.

---

### Post by coffeecat on 2010-10-25
> **choochoousmc said:**
> One thing I have noticed especially in linux. It doesn't like to operate USB devices through a hub. It prefers a direct connect.  So is the USB drive plugged straight in
to the computer  via the usb port?
I have had a couple usb items Linux / ubuntu refused to recognize properly when I used the hub. Plugged straight in worked fine.

That's probably a power issue - nothing to do with Linux. USB hubs really need their own power supply to work properly - that's true of any OS. I have no problem with usb hubs in Linux so long as they are powered. But without power I've seen the same problem in Windows, MacOS and Linux.

---

### Post by choochoousmc on 2010-11-27
I know this doesn't help much, but I was wondering what you were doing that you needed a terabyte size drive to start with. Also if the data was that important why buy one you know has been dropped and damaged.
Based on the info.
If the drive is NOT spinning up via the USB cable, then the dmesg info would be flawed.
If it spins up via a external power source then the motor is good.
But the read write heads may not be operating.
This and the non spinup via the USB cable would mean the controller board inside is damaged somehow and it just picked this time to go south.
However, I went to walmart (yuck) and bought a 320 gig compact USB seagate drive for less than $60.
Buying a used hard drive is about as safe as having sex with your significant other with someone else's used condom. somebody is going to be getting a nasty surprise!

---

