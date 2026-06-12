---
title: "ext3/4 hdd help"
date: 2010-12-10
forum: General Help
---

### Post by v1gorus on 2010-12-10
i bought a internal 2 tb and planned to use it for storage so i got a enclosure for it. i noticed that i was unable drop 8gb iso files in to the hdd. so to fix this i formated it to ext3/4 i did this by right clicking on the drive and format ext3/4. i am building a computer and now need to use the hdd as a main drive for my comp. so want to install win7 on there. i have no were to drop the data off(roughly 1.4tb). i went into disk ultitry to check if i could made the partition smaller and it showed me this: 
[http://farm5.static.flickr.com/4147/5173029280_7e43940371_b.jpg](http://farm5.static.flickr.com/4147/5173029280_7e43940371_b.jpg)
basically saying that the drive isnt partitioned at all. i tried to install win7 on there another way by booting from disk and seeing if the disc would allow me to install it on my drive and win7 denied. i dont know what to do.

---

### Post by cottfcfan on 2010-12-10
If I understand what your saying, you need to burn a Gparted live CD, 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
boot from that. Shrink your ext3/4 to whatever you need, then format the rest as NTFS.
 You should be able to install your win7 on that using a custom install.

---

### Post by v1gorus on 2010-12-11
> **cottfcfan said:**
> If I understand what your saying, you need to burn a Gparted live CD, 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
boot from that. Shrink your ext3/4 to whatever you need, then format the rest as NTFS.
 You should be able to install your win7 on that using a custom install.
i went into gparted and saw this in information for the drive:
[http://farm6.static.flickr.com/5129/5251931097_7d0c2c8640_b.jpg](http://farm6.static.flickr.com/5129/5251931097_7d0c2c8640_b.jpg)
and i saw this when i when to resize it:
[http://farm6.static.flickr.com/5127/5251933733_b71abbcd5f_b.jpg](http://farm6.static.flickr.com/5127/5251933733_b71abbcd5f_b.jpg)
i changed the free space preceding and free space following to various intergers and the resize button wouldnt allow me to click. also wat does MiB mean?

---

### Post by cottfcfan on 2010-12-11
Not too sure.
In your 1st attachment it says at the bottom you need etfsprogs v1.41.
This is in synaptic, try installing that 1st and see if that makes a difference.
Mib is just the size in megabytes.

---

### Post by v1gorus on 2010-12-11
> **cottfcfan said:**
> Not too sure.
In your 1st attachment it says at the bottom you need etfsprogs v1.41.
This is in synaptic, try installing that 1st and see if that makes a difference.
Mib is just the size in megabytes.
i installed it however it still gives me the same info.
here is some code from the install process:
```

icount_store(42, 42) = 42 (OK)
icount_store(1, 1) = 1 (OK)
icount_store(2, 2) = 2 (OK)
icount_store(3, 3) = 3 (OK)
icount_store(10, 1) = 1 (OK)
icount_store(42, 0) = 0 (OK)
icount_increment(5) = 1 (OK)
icount_increment(5) = 2 (OK)
icount_increment(5) = 3 (OK)
icount_increment(5) = 4 (OK)
icount_decrement(5) = 3 (OK)
icount_decrement(5) = 2 (OK)
icount_decrement(5) = 1 (OK)
icount_decrement(5) = 0 (OK)
icount_fetch(10) = 1 (OK)
icount_fetch(1) = 1 (OK)
icount_fetch(2) = 2 (OK)
icount_fetch(3) = 3 (OK)
icount_increment(1) = 2 (OK)
icount_decrement(2) = 1 (OK)
icount_decrement(2) = 0 (OK)
icount_fetch(12) = 0 (OK)
icount size is 0
LD_LIBRARY_PATH=../../lib DYLD_LIBRARY_PATH=../../lib ./tst_super_size
Size of struct ext2_super_block is 1024
LD_LIBRARY_PATH=../../lib DYLD_LIBRARY_PATH=../../lib ./tst_csum
csum0000: UUID 234897e7cfe8254fdbecae4b88a7fabe(241f), grp 0(df47): d3a4=d3a4
csum0001: UUID 234897e7cfe8254fdbecae4b88a7fabe(241f), grp 1(2346): 3ea5=3ea5
csumffff: UUID 234897e7cfe8254fdbecae4b88a7fabe(241f), grp 2(6746): 49a5=49a5
csum_set: UUID 234897e7cfe8254fdbecae4b88a7fabe(241f), grp 0(df47): d3a4=d3a4
new_uuid: UUID 30303030303030303030303030303030(766d), grp 0(76fd): a4ac=a4ac
csum_new: UUID 30303030303030303030303030303030(766d), grp 0(76fd): a4ac=a4ac
csum_blk: UUID 30303030303030303030303030303030(766d), grp 0(76fd): 2e14=2e14
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ext2fs'
making check in lib/blkid
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/blkid'
    LD tst_cache
    LD tst_dev
    LD tst_devname
    LD tst_devno
    LD tst_getsize
    LD tst_probe
    LD tst_read
    LD tst_resolve
    LD tst_save
./save.c: In function ‘blkid_flush_cache’:
./save.c:146: warning: ignoring return value of ‘link’, declared with attribute warn_unused_result
    LD tst_tag
Creating test_probe...
    CC tst_types.c
    LD tst_types
./test_probe
cramfs: ok
ext2: ok
ext3: ok
fat: ok
fat32_label_64MB: ok
iso: ok
jbd: ok
jfs: ok
minix: ok
ocfs2: ok
reiser3: ok
reiser4: ok
romfs: ok
small-fat32: ok
swap0: mkswap: does not support swapspace version 0.
ok
swap1: ok
udf: ok
xfs: ok
zfs: ok
19 tests succeeded    0 tests failed
./tst_types
The blkid_types.h types are correct.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/blkid'
making check in intl
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/intl'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/intl'
making check in e2fsck
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/e2fsck'
    LD tst_refcount
    LD tst_region
LD_LIBRARY_PATH=../lib DYLD_LIBRARY_PATH=../lib ./tst_refcount
Creating refcount with size 5
Storing blk 3 with value 3
Storing blk 4 with value 4
Storing blk 1 with value 1
Storing blk 8 with value 8
Storing blk 2 with value 2
Storing blk 4 with value 0
Storing blk 2 with value 0
Refcount_collapse: size was 5, now 3
Storing blk 6 with value 6
Refcount validation OK.
Storing blk 4 with value 4
Refcount_collapse: size was 5, now 5
Storing blk 2 with value 2
bcode_fetch(1) returns 1
bcode_fetch(2) returns 2
bcode_increment(3) returns 4
bcode_increment(3) returns 5
bcode_decrement(4) returns 3
Storing blk 4 with value 4
Refcount validation OK.
Storing blk 20 with value 20
Storing blk 40 with value 40
Storing blk 30 with value 30
Storing blk 10 with value 10
bcode_decrement(30) returns 29
bcode_fetch(30) returns 29
bcode_decrement(2) returns 1
bcode_decrement(2) returns 0
Refcount_collapse: size was 10, now 9
    blk=1, count=1
    blk=3, count=5
    blk=4, count=4
    blk=6, count=6
    blk=8, count=8
    blk=10, count=10
    blk=20, count=20
    blk=30, count=29
    blk=40, count=40
Refcount validation OK.
Freeing refcount
LD_LIBRARY_PATH=../lib DYLD_LIBRARY_PATH=../lib ./tst_region
Creating region with args(1, 1001)
Printing region (min=1. max=1001)
    
Region_allocate(10, 10) returns 0
Region_allocate(30, 10) returns 0
Printing region (min=1. max=1001)
    (10, 20)  (30, 40)  
Region_allocate(1, 15) returns 1
Region_allocate(15, 8) returns 1
Region_allocate(1, 20) returns 1
Region_allocate(1, 8) returns 0
Printing region (min=1. max=1001)
    (1, 9)  (10, 20)  (30, 40)  
Region_allocate(40, 10) returns 0
Printing region (min=1. max=1001)
    (1, 9)  (10, 20)  (30, 50)  
Region_allocate(22, 5) returns 0
Printing region (min=1. max=1001)
    (1, 9)  (10, 20)  (22, 27)  (30, 50)  
Region_allocate(27, 3) returns 0
Printing region (min=1. max=1001)
    (1, 9)  (10, 20)  (22, 50)  
Region_allocate(20, 2) returns 0
Printing region (min=1. max=1001)
    (1, 9)  (10, 50)  
Region_allocate(49, 1) returns 1
Region_allocate(50, 5) returns 0
Region_allocate(9, 2) returns 1
Region_allocate(9, 1) returns 0
Printing region (min=1. max=1001)
    (1, 55)  
LD_LIBRARY_PATH=../lib DYLD_LIBRARY_PATH=../lib ./tst_crc32
Testing length 64...
All test complete.  No failures expected.
LD_LIBRARY_PATH=../lib DYLD_LIBRARY_PATH=../lib ./tst_problem
e2fsck problem table verified
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/e2fsck'
making check in debugfs
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/debugfs'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/debugfs'
making check in misc
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/misc'
    LD base_device
./base_device < ./base_device.tst > base_device.out
cmp ./base_device.tst base_device.out
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/misc'
making check in resize
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/resize'
LD_LIBRARY_PATH=../lib DYLD_LIBRARY_PATH=../lib ./test_extent < ./test_extent.in \
        > test_extent.out
Test succeeded.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/resize'
making check in tests/progs
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/tests/progs'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/tests/progs'
making check in po
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/po'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/po'
making check in tests
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/tests'
/bin/cp ./mke2fs.conf.in mke2fs.conf
Creating test_script...
Running e2fsprogs test suite...
 
d_loaddump: debugfs load/dump test: ok
e_brel_bma: block relocation table using the memory array implementation: skipped
e_icount_normal: inode counting abstraction optimized for storing inode counts: ok
e_icount_opt: inode counting abstraction optimized for counting: ok
e_irel_ima: inode relocation table using the memory array implementation: skipped
f_16384_block: 16384 byte blocksize: ok
f_8192_block: 8192 byte blocksize: ok
f_bad_disconnected_inode: Disconnected inode with bad fields: ok
f_bad_local_jnl: test for corrupt local journal (bad V1->V2 journal upgrade): ok
f_badbblocks: illegal blocks in bad block inode: ok
f_baddir: corrupted directory entries: ok
f_baddir2: salvage last directory entry: ok
f_baddotdir: bad '.' and '..' entries: ok
f_badinode: corrupted inode entries: ok
f_badjour_indblks: corruption in journal inode's indirect blocks: ok
f_badjourblks: Illegal blocks in journal inode (and backup in superblock): ok
f_badorphan: corrupted orphan list: ok
f_badprimary: bad blocks in the primary superblock and group descriptors: ok
f_badroot: file in root directory inode: ok
f_badsymlinks: corrupted symlinks: ok
f_badtable: bad blocks in bitmaps and inode table: ok
f_bbfile: bad blocks in files: ok
f_bbinode: bad blocks in inode table: ok
f_big_sparse: big sparse file: ok
f_bitmaps: corrupted inode and block bitmaps: ok
f_clear_xattr: clearing i_file_acl when !ext_attr feature: ok
f_crashdisk: Superblock with illegal values: ok
f_dir_bad_mode: directory with corrupted i_mode: ok
f_dirlink: directory hard links: ok
f_dup: blocks claimed by two different files: ok
f_dup2: blocks claimed by three different files: ok
f_dup3: blocks claimed by one file multiple times: ok
f_dup4: find all directory pathnames: ok
f_dup_de: duplicate directory entries: ok
f_dup_de2: duplicate directory entries for non-indexed dirs: ok
f_dup_resize: blocks claimed by the resize inode and another inode: ok
f_dupdot: duplicate '.' and '..' entries: ok
f_dupfsblks: blocks claimed by a file and bitmaps or inode tables: ok
f_dupsuper: blocks claimed by a file and superblock or group descriptors: ok
f_ea_checks: extended attribute block checks: ok
f_end-bitmap: corruption at end of block bitmap: ok
f_expand: expanding lost+found: ok
f_ext_journal: ok
f_extent_bad_node: bad interior node in extent tree: ok
f_extents: basic extents support: ok
f_extents2: multiply claimed blocks in extents and other illegal extents: ok
f_extra_journal: Valid journal inode, but has_journal feature not present: ok
f_fast_symlink_extents: fast symlink with extents flag set: ok
f_file_acl_high: i_file_acl_high should be zero: ok
f_filetype: set filetype information and illegal special files: ok
f_full_bg: inode table in last block of first bg: ok
f_h_badnode: hash directory with bad HTREE nodes: ok
f_h_badroot: bad htree root nodes: ok
f_h_normal: Normal (signed) HTREE directory: ok
f_h_reindex: reindex HTREE Directory with different hash seed: ok
f_h_unsigned: Unsigned HTREE directory: ok
f_holedir: directory with holes and illegal blocks: ok
f_holedir2: directories with holes and zero i_size: ok
f_hurd: GNU/Hurd specific tests: ok
f_illbbitmap: illegal block bitmap: ok
f_illibitmap: illegal inode bitmap: ok
f_illitable: illegal inode table: ok
f_illitable_flexbg: illegal inode table with FLEX_BG: ok
f_imagic: non-imagic filesystem with imagic inodes: ok
f_imagic_fs: imagic filesystem with imagic inodes: ok
f_journal: recover journal from corrupted inode table: ok
f_lotsbad: too many illegal blocks in inode: ok
f_lpf: missing lost+found: ok
f_lpf2: create lost+found and reconnect lost directory: ok
f_lpffile: lost+found is not a directory: ok
f_messy_inode: bad file and directory acl pointers: ok
f_miss_blk_bmap: missing block bitmap: ok
f_miss_journal: Non-existent journal inode: ok
f_misstable: missing inode table: ok
f_mke2fs2b: mke2fs version 0.2b created filesystem: ok
f_noroot: missing root directory: ok
f_okgroup: 8193 block long filesystem: ok
f_orphan: clearing orphan inodes: ok
f_orphan_dotdot_ft: filetype of .. in orphaned directories: ok
f_overfsblks: overlapping inode and block bitmaps: ok
f_preen: preen shouldn't destroy backup superblocks: ok
f_recnect_bad: Reconnecting bad inode: ok
f_reconnect: simple disconnected file inode: ok
f_rehash_dir: ok
f_resize_inode: e2fsck with resize_inode: ok
f_salvage_dir: salvage corrupted directories: ok
f_selinux: SE Linux generated symlinks with EA data: ok
f_special_ea: Special files with extended attributes: ok
f_summary_counts: incorrect inode/block free counts: ok
f_uninit_last_uninit: last group has BLOCK_UNINIT set: ok
f_unsorted_EAs: unsorted EAs in inode should not be deleted: ok
f_unused_itable: Invalid bg_unused_itable shouldn't move files to lost+found: ok
f_valid_ea_in_inode: valid ea-in-inode examplars: ok
f_zero_group: fallback for damaged group descriptors: ok
f_zero_inode_size: superblock with a zero inode size: ok
f_zero_super: fallback for damaged superblock: ok
m_dasd_bs: 2048 byte sector devices: ok
m_large_file: largefile fs type: ok
m_meta_bg: meta blockgroup feature: ok
m_mkfs_overhead: test bg overhead calculation: ok
m_no_opt: no filesystem extensions: ok
m_raid_opt: raid options: ok
m_std: standard filesystem options: ok
m_uninit: uninitialized group feature: ok
r_inline_xattr: shrinking filesystem with in-inode extended attributes: ok
r_move_itable: filesystem resize which requires moving the inode table: ok
r_resize_inode: filesystem resize with a resize_inode present: ok
u_mke2fs: e2undo with mke2fs: ok
u_tune2fs: e2undo with tune2fs: ok
107 tests succeeded    0 tests failed
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/tests'
igor@igor-laptop:/media/Fatazz_/e2fsprogs-1.41.12$ sudo make install
[sudo] password for igor: 
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12'
make[1]: `lib/ext2fs/ext2_types.h' is up to date.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12'
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12'
make[1]: `lib/blkid/blkid_types.h' is up to date.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12'
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12'
make[1]: `lib/uuid/uuid_types.h' is up to date.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12'
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/et'
make[1]: `compile_et' is up to date.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/et'
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ext2fs'
make[1]: `ext2_err.h' is up to date.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ext2fs'
making all in lib/et
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/et'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/et'
making all in lib/ss
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ss'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ss'
making all in lib/e2p
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/e2p'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/e2p'
making all in lib/uuid
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/uuid'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/uuid'
making all in lib/ext2fs
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ext2fs'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ext2fs'
making all in lib/blkid
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/blkid'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/blkid'
making all in intl
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/intl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/intl'
making install in e2fsck
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/e2fsck'
    MKINSTALLDIRS /sbin /usr/share/man/man8
    INSTALL /sbin/e2fsck
    LINK /sbin/fsck.ext2
    LINK /sbin/fsck.ext3
    LINK /sbin/fsck.ext4
    LINK /sbin/fsck.ext4dev
    INSTALL_DATA /usr/share/man/man8/e2fsck.8
    INSTALL_DATA /usr/share/man/man5/e2fsck.conf.5
    LINK /usr/share/man/man8/fsck.ext2.8
    LINK /usr/share/man/man8/fsck.ext3.8
    LINK /usr/share/man/man8/fsck.ext4.8
    LINK /usr/share/man/man8/fsck.ext4dev.8
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/e2fsck'
making install in debugfs
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/debugfs'
    MKINSTALLDIRS /sbin /usr/share/man/man8
    INSTALL /sbin/debugfs
    INSTALL_DATA /usr/share/man/man8/debugfs.8
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/debugfs'
making install in misc
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/misc'
    MKINSTALLDIRS /usr/sbin /sbin /usr/bin /usr/share/man/man1 /usr/share/man/man8 /usr/lib /etc
    INSTALL /sbin/mke2fs
    INSTALL /sbin/badblocks
    INSTALL /sbin/tune2fs
    INSTALL /sbin/dumpe2fs
    INSTALL /sbin/blkid
    INSTALL /sbin/logsave
    INSTALL /sbin/e2image
    INSTALL /sbin/fsck
    INSTALL /sbin/e2undo
    INSTALL /usr/sbin/mklost+found
    INSTALL /usr/sbin/filefrag
    INSTALL /usr/sbin/e2freefrag
    INSTALL /usr/sbin/uuidd
    LINK /sbin/mkfs.ext2
    LINK /sbin/mkfs.ext3
    LINK /sbin/mkfs.ext4
    LINK /sbin/mkfs.ext4dev
    LINK /sbin/findfs
    INSTALL /usr/bin/chattr
    INSTALL /usr/bin/lsattr
    INSTALL /usr/bin/uuidgen
    INSTALL /usr/lib/e2initrd_helper
    INSTALL_DATA /usr/share/man/man8/tune2fs.8
    INSTALL_DATA /usr/share/man/man8/mklost+found.8
    INSTALL_DATA /usr/share/man/man8/mke2fs.8
    INSTALL_DATA /usr/share/man/man8/dumpe2fs.8
    INSTALL_DATA /usr/share/man/man8/badblocks.8
    INSTALL_DATA /usr/share/man/man8/e2label.8
    INSTALL_DATA /usr/share/man/man8/findfs.8
    INSTALL_DATA /usr/share/man/man8/blkid.8
    INSTALL_DATA /usr/share/man/man8/e2image.8
    INSTALL_DATA /usr/share/man/man8/logsave.8
    INSTALL_DATA /usr/share/man/man8/filefrag.8
    INSTALL_DATA /usr/share/man/man8/e2freefrag.8
    INSTALL_DATA /usr/share/man/man8/e2undo.8
    INSTALL_DATA /usr/share/man/man8/uuidd.8
    INSTALL_DATA /usr/share/man/man8/fsck.8
    LINK mkfs.ext2.8
    LINK mkfs.ext3.8
    LINK mkfs.ext4.8
    LINK mkfs.ext4dev.8
    INSTALL_DATA /usr/share/man/man1/chattr.1
    INSTALL_DATA /usr/share/man/man1/lsattr.1
    INSTALL_DATA /usr/share/man/man1/uuidgen.1
    INSTALL_DATA /usr/share/man/man5/mke2fs.conf.5
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/misc'
making install in resize
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/resize'
    MKINSTALLDIRS /sbin /usr/share/man/man8
    INSTALL /sbin/resize2fs
    INSTALL_DATA /usr/share/man/man8/resize2fs.8
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/resize'
making install in tests/progs
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/tests/progs'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/tests/progs'
making install in po
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/po'
/bin/sh ../config/mkinstalldirs /usr/share
installing ca.gmo as /usr/share/locale/ca/LC_MESSAGES/e2fsprogs.mo
installing cs.gmo as /usr/share/locale/cs/LC_MESSAGES/e2fsprogs.mo
installing de.gmo as /usr/share/locale/de/LC_MESSAGES/e2fsprogs.mo
installing es.gmo as /usr/share/locale/es/LC_MESSAGES/e2fsprogs.mo
installing fr.gmo as /usr/share/locale/fr/LC_MESSAGES/e2fsprogs.mo
installing id.gmo as /usr/share/locale/id/LC_MESSAGES/e2fsprogs.mo
installing it.gmo as /usr/share/locale/it/LC_MESSAGES/e2fsprogs.mo
installing nl.gmo as /usr/share/locale/nl/LC_MESSAGES/e2fsprogs.mo
installing pl.gmo as /usr/share/locale/pl/LC_MESSAGES/e2fsprogs.mo
installing sv.gmo as /usr/share/locale/sv/LC_MESSAGES/e2fsprogs.mo
installing tr.gmo as /usr/share/locale/tr/LC_MESSAGES/e2fsprogs.mo
installing vi.gmo as /usr/share/locale/vi/LC_MESSAGES/e2fsprogs.mo
installing zh_CN.gmo as /usr/share/locale/zh_CN/LC_MESSAGES/e2fsprogs.mo
if test "e2fsprogs" = "gettext-tools"; then \
      /bin/sh ../config/mkinstalldirs /usr/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed en@quot.header en@boldquot.header insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/po'
making install-shlibs in lib/et
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/et'
make[1]: Nothing to be done for `install-shlibs'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/et'
making install-shlibs in lib/ss
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ss'
make[1]: Nothing to be done for `install-shlibs'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ss'
making install-shlibs in lib/e2p
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/e2p'
make[1]: Nothing to be done for `install-shlibs'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/e2p'
making install-shlibs in lib/uuid
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/uuid'
make[1]: Nothing to be done for `install-shlibs'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/uuid'
making install-shlibs in lib/ext2fs
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ext2fs'
make[1]: Nothing to be done for `install-shlibs'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/ext2fs'
making install-shlibs in lib/blkid
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/blkid'
make[1]: Nothing to be done for `install-shlibs'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/lib/blkid'
making install-shlibs in intl
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/intl'
make[1]: Nothing to be done for `install-shlibs'.
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/intl'
make[1]: Entering directory `/media/Fatazz_/e2fsprogs-1.41.12/doc'
    MAKEINFO libext2fs.info
Makeinfo is missing. Info documentation will not be built.
    TEXI2DVI libext2fs.dvi
make[1]: texi2dvi: Command not found
make[1]: [libext2fs.dvi] Error 127 (ignored)
    MKINSTALLDIRS /usr/share/info
    INSTALL_DATA /usr/share/info/libext2fs.info*
/usr/bin/install: cannot stat `libext2fs.info*': No such file or directory
make[1]: [install-doc-libs] Error 1 (ignored)
    GZIP /usr/share/info/libext2fs.info*
gzip: /usr/share/info/libext2fs.info*: No such file or directory
make[1]: [install-doc-libs] Error 1 (ignored)
make[1]: Leaving directory `/media/Fatazz_/e2fsprogs-1.41.12/doc'
if test ! -d e2fsck && test ! -d debugfs && test ! -d misc && test ! -d ext2ed ; then make install-libs ; fi


```

---

### Post by cottfcfan on 2010-12-12
When you go into system monitor & File Systems, is the drive listed there?

---

### Post by v1gorus on 2010-12-13
> **cottfcfan said:**
> When you go into system monitor & File Systems, is the drive listed there?
i did this thru a live cd. i messed you with something and not none of my usb ports work with data drive(hdd,usb, and sd slot) but it does power them up.
yes it does appear in my system monitor.
[http://farm6.static.flickr.com/5050/5259807042_14ab0e6896_b.jpg](http://farm6.static.flickr.com/5050/5259807042_14ab0e6896_b.jpg)
went i was in disk utility, the option for format drive was available but i didn't know what it does.
[http://farm6.static.flickr.com/5169/5259807032_b68fd25b8d_b.jpg](http://farm6.static.flickr.com/5169/5259807032_b68fd25b8d_b.jpg)

---

### Post by cottfcfan on 2010-12-14
From what I can see in the pictures you've uploaded everything appears to be in order. So can't understand why you can't access the drive to write to it.
 If there's nothing on the drive you want saving I'd be tempted to reformat the whole drive from within Ubuntu, unmount it 1st and reformat with gparted.
 Other than that i'm at a loss as to what the problem is.

edit.. sorry i forgot from your 1st thread you can't do that.
Think someone a bit more tech savy than me, needs to look at this.

---

### Post by dandnsmith on 2010-12-14
I'm not sure I have a handle on what is going one - some of the info confuses me - but the first picture posted seems to say that this disk has no partition table, and has an ext4 filesystem occupying all of the space.

If that should be true, then you'd have to get rid of any info from the disk, create a partition table, create partitions, declare filesystems, format the filesystems, and go on from there.

HTH

---

### Post by MartyBuntu on 2010-12-14
Beyond re-partitioning, if this data is at all important to you, it really should be backed up to another disk.

---

### Post by v1gorus on 2010-12-14
> **dandnsmith said:**
> I'm not sure I have a handle on what is going one - some of the info confuses me - but the first picture posted seems to say that this disk has no partition table, and has an ext4 filesystem occupying all of the space.

If that should be true, then you'd have to get rid of any info from the disk, create a partition table, create partitions, declare filesystems, format the filesystems, and go on from there.

HTH
so should i make a guid partition table like ive seen here:
[http://farm6.static.flickr.com/5169/5259807032_b68fd25b8d_b.jpg](http://farm6.static.flickr.com/5169/5259807032_b68fd25b8d_b.jpg)
> **MartyBuntu said:**
> Beyond re-partitioning, if this data is at  all important to you, it really should be backed up to another  disk.
1.4tb of stuff and no where to put it.

---

### Post by ppv on 2010-12-14
In the first picture of Disk Utility there is an option to check the filesystem. Can you run that on your hard drive. And they probably wont be but do you see your files present in /media/fataaz

---

### Post by ppv on 2010-12-14
And the GUID screen that is posted, if you go ahead with it that will erase the data on the hard drive. Formatting the drive removes all data on the disk that is being formatted. So if you want the data you should try and see if you can recover the data first.

---

### Post by v1gorus on 2010-12-14
> **ppv said:**
> In the first picture of Disk Utility there is an option to check the filesystem. Can you run that on your hard drive. And they probably wont be but do you see your files present in /media/fataaz
right when i was willing to sacrifice data to reformat it. i cant access it anymore. i think its because of the e2fs tool i installed on it recently.
image of it no being accessible:
[http://farm6.static.flickr.com/5046/5262023452_670a4c6728_b.jpg](http://farm6.static.flickr.com/5046/5262023452_670a4c6728_b.jpg)
also i couldnt check the drive because it gave me this error:
[http://farm6.static.flickr.com/5209/5261407347_8c9cb6763a_b.jpg](http://farm6.static.flickr.com/5209/5261407347_8c9cb6763a_b.jpg)
also the information about the drive in gparted changed:
[http://farm6.static.flickr.com/5281/5261407855_6f6ed174f2_b.jpg](http://farm6.static.flickr.com/5281/5261407855_6f6ed174f2_b.jpg)

---

### Post by ppv on 2010-12-15
ok so now since you are willing to sacrifice data you may well format it but before that let us have one more thing that can be checked. you would need to google it and find out but see if testdisk does it. testdisk is a recovery program and at times fixes the partitioning stuff also. also the first image attached says that you are not owner and so cannot see the files. From a terminal you may try sudo ls -l /media/fatazz to see if it lists the files.

---

### Post by othiena on 2010-12-15
You don't need to format disk utility only shows the partition on the drive. if you install gparted on your desktop you can see how full the drive is


P.S. if you logout of your user account and use the terminal to log in to root and type startx you wont have to use the command line

P.S. i find it easer to use a live installer disk to partion

---

### Post by v1gorus on 2010-12-17
> **ppv said:**
> ok so now since you are willing to sacrifice data you may well format it but before that let us have one more thing that can be checked. you would need to google it and find out but see if testdisk does it. testdisk is a recovery program and at times fixes the partitioning stuff also. also the first image attached says that you are not owner and so cannot see the files. From a terminal you may try sudo ls -l /media/fatazz to see if it lists the files.
i would but now i cant access the hdd at all.
its the same when it is mounted and when it is not connect at all. 
[http://farm6.static.flickr.com/5169/5269625356_b3c21d5de3_b.jpg](http://farm6.static.flickr.com/5169/5269625356_b3c21d5de3_b.jpg)
i also cant access the hdd, this folder here is always there.
[http://farm6.static.flickr.com/5244/5269014199_7fd9b91343_b.jpg](http://farm6.static.flickr.com/5244/5269014199_7fd9b91343_b.jpg)
[http://farm6.static.flickr.com/5050/5269014115_49d60cf643_b.jpg](http://farm6.static.flickr.com/5050/5269014115_49d60cf643_b.jpg)

---

### Post by cottfcfan on 2010-12-17
Looks from the last pic, like its a permissions problem.
The directory is owned by root and not by you.
I'm not too sure about this, but in a terminal, type "sudo nautilus"
navigate to the directory, right click, properties, permissions, and change the owner to you, from the dropdown menu.
 If that solves it fine, if thats not it you can always change them back.

---

### Post by v1gorus on 2010-12-17
> **cottfcfan said:**
> Looks from the last pic, like its a permissions problem.
The directory is owned by root and not by you.
I'm not too sure about this, but in a terminal, type "sudo nautilus"
navigate to the directory, right click, properties, permissions, and change the owner to you, from the dropdown menu.
 If that solves it fine, if thats not it you can always change them back.
ok now i can get in the folder but there is nothing in it with and without the drive connected. i think it has something to do with 
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
i got this when i typed mount in console.

---

### Post by cottfcfan on 2010-12-17
Now you have access to it what error message does it give when you try and copy something across onto the drive?

---

### Post by v1gorus on 2010-12-17
> **cottfcfan said:**
> Now you have access to it what error message does it give when you try and copy something across onto the drive?
its drive isnt showing up. for some reason there is a folder in media named the name as my drive. also it he there when the drive is connect and not. when i plug my drive in nothing shows up on the desktop. i can drag stuff in the folder but its not the drive. i remember that when my drive did show up i it was called Fatazz_ thou i named it just Fatazz.

---

### Post by cottfcfan on 2010-12-17
Thats OK.
When I plug in my USB Drive, it also shows up in media. Its the same drive.
As long as in properties/permissions you are the owner & can create and delete files you should be good to go.

---

### Post by v1gorus on 2010-12-17
> **cottfcfan said:**
> Thats OK.
When I plug in my USB Drive, it also shows up in media. Its the same drive.
As long as in properties/permissions you are the owner & can create and delete files you should be good to go.
there is nothing in that folder. im pretty sure the folder Fatazz is not the drive. since its there when i disconnect the drive.

---

### Post by cottfcfan on 2010-12-18
Sorry i'm lost.
Nearly all hard drives just plug in, you format them to what you want and start using them, end of.
 Either theres something wrong with the drive, its not compatible (unlikely), or theres something were all missing.
If theres nothing in the folder media/fatazz, then delete the folder,with your drive unplugged, Plug your drive in again, and see if it appears in media.

---

### Post by v1gorus on 2010-12-18
> **cottfcfan said:**
> Sorry i'm lost.
Nearly all hard drives just plug in, you format them to what you want and start using them, end of.
 Either theres something wrong with the drive, its not compatible (unlikely), or theres something were all missing.
If theres nothing in the folder media/fatazz, then delete the folder,with your drive unplugged, Plug your drive in again, and see if it appears in media.
couldn't delete it. move to trash option is unselected and i couldnt do it thru terminal.
[http://farm6.static.flickr.com/5242/5271890276_e074c816b4_b.jpg](http://farm6.static.flickr.com/5242/5271890276_e074c816b4_b.jpg)

---

### Post by cottfcfan on 2010-12-18
Not even if you run "sudo nautilus" in a terminal, navigate to it, then delete it?

---

### Post by psusi on 2010-12-18
I'm not sure what you've managed to do to it since then, but the first images you posted do show that you formatted the drive wrong in the first place.  You used the entire drive rather than a partition in it, so now it has no partition table, and therefore, you can't shrink it and add a windows partition.

---

### Post by v1gorus on 2010-12-18
> **psusi said:**
> I'm not sure what you've managed to do to it since then, but the first images you posted do show that you formatted the drive wrong in the first place.  You used the entire drive rather than a partition in it, so now it has no partition table, and therefore, you can't shrink it and add a windows partition.
yes that is what i did. so there is no way to fix it besides removin the data and reformattin?

---

### Post by v1gorus on 2010-12-18
> **cottfcfan said:**
> Not even if you run "sudo nautilus" in a terminal, navigate to it, then delete it?
did that and it worked. now there is nothin in media even when drive pluged in.

---

### Post by cottfcfan on 2010-12-18
At least we're getting somewhere then.
Is the drive showing up anywhere when its plugged in?
If not Ubuntu isn't even recognizing its there.

---

### Post by psusi on 2010-12-18
> **v1gorus said:**
> yes that is what i did. so there is no way to fix it besides removin the data and reformattin?

Generally no.  You might be able to hack it with resize2fs and dd to shrink and then slide the filesystem over to make room to add a partition table.

---

### Post by v1gorus on 2010-12-18
> **cottfcfan said:**
> At least we're getting somewhere then.
Is the drive showing up anywhere when its plugged in?
If not Ubuntu isn't even recognizing its there.
nope no where. this what i get in terminal with and without the drive being pluged in. also this problem first occured when i installed etfsprogs v1.41. on it. also the drive works on live cd. 
igor@igor-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)

---

### Post by cottfcfan on 2010-12-18
Its possible that the drive isn't even being mounted at boot.
You might need to follow this tutorial, and see if that works.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by v1gorus on 2010-12-18
> **psusi said:**
> Generally no.  You might be able to hack it with resize2fs and dd to shrink and then slide the filesystem over to make room to add a partition table.
is this hard and what is dd? also it formatted ext4 will resize2fs still work?

---

### Post by v1gorus on 2010-12-18
> **cottfcfan said:**
> Its possible that the drive isn't even being mounted at boot.
You might need to follow this tutorial, and see if that works.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
i couldnt do this line

```

igor@igor-laptop:~$ ls -1 /dev/sda2/by-uuid
ls: cannot access /dev/sda2/by-uuid: Not a directory
igor@igor-laptop:~$ cd /
igor@igor-laptop:/$ ls -1 /dev/sda2/by-uuid
ls: cannot access /dev/sda2/by-uuid: Not a directory
igor@igor-laptop:/$ ls -1 dev/sda2/by-uuid
ls: cannot access dev/sda2/by-uuid: Not a directory
igor@igor-laptop:/$ ls -l /dev/sda2/by-uuid
ls: cannot access /dev/sda2/by-uuid: Not a directory
igor@igor-laptop:/$ ls -l dev/sda2/by-uuid
ls: cannot access dev/sda2/by-uuid: Not a directory

```

---

### Post by cottfcfan on 2010-12-18
Where did you get sda2 from?
Looking at your 1st post the drive you're trying to mount is sdb1?

---

### Post by cottfcfan on 2010-12-18
Ok lets start again and i'll try and guide you through it.
1st go into gparted.
Right click on the drive you're tring to mount (sdb1)
go to information and there will be a UUID no.
post the UUID and we can go from there.

---

### Post by cottfcfan on 2010-12-18
Igor.
Follow this and see how you go:

sudo mkdir /storage           (in a terminal)
sudo gedit /etc/fstab         (in a terminal)
Then add the line:
UUID=de4axxxxx8153-4xx8-bxxd-9xxxxx1adf7f /storage        ext4    defaults        0       0
(or whatever the uuid is)
sudo mount -a                       (in a terminal)
sudo chown -R igor:igor /storage       (in a terminal)
sudo chmod -R 755 /storage                (in a terminal)
reboot
done

the Mounted partition should be in your filesystem called “storage”
You should be able to read and write from it.

---

### Post by v1gorus on 2010-12-18
> **cottfcfan said:**
> Ok lets start again and i'll try and guide you through it.
1st go into gparted.
Right click on the drive you're tring to mount (sdb1)
go to information and there will be a UUID no.
post the UUID and we can go from there.
sry it is sdb1. also the uuid is blank.
[http://farm6.static.flickr.com/5167/5273127296_cbfcf7da93_b.jpg](http://farm6.static.flickr.com/5167/5273127296_cbfcf7da93_b.jpg)
> **cottfcfan said:**
> Igor.
Follow this and see how you go:

sudo mkdir /storage           (in a terminal)
sudo gedit /etc/fstab         (in a terminal)
Then add the line:
UUID=de4axxxxx8153-4xx8-bxxd-9xxxxx1adf7f /storage        ext4    defaults        0       0
(or whatever the uuid is)
sudo mount -a                       (in a terminal)
sudo chown -R igor:igor /storage       (in a terminal)
sudo chmod -R 755 /storage                (in a terminal)
reboot
done

the Mounted partition should be in your filesystem called “storage”
You should be able to read and write from it.

sudo mkdir /storage
but cant do the next due to the missing uuid.

---

### Post by cottfcfan on 2010-12-19
The problem looks like its to do with the message "couldn't find valid filesystem superblock".
 If yo google it, it sounds like its file system damage.
I found this which may help:
[http://allensood.livejournal.com/4784.html](http://allensood.livejournal.com/4784.html)

But you might want to google around.

ps It also seems that post 27 is right, that message appears when its formatted wrong in the 1st place, but not sure what you need to do about that.

---

### Post by v1gorus on 2010-12-19
omg. ubuntu ruined my life. after doing those commands. and rebooting. my wifi is not workin. also it didnt fix my hdd problem. im now using live cd where is sees the drive and the wifi works. im trying to recover my files thru live cd and placin it on a extrenal but some of the files and folders have do no allow me to move access them. what is the command to make all files and folders: changing folder access in permissions to access files. I can do it for a folder but then the folders inside are not effected. and i have alot of folders in folders.

wow. things got worst. why is ubuntu intent on hurting me. while recovering the files which arent blocked by persmissions. i try to drag a folder into my backup drive and it gives me the error: drive is read-only, i got to permission of drive and it says: Permissions of drive could not be determined. wtf it was not a read-only drive 5 minutes ago, wtf changed?

---

