---
title: "Copy videos to flash drive doesnt work!"
date: 2009-12-19
forum: General Help
---

### Post by SuperJonny on 2009-12-19
Hello

I have a problem using a flash drive that I have bought recently

Ubuntu is happy to recognise that it is a flash drive, and its happy to read from it, and its happy to try to write to it

However, when copying it doesnt seem to work

Ive got lots of videos and films which Ive tried to copy on there, and it says that they have copied normally, and everything is okay

However when I attempt to play them i get an error message saying that it is unable to establish the type of stream or something along those lines anyway!

And its not because i dont have the correct codecs, cos the originals play just fine!

Ive tried copying to another flash drive and it works

So im confused

The flash drive I am using is a 16 GB sony something or other

I dont know if size comes into these things?

It all worked wonderfully on my 4 GB cheap one from tesco

Andddd it all worked on an XP installation

Anyone got any ideas on this?

---

### Post by audiomick on 2009-12-19
I don't think size is an issue, but "sony" might be. I'm guessing a bit, though.

---

### Post by coffeecat on 2009-12-19
Are the video and film file sizes greater than 4GB? Because the FAT32 filesystem that flash drive is most probably formatted with won't support files greater than 4GB.

---

### Post by SuperJonny on 2009-12-19
Well the files I am copying are mostly around the 175mb area each

So that shouldnt be an issue


If it is the drive itself it is objecting to, is there anything I can do about it?

I was under the impression that flash drives were all pretty much the same...

Evidently not....

---

### Post by joes7 on 2009-12-19
Normal.

---

### Post by SuperJonny on 2009-12-19
> **joes7 said:**
> Normal.

This is normal?

Failure to operate in some form of useful manner is normal?

---

### Post by coffeecat on 2009-12-19
> **SuperJonny said:**
> Well the files I am copying are mostly around the 175mb area each

So that shouldnt be an issue


Agreed.

> **SuperJonny said:**
>  If it is the drive itself it is objecting to, is there anything I can do about it?

I was under the impression that flash drives were all pretty much the same...

Hmmm. That's what I would have thought.

Have you tried copying other types of files to the flash drive? Do they get corrupted? The only other thing I can think of is to reformat the drive in Ubuntu and try again. Does it have some sort of windows utility on it or an odd partition layout? Some USB flash drives do come with some weird and wonderful stuff (for use in Windows), so perhaps a complete reformat might help.

One other thought. Is it formatted exFAT? I know next to nothing about exFAT and whether Linux has good support for it, but we are going to be seeing more of this filesystem on flash drives.

---

### Post by 3rdalbum on 2009-12-19
> **audiomick said:**
> I don't think size is an issue, but "sony" might be. I'm guessing a bit, though.

Guess again. Sony doesn't make flash drive internals, they just repackage Sandisk/Toshiba NAND flash and controllers. What's with the Sony hate?

Is this a flash drive that you've bought off eBay? There's quite a well-known scam that still gets people, where a low-capacity flash drive is modified so it reports a high capacity, and then it gets sold on eBay as a high capacity flash drive.

The data that is supposed to be written after the real capacity of the drive is actually lost.

If you know this drive is legitimate, then you might want to try reformatting it or running an fsck so any bad blocks get flagged.

---

### Post by spiderbatdad on 2009-12-19
Maybe wipe the thing then format.
```
dd if=/dev/zero of=/dev/sdb
This will take some time. Also be absolutlely sure the drive is sdb and not sdc or whatever. Finally:
sudo mkdosfs -F32 /dev/sdb
```

---

### Post by Grenage on 2009-12-19
Agreed; you're best of formatting the drive.  Either the drive hadn't finished writing when it was removed, or it's got some sort of file system issues (possibly some duff sectors and it's not marked them as such).

---

### Post by |{urse on 2009-12-19
Okay. so after months of this very issue causing me problems I happened upon the answer in an old suse linux book.

1)Drag and drop all your videos like normal.
2)Open a terminal and type in this command
```
sync
```
3)Wait for the command to complete then remove your flash drive

Thats it (hopefully)

For some reason the file transfer progress bars are horribly inaccurate with flash drives larger than 4gb. So what is happening is the files seem to have completely transferred when in fact they are still incomplete when the drive is being removed.

Please post back with results.
Hope it helps ^^

---

### Post by 3rdalbum on 2009-12-19
> **spiderbatdad said:**
> Maybe wipe the thing then format to fat16
```
dd if=/dev/zero of=/dev/sdb
This will take some time. Also be absolutlely sure the drive is sdb and not sdc or whatever. Finally:
sudo mkdosfs -F16 /dev/sdb
```

Don't you mean Fat32?

I don't see the point in using Fat16 and being limited to 2GiB of disk space.

---

### Post by SuperJonny on 2009-12-19
It did indeed come from ebay

But yea, i think its okay, I mean it does have 16 GB printed on the side of it?

Ive reformatted it when I tried it in the Windows machine

didnt change anything when I got back to the ubuntu one

The windows machine managed to copy to it fine

I just dont understand what ubuntu sees as being wrong with it?

Where could it possibly be going wrong?

---

### Post by 3rdalbum on 2009-12-19
> **|{urse said:**
> Okay. so after months of this very issue causing me problems I happened upon the answer in an old suse linux book.

1)Drag and drop all your videos like normal.
2)Open a terminal and type in this command
```
sync
```
3)Wait for the command to complete then remove your flash drive

Thats it (hopefully)

For some reason the file transfer progress bars are horribly inaccurate with flash drives larger than 4gb. So what is happening is the files seem to have completely transferred when in fact they are still incomplete when the drive is being removed.

This is wrong on so many levels:

1. In Karmic, the copy progress bar will only disappear when all data has been synced to the destination device. This is a change from earlier versions where the copy operation was reported as complete when the last bytes of the file had been copied into the buffer (but may not have hit the destination device yet).

2. If you right-click the device and choose "Eject", "Unmount" or "Safely Remove", it will make sure that the device is synced before removing its icon from the desktop. If the syncing is going to take a while, you'll recieve a notification on screen that there is still data being written out, and then you'll get another notification when it's safe to remove the drive.

If you're just yanking out the drive without unmounting it first, you're doing it wrong. On any operating system.

3. If you have data going to other disks (for instance, copying between other disks) and you issue "sync", the sync command will only complete when all data is synced to all devices, not just to your flash drive. So typing "sync" is not the best solution - just properly unmount any devices before removing them.

---

### Post by |{urse on 2009-12-19
try issuing the sync command as per my post above im ~90% certain this will fixya, if not then more than likely you need to fsck that badboy.

---

### Post by Grenage on 2009-12-19
> This is wrong on so many levels:

1. In Karmic, the copy progress bar will only disappear when all data has been synced to the destination device. This is a change from earlier versions.

2. If you right-click the device and choose "Eject", "Unmount" or "Safely Remove", it will make sure that the device is synced before removing its icon from the desktop.

If you're just yanking out the drive without unmounting it first, you're doing it wrong. On any operating system.

No it's not.  A sync command can solve problems when the OS borks a transfer.

---

### Post by |{urse on 2009-12-19
> **3rdalbum said:**
> This is wrong on so many levels:

1. In Karmic, the copy progress bar will only disappear when all data has been synced to the destination device. This is a change from earlier versions.

2. If you right-click the device and choose "Eject", "Unmount" or "Safely Remove", it will make sure that the device is synced before removing its icon from the desktop.

If you're just yanking out the drive without unmounting it first, you're doing it wrong. On any operating system.

Yeah, I know all that. Funny thing is this has always fixed this problem for me. Go figure lol :)

1.) The OP never said he was using karmic
2.) If this feature was only just recently implemented, then why is it not worth a try?

Im diggin this 2 supporting arguments stuff ^^

Also a question for the original poster: Do you know how to open the terminal?

---

### Post by SuperJonny on 2009-12-19
Just to make it clear to everyone,

I am using Ubuntu Karmic

And yea

Try not to get majorly technical, cos yea, im not a pro!

ive got some idea of what im doing, some experience using the terminal and such like

I will have a go at this sync thing

And I shall report back as to whether it works or not =]

---

### Post by Grenage on 2009-12-19
I'd format the drive in Karmic first, just to see if that makes the difference.  Sync *shouldn't* be required, but it does help when the computer is being stubborn.

---

### Post by audiomick on 2009-12-19
> **3rdalbum said:**
>  What's with the Sony hate?


Not hate as such. They are a bit too keen for my taste on slick solutions that work great with other sony products, and who cares about the rest of the world. Or, as coffecat put it
> Some USB flash drives do come with some weird and wonderful stuff (for use in Windows)

The machines as such are excellent.

One thing though. Nokia chargers, for example, are practically universal. There's the old one with the bigger plug, and the newer one with the smaller plug.

Sony seems to manage to have a different and unique power supply or charger for every single thing they ever made...:)

---

### Post by |{urse on 2009-12-19
lol.. I have tons of "<3" for sony. If youve ever had to replace the mainboard on a sony laptop, then expletive expletive mother expletive thing, wait... why do i need to take the whole thing apart just to add a sodimm?

Maybe it's just me but purposefully making something convoluted just for the sake of originality (read proprietary) is kind of a step in the opposite direction of linuxy goodness. 

(/me continues to wait to hear back on this flash drive thing)

---

### Post by dcstar on 2009-12-19
> **Grenage said:**
> No it's not.  A sync command can solve problems when the OS borks a transfer.

AFAIK "sync" just tells the OS to send the cached write data to the device. Each device still has its own driver routines designed to do the actual physical writing which are dependant on the hardware (and probably also on the mount options).

It may be dangerous assuming that the generic "sync" command actually forces a write to a USB device.

PS: This may be worth looking at:

[http://elliotli.blogspot.com/2009/01/safely-remove-usb-hard-drive-in-linux.html](http://elliotli.blogspot.com/2009/01/safely-remove-usb-hard-drive-in-linux.html)

---

### Post by Grenage on 2009-12-21
Hi, dcstar.

While I agree that assuming anything is less than ideas, it has always done the job for me.  Cheers for the link.

Russell.

---

