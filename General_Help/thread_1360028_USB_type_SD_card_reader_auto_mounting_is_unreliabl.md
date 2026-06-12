---
title: "USB type SD card reader auto mounting is unreliable"
date: 2009-12-20
forum: General Help
---

### Post by tedrogers on 2009-12-20
Hi all,

I have a generic USB multi card reader from China that I purchased from a well know auction website, and it works fine - when I can get it to mount that is!

It takes several minutes of plugging, unplugging, attaching the card reader first before inserting the card, detaching it again,  then attaching the card reader with the card already in etc. before I can get it to auto mount.

There doesn't seem to be a pattern to it - blind luck seems the only way.

Now, I don't believe in luck, so there has to be a logical answer to this.

I don't know enough about this sort of thing to self diagnose and wondered if anyone can assist?

Thanks (and seasons greetings!)

---

### Post by joeknoodle on 2009-12-20
> **tedrogers said:**
> Hi all,

I have a generic USB multi card reader from China that I purchased from a well know auction website, and it works fine - when I can get it to mount that is!

It takes several minutes of plugging, unplugging, attaching the card reader first before inserting the card, detaching it again,  then attaching the card reader with the card already in etc. before I can get it to auto mount.

There doesn't seem to be a pattern to it - blind luck seems the only way.

Now, I don't believe in luck, so there has to be a logical answer to this.

I don't know enough about this sort of thing to self diagnose and wondered if anyone can assist?

Thanks (and seasons greetings!)
Maybe not much help, but make sure you use the unmount feature before unplugging it. I went for a long time goofing this part up and experienced the same symptoms.

---

### Post by TheOnlyMrK on 2009-12-20
I have this same problem and it's very annoying. I have to plug in my memory card(s) into the reader before I plug it into the computer otherwise it won't detect them, and as for my cellphone it will never be detected because I have to plug it into the USB port, wait for the menu on my phone to come up asking if I want to use it as a mass storage device and click yes, which is basically the same as plugging in a memory card reader before the memory card is inserted.
I hope someone can find a fix to this...

---

### Post by tedrogers on 2009-12-20
Well, glad to know it's not only me! :)

I always do use the proper unmounting procedure...so this can't be the cause.

I also hope someone has a fix, I use my SD card with my beloved Ubuntu all the time!

Fingers crossed guys.

---

### Post by TheOnlyMrK on 2009-12-20
> **tedrogers said:**
> Well, glad to know it's not only me! :)

I always do use the proper unmounting procedure...so this can't be the cause.

I also hope someone has a fix, I use my SD card with my beloved Ubuntu all the time!

Fingers crossed guys.

I used to use Bluetooth, then that stopped working so I tried the USB cable for my phone figuring it's faster any ways, that never worked so I dug up my memory card reader, now I'm in the same position as you. Lol.

---

### Post by tedrogers on 2009-12-20
Well, generally everything works well for me except this. Bluetooth is fine, Wireless is fine...just this card reader annoyance.

And guess what? Works fine in Win(blows)!

Come on Ubuntu!

---

### Post by VeeDubb on 2009-12-20
> **tedrogers said:**
> Hi all,

I have a generic USB multi card reader from China that I purchased from a well know auction website......



That's your real problem, end of story.

Card readers are VERY inexpensive, and you can get a good solid name-brand one from newegg for $10-$25.  I have one that is mounted in a 3.5" bay in my case and plugs into the on-board USB connectors on my motherboard.  

It's the second one of them I have owned, both made by Rosewill, and I have never had any problems with either, even under ultra-high usage.  The only reason I bought a second one, was that I bought the first one before SDHC came out, and later bought a camera that uses SDHC memory cards.

---

### Post by TheOnlyMrK on 2009-12-20
> **VeeDubb said:**
> That's your real problem, end of story.

Card readers are VERY inexpensive, and you can get a good solid name-brand one from newegg for $10-$25.  I have one that is mounted in a 3.5" bay in my case and plugs into the on-board USB connectors on my motherboard.  

It's the second one of them I have owned, both made by Rosewill, and I have never had any problems with either, even under ultra-high usage.  The only reason I bought a second one, was that I bought the first one before SDHC came out, and later bought a camera that uses SDHC memory cards.

Then why would I have the same problem when I have a SanDisk brand card reader? Which in my personal opinion is the best company when it comes to flash memory and anything related to it.

---

### Post by tedrogers on 2009-12-20
Yes I agree.

I think the problem must be that it is externally USB wired, although I don't know why / how this would *any* difference to an internal USB connection.

---

### Post by TheOnlyMrK on 2009-12-20
> **tedrogers said:**
> Yes I agree.

I think the problem must be that it is externally USB wired, although I don't know why / how this would *any* difference to an internal USB connection.

I'm wondering if it only happens when the memory card reader is plugged in after the system is started since "VeeDubb" has a USB reader and it's plugged in 24/7 and his always works. I'm about to test to see if it will read the memory card if the reader is left in.

Also, the only difference in external and internal USB is the plug itself, nothing else.

---

### Post by tedrogers on 2009-12-21
Well for a while there I though you had hit on something there, but it's not perfect yet and still quite random.

Sometimes if I reboot with my SD reader inserted, then once logged into Ubuntu I proceed to slot my card in...lovely jubbly - card mounts no problems. But it is still unreliable overall.

I also tried logging in and out in the hope that it would force it to check the USB port for the reader...but this did not work. :(

One reliable way is to manually mount, but this is untidy as it puts everything in the /media mount point:

```
sudo mount /dev/sdb1 /media
```

I've been looking into pmount as well, but so far with mixed success. It seems like it would be more helpful as it makes a mount point for you, so you don't need to bother with fstab.

You can try too if you like. First make sure your repo's are up to date and install pmount:

```
sudo apt-get update
sudo apt-get install pmount
```

Then to mount (note for ANY_NAME - I use "sd"):

```
pmount /dev/sdb1 ANY_NAME
```

It should mount on the desktop, keep trying if it doesn't. 

And to umount:

```
pumount ANY_NAME
```

My two real life examples would be:

```
pmount /dev/sdb1 sd          <<< TO MOUNT
pumount sd                   <<< TO UNMOUNT
```

Like I said I had mixed success with this too...but hope this helps until there is something more reliable.

Let me know if it works or doesn't. 

Thanks.

---

### Post by tedrogers on 2009-12-26
Did any of you have much success with this pmount idea at all?

This problem is still annoying the hell out of me.

---

### Post by TheOnlyMrK on 2009-12-26
> **tedrogers said:**
> Did any of you have much success with this pmount idea at all?

This problem is still annoying the hell out of me.

Sorry, I haven't been able to try it since I've been busy trying to figure out another problem with my computer, I've been using my memory card reader lately and for some reason it's just stopped having problems and works fine now. I even just tested it with two different memory cards to make sure and no problems. Was an update released to fix this that anyone knows of or am I just having weird good luck?

---

### Post by tedrogers on 2009-12-27
I've had moments like this....but then its all gone wrong the next time.

I reformatted my card on a win(blows) machine, and it worked and mounted repeatedly like a dream in Ubuntu...next day it was back to the usual nonsense! :(

---

### Post by tedrogers on 2010-01-02
Has anyone had any more joy with finding a more reliable solution to this problem that just ramming the SD card in and out of the reader until it mounts by accident! :)

---

### Post by NoozeHound on 2011-08-17
pmount /dev/sdb1 SD
Error: device /dev/sdb1 is not removable

Doesn't work for me :(

---

