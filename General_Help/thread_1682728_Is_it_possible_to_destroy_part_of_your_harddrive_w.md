---
title: "Is it possible to destroy part of your harddrive with with GParted?"
date: 2011-02-06
forum: General Help
---

### Post by ninjaaron on 2011-02-06
Back when I installed Maverick on this computer, it took a really long time to repartition. The first time it tried, I thought it had stalled (which it might have, but maybe not, in hindsight), so  I forced it to shutdown by holding down the power button.

My before that, my harddrive always registered as 320GB. Now it registers as 298GB. I [FONT="Courier New"]fdisk -l[/FONT] doesn't say anything is broken. it just says the same as everything else: 298GB.

I've done a fresh install since then and completely wiped everything. Still 298GB

What the heck happened to that space, and is there any chance of getting it back? 

(without having to pay, I mean. 300GB should be plenty, but I'd like to get that extra 20 back if it doesn't cost anything.)

I

---

### Post by mcduck on 2011-02-06
Actually sounds just like the difference between the hard disk manufacturer's way of counting space (1000 as multiplier for kilo, mega & giga) and the way computers actually use it (1024 as the multiplier).

320GB = 320000MB = 320000000KB = 320000000000B

while:

320000000000B = 312500000 Kib = 305175 MiB = 298 GiB

..so no, there's nothing wrong. Different programs may use different method when representing disk size to you. And quite often they do that without making any distinction in the same of the unit (so they might use 1024 as multiplier while still using GB as the unit)

---

### Post by ninjaaron on 2011-02-06
This makes loads of sense. I still liked it better when it said 320. :p

Thanks man. Should I mark this as SOLVED even if the problem wasn't real to begin with?

Interestingly, I just tried the Natty alpha 2, and when booting from the USB, it said my HD was 314GB (which is 320 minus the size of the swap partition).

I guess Ubuntu is changing the way it counts too.

I have to admit, 1000 makes a little more sense from a *human* perspective than 1024. I can't really speak for the machines on this issue, though I was under the impression we invented them...

This must have something to do with the number eight... eight bits in a byte... Who the hell thought eight bits in a byte was a good idea anyway? Just make it ten and be done with it!

Sorry, tangent. I don't know anything about this stuff... or, just enough to make me angry, I ought to say.:lolflag:

---

### Post by mcduck on 2011-02-06
Yes, 1000 would make more sense for humans, but computers operate on binary mathematics which makes things a bit different...

And knowing that, the 1000 as multiuplir is just confusing (although it allows hard drive manufacturers to print larger numbers on the drives. You'll just never get that much actual bytes on the drive. :D).

RAM and pretty much everything else is counted the way the computer actually uses it, with 1024 as multiplier. So if you have 1GB of RAM and 1GB of hard drive space, you can't actually write all the data to the drive (even if you ignore stuff like file system overhead etc). Which is why I'd prefer if the stupid 1000-as-multiplier thing would just disappear...

---

### Post by srs5694 on 2011-02-06
> **ninjaaron said:**
> Back when I installed Maverick on this computer, it took a really long time to repartition. The first time it tried, I thought it had stalled (which it might have, but maybe not, in hindsight), so  I forced it to shutdown by holding down the power button.

I know this isn't what you were asking about, but for your benefit and that of anybody else who may read this: ***Don't do that!!!!*** Partition resize operations can take hours to complete and they involve manipulating low-level data structures. Interrupting such operations is ***very very dangerous!!*** It sounds like you were lucky and didn't lose any data, but others who've done what you did have posted panicked pleas for help in recovering their data. If a partition resize operation runs for a day or two without completing, you might have nothing to lose by shutting down; but if it's just been a few hours, don't even think about it.

As a practical matter, I strongly recommend you perform a disk check on whatever volume you were resizing. If this was a Windows partition, you should do this using the Windows disk utilities; tell them to perform a disk check. (I don't recall all the GUI steps to do this, but it can be done with the CHKDSK command, at least from a Windows recovery disk; I'm not sure if CHKDSK will work when you've booted normally.)

> I have to admit, 1000 makes a little more sense from a *human*  perspective than 1024. I can't really speak for the machines on this  issue, though I was under the impression we invented them...

This must have something to do with the number eight... eight bits in a  byte... Who the hell thought eight bits in a byte was a good idea  anyway? Just make it ten and be done with it!

Actually, it's a binary (base 2) issue. Except for some exotic laboratory devices, computers work in binary, since circuits that can take two states (on or off) are easy to construct. A ten-bit value can encode 2^10 = 1024 numbers (0-1023); an 8-bit value can encode 2^8 = 256 numbers (0-255). The number 10 (in the base 10 we humans most commonly use) is not a power of 2, so it and its powers and multiples don't map to binary representations in the neat way we'd like. FWIW, from a mathematical perspective, 10 is a poor number for a base simply because it's the product of just two primes (2 and 5). I've seen arguments that humans should switch to something else, like base 8 (2 * 2 * 2), base 12 (2 * 2 * 3), or base 16 (2 * 2 * 2 * 2). If we were raised from childhood with such a number system, it would seem as natural as base 10 does to us. Of course, we aren't likely to make such a change; base 10 is just far too entrenched in our culture.

The value 1024 (2^10) is as close as we can get to expressing the value 1000 in binary as a simple power of 2, and so in the old days, much of the computer industry appropriated the [SI unit prefixes](http://physics.nist.gov/cuu/Units/) (K, M, and so on) for values that are multiples of 2^10 units. This has caused increasing confusion, though, particularly as common values keep increasing -- the difference between 1024 and 1000 (kilo) is less than the difference between 1,048,576 and 1,000,000 (mega), which in turn is less than the difference between 1,073,741,824 and 1,000,000,000 (giga), and so on. Thus, there's been a move in the past decade to adopt a new set of prefixes for binary units -- kibibytes (KiB), mebibytes (MiB), gibibytes (GiB), and so on now unambiguously denote binary values (2^10, 2^20, 2^30, and so on), leaving the SI prefixes and names to refer to the base-10 values (10^3, 10^6, 10^9, and so on). There's a lot of resistance to this shift, but a lot of software has begun to adopt it, and in the long run, it promotes clarity in communication, so IMHO it's a good idea.

---

### Post by srs5694 on 2011-02-06
> **mcduck said:**
> RAM and pretty much everything else is counted the way the computer actually uses it, with 1024 as multiplier. So if you have 1GB of RAM and 1GB of hard drive space, you can't actually write all the data to the drive (even if you ignore stuff like file system overhead etc). Which is why I'd prefer if the stupid 1000-as-multiplier thing would just disappear...

The "stupid" use of 1000 as a multiplier is the standard in the metric system, which all of the civilized world uses, except for the United States. The misappropriation of metric prefixes by the computer industry is therefore the confusing thing, particularly to people who are well-versed in the metric system. IMHO, the shift to using new prefixes for computer values is the proper solution. If you like, you can stop using the metric prefixes altogether; just add an "i" to everything (like KiB, MiB, etc.) and you'll be set, at least for your own outgoing communication. You'll have to be careful when repeating values that might be expressed in power-of-10 units, though (like when repeating manufacturer disk size claims).

---

### Post by elliotn on 2011-02-06
> **mcduck said:**
> Actually sounds just like the difference between the hard disk manufacturer's way of counting space (1000 as multiplier for kilo, mega & giga) and the way computers actually use it (1024 as the multiplier).

320GB = 320000MB = 320000000KB = 320000000000B

while:

320000000000B = 312500000 Kib = 305175 MiB = 298 GiB

..so no, there's nothing wrong. Different programs may use different method when representing disk size to you. And quite often they do that without making any distinction in the same of the unit (so they might use 1024 as multiplier while still using GB as the unit)

+1 to that

---

### Post by mcduck on 2011-02-06
> **srs5694 said:**
> The "stupid" use of 1000 as a multiplier is the standard in the metric system, which all of the civilized world uses, except for the United States. The misappropriation of metric prefixes by the computer industry is therefore the confusing thing, particularly to people who are well-versed in the metric system. IMHO, the shift to using new prefixes for computer values is the proper solution. If you like, you can stop using the metric prefixes altogether; just add an "i" to everything (like KiB, MiB, etc.) and you'll be set, at least for your own outgoing communication. You'll have to be careful when repeating values that might be expressed in power-of-10 units, though (like when repeating manufacturer disk size claims).

The thing is I prefer counting things as they are used, no matter if the naming scheme fits with the SI standard's prefixes or not. Reality over standards, in my opinion.

The addition of the artificial "Ki", Mi" and "Gi" etc. prefixes didn't serve to reduce confusion about data sizes, quite the opposite. nobody had troubles with the 1024-as-multiplier system (apart from hard drive manufacturers who at some point decided to start using 1000 instead). Now it's causing all kinds of confusion and the prefixes are used pretty randomly and you quite often just have to calculate things yourself to find out which multiplier some program is using. And *still* hard drives are the only devices actually sold with the 1000 as multiplier, even flash drives and SSD drives use 1024... :D

---

### Post by ninjaaron on 2011-02-06
> **srs5694 said:**
> I know this isn't what you were asking about, but for your benefit and that of anybody else who may read this: ***Don't do that!!!!*** Partition resize operations can take hours to complete and they involve manipulating low-level data structures. so I hear. That's why I asked if I destroyed something.

> It sounds like you were lucky and didn't lose any data... I actually lost data, but I was wiping the drive, and it was a new machine, and I backup my stuff on an external HD, and my mission-critical stuff on Ubuntu One. 

> As a practical matter, I strongly recommend you perform a disk check on whatever volume you were resizing. If this was a Windows partition, you should do this using the Windows disk utilities; tell them to perform a disk check.Oh don't you worry, that Windows partition got what was coming to it. :twisted:

---

### Post by ninjaaron on 2011-02-06
> **mcduck said:**
> Yes, 1000 would make more sense for humans, but computers operate on binary mathematics which makes things a bit different...

And knowing that, the 1000 as multiuplir is just confusing (although it allows hard drive manufacturers to print larger numbers on the drives. You'll just never get that much actual bytes on the drive. :D).

RAM and pretty much everything else is counted the way the computer actually uses it, with 1024 as multiplier. So if you have 1GB of RAM and 1GB of hard drive space, you can't actually write all the data to the drive (even if you ignore stuff like file system overhead etc). Which is why I'd prefer if the stupid 1000-as-multiplier thing would just disappear...

Final argument: I have ten fingers. BOOM! Case closed. That's it. (For those taking notes, The sumerians were on some kind of base 60 system, the Mayans I think used base 12, and it appears that in very ancient times some the nordic peoples use a base of eight, though that is a matter of dispute).

Really, I couldn't care less which system they use to count bytes as I'm not going to be the one counting them. I just wish they would come to an agreement about how they are to be counted so I don't get confused.

---

### Post by srs5694 on 2011-02-06
> **mcduck said:**
> The thing is I prefer counting things as they are used, no matter if the naming scheme fits with the SI standard's prefixes or not. Reality over standards, in my opinion.

For many uses of language, I agree; but not for this one, any more than I'd agree with sloppy use of other scientific or technical terms. In those fields, precision of expression is important. When ambiguity or imprecision comes into play, problems happen. Just look at the [Mars Climate Orbiter,](http://en.wikipedia.org/wiki/Mars_Climate_Orbiter) which was lost because of a sloppy mistake over units (metric vs. English measurements, in this case). The previous state in which "K" could mean either 1000 or 1024 (and so on for other units) was imprecise, sloppy, and confusing. Granted, most people aren't at risk of losing expensive interplanetary space probes over this issue, but there are an awful lot of questions posed about it, and there have been for decades....

> The addition of the artificial "Ki", Mi" and "Gi" etc. prefixes didn't serve to reduce confusion about data sizes, quite the opposite. nobody had troubles with the 1024-as-multiplier system (apart from hard drive manufacturers who at some point decided to start using 1000 instead).

ROTFL! I was fielding questions from people confused about this issue in the 1980s and 1990s, before the new prefixes came out! I admit that the new prefixes are causing some additional short-term confusion; but in the long run, we're better off with them than without them. At least if somebody uses one of the new prefixes (and uses it properly, of course), you'll know what's meant. Right now we're slogging through a period where the traditional SI prefixes are sometimes being used correctly and sometimes being abused. That will settle down eventually, though, and we'll be better off for it.

> Now it's causing all kinds of confusion and the prefixes are used pretty randomly and you quite often just have to calculate things yourself to find out which multiplier some program is using. And *still* hard drives are the only devices actually sold with the 1000 as multiplier, even flash drives and SSD drives use 1024... :D

All my USB flash drives use the SI units properly; for instance, check out a "16 GB" flash drive I've got:

```
$ **sudo fdisk -l /dev/sdb**
Disk /dev/sdb: 16.2 GB, 16166944768 bytes

```

Note I've edited the output for brevity. The point is that it's 16,166,944,768 bytes, 16.2 GB, or 15.1 GiB. All the major Linux partitioning tools (GNU Parted, GParted, fdisk, and gdisk) use the units correctly, although they use different units -- GNU Parted and fdisk use power-of-10 units, while GParted and gdisk use power-of-2 units.

Memory (RAM) manufacturers are still mis-using the SI units for power-of-2 values, at least judging by some quick checks I did on the Web.

---

### Post by srs5694 on 2011-02-06
> **ninjaaron said:**
> so I hear. That's why I asked if I destroyed something.

There's destruction of data and then there's destruction of hardware. It's very difficult to destroy hardware with software. A couple decades ago, it was possible to destroy a monitor by feeding it an improper signal; but modern monitors all include circuitry to prevent that. Overclocking (a software setting, but one set in the BIOS, not the OS) can destroy a CPU if done too aggressively. Other than that, I can't think of any examples of software destroying hardware, although it might be possible to destroy a hard disk by triggering excessive head movements. That would take a long time to do any damage, though. Certainly editing a partition table, even improperly, won't destroy the disk or reduce its true capacity.

Destruction of data, of course, is another matter, but in the case of something like "losing" disk capacity, it would be easily undone. If your disk had been reduced in capacity, it would probably be because a partition was resized. You could then easily resize the partition back to its original size, although in some cases you might need to create a new partition to do this. The point, though, is that the change would not be permanent; if you're willing to pay the cost (in backup/restore operations, time, or whatever), you could get the space back.

---

### Post by ninjaaron on 2011-02-07
Ah! This was the answer I was looking for. So, I can interrupt partitioning operations all day long and my drive will be none the worse for it.

Good to know.

I think I agree with you about this KiB vs. KB thing.  Kilo meant one-thousand long before computers existed, and I don't guess there is any good reason to misuse it like that. As for Kibi, well if someone tells me that it means 1024, I guess that's alright with me.

Stupid thing is that Nautilus uses GB when it means GiB. Ah well.

---

### Post by cascade9 on 2011-02-08
> **srs5694 said:**
> Memory (RAM) manufacturers are still mis-using the SI units for power-of-2 values, at least judging by some quick checks I did on the Web.

JEDEC still goes by 'common usage', not SI. IIRC the cache on CPUs is still measured in binary powers as well. 

BTW, I generally agree with mcduck on this issue. I can see why they changed it, but IMO it went far to much to the benefit of the HDD manufactuers and did not clear up any confusion.

A much fairer way would have been to contiune to use binary powers for KB, MB, GB, etc but change the meaning to kibibyte, mibibyte, gibibyte, etc. and have KiB/kilobyte, MiB/megabyte, GiB/gigabyte mean SI units.

---

### Post by mcduck on 2011-02-08
> **cascade9 said:**
> JEDEC still goes by 'common usage', not SI. IIRC the cache on CPUs is still measured in binary powers as well. 

BTW, I generally agree with mcduck on this issue. I can see why they changed it, but IMO it went far to much to the benefit of the HDD manufactuers and did not clear up any confusion.

A much fairer way would have been to contiune to use binary powers for KB, MB, GB, etc but change the meaning to kibibyte, mibibyte, gibibyte, etc. and have KiB/kilobyte, MiB/megabyte, GiB/gigabyte mean SI units.

I think that would be even more confusing thatn the current situation... :)

What I'd prefer, and what would be simple as well, would be just using the 1024 for everything when it comes to computers, even for the hard drive space (that's how it was, I remember the 1000-as-muliplier thing first appearing around the time when hard drives reached gigabytes of size. I still have one of my old hard drives from time before that, label telling that it's "128MB / 134217728 Bytes". :))

Single unit, and the only thing to explain to anybody is that when it comes to computers, use 1024 as multiplier instead of 1000. Instead of having to deal with two different units that are misused and mixed all the time, and one of them doesn't even fit with the way how the computers actually work... :D)

(btw, you are correct, cache is measured with proper binary sizes, it's how it's built and you'll always end with cache size that's base-2, never base-10. Same as with RAM and Flash memory chips, bus widths, even the cache on the hard drives themselves, or really anything directly related to how computers work.)

---

### Post by Skaperen on 2011-02-08
> **srs5694 said:**
> Memory (RAM) manufacturers are still mis-using the SI units for power-of-2 values, at least judging by some quick checks I did on the Web.
Whether to use k=1000 or k=1024 depends on the context.  For most things, including disk drives, k=1000 is appropriate.  RAM is one of the exceptions.  For RAM, 16k is 16384, not 16000, and 16G is 17179869184, not 16000000000.

As for those newfangled suffixes, I've yet to see a proper authority standardizing them with the appropriate input, feedback, and discussion cycles.

---

### Post by mcduck on 2011-02-09
> **Skaperen said:**
> Whether to use k=1000 or k=1024 depends on the context.  For most things, including disk drives, k=1000 is appropriate.  RAM is one of the exceptions.  For RAM, 16k is 16384, not 16000, and 16G is 17179869184, not 16000000000.

As for those newfangled suffixes, I've yet to see a proper authority standardizing them with the appropriate input, feedback, and discussion cycles.

Yet, if you have a file that is 1kB in size in RAM (as RAM is measured), and you write it to disk, the same file would now have size of 1,024kB (as hard drive space is measured). How does that make sense?

And unless you invent a whole new way how computers could work, completely different from anything we have this far, you *can't* change the fact that RAM and everything else are in base-2, so the only place where this can be simplified is the measurement of hard drive space...

Well, anyway. This is getting a bit off topic. And it's probably never going to change into any sensible system anyway so I guess I'll just have to live with the way hard drive space is counted these days. And keep on explaining it to all the people who are wondering where a fair amount of their drive space "disappeared"... :D

---

### Post by cascade9 on 2011-02-09
> **mcduck said:**
> I think that would be even more confusing thatn the current situation... :smile:

What I'd prefer, and what would be simple as well, would be just using the 1024 for everything when it comes to computers, even for the hard drive space (that's how it was, I remember the 1000-as-muliplier thing first appearing around the time when hard drives reached gigabytes of size. I still have one of my old hard drives from time before that, label telling that it's "128MB / 134217728 Bytes". :smile:)

I think I need to spell out just how cunning my plan was. :lolflag: 

Some of the details here may well be wrong, hopefully srs5694 will correct me on detail if I am. (I'm serious, I'd actually like to know)

The 'problem' is/was that Systeme International d'unities had defined 'kilo' as '1000', etc. So when one of the HDD manufacturers got taken to court over the whole 1000/1024 issue, they just used the SI units as a defence. .....So we end up with HDD manufacturers saying 'kB = kilobyte, kilo = 1000, so a kilobyte = 1000'. The memory manufactuers stick with kilo = 1024 due to common useage (and common sense IMO). Basicly, the HDD manufcuters want to keep using kB, MB, GB, etc as 1000, and think that memory should by KiB, MiB, GiB. Or possibly they are silly enough to think that we should be buying 2.148 GB RAM sticks.....

If you kept the current 'common use' meaning for kB, etc, then the HDD manufacturers who want a 'bigger number' would have to label HDDs as KiB, etc, and people can see the difference. IMO in the end you would see HDDs sold in 'real', binary sizes. KiB would be an amusing technicality, and would drop from use. 

Mind you the HDD manufacturers would possible move to labeling HDDs as 'gigabyte' not GB so maybe it wouldn't work. :S 

I agree 100% mcduck, as far as I'm concerned things that work in binary should use base-2 measurements, not base-10. 

> **Skaperen said:**
> As for those newfangled suffixes, I've yet to see a proper authority standardizing them with the appropriate input, feedback, and discussion cycles.

As far as Systeme International d'unities is concerned, kilo = 1000. kB = kilobytre, so 1kB = 1000 bytes. End of story. 

The actual naming for the 'new' naming might be open, but only that (and IIRC SI think that they have the right to give new names, new sufixes, etc)

---

### Post by srs5694 on 2011-02-09
> **Skaperen said:**
> As for those newfangled suffixes, I've yet to see a proper authority standardizing them with the appropriate input, feedback, and discussion cycles.

There's [IEEE-1541.](http://en.wikipedia.org/wiki/IEEE_1541)

It appears to me that the people who maintain the standards for such things are pretty well settled on this. At the moment, it's RAM manufacturers and common usage in the computer industry that are the holdouts against a properly defined standard. Common usage is starting to change, at least judging by changes to software I've seen in the last few years; more programs are explicitly supporting the IEEE-1541 units and/or are using the SI units exclusively for power-of-10 values. This isn't yet universal, of course, but the trend is in that direction.

---

