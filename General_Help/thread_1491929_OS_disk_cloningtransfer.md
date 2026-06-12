---
title: "OS disk cloning/transfer?"
date: 2010-05-24
forum: General Help
---

### Post by BklynKid on 2010-05-24
Hi there.
New to Ubuntu/linux here. Wondering, can I easily transfer my OS partition (and swap partition) to another hard drive? The current one is getting a little small. 

For Windows I guess I would use something like Ghost. But with linux, are there any references that need to be updated or anything like that for it to function correctly afterwards?

Any links or references would be much appreciated.

---

### Post by jerome1232 on 2010-05-24
You could use partimage, it's alot like ghost actually.

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

or dd from a live cd, the problem with it is it can be slow since it copies everything bit for bit, meaning empty space too.

---

### Post by Grenage on 2010-05-24
Clonezilla is also quite popular.

---

### Post by Ad@m on 2010-05-24
[http://www.partimage.org/Partimage-FAQ#Can_I_restore_it_to_a_smaller_or_bigger_partition_.3F](http://www.partimage.org/Partimage-FAQ#Can_I_restore_it_to_a_smaller_or_bigger_partition_.3F)

---

### Post by BklynKid on 2010-05-24
Thanks those look great!

But now if I clone the OS partition to another drive and boot from that new partition, will everything work correctly?

---

### Post by jerome1232 on 2010-05-24
Yeah, assuming the operation goes correctly everything will boot. 

Make sure your cloning the entire drive (including the boot sector) and not just individual partitions

You may need to expand your partition's to take advantage of the extra space on the new disk however. You would use gparted from a live cd to do that.

---

### Post by zaphod777 on 2010-05-24
> **Grenage said:**
> Clonezilla is also quite popular.

I am also a big fan of clonezilla.

---

### Post by BklynKid on 2010-05-24
Great, I think I'll try partimage when I get home later. :popcorn:

---

### Post by BklynKid on 2010-05-24
Hmmm trying to do this now but my destination partition is smaller than the original partition. Anyway to get around this? Or should I make it larger and then make the partition smaller later (without losing my data, is that possible?)

---

### Post by louieb on 2010-05-24
FYI - partimage does not work with ext4 formated partitions. Looking for a replacement myself -  Have tried Clonezilla and FS Archiver - both work. Just have not decided which I like better.   


When restoring - the to partition has to be the same size or larger. Can be shrunk later. 

Another way is Gparted.  Kind of weird the way you use it to copy/clone - but it works - [Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm")

---

### Post by defishguy on 2010-05-24
I'm a huge fan of [Remastersys]("http://geekconnection.org/remastersys/") it has solved an awful lot of problems for me, and has always been reliable.

---

### Post by BklynKid on 2010-05-24
Yea I ended up going with Clonezilla after making the source partition smaller with gparted. The clone itself worked fine but it didn't copy the bootsector it seems. At least I can't boot from the newly cloned drive. How can I make it bootable?

[edit] Seems that I did a partition->partition copy which is why the MBR wasn't included. How can I copy this? Also the source HD used 'Master Boot Record' as the partitioning schema while the new one uses the 'GUID Partition Table'. Will that cause any problems?

---

### Post by BklynKid on 2010-05-25
After a lot of searching and reading it seems that my GPT layout is the cause for my problems. Couldn't get grub installed for what seem now like obvious reasons.

So... anyone know of a good set of instructions/guide that will get me out of this mess? I still have my old hard drive. Could I use the ubuntu installer to set everything up for me correctly to the point where I could then use clonezilla again to simply transfer my old files back to the newly created partition layout? I'm really not interested in using MBR again though.

---

### Post by john newbuntu on 2010-05-25
Assuming you are on grub2, did you try installing grub to GPT of the new drive by following step #13 by drs305.  You need to do this from a liveCD/USB.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

From a liveCD, you may have to mount the new root partition and modify UUIDs in /etc/fstab as that changes when you move from one disk/partition to another.
"sudo blkid -c /dev/null" should give you the UUIDs.

---

### Post by dogafin on 2010-05-25
i used ddrescue

apt-get install gddrescue

Type in the following command, substituting SOURCE with the name of your source drive and DESTINATION with the name of your destination drive: sudo ddrescue -v /dev/SOURCE /dev/DESTINATION

easy!

the cloned drive didnt initially boot up but after running fsck -y to fix errors it booted up beautifully. 

my only mistake was cloning an 80gb harddrive onto a 160, so it made half of it an unallocated space, unfortunately you have to use a target drive the same size as the source drive or else it will also mimic its physical size. im now trying to figure out how to turn it into free space with gparted, but before i tweak with it ive asked our folks here at ubuntu forums for a little help but noones replied to my post yet.

here is my result
[IMG]http://img.photobucket.com/albums/v102/_H_E_L_/Screenshot--dev-sda-GParted.png[/IMG]

---

### Post by jerome1232 on 2010-05-25
You should be able to drag the extended partition (the little blue line around swap) out and create more logical partitions inside of it.

Or since it's just swap delete them both and recreate, that would give you the option of growing the root partition there too.

---

### Post by OwenHell on 2010-05-30
If I may interject and ask a question   How do you clone/Copy a hard Drive of data YES! i tried to copy and past and it just  gives up after 10 or 20GB  and as for Clonezilla dose exactly what i want but stupid windows dose not see it in my computer folder  two hard drives over USB with a laptop(Ubuntu) in the middle all i need is windows(HTPC) to see it as a external hard drive  any ideas thank you for the reply

---

