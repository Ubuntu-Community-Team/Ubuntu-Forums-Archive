---
title: "Is it pretty safe to hard power down (hold power button or pull plug) often?"
date: 2010-10-07
forum: General Help
---

### Post by NDLunchbox on 2010-10-07
So I'm using Ubuntu minimal and LXDE installed on a USB flash drive in an appliance setting (digital picture frame made out of old laptop parts).  I don't want to always have to put a mouse on it just to shut it down.  Is it fairly safe just to regularly hard power-down or just pull the plug?

Remember, this is a static appliance, so I'm not worried about data-loss (it just cycles pictures in a folder) - just stability.

We have a few linux based hardware appliances here and in remote offices that regularly get shutdown that way and are always rock solid (riverbed, Juniper / netscreen (though I think they're BSD based) products, etc.) - is there anything special they do to get them that way?

---

### Post by HPD2 on 2010-10-07
I wouldn't recommend it, its a good way to loose data due to corruption. If it corrupted a system folder then your stability will be affected.

---

### Post by cgroza on 2010-10-07
If the system is writing something to the hard disk when you do this the file system might get corrupted.

---

### Post by Rasa1111 on 2010-10-07
I also wouldnt recommend it,
but if you have to you have to.
I used to have to sometimes, (mostly when i had windohs]
and a few times in Ubuntu,  before i learned the "magic keys".
Now I never have to use it, now that im on 10.10, 
but, 
alt+prt scr+ REISUB will safely restart it, 
and alt+prt scr + REISUO will safely shut the machine down. 

I learned it here~
**_[COLOR="Red"][read first][/COLOR]_**
[http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

 n00bs be safe*(that's what i was told by a mod when i mentioned it once]. lol

  after karmic kept freezing on me.. 
I got pretty good at these magic keys... :lol:
Had to do it in Lucid sometimes to..
never in 10.10 yet though. :)

[I] OH Wait~ digital picture frame?
no keyboard then....  lol[/I]

  mybad. idunno what's goin' on. :lol:
please disregard. lol O_o

---

### Post by Quackers on 2010-10-07
That's useful Rasa1111, I've made a note. I suspect that I may need 3 hands to use it though :-(

---

### Post by Rasa1111 on 2010-10-07
> **Quackers said:**
> That's useful Rasa1111, I've made a note. I suspect that I may need 3 hands to use it though :-(

lol, Yeah works well if you need it.
I thought i was going to need 3 hands to at first. 

 The first handful of times I did it, i just did it really slow, and made sure to hit all keys in right order..
and I always 'worked it out in my head' beforehand, so i knew where my fingers would best work. :lol:

 after a few times though i got used to it and it was very easy.
[had to do it like 5x a day sometimes] haha. :lolflag:

 But i think the OP can't use this suggestion.. lol

 hope it helps ya, just go slow and breatheee the first few times.. lol ;)

---

### Post by JBAlaska on 2010-10-07
It's easy if you use your tongue on the alt key :P

---

### Post by Rasa1111 on 2010-10-07
> **JBAlaska said:**
> It's easy if you use your tongue on the alt key :P

haha. :P

luckily it didn't come down to that. lol

lets see, here's how I do it...

_Right hand>_  Thumb on **Alt** , Middle finger on **Prt Scr** *[hold in both]*

_Left hand<_ index finger on **R** [hold like 2-3 secs.]
then let go and press **E** [with middle finger, hold for like 2-3  secs], 
then index finger to **I ** (it's a stretch)[hold 2-3 secs],
then pinky finger to **S** [hold 2-3 secs]
then index finger presses **U** [holds for 2-4 secs]
then thumb to **B** [holds for like a second or two], 
and then let go of B, Alt, and Prt Scr at the same time.

 Then it restarts properly.

 But, if you just want a shutdown, 
Instead of pressing **B** at the end, you press **O**

---

### Post by NDLunchbox on 2010-10-07
> **HPD2 said:**
> I wouldn't recommend it, its a good way to loose data due to corruption. If it corrupted a system folder then your stability will be affected.


Is there something that regularly writes system data that I can change / disable?

It's EXT4, so wouldn't journaling eliminate that?  I thought on journaled file systems like EXT and NTFS you only had to worry about data that was sent to the drive's on-board cache (so the O/S committed the write) but had not yet actually been written to disk... a rare occurrence outside of servers - which is why they have battery (or now Flash) backed write caches.  Non committed writes would be fixed during an FS check at next boot.

...BUT, I'm not using a hard disk, rather a USB flash drive - so no cache to worry about.

None of this would be an issue if I could get the power button to shutdown the system gracefully (ACPI I guess), but I press it now and nothing happens.  :confused:

I think, for the sake of the boards, I'll test this out and report back after a month!  We can get Vegas to post odds and start betting...

---

### Post by srs5694 on 2010-10-08
A journal just speeds up the disk check times when you abuse the filesystem by shutting it down improperly; it doesn't protect against data loss that might be caused by data being cached in memory at the time the plug is pulled.

The best thing you can do to minimize the risk of data loss in situations like appliances is to partition the disk so that as much of the data as possible is on partition(s) that can be mounted read-only. For instance, split off /usr and /home and mount them both read-only, except when you need to modify them. You can also keep some partitions regularly unmounted. For instance, /boot doesn't normally need to be mounted; you only need to mount it when you upgrade your kernel or mess with the boot loader configuration.

There are probably HOWTOs and forums dedicated to embedded Linux where you can get more knowledgeable advice on this question. There may be filesystem choices, mount options, package selections, and other system settings that can help reduce the odds of problems.

---

### Post by whoop on 2010-10-08
I've got a headless server with a network card (Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 20)) that occasionally stops working ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545334](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545334)) 

I shut that one down a couple of times via pressing and holding the power button. Nothing went wrong...

---

