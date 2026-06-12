---
title: "gparted cant add unallocated memory to windows partition"
date: 2009-10-10
forum: General Help
---

### Post by chriszatch on 2009-10-10
I'm trying to add some space to my windows partition. I took space from my linux partition and tried to allocate it to the windows partition but all that happens is that it becomes unallocated space. It gets to the part where it starts growing the windows partition but at 5:30 minutes left (pretty consistently might i add) it stops, then i get an error screen after a while that says there was an error while applying the operation then it does nothing so i close the operation window. When gparted scans my system, the space got taken off of linux and didnt allocate to windows. I tried it again and got the same thing. Rebooted, same thing. ran off live cd, same thing. So i thought maybe my hard drive was bad, so i tried to put it back in linux. it went back in without any problems and linux runs fine. Is there anything else i should try? how can i get this to work? I am willing to format my windows partition and re-install, but thats a pain in the butt and i would rather not go through that process. 

System stuff: hp dv6000 jaunty 32 bit. Dual boot windows and ubuntu. the windows os is vista, and it is a legit version. The specific operation in gparted is 'move /dev/sda2 to the left and grow it from 19.72 GiB to 25.39 GiB.'

---

### Post by chriszatch on 2009-10-10
am i in the right forum? sorry if this should be in another

---

### Post by chriszatch on 2009-10-10
okay, i tried just moving the windows partition to the right, without adding any memory, (but the estimated number changed, which i didnt get) anyway, it didnt work either, so i saved the details. here they are. 
GParted 0.4.3

Libparted 1.8.8

Move /dev/sda2 to the left and grow it from 19.72 GiB to 19.73 GiB  00:09:41    ( ERROR )
    	
calibrate /dev/sda2  00:00:01    ( SUCCESS )
    	
path: /dev/sda2
start: 258439168
end: 299804671
size: 41365504 (19.72 GiB)
calculate new size and position of /dev/sda2  00:00:00    ( SUCCESS )
    	
requested start: 246549555
requested end: 287916929
requested size: 41367375 (19.73 GiB)
new start: 246549555
new end: 287916929
new size: 41367375 (19.73 GiB)
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:04    ( SUCCESS )
    	
ntfsresize -P -i -f -v /dev/sda2
    	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 21179134464 bytes (21180 MB)
Current device size: 21179138048 bytes (21180 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 20161 MB (95.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 19951 MB 0
Multi-Record : 21109 MB 50161
$MFTMirr : 10590 MB 1
Compressed : 21056 MB 52061
Sparse : 20151 MB 49994
Ordinary : 21180 MB 68388
You might resize at 20160106496 bytes or 20161 MB (freeing 1019 MB).
Please make a test run using both the -n and -s options before real resizing!
move partition to the left  00:00:11    ( SUCCESS )
    	
old start: 258439168
old end: 299804671
old size: 41365504 (19.72 GiB)
new start: 246549555
new end: 287915058
new size: 41365504 (19.72 GiB)
move file system to the left  00:09:13    ( ERROR )
    	
perform read-only test  00:09:13    ( ERROR )
    	
using internal algorithm
read 41365504 sectors
finding optimal blocksize
    	
read 65536 sectors using a blocksize of 128 sectors  00:00:01    ( SUCCESS )
    	
65536 of 65536 read
1.44718 seconds
read 65536 sectors using a blocksize of 256 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 read
1.77124 seconds
read 65536 sectors using a blocksize of 512 sectors  00:00:01    ( SUCCESS )
    	
65536 of 65536 read
1.6163 seconds
read 65536 sectors using a blocksize of 1024 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 read
1.57464 seconds
read 65536 sectors using a blocksize of 2048 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 read
1.58958 seconds
read 65536 sectors using a blocksize of 4096 sectors  00:00:01    ( SUCCESS )
    	
65536 of 65536 read
1.47272 seconds
read 65536 sectors using a blocksize of 8192 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 read
1.61354 seconds
read 65536 sectors using a blocksize of 16384 sectors  00:00:01    ( SUCCESS )
    	
65536 of 65536 read
1.44879 seconds
read 65536 sectors using a blocksize of 32768 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 read
1.44023 seconds
read 65536 sectors using a blocksize of 65536 sectors  00:00:01    ( SUCCESS )
    	
65536 of 65536 read
1.68402 seconds
optimal blocksize is 32768 sectors (16.00 MiB)
read 40710144 sectors using a blocksize of 32768 sectors  00:08:58    ( ERROR )
    	
20328448 of 40710144 read
Error while reading block at sector 279422976
20983808 sectors read
rollback last change to the partition table  00:00:12    ( SUCCESS )
    	
move partition to the right  00:00:12    ( SUCCESS )
    	
old start: 246549555
old end: 287915058
old size: 41365504 (19.72 GiB)
new start: 258439168
new end: 299804671
new size: 41365504 (19.72 GiB)
libparted messages    ( INFO )
    	
Input/output error during read on /dev/sda

---

