---
title: "Identifying bad sectors?"
date: 2011-09-24
forum: General Help
---

### Post by davethewave83 on 2011-09-24
How do I identify which sectors are bad? It's not enough for me to know there are simply bad sectors, I'd like to try to repair them manually. Thanks!

---

### Post by cherva on 2011-09-24
Download a Hiren's Boot CD and run MHDD. It will tell you the bad sectors... you can repair it, but IF THERE ARE BAD SECTORS REPLACE THE HARD DRIVE. I don't know of an effective way to repair them.

---

### Post by davethewave83 on 2011-09-24
> **cherva said:**
> Download a Hiren's Boot CD and run MHDD. It will tell you the bad sectors... you can repair it, but IF THERE ARE BAD SECTORS REPLACE THE HARD DRIVE. I don't know of an effective way to repair them.

Thanks! I'll try that. I don't really want to use my hard drive so much as just want to try to muscle it into working properly once again "Just because" :popcorn: 

if anyone knows a good deal on external usb drives I'm listening :)

I'd like two 500gb (at least) but I noticed everywhere I look, two 500gb are more expensive than 1 1tb. I've been looking for a reasonable price and so far the lowest I can find is about $100 for two 500gb.

---

### Post by cherva on 2011-09-24
You can't get it to working properly, because HDD Regenerator (part of old Hiren's Boot CD ( around 9.x ) will regenerate the bad sectors, but after a few days they will be bad again and corrupting the sectors around them ... About cheap drives ... sorry man can't help you with that where ever you are on the globe :) ( except Bulgaria )

---

### Post by David Andersson on 2011-09-24
> **davethewave83 said:**
> How do I identify which sectors are bad? It's not enough for me to know there are simply bad sectors, I'd like to try to repair them manually. Thanks!

The *badblocks* command will read all blocks on a device or partition, and list the block number of all bad blocks.

Technically you don't repair bad blocks. But if you *write* to a bad block, and there are spare blocks left on the device, the bad block will be replaced with a spare block. That is, a fresh block on another part of the disk is assigned the block number of the bad block, and the bad block will never be accessed again. It appears the bad block is magically "repaired" when written to.

The the badblocks command can be used when formatting a drive to tell the filesystem to avoid the bad blocks. For example *mkfs.ext4 -l badblocks.log ...* formats for ext4 such that no known bad block will be used. (However, the man page of badblocks says it is safer to format with *mkfs.ext4 -c ...* which should be the same thing.)

---

### Post by davethewave83 on 2011-09-25
> **David Andersson said:**
> The *badblocks* command will read all blocks on a device or partition, and list the block number of all bad blocks.

Technically you don't repair bad blocks. But if you *write* to a bad block, and there are spare blocks left on the device, the bad block will be replaced with a spare block. That is, a fresh block on another part of the disk is assigned the block number of the bad block, and the bad block will never be accessed again. It appears the bad block is magically "repaired" when written to.

The the badblocks command can be used when formatting a drive to tell the filesystem to avoid the bad blocks. For example *mkfs.ext4 -l badblocks.log ...* formats for ext4 such that no known bad block will be used. (However, the man page of badblocks says it is safer to format with *mkfs.ext4 -c ...* which should be the same thing.)

I don't know about within Linux, but I've used Steve Gibson's "Spinrite" to recover bad sectors on my hard drives in the past, it worked, and they fully recovered. they were just depolarized(?) demagnetized etc, so writing repeatedly to the block repaired it to working order so that the disk would hold a magnetic field of positive or negative ( 1 or 0 ) again. 

I was hoping to do this manually since I cannot use Spinrite with a USB drive, I wanted to locate the bad sector, write hex FF and 00 to it repeatedly until it recovered. (I've done that on windows once using a hex editor, I think it was either Hex Edit or HxD) but I did that on a floppy disk not a hard disk. 

so just because a sector is bad, it doesn't mean it can't be repaired :) the SMART technology just gives up, and marks it bad, and replaces it. I think, personally, that the smart technology should do it's own extensive attempt to recover the sector before giving up but then you wouldn't buy a new hard drive see.

Also, a fun note. In the past when I worked at a department store we had those magnetic EMP like devices to deactivate the security tags, so I placed a floppy disk on top of it which I knew worked and tested it fully. I swiped a security tag across it with the floppy on top, the floppy bounced as the device deactivated the tag, and the PC would not read the floppy any longer. I tried to do the extensive recovery with Spinrite and it did moderately ok, but still couldn't fully recover it. those things are dangerous for magnetic storage :P

---

### Post by wildmanne39 on 2011-09-25
Hi, you can get a 1 tb at sam's club for 100 and 2 tb for about 30 dollars more.

How many bad sectors do you have, if it is just a few like 12 you can reformat the drive and it will block those sectors so no my data gets put there, then just keep an eye on the drive and make sure the bad sectors do not grow but I recommend doing a daily back up which is not a bad idea anyway.

I know of no good way to repair the bad sectors reliably.
Thank you

---

### Post by dcstar on 2011-09-25
> **davethewave83 said:**
> I don't know about within Linux, but I've used Steve Gibson's "Spinrite" to recover bad sectors on my hard drives in the past, it worked, and they fully recovered. they were just depolarized(?) demagnetized etc, so writing repeatedly to the block repaired it to working order so that the disk would hold a magnetic field of positive or negative ( 1 or 0 ) again. 

I was hoping to do this manually since I cannot use Spinrite with a USB drive, I wanted to locate the bad sector, write hex FF and 00 to it repeatedly until it recovered. (I've done that on windows once using a hex editor, I think it was either Hex Edit or HxD) but I did that on a floppy disk not a hard disk. 
..........

No one - repeat NO ONE - has been able to write "write hex FF and 00" to any hard drive for about 20 years now.

Modern hard drive encoding techniques ensure that the data you send to a hard drive has no resemblance whatsoever to what is actually written to the magnetic surface.

This is the reason that things like disk "wiping" are a joke, because you simply have no control whatsoever on the actual patterns written to the disk surface - but there is still a large industry perpetuating the misconception.

---

