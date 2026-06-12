---
title: "Safely remove hardware..........?"
date: 2011-10-12
forum: General Help
---

### Post by pretty_whistle on 2011-10-12
Is it recommended to select "safely remove hardware" before removing any storage media?

I'm figuring the answer's yes.

---

### Post by cryptotheslow on 2011-10-12
Yes. :D

Just yanking it out while the filesystem is still mounted will inevitably lead to tears and much gnashing of teeth sooner or later.

---

### Post by WasMeHere on 2011-10-12
> **pretty_whistle said:**
> Is it recommended to select "safely remove hardware" before removing any storage media?

I'm figuring the answer's yes.

Yes, that finishes any pending write operations :-)

*Edit: and unmounts the partitions as pointed out by cryptotheslow*

---

### Post by pretty_whistle on 2011-10-12
> **cryptotheslow said:**
> Yes. :D

Just yanking it out while the filesystem is still mounted will inevitably lead to tears and much gnashing of teeth sooner or later.

I thought as much.

I learned this just yesterday.  I copied a few files to a flash drive and had them vanish later, lol.  Luckily they weren't the originals.

And to think I was doing it the wrong way for 4 years....lol.

---

### Post by pretty_whistle on 2011-10-12
> **Olle Wiklund said:**
> Yes, that finishes any pending write operations :-)

*Edit: and unmounts the partitions as pointed out by cryptotheslow*

Oh, so that's why.

---

### Post by pretty_whistle on 2011-10-12
4 years of doing it wrong.  Lol.  That's a funny one. :D :lolflag: :mrgreen: :lol:

---

### Post by cryptotheslow on 2011-10-12
Wow 4 years :lolflag:
What format is the drive? I'm suprised you haven't encountered a problem before now!

---

### Post by pretty_whistle on 2011-10-12
> **cryptotheslow said:**
> Wow 4 years :lolflag:
What format is the drive? I'm suprised you haven't encountered a problem before now!

I did get it before but because it wasn't a constant problem I figured the computer just had a temporary glitch. ROF...way off man, way off....

LOL.

The drive is FAT32.  Wait...the others are FAT32, the one yesterday where files vanished was an NTFS flash drive.

---

### Post by cryptotheslow on 2011-10-12
Probably something to do with NTFS being a journalling filesystem and FAT32 not. I can honestly say I don't know enough about it to make any more than a wild stab in the dark about it than that :D


Edit to add after some reading :D......
[http://superuser.com/questions/194412/is-ntfs-fail-safe-in-case-of-a-power-outage](http://superuser.com/questions/194412/is-ntfs-fail-safe-in-case-of-a-power-outage)

Basically the NTFS filesystem tries to protect the consistency of the file and directory structures in case of an unclean dismount - but does not protect file data specifically. So in your case I would think it went something like this - you "wrote" the files to the disk, the filesystem metadata about the files was written but the actual file data was not committed to disk yet (still cached), you yanked the drive. On connecting the drive, the filesystem goes "oohhh not good - I have metadata about these files but no files....  I know, I'll keep myself sane by just forgetting that metadata". :D

---

### Post by pretty_whistle on 2011-10-12
@cryptotheslow

I tested a lot and found files vanish if I don't select 'safely remove hardware' first, even though it's formatted NTFS.

---

### Post by cryptotheslow on 2011-10-12
Yep that would be expected. The metadata *about* the files is written first and the actual data of the files held in cache until a suitable time to commit it to the disk (i.e. it's not doing anything else, or it reaches a defined maximum time elapsed with data in cache).

So basically the file data is not physically written to the disk at the point you pull the plug. On re-plugging the drive, the filesystem looks at the journal and sees that it had written the metadata but the actual file data was not committed. As it no longer has the file data to write, it reverses out the file metadata to keep itself clean.

I now understand more than I did an hour ago - all good :D

---

### Post by pretty_whistle on 2011-10-12
> **cryptotheslow said:**
> Probably something to do with NTFS being a journalling filesystem and FAT32 not. I can honestly say I don't know enough about it to make any more than a wild stab in the dark about it than that :D


Edit to add after some reading :D......
[http://superuser.com/questions/194412/is-ntfs-fail-safe-in-case-of-a-power-outage](http://superuser.com/questions/194412/is-ntfs-fail-safe-in-case-of-a-power-outage)

Basically the NTFS filesystem tries to protect the consistency of the file and directory structures in case of an unclean dismount - but does not protect file data specifically. So in your case I would think it went something like this - you "wrote" the files to the disk, the filesystem metadata about the files was written but the actual file data was not committed to disk yet (still cached), you yanked the drive. On connecting the drive, the filesystem goes "oohhh not good - I have metadata about these files but no files....  I know, I'll keep myself sane by just forgetting that metadata". :D

Good technical explanation for why my files vanished.

---

### Post by pretty_whistle on 2011-10-12
> **cryptotheslow said:**
> Yep that would be expected. The metadata *about* the files is written first and the actual data of the files held in cache until a suitable time to commit it to the disk (i.e. it's not doing anything else, or it reaches a defined maximum time elapsed with data in cache).

So basically the file data is not physically written to the disk at the point you pull the plug. On re-plugging the drive, the filesystem looks at the journal and sees that it had written the metadata but the actual file data was not committed. As it no longer has the file data to write, it reverses out the file metadata to keep itself clean.

I now understand more than I did an hour ago - all good :D

I understand more than an hour ago too. :D

---

### Post by mbhammerbro on 2011-10-12
> **pretty_whistle said:**
> I understand more than an hour ago too. :D

You also have to be careful as to if your flash drive is configured for performance.  Removing it without safely removing in this case can actually damage the files themselves and cause them to become corrupt.  I had this happen to me a few times just being careless.

---

### Post by pretty_whistle on 2011-10-12
> **mbhammerbro said:**
> You also have to be careful as to if your flash drive is configured for performance.  Removing it without safely removing in this case can actually damage the files themselves and cause them to become corrupt.  I had this happen to me a few times just being careless.

I've had corrupted files too, as well as vanishing which I said before.

Now I know more about computers and related stuff.  Good, I love that part.  :D

Funny thing is when I got the computer in late '06 I spent lots of time since then looking around on the computer for things I didn't know and could learn.  Amazing I kept missing this stuff!  Where was my head?? Hahaha.

---

### Post by cryptotheslow on 2011-10-12
It's always good to learn. As long as it doesn't fall out of your head again :lolflag:

I actually came across something like this a while back with an ext4 formatted internal drive and a dodgy power supply that would just arbitrarily switch off when it wanted. Recently saved file changes before the power cut just "vanished". I read up on journalling and caching then too.....   it seems my brain also uses journalling and sometimes fails to commit its cache in a timely manner too :D

---

### Post by pretty_whistle on 2011-10-12
> **cryptotheslow said:**
> It's always good to learn. As long as it doesn't fall out of your head again :lolflag:

I actually came across something like this a while back with an ext4 formatted internal drive and a dodgy power supply that would just arbitrarily switch off when it wanted. Recently saved file changes before the power cut just "vanished". I read up on journalling and caching then too.....   it seems my brain also uses journalling and sometimes fails to commit its cache in a timely manner too :D

*"... it seems my brain also uses journalling and sometimes fails to commit its cache in a timely manner too :D"*

That was a funny one :P  :lolflag:

---

### Post by pretty_whistle on 2011-10-12
Wow, that was close.  I just checked all my flash drives which had files on them to be sure they'd still be there when plugged back in.  Thankfully I hadn't lost anything.

Close call.  Yikes.

Haha, still funny though.

---

### Post by cryptotheslow on 2011-10-12
You wouldn't be finding it so funny had you managed to corrupt one of the FAT32 filesystems. Rather than just nicely back out the non-sane most recent changes using a journal as reference - they tend to go into a complete flat-spin, throw the toys out of the pram and sulk state - typically losing a great deal more than the last few files you worked on. Leaving you reaching for photorec and a cold beer to steady the nerves. :D

Still... no damage done and lesson learned I guess :guitar:

---

### Post by pretty_whistle on 2011-10-12
> **cryptotheslow said:**
> You wouldn't be finding it so funny had you managed to corrupt one of the FAT32 filesystems. Rather than just nicely back out the non-sane most recent changes using a journal as reference - they tend to go into a complete flat-spin, throw the toys out of the pram and sulk state - typically losing a great deal more than the last few files you worked on. Leaving you reaching for photorec and a cold beer to steady the nerves. :D

Still... no damage done and lesson learned I guess :guitar:

Yep.  I agree.

Photorec is what I had to use back in '07 when I had a corrupted folder.  I recovered just a tad of what I had.  Boy was I mad.  And worse, it happened twice.  I ended up giving up on saving files after that, thinking the 'computer glitch' had cost me too much and I wasn't about to repeat saving files just to have them lost again.

Little did I know what the actual cause was...oh boy.

---

### Post by Slim Odds on 2011-10-12
This is why the original Mac computers did not have a physical eject button for the floppy drive. The user had to request the disk be ejected, therefore the OS could make sure that all of the data that needed to be written to the floppy could be written before it allowed the disk to be removed.

---

### Post by pretty_whistle on 2011-10-12
> **Slim Odds said:**
> This is why the original Mac computers did not have a physical eject button for the floppy drive. The user had to request the disk be ejected, therefore the OS could make sure that all of the data that needed to be written to the floppy could be written before it allowed the disk to be removed.

That's how things should work.

---

### Post by cryptotheslow on 2011-10-12
Until of course some OS / software glitch causes the media to fail to eject. Leaving the user to resort to physical means to prise it free :D e.g. the little pin-hole in most optical drives to mechanically release the tray.

Not sure what if any facility the original Mac provided for this scenario - did they just manufacture them based on the assumption that nothing could ever go wrong and the scenario could never ever occur? Brave if so :D

---

### Post by pretty_whistle on 2011-10-12
> **cryptotheslow said:**
> Until of course some OS / software glitch causes the media to fail to eject. Leaving the user to resort to physical means to prise it free :D e.g. the little pin-hole in most optical drives to mechanically release the tray.

Not sure what if any facility the original Mac provided for this scenario - did they just manufacture them based on the assumption that nothing could ever go wrong and the scenario could never ever occur? Brave if so :D

That scared me.  I retract my last statement.

:)

---

### Post by cryptotheslow on 2011-10-12
I only mentioned it as many years ago I had a CDROM drive which refused to eject and had no pin-hole. The act of rescuing the CD it had developed such a liking for resulted in the fatal dismemberment of the drive into a myriad of tiny pieces. I suspect the sensitivity of my surgery on the thing was somewhat diminished by pure exasperation at "the stupid ^%$£$% thing". :D

---

### Post by pretty_whistle on 2011-10-12
> **cryptotheslow said:**
> I only mentioned it as many years ago I had a CDROM drive which refused to eject and had no pin-hole. The act of rescuing the CD it had developed such a liking for resulted in the fatal dismemberment of the drive into a myriad of tiny pieces. I suspect the sensitivity of my surgery on the thing was somewhat diminished by pure exasperation at "the stupid ^%$£$% thing". :D
Wow.

No pin-hole?  WHO is the pin head who made it that way?!!

---

### Post by cryptotheslow on 2011-10-12
LOL @ "pin-head"! Haven't heard that one in a very long time.

I've no idea what make the drive was, it's a long time ago and the dismembered corpse of the drive was rapidly committed to its final resting place. a.k.a. the bin. :D

---

### Post by pretty_whistle on 2011-10-12
> **cryptotheslow said:**
> LOL @ "pin-head"! Haven't heard that one in a very long time.

I've no idea what make the drive was, it's a long time ago and the dismembered corpse of the drive was rapidly committed to its final resting place. a.k.a. the bin. :D

Haha about pin-head.

Trashed drive?  Wow.  That's quite a hit all because of no pin-hole.

---

### Post by cryptotheslow on 2011-10-12
Yep trashed. As I mentioned... my surgical technique in rescuing the CD was probably not the most patient. It would probably have been possible to dismantle it in a way that meant it could have been put back together just fine - but it would still be a drive I'd have no faith in not doing the same thing again, so the end result was effectively the same.....  CD rescued, drive binned :D

---

### Post by mhh1422 on 2011-11-06
Hey,

Actually, I came here because I've lost <<some>> files (about 6GB) by moving files from my mobile phone to NTFS disk!! When switching to Windows7 I've missed them and then returned back to Ubuntu to find I've lost them!!! Googled a little and arrived here...

Do anyone please have any idea how to recover those lost files either to mobile or to the PC?

Thanks

---

### Post by mhh1422 on 2011-11-06
I've did a 'safely remove' before restarting to Windows...

---

