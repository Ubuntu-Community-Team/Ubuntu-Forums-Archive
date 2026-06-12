---
title: "SSD not booting on Ubuntu 9.10"
date: 2009-11-05
forum: General Help
---

### Post by lajo01 on 2009-11-05
Hi,
I have installed 9.10 using a SSD disk as root drive and done a few extra installations to build a file server (RAID card with lots of storage).
Now all of a sudden the system will not boot of the SSD, it stops immediately after the hardware checking is done during boot sequence.

However, when I boot of the Live CD and choose "Boot from first hard drive" the system continues to boot off the SSD as if nothing has happened and the system comes up as it should.

Checking the /dev/sda (boot) partition with fsck everything is ok, it is flagged as bootable and so on, but will not boot.

Anyone got any suggestions?

Thanks!

---

### Post by Giblet5 on 2009-11-05
Grub is probably hosed.

```
sudo update-grub
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

should fix you right up.

---

### Post by P4man on 2009-11-05
A much as I admire clever little bash scripts like that one, it might not be very easy to type in situations where you cant copy paste from this website.
```

sudo grub-install /dev/sd[COLOR="Red"]x[/COLOR]
where x is your boot drive
```

is probably less prone to typo's.

---

### Post by lajo01 on 2009-11-05
Thanks for your advice. 
Since your posts pointed me in the direction of grub, I learned that there apperas to be a serious bug in the new grub2, this is probably what has happened here as well....?

---

### Post by Giblet5 on 2009-11-05
> **lajo01 said:**
> Thanks for your advice. 
Since your posts pointed me in the direction of grub, I learned that there apperas to be a serious bug in the new grub2, this is probably what has happened here as well....?

Could be. Probably isn't.

To find if reinstalling the MBR will work, try it.
 - Napoleon Bonaparte's IT guy

---

### Post by P4man on 2009-11-05
> **lajo01 said:**
> Thanks for your advice. 
Since your posts pointed me in the direction of grub, I learned that there apperas to be a serious bug in the new grub2, this is probably what has happened here as well....?

Im only aware of a grub bug that arises if you do an upgrade jaunty > karnic **and** you have a seperate /boot partition, in which case grub gets confused it seems, and needs another grub-update

Actually what you are having is kind of weird, rereading it. Booting the first harddrive using the live cd.. would pretty much be the same as doing it  without lievcd. I could be wrong, but I dont see the difference. In both cases grub (including stage 1 on the mbr) should be booted from the ssd. I think

Is it possible you have simply misconfigured your bios to boot from the wrong device? Or that the ssd takes longer to become ready (although you'd expect the exact opposite)

---

### Post by Giblet5 on 2009-11-05
20 minutes of chirruping crickets makes me think the MBR was the problem.

---

### Post by P4man on 2009-11-05
> **Giblet5 said:**
> 20 minutes of chirruping crickets makes me think the MBR was the problem.

Id try the same solution as you, but im wondering if you boot from a livecd, and tell it to boot the first hdd, does it not need the hdd MBR just as well?

---

### Post by Giblet5 on 2009-11-05
> **P4man said:**
> Id try the same solution as you, but im wondering if you boot from a livecd, and tell it to boot the first hdd, does it not need the hdd MBR just as well?

I haven't looked at what it actually *does* when you select that.

It's unlikely that it does the same thing that BIOS does, else OP would see the same behavior either way.

This might be a SATA controller BIOS setup thing. IDE vs AHCI.

---

### Post by lajo01 on 2009-11-06
Giblet5 & P4man,
Thanks for sharing your ideas with me! :)
I tried updating/reinstalling grub as suggested, but that didn't change anything.
Also tried the workaround for the grub bug, still no sunshine.

So I'm inclined to believe that the system doesn't even get as far as grub, i.e. it doesn't see the SSD drive at all.... Booting via LiveCD bypases this problem by pointing to CD/DVD device, from which I then point back to the SSD where grub continues to load Ubuntu (at record speed which is very enjoyable to watch... :) )

So the idea about IDE vs AHCI, where do I see what the current setting is and how to change? I checked the BIOS settings on start-up (press-delete-key), but didn't see any settings about AHCI....

---

### Post by P4man on 2009-11-06
I guess this is were you give us a bit more information.

If you try to boot the ssd (no cd in the drive) what exactly is happening?
How do you make it boot from ssd, using an F11 bios boot menu, or by setting the ssd drive as first boot device in bios settings (presumably accessed through F12 on your machine) ?

Can you try both approaches?

You mention a raid controller. is the ssd connected to the oboard sata controller or to the raid controller card ?

---

### Post by lajo01 on 2009-11-06
OK, so now I found the SATA settings, they were IDE. 
I changed them to AHCI and now the SSD drive was actually found by the system, grub was loaded and Ubuntu starts to load. But now it hangs showing the Ubuntu logo, normally Ubunto loads in <10 sec, now it stops.

Is there a way to boot Ubuntu showing the logs on-screen?

(Also having set SATA to AHCI, I'm now unable to load from CD, which is also a connected on the SATA bus....)

Some additional info,
The approach in this post (when hanging) was having the SSD on the local controller. 

The workaround when booting via Live CD the SSD was on the RAID card. This still works when changing back to IDE on the onboard SATA for the CD to work.

---

### Post by P4man on 2009-11-06
> **lajo01 said:**
> OK, so now I found the SATA settings, they were IDE. 
I changed them to AHCI and now the SSD drive was actually found by the system, grub was loaded and Ubuntu starts to load. 


Many people have trouble with AHCI enabled, so its kinda annoying you'd have to enable it to boot from the ssd :s

To view ubuntu's output during the boot process, go in the grub menu and edit (press E)  the kernel line and remove the "quiet" and "splash" options. This will only apply for that boot, its not persistent.

---

### Post by lajo01 on 2009-11-06
Now some more attempts.
Disconnected the CD and Raid disks, only SSD connected on local SATA bus.

Booting on AHCI, again hangs after Ubuntu has initiated loading and the circular logo is shown.
Booting on IDE, hangs after grub, screen fills with errormessages after a while.

Starting to think either my SSD is fishy or my Ununtu installation is corrupt, either way it shouldn't load through the Live CD if that was the case.....

Maybe I should just skip the SSD and re-install Ubuntu on a separate partition of the RAID array....

---

### Post by blackSP on 2009-11-06
Comment removed as it was not relevant

---

### Post by P4man on 2009-11-06
> **lajo01 said:**
> Now some more attempts.
Disconnected the CD and Raid disks, only SSD connected on local SATA bus.

Booting on AHCI, again hangs after Ubuntu has initiated loading and the circular logo is shown.
Booting on IDE, hangs after grub, screen fills with errormessages after a while.

Try having some patience. Ive seen ubuntu generate errors something with error reading block on device sr0 or something, but after a minute or so it boots perfectly. its annoying if you boot frequently but give it a try. IIRC I had this on one USB stick and then only when my cdrom drive was configured as 2nd or 3rd boot device in the BIOS. It made absolutely no sense whatsoever but removing the cdrom as boot device (even as third boot device despite booting from the first, being USB) made it go away.

Either way I would post a bug report because I think the information it boots fine with a livecd grub "kickstart" could be revealing.

> Starting to think either my SSD is fishy or my Ununtu installation is corrupt, either way it shouldn't load through the Live CD if that was the case.....

Exactly. Plus the only thing that could be different is using or not the MBR, and since it does seem to read the MBR when booting straight from SSD, its something.. weird.

---

### Post by Giblet5 on 2009-11-06
This seems like a good time to interject some old-timey, down-home, NAND flash wisdom:

SSD disk drives will fail more frequently than mechanical disks.

It doesn't matter how terrific the SSD's randomized-write logic is; that drive will fail faster than a mechanical drive.

IMO, it's a mistake to use them for any critical (or even important) purposes until the reliability of the devices approaches that of conventional hard disk technology (eg, 20,000+ hour MTBF). SSDs aren't there yet.

---

### Post by P4man on 2009-11-06
> **Giblet5 said:**
> 
SSD disk drives will fail more frequently than mechanical disks.

Thats no longer true. Quite the opposite. SSDs are making headway into the server market *because* of their reliability.SLC drives can sustain 1M write cycles these days. Add to that write buffering and wear levelling, and you can imagine it takes a while to reach that.. 

You can actually calculate how long it will take to kill an SSD under the worst of circumstances.

Lets assume a 100GB SSD that can do 100MB/s writes. Worst case scenario for an SSD is nonstop sequential writes filling the drive and starting over (rendering wear levelling and buffering useless). One write cycle takes 10000 seconds or about 16 minutes. Doing that 1M times equals ..
~32 years. 

That is assuming the 1m write cycles is achieved, but there are also spares in case some cells dont. And in the real world, nonstop 100MB/s sequential writes around the clock are not exactly the most common scenario. 30 year old machines are pretty rare too.

SSDs drives (especially SLC variant) absolute rock when it comes to longevity, despite common perception.

---

### Post by lajo01 on 2009-11-07
To close this sad chapter of my life.
Last night, as the rest of the family were in bed, I decided to re-install Ubuntu from scratch (Friday-night-fun... :rolleyes:). 
Removed RAID card, changed to an IDE CD/DVD and set the SATA bus on AHCI mode.
The Ubuntu installation was unable to complete, failed to write the grub config, but the file copying up yutil that stage was swift. 
It also behaved very strage, taking more than two minutes to scan the disc before loading partitioner.

Trying the same operation with SATA set to IDE, gave roughly the same result.

My conclusion from this is that there apperas to be difficulties reading from the SSD, but writing to it is ok.

Unless someone out there on this forum has any other ideas, I will return the SSD as faulty and claim a new one. (Btw it is a new and modern SSD, Corsair X32, not the old stuff.)

---

### Post by P4man on 2009-11-07
Not sure if this was already mentioned or not, but did you check for a bios update for your mb and your raid controller?

---

### Post by lajo01 on 2009-11-09
Updated (I actually don't know what version I was on) the mobo bios to the latest one, but the problem remains. 
I was actually able to install Ubuntu successfully by first "Try Ubuntu before installing..." and from there installing it onto the SSD. 
But still Ubuntu will not boot, "error reading device, device timeout" etc appears after GRUB has initiated.

I'll try installing from another PC I have which also has a Gigabyte mobo, to see if that works....

---

### Post by lajo01 on 2009-11-10
The saga continues, it has dawned on me that I've been misled by a "double-fault".
Fault 1, the SSD will not work very well with my mobo, that's all too obvioius.
Fault 2, the SSD will not boot (load GRUB) when booted from Raid card (see the post about booting from Live CD).

So last night I installed Ubuntu on one of my Raid arrays, a 1 TB raid-1 mirror. I created a boot volume and installed Ubuntu (becoming an expert on that installation.....)

And, lo and behold, GRUB will not load from the raid mirror either, i.e. Fault-1 had nothing to do with the fact that it was a SSD drive.

Question now is, the GRUB config that is generated automatically during installation doesn't seem to work very well with the drives connected through the (3ware 9590SE 16 port) Raid card, what do I need to change...?

---

### Post by P4man on 2009-11-10
I think the problem is grub can not see the raid controller, it has no driver for it. You'll have to make a sperate boot partition and put grub on that, on a sata drive not attached to the raid. At least thats my guess. The ubuntu kernel does have support for your card so should be able to boot from it, but only after grub loaded. 

Grub has 2 stages. The first one is the MBR, the second one by default sits on a folder in your root partition (/boot/grub). Have a look here how to set up a boot partition:
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

---

### Post by lajo01 on 2009-11-10
Grub finds the RAID card. 
I just Googled the problem and it has been known for a long time for lots of different Linux flavours using GRUB and 3ware RAID connected disks.

Grub is mixed up in its configuration pointing to the boot device on the RADI card.
Need to do some experimenting, will also contact 3ware support to get advice.

---

