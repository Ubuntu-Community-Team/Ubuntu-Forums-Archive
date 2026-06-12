---
title: "NTFS or FAT32 for Shared Partition?"
date: 2009-11-19
forum: General Help
---

### Post by PrarieD0G on 2009-11-19
I just installed Windows 7 (64-bit) and was planning on dual booting with Ubuntu (64-bit). I"m planning to to have a shared partition to store my videos, music, documents, etc. on. Should I make the shared partition NTFS or FAT32?

This is all going on a 160GB hard drive. I have some PC games too, which I may add to the shared partition as well. What size would be good to partition everything at? I was thinking maybe 20GB for Windows, 20GB for Ubuntu, and the rest (~120GB) for the shared partition. Does that sound about right? I'm not really sure how much space I'm going to need for each OS + applications...

Thanks for your help. =]

---------

EDIT: So the consensus is NTFS. Thanks. Now I'm trying to figure out if I even *need* a "shared partition" or not. What do you think:

Better to just have 2 main partitions--1 for Windows and 1 for Ubuntu, or better to have 1 for each OS + a shared partition? Any major benefits to a shared partition? Recommended sizes for each?

EDIT2: Gah, I'm just overthinking this. I'll just go with a shared partition and be done with it! haha

Here's what I ended up doing:

[LIST]
[*]  Win7 - 40GB NTFS
[*] Shared - ~105GB NTFS (actual = 93.3GB)
[*] Ubuntu - 15GB ext4
[*]Swap - 0.5GB swap
[/LIST]

---

### Post by Archmage on 2009-11-19
Please keep in mind that NTFS is owned by MS only. So therefore if something goes wrong, it is because of bad documentation from MS.

But I would go for NTFS. This can handle large files (over 4 GB) and should work with both OS. But I think 20 GB will be a little to small for an OS. Windows 7 may need a little more space.

---

### Post by Sammi on 2009-11-19
NTFS is significantly technically superior to FAT32 and the NTFS-3G driver is fast, mature and stable, so of course I'd go with NTFS.

---

### Post by dcstar on 2009-11-19
Or use a decent filesystem like EXT3 and put the utilities on Windows to access it.

---

### Post by PrarieD0G on 2009-11-19
I guess I'll go with NTFS then, unless anyone has something else to add. Maybe I'll give Win7 30GB too, instead of just 20GB. Thanks!

---

### Post by fluffman86 on 2009-11-19
If it were me and I were running Win7 pretty often, I would make Ubuntu like 10 or 15 GB, then make the rest Windows.  You don't need a "shared" partition.  Just set up symlinks in Ubuntu for your Music folder to point to your My Music folder in Windows.  

Then you don't have to fool around with installing large programs on a D drive in Windows...it's all just on C.

---

### Post by PrarieD0G on 2009-11-19
Fair point. The thing I like about having a "shared" partition though, is that when you want to reinstall your OS, you don't have to go through the trouble of transferring all your old documents back. Also, the file layout is simpler (ie. D:/Music instead of C:/users/username/Music) so it's easier to get to stuff (less clicks :P). I dunno. I still can't really decide which would be better.

Are there any other benefits to having a shared partition rather than just having everything on 2 partitions (Win7 and Ubuntu)?

---

### Post by PrarieD0G on 2009-11-19
Sorry to double post, but I'm impatient, heh, and would like to do this sometime tonight.

Are there any major benefits to having a shared partition, or would I be better of doing like fluffman86 said and just have 2 major partitions with Ubuntu and Windows?

---

### Post by coffeecat on 2009-11-19
Sorry I can't give you any links, but I remember reading that Vista sometimes got in a right tizwoz if you wrote or amended files in the Windows equivalent of /home (whatever they call that now :rolleyes:) with Linux. This wasn't true of XP and I don't know whether it's true of W7. So - perhaps safer to have a separate NTFS Data partition accessible by both Ubuntu and Windows.


I guess safer because, so far, I have failed to induce a grande sulk in either Vista or W7 by writing to the shared data partition from Ubuntu.

---

### Post by PrarieD0G on 2009-11-19
Hm, good to know. I'm leaning more towards a shared partition now... still not 100% sure though. The only thing I don't like is the potential for wasted space. Like, for example, I give Win7 a 40GB partition and only end up needing ~25GB for the OS+applications. Then I have 15GB of unused/wasted space on my Win7 partition. Same deal for the Ubuntu partition.

I mean, I suppose I could resize/shrink the partitions later, but I'm not sure how much of a risk it would be for losing/corrupting data when you're trying to trim down your partitions that close to that data files... if that makes sense? (No, it probably doesn't. :P Sorry, my computer vocabulary sucks).

((Also "a right tizwoz"--that's a new one for me, haha. j/p, XP))

EDIT: Gah, I think I'm overthinking this. I'll just go with a shared partition (Win7 - 30GB NTFS, Shared - 110GB NTFS, Ubuntu - 20GB ext4)  and be done with it! haha

---

### Post by coffeecat on 2009-11-19
> **PrarieD0G said:**
> I mean, I suppose I could resize/shrink the partitions later, but I'm not sure how much of a risk it would be for losing/corrupting data when you're trying to trim down your partitions that close to that data files... if that makes sense? (No, it probably doesn't. :P Sorry, my computer vocabulary sucks).

That's a reasonable concern. I don't want to worry you :p but any resizing of partitions involves a small but significant risk of something going wrong. Particularly if there's a power cut halfway through. So - the fewer times you have to fiddle with partitions the lower the risk.

And, yes, "wasted" space on a 160GB drive is a consideration. I don't know what your budget is, but have you thought of getting a second hard drive? Prices just seem to keep coming down in real terms. If you haven't priced a 250GB drive recently, have a look now. You might be pleasantly surprised. The advantage would be that you could format the whole drive as one big data partition, and keep your OSs on the 160GB drive. A tidy solution.

> **PrarieD0G said:**
> ((Also "a right tizwoz"--that's a new one for me, haha. j/p, XP))

It's a sort of amalgam of getting in a tizzy and the name of a long defunct children's show here in the UK: Tizwaz. Random quote from the internet:

> Tizwaz was basically an excuse for grown men to run around behaving like kidsNow I wonder why that crept out of my unconscious when I thought of Vista. :-s

---

### Post by akakingess on 2009-11-19
> **Archmage said:**
> Please keep in mind that NTFS is owned by MS only. So therefore if something goes wrong, it is because of bad documentation from MS.

But I would go for NTFS. This can handle large files (over 4 GB) and should work with both OS. But I think 20 GB will be a little to small for an OS. Windows 7 may need a little more space.


+1 on the fact that unfortunately 20GB is way too small for Windows 7, even just the OS.

---

### Post by PrarieD0G on 2009-11-19
> **coffeecat said:**
> And, yes, "wasted" space on a 160GB drive is a consideration. I don't know what your budget is, but have you thought of getting a second hard drive? Prices just seem to keep coming down in real terms. If you haven't priced a 250GB drive recently, have a look now. You might be pleasantly surprised. The advantage would be that you could format the whole drive as one big data partition, and keep your OSs on the 160GB drive. A tidy solution.

That would be ideal actually, except I forgot to mention that this is on a laptop :X. There isn't really room for another drive. Or wait...

My DVD drive is broken, so I took it out. I wonder if I could put another hard drive where that used to be... hmmm... Might have to look into that. Thanks for the idea.

Haha, so that's what tizwoz came from. I shoulda known it was a UK thing, haha. 

Yep, I'll definitely be making the Win7 partition bigger than 20GB.

---

