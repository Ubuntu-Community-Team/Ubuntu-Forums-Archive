---
title: "ohoh, ext4 partition corrupted, how rescue data?"
date: 2010-08-13
forum: General Help
---

### Post by antiplex on 2010-08-13
hi all,

i was afraid this would strike me one (again), it seems my 900GB ext4 data partition has gone bananas. well, seems its not dead entirely, but i cant mount it and access my data.

even worse: i wrote the corrupted partition over my backup in a second of confusion, so i now have 2 corrupt partitions *doh!*

i would really appreciate any ideas or hints of how i might be able to rescue my data but i am aware that chances are not all too well...

here is what i found out so far:

hardware seems ok. there are other partitions on that disk without any problems. low-level-check did not find any issues. 

but if i try to mount the partition i get a 'mount: you must specify the filesystem type'

[this is what 'sudo e2fsck -n /dev/<mydev>' gives back. ]("http://pastebin.com/ifZ18HX0")(not looking good to me,,,)

dumpe2fs returns a 'Bad magic number in super-block while trying to open /dev/<mydevice>
Couldn't find valid filesystem superblock.'

any ideas?

regards, anti

---

### Post by andrewc6l on 2010-08-13
Since you have a spare copy of the corrupt filesystem, if it were me I'd try

```
sudo e2fsck -y /dev/<mydev>
```

just to see what happens. If you're lucky you'll get something back; if not, you're not out more than you've already lost. I'd do it on the copy rather than on the original just in case your hard drive's going bad.

---

### Post by Grierson Huffman on 2010-08-13
Have you tried [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")?

---

### Post by antiplex on 2010-08-15
thank you very much for your response!

i already tried letting e2fsck doing its best with ```
sudo e2fsck -y /dev/<mydev>
``` on a copy. what i got was an empty filesystem but plenty folders with only numbers as names in lost&found. files in these folgers were intact but i am not sure what percentage of files is there...

i'll try testdisk soon, thanks for the link!

---

### Post by antiplex on 2010-08-18
hi all,

after letting run testdisk in analyze for about 32 hours i can give some more information.

when i run testdisk on /dev/<mydev> i first get this output:
```
TestDisk 6.11, Data Recovery Utility, April 2009 
Christophe GRENIER <grenier@cgsecurity.org>                  
http://www.cgsecurity.org                                    
                                                             
Disk /dev/<mydev> - 966 GB / 900 GiB - CHS 1887685120 1 1    
Current partition structure:                                 
     Partition                  Start        End    Size in sectors  
                                                            
                                                            
Partition sector doesn't have the endmark 0xAA55            
                                                             
                                                             
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted    
[QuickSearch]                   
Try to locate partition
```
i decided to run a quick search (well, quick is all relative, isnt it ;) ) without the vista-option since i never had vista (or above) running on my computer.
at the end of the analysis-run i got this output (note that the values below the [continue] correspond to the partition-info when the were highlighted in the right order):
```
TestDisk 6.11, Data Recovery Utility, April 2009  
Christophe GRENIER <grenier@cgsecurity.org>       
http://www.cgsecurity.org                         
                                                  
Disk /dev/<mydev> - 966 GB / 900 GiB - CHS 1887685120 1 1   
                                                            
The harddisk (966 GB / 900 GiB) seems too small! (< 16076529 TB / 14621518 TiB)  
Check the harddisk size: HD jumpers settings, BIOS detection...                  
                                                                                 
The following partitions can't be recovered:                                     
     Partition               Start        End    Size in sectors                 
  Unixware, HURD, SCO    240470467 86177550658 85937080192 [^\~J~R               
  HFS                    253964658 3442817848 3188853191 [~Y -~R^B~H^BM- b1~P^NM-='^[r.6W~_W ^^~G] 
  Linux                  892437284 28731485884431001 28731484991993717                             
  Linux                 1010188763 31399471265301106 31399470255112343                             
                                                                
                                                                
[ Continue ]                                                    
SysV4, 43 TB / 40 TiB                                           
HFS, 1632 GB / 1520 GiB
JFS 1162430034, 14710520 TB / 13379140 TiB
JFS 2568530656, 16076528 TB / 14621517 TiB
```
the sizes don't really make sense because i know there was just one partition here and it took about all the available space. but anyhow, the arent recoverable as it seems so lets ignore them for now?
after hitting [continue] i got this output:
```
TestDisk 6.11, Data Recovery Utility, April 2009            
Christophe GRENIER <grenier@cgsecurity.org>                 
http://www.cgsecurity.org                                   
                                                            
Disk /dev/<mydev> - 966 GB / 900 GiB - CHS 1887685120 1 1   
     Partition               Start        End    Size in sectors  
D FAT32 LBA              304717824  306656959    1939136          
D HFS                    854077504  854262287     184784          
D HPFS - NTFS            868842052  868848225       6174          
D FAT12                  868856521  868877259      20739 [NO NAME]
D FAT16 LBA              883196064  883267499      71436          
D HFS                    883349798  883534581     184784          
D HPFS - NTFS            905691280  926639976   20948697          
D HPFS - NTFS            930850664  951799360   20948697          
D FAT16 LBA             1045119184 1045260343     141160          
D FAT16 LBA             1063321808 1063401040      79233          
                                                                  
                                                                  
Structure: Ok.  Use Up/Down Arrow keys to select partition.       
Use Left/Right Arrow keys to CHANGE partition characteristics:    
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted   
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 992 MB / 946 MiB
HFS+, 94 MB / 90 MiB
NTFS, 3161 KB / 3087 KiB
FAT12, 10 MB / 10 MiB
FAT16, 36 MB / 34 MiB
HFS+, 94 MB / 90 MiB
NTFS, 10725 MB / 10228 MiB
NTFS, 10725 MB / 10228 MiB
FAT16, 72 MB / 68 MiB
FAT16, 40 MB / 38 MiB       
```
now this is disappointing for the fact that my 900GB parition is not shown but interesting for a different matter: i believe that at least some of the 'partitions' found here are images i had stored on that partition. the 10725 MB NTFS-partitions are probably my virtualbox-containers where i had windows installed, at least i remember setting them to something around 10GB. there should be more images but that might be a start. note that like before, the listings after 'Enter: to continue' are corresponding to the entries listed above when they are highlighted.

i did not have the guts to restore any of the found pseudo-partitions since i would prefer to get the whole filesystem back to work.

if anybody has a good advice / ideas how i might proceed here, i'd be thankful it he/she shares it here with me.

my guess is that the filesystem (ext4) got somehow severely corrupted but i don't have a clue how i might be able to handle this, the key is maybe somewhere around that message 'Partition sector doesn't have the endmark 0xAA55', what do you think? 


regards,
anti

---

### Post by antiplex on 2011-03-19
hi there,

i finally ended giving up my corrupted partition after several tries to restore the ext4 filesystem failed.
since the harddisk shows no sign of failure itself i can't determine what happened but learned to backup more frequently to prevent such scenarios.

some particular helpful websites that provided me with great tutorials and ideas about how to rescue my data were
[LIST]
[*][myharddrivedied.com blog]("http://www.myharddrivedied.com/blog")
[*][blogentry of animesh das]("http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock")
[*][www.hanksaves.com]("http://www.hanksaves.com/hddrecovery/index.php")[/LIST]
maybe this is helpful for someone in a similar situation...

regards,
anti

---

### Post by GuiGuy on 2011-04-01
I have now had several HDD formatted as ext4 **seemingly** fail. After the usual stuffing around and not being able to recover anything the HDD were reformatted, and checked out to be OK. 

So what gives?

Well, as it turns out in each case the HDD had filled to the brim and the user (me three times :D , someone else once), ignored system warnings to free up space.

Soon afterwards the HDD failed to mount. Data recovery using a range of tools and strategies in all cases failed. Just now I am dealing with a 2T WD HDD. TestDisk is reporting it as a 1T drive and telling me there are no files other than a couple in a "lost" folder.

All in all it would be easy to conclude that ext4 is flaky if it cannot cope when the HDD has filled up.

---

### Post by GuiGuy on 2011-04-01
Quick update - I have just tried [Raise Data Recovery]("http://www.ufsexplorer.com/rdr_ext23.php") from SYSDEV Laboratories. Where everything else has failed me, this thing almost instantly showed up the complete directory tree and, if I pay the money and I will, seems set to recover the HDD. I'[ll let you know...

UPDATE 2: This is brilliant recovery software; only downside, it runs off Windows. As I said, I had all but given up on recovering this 2T HDD, the RAISE software for relatively small amount of money looks like achieving full recovery. I'm excited! Cheers

---

### Post by antiplex on 2011-04-21
gui guy,

thanks a lot for your input!
i finally decided to take a look software of sysdev laboratories you mentioned. 
there are several products available and it took a moment until i understood what the differences were:

basically there is the full package supporting all kinds of filesystems called 'ufs explorer' coming in a standard and a pro version. difference here is mainly the raid support. 
but the important thing is that **ufs explorer standard in version 4 is also available for freeBSD, _linux (ubuntu)_ and macOS**, there is also a **rescue .iso boot-cd based on ubuntu 9.04.** available.
a license of this package costs about 40€.
then there are the stripped modules of the full package called 'raise data recovery' which are limited to a specific filesystem and are only available for windows OS. but they are cheaper (~ 22€).

the trial version offers full detection functionality but allows recovery of files < 64 kb.

[here is a link]("http://www.ufsexplorer.com/products.php") to the product comparison page.

i gave the boot-cd a try and was amazed to find that this piece of software is indeed capable of recovering some of my data! many filenames seem broken, especially the directory names closer to / but a will verify the contents of some smaller files found end if the contained data is correct consider the purchase of this product.

please note that i don't mean to advertise a commercial product here, i have no connection to sysdev besides being probably a satisfied customer soon. i've been trying to recover my data for several months and this is by far the best result i got so far.


something else: guiguy mentions that his failure occured on very filled up state, in my case this was way different (fill-rate about 55-60%). nevertheless a good warning or something to look out for.

---

### Post by GuiGuy on 2011-04-22
> **antiplex said:**
> 
please note that i don't mean to advertise a commercial product here, i have no connection to sysdev besides being probably a satisfied customer soon. i've been trying to recover my data for several months and this is by far the best result i got so far.

I'll just confirm that I recovered everything off that HDD (2T's worth), except for two video files of no great consequence.

I'd give this software a plug any time, and I certainly don't mind paying for things that work. 

NB: I even paid for Win7 home premium. Because it works! ;)


Cheers

---

### Post by shaneukcouk on 2011-08-15
I have just registered here to say a big thankyou for suggesting this!  after spending days messing with testdisk, gparted, fdisk and a bunch of other apps i was able to pull the drive out the server mount it in a USB caddy and use this windows software to recover everything. Like you i had used EXT4 and filled the drive to the brim quite a few times. I will be formatting in ext3 I think this time round and not filling the drive :-) Lesson learnt!  the software is well worth the 20 GBP and works perfectly, very simple interface and gets the job done! 

A big thanks. 

Shane.

---

### Post by GuiGuy on 2011-08-16
> **shaneukcouk said:**
> Lesson learnt!  the software is well worth the 20 GBP and works perfectly, very simple interface and gets the job done! 


Great to hear. Of course you realise now that you've licensed the software you'll never ever need it again? :) 

 

Cheers

---

### Post by antiplex on 2011-10-24
> **GuiGuy said:**
> ... Of course you realise now that you've licensed the software you'll never ever need it again? :) 

never say never; being aware of the possibilities of recovery i was able to help 2 close friends that had a severe problem in their own small company by using this nice piece of software.

but the best of all is that i believe i very recently found what caused the corruption of my partition when i found an old entry in my fstab declaring an encrypted swap partition on a virtual device /dev/mapper/xyz1.
nothing happened when i did not have my encrypted data partition mounted until the day where i mounted it and my system ran out of memory and i had left that partition mounted.
interestingly the encrypted device was mounted to a different path (/dev/mapper/uvw1) but i am confident that this did not keep mkswap away from using this device as swap-area #-o

so after removing this entry from fstab, checking the drive thoroughly several times and spending many hours on restoring my data i still use this disk, but backup more often ;)

regards,
anti

---

