---
title: "Permanently deleting all data on a hard drive"
date: 2009-09-23
forum: General Help
---

### Post by jsvidyad on 2009-09-23
Hi!!

     I recently had my hard drive replaced as the old drive was giving errors while trying to boot ubuntu. I have to return the old hard drive to Dell. If I don't do that, I will have to pay for the new hard drive. But, before returning it, I want to delete all the data on the hard drive in a way such that it can't be recovered.

   Does anyone have any ideas on how to do this??

         Thank You in advance.

---

### Post by Joshua Lückers on 2009-09-23
Try to mount it and use gParted and format it a few times (they say doing it 30times is the safest way).

---

### Post by wojox on 2009-09-23
DBAN: [http://www.dban.org/](http://www.dban.org/)

---

### Post by jsvidyad on 2009-09-23
Well, I guess if I use DBAN, it will also destroy all the data on my new hard drive too!! So, I can't use it. Any other suggestions.

From what I read on the internet, formatting does not destroy the data on the hard drive.

---

### Post by tvtech on 2009-09-23
> **jsvidyad said:**
> Well, I guess if I use DBAN, it will also destroy all the data on my new hard drive too!! So, I can't use it. Any other suggestions.

From what I read on the internet, formatting does not destroy the data on the hard drive.

You are absolutely correct about that.  Deleting the Data doesn't do a whole lot, it's more secure in EXT and Journaled file systems since they don't create files like NTFS does but... the data's residual magnetic imprint can be there up to 10 re-writes later, 20 if your the NSA.  Which is great if you've accidentally deleted something and need to recover it!  If you have sensitive financial DATA, you really aught to look into buying a sledge hammer.  I recommend a 20 lber.  The best way to really scramble it beyond using an NSA grade scrubber, which is a little sketchy, seriously only criminals use those, and yes they throw up red flags when purchased.  Is to buy/make a good old fashioned electromagnet, disassemble the drive and run the magnet over the platters, just keep it away from your credit cards or new HDD, or anything magnetic and don't electrocute yourself.  You don't have to destroy the HDD you can just run a really strong electromagnet over it but dell might tell you to Screw on the RMA. Saying you caused the Damage

I recommend using SSD's they don't store magnetically and once the data is deleted it is deleted you'd have to be the NSA to recover it and even then, not likely.  Transistor gates don't tend to leave a magnetic memory, that is also part of the reason why they break down so much faster than traditional magnetic media they are a physical open or close to store the 1's and 0's.

Your absolute best bet is to reformat it using windows NTFS full format option at least 3 times.  This deep cycles the drive and takes a LONG time, after that the only way to pull anything off is having some serious serious software/hardware retrieval and a real need to get at the data. It's simple it's cheep.  Don't use Gparted's format it just deletes the partition table it doesn't actually overwrite the sectors. it just scans for bad ones.  It's equivalent to using a quick format in windows, also not recommended

---

### Post by credobyte on 2009-09-23
```
dd if=/dev/random of=/dev/sda

```

Run it a few times from the LiveCD and you are covered :)

---

### Post by peculiar penguin on 2009-09-23
```
sudo shred -vn <iterations> <device>
```...will overwrite the given device iterations times with random data (once is good enough for most scenarios). Make sure you don't point it at the wrong thing, obviously.

If the drive has errors, this may not work properly (at all, or it could stop halfway through). In that case try something that uses the drive's internal secure erase command (e.g. [Secure Erase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml")).

---

### Post by dcstar on 2009-09-25
> **peculiar penguin said:**
> ```
sudo shred -vn <iterations> <device>
```...will overwrite the given device iterations times with random data (once is good enough for most scenarios). Make sure you don't point it at the wrong thing, obviously.

If the drive has errors, this may not work properly (at all, or it could stop halfway through). In that case try something that uses the drive's internal secure erase command (e.g. [Secure Erase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml")).

A single fill of zeros is enough for modern drives as the actual magnetic data written to the platter is encoded sufficiently to scramble things.

Anyone with sufficient paranoia can use the Secure Erase program, as it actually works on modern drives in comparison to the multi-pass write programs that people still recommend even thought they are 10+ years out of date and of little use.

---

### Post by megamania on 2009-09-25
> **jsvidyad said:**
> 
     I recently had my hard drive replaced as the old drive was giving errors while trying to boot ubuntu. I have to return the old hard drive to Dell. If I don't do that, I will have to pay for the new hard drive. But, before returning it, I want to delete all the data on the hard drive in a way such that it can't be recovered.

I was going to suggest "shred" too.

However, since your drive is already faulty and it's being returned as such, just turn it on and while it's spinning hit it hard with a hammer a few times until it becomes completely unusable.

When Dell receives it, nobody there will waste time trying to look for data on your *broken* hard disk.

---

### Post by t0p on 2009-09-25
Everything you could ever want to know about secure deletion is to be found [here]("http://mirror.href.com/thestarman/asm/mbr/WIPE.html"). An excellent resource.

> **jsvidyad said:**
> Well, I guess if I use DBAN, it will also destroy all the data on my new hard drive too!! So, I can't use it.

DBAN can be configured to nuke only those drives you want it to nuke.  It will destroy the data on your new drive only if you tell it too.

> **jsvidyad said:**
> 
From what I read on the internet, formatting does not destroy the data on the hard drive.

This is true.

> **megamania said:**
> However, since your drive is already faulty and it's being returned as such, just turn it on and while it's spinning hit it hard with a hammer a few times until it becomes completely unusable.

When Dell receives it, nobody there will waste time trying to look for data on your *broken* hard disk.

But they might refuse to refund your money.   Hitting the disk with a hammer is likely to void the warranty, and you'll find it difficult to prove it was faulty before you smashed it.

YOU: But it was faulty...

DELL:  Yes, repeated hammer blows tend to do that.

---

### Post by P4man on 2009-09-25
> **tvtech said:**
> the data's residual magnetic imprint can be there up to 10 re-writes later, 20 if your the NSA. 

I don't believe that. Maybe if you zero fill a drive once, or even a few times, you could retrieve *some* data by measuring left over magnetic signals. You could amplify the signal and with some statistics you might be able to retrieve some stuff on there.

But if you write ***random*** data to the drive just once or twice, i can not believe you would be able recover anything. Let alone after 10x.  NSA or no NSA. Keep in mind each sector alreay has a several year history if being written to, 

If it were possible, then it would be possible to increase harddrive capacity 10x or 20x and somehow I do think HD manufacturers would use that miraculous magnetic memory, even if "only" to double or quadruple drive capacity and use the remaining margin for error correction.

---

### Post by macabrem on 2009-09-25
> **P4man said:**
> I don't believe that. Maybe if you zero fill a drive once, or even a few times, you could retrieve *some* data by measuring left over magnetic signals. You could amplify the signal and with some statistics you might be able to retrieve some stuff on there.

But if you write ***random*** data to the drive just once or twice, i can not believe you would be able recover anything. Let alone after 10x.  NSA or no NSA. Keep in mind each sector alreay has a several year history if being written to, 

If it were possible, then it would be possible to increase harddrive capacity 10x or 20x and somehow I do think HD manufacturers would use that miraculous magnetic memory, even if "only" to double or quadruple drive capacity and use the remaining margin for error correction.

I haven't used Ubuntu in awhile, but doesn't it have the SRM command available?  [http://en.wikipedia.org/wiki/Srm_(Unix](http://en.wikipedia.org/wiki/Srm_(Unix))

It says it will use a 35 pass algorithm.

---

### Post by megamania on 2009-09-25
> **megamania said:**
> since your drive is already faulty and it's being returned as such, just turn it on and while it's spinning hit it hard with a hammer a few times until it becomes completely unusable.


> **t0p said:**
> But they might refuse to refund your money.   Hitting the disk with a hammer is likely to void the warranty, and you'll find it difficult to prove it was faulty before you smashed it.

YOU: But it was faulty...

DELL:  Yes, repeated hammer blows tend to do that.
:-)

You don't have to phisically destroy it! Cover it with a t-shirt and hit it with a hammer while it's spinning - no outside damage and heads gone.

---

### Post by Grenage on 2009-09-25
> **P4man said:**
> I don't believe that. Maybe if you zero fill a drive once, or even a few times, you could retrieve *some* data by measuring left over magnetic signals. You could amplify the signal and with some statistics you might be able to retrieve some stuff on there.

I also have trouble believing that anyone could get data off after 1 complete write.  Sure, with a format or 5, but not with random data; I've never seen it done.

OP: DBAN or any random data write will ensure that no Dell tech gets his/her hands on your Government secrets (or tentacle porn).

---

### Post by P4man on 2009-09-25
> **Grenage said:**
> I also have trouble believing that anyone could get data off after 1 complete write.  Sure, with a format or 5, but not with random data; I've never seen it done.


Actually, Ive been thinking this over. and yeah it might be possible.

A harddrive doesnt read binary data, it reads an analogue magnetic signal and then interprets the value as a (highly) probable 1 or zero. Assume you'd overwrite an area with all "1s", then  I assume by measuring the actual magnetic strength and using some statistics you could do some good guesses about each bit having been a 1 or a zero before the overwrite.  Simply put, the 0.9s you measure where more likely 1s before the overwrite and the 0.6s where more likely 0's.

Now if you write random data.. not all that much changes. After all, you are writing binary data, so 1s or zero's, and nothing inbetween, so you know the data you overwrote with (its random, but it *is* readable), and you could therefore "subtract" that from the measured analogue values and come up with some guesses again. 

Thats not likely good enough to make an install bootable again :) but it could be good enough to retrieve fragments of a file in a forensic investigation. Or e.g. to prove that some known file has been on your computer before you tried wiping it.

If you do one pass with random data, id say your data is entirely safe for all normal intents and purposes, and no one is going to be able to retrieve 100%, but if you're storing nuclear launch codes, I imagine a well equipped lab might be able to retrieve bits of it with some statistical confidence.

---

### Post by Grenage on 2009-09-25
Yes, that's the theory, and it sounds... well it sounds sound.  I would however love to see the results of such a high-end attempt.  I'd wager nothing remotely legible would be retrieved.

---

### Post by P4man on 2009-09-25
> **Grenage said:**
> Yes, that's the theory, and it sounds... well it sounds sound.  I would however love to see the results of such a high-end attempt.  I'd wager nothing remotely legible would be retrieved.

Considering drive manufacturers would be keen to exploit any excess margin to increase drive capacity/density, I agree with you. My WAG would be that in the perfect lab, they could recover 50% of the data after 1 overwrite, without knowing which 50% is right, and which is wrong. Like I said, for some forensic investigation that could be extremely valuable (if you got a few millions bits like that, you could prove with statistical certainty that you for instance, did have some known video on your computer if 50% of the data matches), but no one at dell is going to be reading your emails that way.

---

### Post by Grenage on 2009-09-25
Well I think I might have a look around tonight, see if I can find any information on such attempted scans.  It would be interesting to see what has actually been managed so far.

---

### Post by niteshifter on 2009-09-25
Hi,

[QUOTE=peculiar penguin]If the drive has errors, this may not work properly (at all, or it could stop halfway through). In that case try something that uses the drive's internal secure erase command (e.g. Secure Erase).[/QUOTE]

[QUOTE=dcstar]A single fill of zeros is enough for modern drives as the actual magnetic data written to the platter is encoded sufficiently to scramble things.

Anyone with sufficient paranoia can use the Secure Erase program, as it actually works on modern drives in comparison to the multi-pass write programs that people still recommend even thought they are 10+ years out of date and of little use.
[/QUOTE]


About that Secure Erase ...

It's a nice tool (DOS based) that essentially does what one can already do from LiveCD: run dd or shred against the drive **OR** _it will use the drive's internal firmware to accomplish the task_. This part - from CMRR's own *Tutorial on Disk Drive Data Sanitization* (available [here]("http://cmrr.ucsd.edu/people/Hughes/DataSanitizationTutorial.pdf"), cmrr.ucsd.edu, pdf file) is telling. The context of the quoted text below is they are refering to usage of drive-level full encryption (vs computer-level products):
> Full Disk Encryption (FDE) Enhanced Secure Erase,” (“FDE-SE”), securely changes the internal drive encryption key, to render encrypted user data on disk indecipherable. This is enabled via the Enhanced SE command in the present ATA ANSI specs.

FDE SE encryption needs to be tested for protection against advanced forensic analysis. The results will determine the erasure security data level - Confidential, Secret, Top Secret, or higher. The US Commerce Department prohibits most 256-bit and higher encryption export overseas, limiting FDE E-SE to AES-128-bit encryption (since disk drives are a global industry).

AES-256 bit encryption in FDE drives could allow FDE SE at a somewhat higher security level. Note that a FDE E-SE operation amounts to double AES-128, because the data encrypted by the discarded key is decrypted by the new key, and AES is a symmetric encryption scheme. It would appear that a brute force attack on double AES-128 requires the same computational effort as single AES-256.

**For paranoid-level security, the cypt-text in an FDE disk drive could be eliminated by a Normal OW SE done after the FDE E-SE.**

Emphasis added by me. A couple of things I'd like to point out:

1. Security is based upon trust. Can one trust closed-source software (firmware in this case) of the drive manufacturer? Who vetted this software? Where can we see the results of the vetting / analysis?

2. As the emphasized text above shows, even CMRR tacitly admits to the problems in 1, above.

So ... methinks either:
```
dd if=/dev/zero of=/dev/sdX bs=512
```

or shred - used effectively (it's not of little use, just over-kill)
```
shred -n1 /dev/sdX
```

Of the two dd will be the quickest. And one already has it. The only advantage using shred is it's not so obvious that the drive was wiped.


Either method will work fine on any drive that use perpendicular recording methods (any drive since the mid- late-'90s). The 'lore' that's out there about recovering data from previous writes is in fact quite dated. It's not applicable to the 'new' recording methods, just to older longitudinal methods.

Drives older than that ('90's) - why waste time with full multi-pass overwrites? Just take a hammer to it ;) It's not like you can get exact replacments. At least not at prices you'll like.

---

### Post by P4man on 2009-09-25
My googling turned up this:
[http://www.nber.org/sys-admin/overwritten-data-guttman.html](http://www.nber.org/sys-admin/overwritten-data-guttman.html)

It has some good references too.

Long story short: a **single** random overwrite on a modern harddrive = no recoverable data.

---

