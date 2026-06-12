---
title: "&quot;hard&quot; format"
date: 2009-11-20
forum: General Help
---

### Post by DouglasAdams on 2009-11-20
i've got a pen drive that says it's 64Gb but is really only 16Gb.
ordinary formatting utilities simply format it as 64Gb. even the check option is ok.
but when you copy files to them, anything over 16Gb and the filenames become corrupted.
i know there are windows utilities that will re-size these drives to their "real" size.
is there a Linux utility that will do that?

---

### Post by phillw on 2009-11-20
Hi..

Have you got any important data on it ?

If not, format it  [http://www.cyberciti.biz/faq/howto-f...usb-pen-drive/]("http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/")

If you're going to use it near windows machines, you'll want the 
     ```

     $ sudo mkfs.vfat /dev/sda1 
```
Version - as it says -- make sure you get the device name correct - those commands WILL format what you tell them to - no 'Are you sure Y/N' stuff !!!

Regards,

Phill.

---

### Post by dcstar on 2009-11-20
> **DouglasAdams said:**
> i've got a pen drive that says it's 64Gb but is really only 16Gb.
ordinary formatting utilities simply format it as 64Gb. even the check option is ok.
but when you copy files to them, anything over 16Gb and the filenames become corrupted.
i know there are windows utilities that will re-size these drives to their "real" size.
is there a Linux utility that will do that?

Try the "Device" option in gparted (Partition Editor).

---

### Post by DouglasAdams on 2009-11-21
dcstar:
sorry but gparted doesn't do a "hard" format.

this is a 16Gb pen drive which has been, somehow, frigged (can i say that) by some little wizkid, who's probably about 13 yrs old, to "look" like it's 64Gb.
gparted simply re-formats it as 64Gb.
copy files **to** it and you can copy 64Gb to it.
however, after 16Gb the files overwrite themselves.
you end up with a contents list of your pen containing lots of strange,
sort of kanji playing cards, characters.
provided you only copy 16Gb to it then it's fine.
but i would like to make it "look like" what it really is.
that needs a ***really*** low level writing process.

phillw:
no, nothing on it.
i got this:
mkfs.vfat: Device partition expected, not making filesystem on entire device '/dev/sdc' (use -I to override)
after looking at the --help command for mkfs i decided to try the -I option
viz: $ sudo mkfs.vfat /dev/sdc -I
and got the reply:
mkfs.vfat 3.0.3 (18 May 2009)
after a while, clearly while it was doing the format, the pronpt returned.
however, now the file manager will not mount it.
quote:
Unable to mount location
Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

so i did some reading ...
first on mkfs
then, via a few links to dosfsck
so i did: $ sudo dosfsck -atvw /dev/sdc
and got, with a **very** long wait before it ended:
dosfsck 3.0.3 (18 May 2009)
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "mkdosfs"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     16384 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
  16769536 bytes per FAT (= 32753 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 33555456 (sector 65538)
   4192255 data clusters (68685905920 bytes)
63 sectors/track, 255 heads
         0 hidden sectors
 134217728 sectors total
Checking for bad clusters.
Reclaiming unconnected clusters.
Checking free cluster summary.
/dev/sdc: 0 files, 1/4192255 clusters

so i again tried: sudo mkfs -t vfat -c /dev/sdc -I
(which i beleive is virtually the same as you quoted, without the -I)
again it took forever (pity there's no timestamp on terminal commands)
$ sudo mkfs -t vfat -c /dev/sdc -I
mkfs.vfat 3.0.3 (18 May 2009)
again, i could not mount using the file manager - same message.
so i tried: $ sudo mkfs.vfat -c -C -F 16 -I -v /dev/sdc 17179869184
and got:
mkfs.vfat 3.0.3 (18 May 2009)
mkfs.vfat: unable to create /dev/sdc
so i tried: $ sudo mkfs.vfat -c -F 16 -I -v /dev/sdc
and got:
mkfs.vfat 3.0.3 (18 May 2009)
WARNING: Not enough clusters for a 16 bit FAT! The filesystem will be
misinterpreted as having a 12 bit FAT without mount option "fat=16".
mkfs.vfat: Attempting to create a too large file system
so i went for: $ sudo mkfs.vfat -c -F 12 -I -v /dev/sdc
and got:
mkfs.vfat 3.0.3 (18 May 2009)
mkfs.vfat: Attempting to create a too large file system
so i tried dropping the non FAT32 option, viz: $ sudo mkfs.vfat -c -I -v /dev/sdc
and got:
mkfs.vfat 3.0.3 (18 May 2009)
Auto-selecting FAT32 for large filesystem
/dev/sdc has 255 heads and 63 sectors per track,
logical sector size is 512,
using 0xf8 media descriptor, with 134217728 sectors;
file system has 2 32-bit FATs and 32 sectors per cluster.
FAT size is 32753 sectors, and provides 4192255 clusters.
Volume ID is 0ca635f9, no volume label.
Searching for bad blocks 85952... 171072... 256064 (plus a long list of bad blocks)

clearly, these "bad blocks" are the ones which don't really exist.
any ideas please?

---

### Post by jeb800e on 2009-11-21
DBAN.org

---

### Post by DouglasAdams on 2009-11-21
"DBAN will automatically and completely delete the contents of any hard disk that it can detect"

it doesn't seem to ***say*** that it would "fix" such a drive as mine ... or am i missing something?

---

### Post by lswb on 2009-11-21
I've got a couple similar SD cards. I found that I could partition them using gparted. Set the 1st partion to the actual useable size, and install filesystem of your choice. Leave the remainder unused (don't make it a partition or install a filesystem).

---

### Post by DouglasAdams on 2009-11-22
> **lswb said:**
> I've got a couple similar SD cards. I found that I could partition them using gparted. Set the 1st partion to the actual useable size, and install filesystem of your choice. Leave the remainder unused (don't make it a partition or install a filesystem).
what a brilliant idea!
i'll certainly try that as soon as my latest attempt to do a "dosfsck -atvw /dev/sdc" to enable me to mount it ends.
thanks very much for sharing your stroke of genius.

---

### Post by QLee on 2009-11-22
Yo, Doug man! Gimme some knuckle, dude!<G>

Remember that you format a partition not a drive. (i.e. sda1)

I suspect you won't need any more than that once you think about it.

---

### Post by jeb800e on 2009-11-22
Completely wiping the drive using a program like DBAN or any other similar may fix it, as it is erasing ans re-writing over (just so, so, so close to) everything. This will perform, basically, a "hard format" you were talking about.
You can also email DBAN to make sure before you ever try it, as who knows? It may just make your flash drive worse. The email address is located within their website (dban.org).

Or, you can always contact the makers of your USB flash drive. They will probably know what is wrong with it, and if you are still within warentee coverage, they may be able to give you a new one or fix it, maybe refund it for you.

---

### Post by phillw on 2009-11-22
If I had a storage device reporting numbers of bad sectors, I'd carefully file it in the nearest waste-bin. IMHO it just isn't worth the risk. As mentioned, if in guarantee - get it replaced.

Regards,

Phill.

---

### Post by DouglasAdams on 2009-11-22
> **QLee said:**
> Remember that you format a partition not a drive. (i.e. sda1)

yup, but i need to partiton the drive before i can format a partition - especially if i want to try lswb's workaround.

> **jeb800e said:**
> email DBAN to make sure before
i will ... and thanks for you idea.

> **jeb800e said:**
> 
They will probably know what is wrong with it
problem is m8, they are the one's who "over-sized" the drive in the first place.
(there is {certainly was} a write-up on ebay about these "faked" drives/memory cards.

> **jeb800e said:**
> 
refund
LOL, it was a no bids bargin, 99p plus £2.99 postage, a "far eastern specail" (SNG).
i bought it in the full knowledge that even if it had only really and 8gb drive i would have made a great buy.

---

### Post by phillw on 2009-11-22
> LOL, it was a no bids bargin, 99p plus £2.99 postage, a "far eastern specail" (SNG).
i bought it in the full knowledge that even if it had only really and 8gb drive i would have made a great buy. 		                   		  		  		 		 			 				

Ahhh..  DodgyCards-R-Us - a well known brand ;)

Good luck with your card.

Phill.

---

### Post by QLee on 2009-11-22
[QUOTE=DouglasAdams]yup, but i need to partiton the drive before i can format a partition - especially if i want to try lswb's workaround.[/QUOTE]

...And that you fsck a partition too, not a drive.

However, I have not seen a drive like you mention but other posters seem to have good advice for your specific situation.

---

### Post by egalvan on 2009-11-22
> **DouglasAdams said:**
> 
 "faked" drives/memory cards.

LOL, it was a no bids bargin, **99p plus £2.99** postage, a "far eastern specail" (SNG).
i bought it in the full knowledge that even if it had only really and 8gb drive i would have made a great buy.

Hey, at that price I would be willing to buy two or three to experiment with.
I would like to try dban on them,
and other, more nefarious techniques that I would not want to subject my "good" cards to :)

Would you share the seller's eBay ID?

Thanks

---

### Post by egalvan on 2009-11-22
> **QLee said:**
> ...And that you fsck a partition too, not a drive.


One layer lower.

You fsck a *file system*, not a partition.


"Now that's splitting hares"
said the butcher while cutting rabbits in half :)


rim shot
duck
run
hide

---

### Post by jeb800e on 2009-11-22
> **egalvan said:**
> One layer lower.

You fsck a *file system*, not a partition.


"Now that's splitting hares"
said the butcher while cutting rabbits in half :)


rim shot
duck
run
hide

Yes, but chances are, your partition IS a filesystem. Go into GPArted or any other similar program you may have. See what that program says about the partition.

---

### Post by QLee on 2009-11-22
> **egalvan said:**
> One layer lower.

You fsck a *file system*, not a partition.


"Now that's splitting hares"
said the butcher while cutting rabbits in half :)

You are correct and Doug will benefit from that hare splitting, he like dead parrots too. Eh, Doug? <G>

---

### Post by jeb800e on 2009-11-22
Wait, you are running Ubuntu 9.10 on your current computer you are having the problems with the USB flash drive right now, right? Go into Palimpset and run all the self tests for your flash drive. Read all the information Palimpset has to say about it. Maybe it is something fixable, if DBAN, etc. doesnt work. (or you can do it before DBAN, etc. just to make sure it isn't broken)

---

### Post by DouglasAdams on 2009-11-22
phillw
"brand" - no way, certainly a lot more than just one brand.

QLee
"fsck" - at first glance, i thought you were swearing at me  LOL
actually, i was gonna use gparted m8, at least on this occasion as i've already got a large reading list  :)

egalvan
sorry m8. you're clearly not a "real" ebayer   :)
this was a zero bid item (actually, i had bid for about 10/12 of them), i.e. look for items without any bids and just go for it.
you will also find that many of these sellers (who you can get zero bid bargins from) restrict buyers to just one purchase in ten days. in this particular case i was even luckier. the morning after the auction closed the seller sent me an email saying that he had withdrawn the sale and that he would arrange a refund. i sent quite a strong email saying that it was a con and that he should have withdrawn the item before it closed. he replied that he had been selling drives with writing on them but he had sold out. i replied that i didn't care about the writing, just the drive. hence my bargin.

---

### Post by DouglasAdams on 2009-11-22
> **QLee said:**
> You are correct and Doug will benefit from that hare splitting, he like dead parrots too. Eh, Doug? <G>
certainly do.
bit of a slip with your french pronouns QLee  :)

---

### Post by DouglasAdams on 2009-11-22
> **jeb800e said:**
> Wait, you are running Ubuntu 9.10 on your current computer you are having the problems with the USB flash drive right now, right? Go into Palimpset and run all the self tests for your flash drive. Read all the information Palimpset has to say about it. Maybe it is something fixable, if DBAN, etc. doesnt work. (or you can do it before DBAN, etc. just to make sure it isn't broken)

Palimpset - great, new toy time!
i'm just stepping outside, i may be some time ...

---

### Post by DouglasAdams on 2009-11-22
jeb800e
email gone[]("http://ubuntuforums.org/member.php?u=885262")

---

### Post by DouglasAdams on 2009-11-22
FYI

Palimpset
was go joy

gparted
i made a partition of 16,000Mb (15.63Gb) and names it "16Gb"
- i thought it was better to make it a little under the point where the "problem" might be.

remember, this is after the
  sudo dosfsck -atvw /dev/sdc
had finished.

now i'm copying some files to that "16Gb" partition

---

### Post by jeb800e on 2009-11-22
Well, also you can't just assume that making a 16 gb partition will fix your drive.

---

### Post by DouglasAdams on 2009-11-23
> **jeb800e said:**
> Well, also you can't just assume that making a 16 gb partition will fix your drive.

true but this great idea was not meant to "fix" the actual problem with the drive.
however, it does, subject to the results of the tests which i am still running, offer a truely brilliant "workaround" to make this drive totally usable - even to my kids who would not monitor the total quantity of files on the drive. in short, again provided my testing is successful, this fix would allow it to operate exactly the same as a 16Gb drive that was perfect for all "normal" usage.

---

### Post by DouglasAdams on 2009-11-23
> **jeb800e said:**
> Well, also you can't just assume that making a 16 gb partition will fix your drive.

plus
depending what the nice folk at dban say, i'm sure i'll continue experimenting to find the "best" solution for the average user.

---

