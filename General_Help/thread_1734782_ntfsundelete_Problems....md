---
title: "ntfsundelete Problems..."
date: 2011-04-20
forum: General Help
---

### Post by Githlar on 2011-04-20
Yeah, well I made a big mistake and deleted about 150G worth of valuable data due to a typo. Whoops. It was an "rm -R" on a folder (instead of one of it's child folders like it was supposed to be) on an NTFS partition. Realizing what I had done, I immediately (or as quickly as my fingers could fly) used ^C to break out of the 'rm' and unmounted the drive to prevent any further potential damage.

After this fiasco I read about ntfsundelete from ntfsprogs. However, it can't seem to find ANYTHING of any value in its output. The only file it finds that has a name is "bootex.log," everything else is nameless. A lot of the nameless files are the exact same size as well - so they're probably not what I'm looking for.

So, I also tried using one of my favorite data recovery suites: testdisk/photorec. It's the same thing with these too, they only find bootex.log.

The drive I'm trying to recover from is a 1TB WD My Passport 2.5" with the factory partition on it.

The partition info is as follows:
```
me@domain:~$ sudo ntfsinfo -m /dev/sdb1
Volume Information 
	Name of device: /dev/sdb1
	Device state: 11
	Volume Name: TB
	Volume State: 1
	Volume Version: 3.1
	Sector Size: 512
	Cluster Size: 4096
	Volume Size in Clusters: 244017308
MFT Information 
	MFT Record Size: 1024
	MFT Zone Multiplier: 1
	MFT Data Position: 24
	MFT Zone Start: 0
	MFT Zone End: 30502167
	MFT Zone Position: 4
	Current Position in First Data Zone: 30502167
	Current Position in Second Data Zone: 0
	LCN of Data Attribute for FILE_MFT: 4
	FILE_MFTMirr Size: 4
	LCN of Data Attribute for File_MFTMirr: 122008654
	Size of Attribute Definition Table: 2560
FILE_Bitmap Information 
	FILE_Bitmap MFT Record Number: 6
	State of FILE_Bitmap Inode: 0
	Length of Attribute List: 0
	Attribute List: (null)
	Number of Attached Extent Inodes: 0
FILE_Bitmap Data Attribute Information
	Decompressed Runlist: not done yet
	Base Inode: 6
	Attribute Types: not done yet
	Attribute Name Length: 0
	Attribute State: 3
	Attribute Allocated Size: 30502912
	Attribute Data Size: 30502168
	Attribute Initialized Size: 30502168
	Attribute Compressed Size: 0
	Compression Block Size: 0
	Compression Block Size Bits: 0
	Compression Block Clusters: 0
```

I'm kind of at a loss now. I can't exactly image my drive because of its size, but short of going through the drive byte-by-byte and looking for the 7z (the files I'm trying to recover) file header and trying to figure out where the file ends, I don't know what to do.

---

### Post by Githlar on 2011-04-20
Wow, it appears I'm a total idiot. I guess I was able to break out of the loop before 'rm' actually started deleting stuff. Perhaps I was too busy panicking to see that all my files are still there! *WHEW*

So, basically... I spent hours trying to recover files that were never gone in the first place... that would explain it! So... time to back up this data elsewhere in case this happens again!

---

