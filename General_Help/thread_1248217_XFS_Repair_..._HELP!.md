---
title: "XFS_Repair ... HELP!"
date: 2009-08-23
forum: General Help
---

### Post by datarhythm on 2009-08-23
After some issues with mdadm and my array, I finally was able to get it restarted but not all the files were visible/readable. Poking around, I realized it was most likely an issue with my filesystem (XFS). I attempted to do a repair with v3.0.1 and this is what I get (below). Due to the length, I had to take snippets of it (over 40K lines of output). Any ideas what the issue is? Is my data toast? 


Phase 1 - find and verify superblock...
Phase 2 - using internal log
        - zero log...
        - scan filesystem freespace and inode maps...
bad magic # 0x584bf1a6 in inobt block 0/1284031
expected level 0 got 2874 in inobt block 0/1284031
dubious inode btree block header 0/1284031
badly aligned inode rec (starting inode = 20514529)
ir_freecount/free mismatch, inode chunk 0/20514529, freecount 20543508 nfree 18
badly aligned inode rec (starting inode = 1234182162)
.
.
.
expected level 1 got 258 in inobt block 7/528143
bad magic # 0x6e73235f in inobt block 7/1000
bad magic # 0x494e81ed in inobt block 10/2325539
expected level 1 got 258 in inobt block 10/2325539
bad magic # 0x2e517443 in btbno block 48/2316593
expected level 0 got 28530 in btbno block 48/2316593
block (48,5394796) multiply claimed by bno space tree, state - 1
block (48,5394797) multiply claimed by bno space tree, state - 1
block (48,5394798) multiply claimed by bno space tree, state - 1
block (48,5394799) multiply claimed by bno space tree, state - 1
block (48,5394800) multiply claimed by bno space tree, state - 1
block (48,5394801) multiply claimed by bno space tree, state - 1
block (48,5394802) multiply claimed by bno space tree, state - 1
block (48,5394803) multiply claimed by bno space tree, state - 1
.
.
.
Phase 3 - for each AG...
        - scan and clear agi unlinked lists...
found inodes not in the inode allocation tree
        - process known inodes and perform inode discovery...
        - agno = 0
bad directory block magic # 0xe6980466 in block 0 for directory inode 136
corrupt block 0 in directory inode 136
	will junk block
no . entry for directory 136
no .. entry for directory 136
problem with directory contents in inode 136
cleared inode 136
bad directory block magic # 0x4b7e0c3b in block 0 for directory inode 137
corrupt block 0 in directory inode 137
	will junk block
no . entry for directory 137
no .. entry for directory 137
problem with directory contents in inode 137
cleared inode 137
bad directory block magic # 0x784d861c in block 0 for directory inode 140
corrupt block 0 in directory inode 140
	will junk block
no . entry for directory 140
no .. entry for directory 140
problem with directory contents in inode 140
cleared inode 140
bad directory block magic # 0x6bd8fb47 in block 0 for directory inode 172
corrupt block 0 in directory inode 172
	will junk block
no . entry for directory 172
no .. entry for directory 172
problem with directory contents in inode 172
cleared inode 172
bad directory block magic # 0xb036e8c5 in block 0 for directory inode 177
corrupt block 0 in directory inode 177
	will junk block
no . entry for directory 177
no .. entry for directory 177
problem with directory contents in inode 177
cleared inode 177
bad magic number 0x2e0d on inode 256
bad version number 0x28 on inode 256
bad (negative) size -8154101291994316643 on inode 256
bad magic number 0x94d3 on inode 257
bad version number 0xffffffb7 on inode 257
bad (negative) size -6515628478204664961 on inode 257
.
.
.
local inode 200201 data fork is too large (size = 14587, max = 156)
bad data fork in inode 200201
cleared inode 200201
local inode 200202 data fork is too large (size = 53642, max = 156)
bad data fork in inode 200202
cleared inode 200202
local inode 200203 data fork is too large (size = 60910, max = 156)
bad data fork in inode 200203
cleared inode 200203
local inode 200204 data fork is too large (size = 321, max = 156)
bad data fork in inode 200204
cleared inode 200204
local inode 200205 data fork is too large (size = 89360, max = 156)
bad data fork in inode 200205
cleared inode 200205
data fork in ino 200209 claims free block 17313851
data fork in ino 200209 claims free block 17313852
data fork in ino 200209 claims free block 17313853
data fork in ino 200209 claims free block 17313854
data fork in ino 200209 claims free block 17313855
data fork in ino 200209 claims free block 17313856
data fork in ino 200209 claims free block 17313857
.
.
.
bad magic number 0x6174 on inode 200253
bad version number 0x65 on inode 200253
bad inode format in inode 200253
bad magic number 0x6c62 on inode 200254
bad version number 0x3e on inode 200254
bad inode format in inode 200254
bad magic number 0x3c53 on inode 200255
bad version number 0x72 on inode 200255
bad inode format in inode 200255
bad magic number 0x5844 on inode 200224, resetting magic number
bad inode format in inode 200224
cleared inode 200224
bad magic number 0x0 on inode 200225, resetting magic number
bad version number 0x0 on inode 200225, resetting version number
imap claims a free inode 200225 is in use, correcting imap and clearing inode
cleared inode 200225
bad magic number 0x7265 on inode 200226, resetting magic number
bad version number 0x2f on inode 200226, resetting version number
bad inode format in inode 200226
cleared inode 200226
bad magic number 0x6c61 on inode 200227, resetting magic number
bad version number 0x64 on inode 200227, resetting version number
bad inode format in inode 200227
cleared inode 200227
.
.
.
data fork in ino 200256 claims free block 50867210
data fork in ino 200256 claims free block 50867211
data fork in ino 200256 claims free block 50867212
data fork in ino 200256 claims free block 50867213
data fork in ino 200256 claims free block 50867214
data fork in ino 200256 claims free block 50867215
data fork in ino 200256 claims free block 50867216
.
.
.

Segmentation fault

---

