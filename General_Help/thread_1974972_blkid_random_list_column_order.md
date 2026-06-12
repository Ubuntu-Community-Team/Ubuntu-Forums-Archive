---
title: "blkid random list column order ?"
date: 2012-05-06
forum: General Help
---

### Post by masuch on 2012-05-06
Hi,

$ blkid|sort

/dev/md122: LABEL="rlraid0ocz" UUID="f3ecef8f-de39-43e4-a1d0-1cd99a45a85c" TYPE="ext4" 
/dev/md123: UUID="87e10834-fcd0-4f11-8227-5e39bfa7d33d" TYPE="ext4" LABEL="rlraid0ext41"


why is in the first line LABEL "second" column
and in the second line is LABEL "last" column ?

thank you,
M.

---

### Post by oldfred on 2012-05-06
It used to have a -l command for formating, but then they changed the definition of -l.

Try this:

 sudo blkid -o list

```
fred@fred-Precise:~$ sudo blkid -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    /mnt/cdrive    04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdc2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdc3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdc4  ext4    MavData  (not mounted)  431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdd1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdd2  ntfs    Shared   /mnt/shared    44332FD360AA9657
/dev/sdd4  ext2    bios_gpt (not mounted)  bbda6045-bb8a-4666-8bd4-04b3945ca581
/dev/sdd5  ext4    Karmic   /media/Karmic  117412d5-2dbe-4011-8aec-ae310d1ee6c7
/dev/sdd6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05
/dev/sdd7  ext4    LUCID    /media/LUCID   5e25282c-9c54-45df-9e79-514011e98648
/dev/sdd8  ext4    Test     (not mounted)  af29c61a-34e9-48eb-9c94-afcb4bb61582
/dev/sdd9  vfat    OLDG     (not mounted)  F6A6-705D
/dev/sdd10 ext4    newhome  /media/newhome b8a7e331-a716-4ac1-bf58-6ac515606c6d
/dev/sdd11 swap             <swap>         09367687-86d1-4fd0-9b81-2787d3196159
/dev/sdd12 ext4    Puppy    (not mounted)  07e2a08d-37ca-4cf1-877b-f02b0eabcbca
/dev/sdd13 ext4    natty    (not mounted)  318fd41e-4210-4960-a0d9-ee9b48388d69
/dev/sdd14 ext4    kubuntu  (not mounted)  2b42c9ad-4304-4a8a-8991-08cfe35717ec
/dev/sdd15 swap             <swap>         2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9
/dev/sdd16 ext4    oneiric  (not mounted)  63d146fd-1c63-4b31-95c5-ab52e2892283
/dev/sdd17 ext4    server   (not mounted)  63045773-e42a-46eb-9e96-b93428542527
/dev/sdd18 ext4             (not mounted)  117e0c31-7e16-4e8b-90b7-a3c688a34f26
/dev/sde1  vfat    EFI      (not mounted)  7B30-5ACA
/dev/sde3  ext4    Precise  /              adc013e9-a23d-4a36-849b-3faeac005667
/dev/sde4  ext4             (not mounted)  44af9906-aa54-4130-9470-5506c83f03e4

```

---

### Post by masuch on 2012-05-06
how did you get such nice blkid look. look at mine:

```
sudo blkid -o list 
device                                                    fs_type         label            mount point                                                   UUID
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                                       ext4             DEV_EXT4          (not mounted)                                                       dbd8c391-e84d-d446-49e8-05ebf55998c7
/dev/sda2                                                       linux_raid_member PCEUBU1:raid0ext41 (in use)                                                          8248abdc-c6cb-1226-1f60-ded43b5dbffa
/dev/sda3                                                       linux_raid_member PCEUBU1:raid0btrfs1 (in use)                                                         11d759ba-1e0a-545d-f591-ceda3203976a
/dev/sda4                                                       linux_raid_member PCEUBU1:raid0jfs1 (in use)                                                           47304dbe-051d-e596-f9b4-bdefa21ad63e
/dev/sda5                                                       linux_raid_member PCEUBU1:raid0reiserfs1 (in use)                                                      a95d4031-52c0-bfcc-5845-87d685fa6eec
/dev/sda6                                                       linux_raid_member PCEUBU1:raid0xfs1 (in use)                                                           853cf572-b972-d3b3-c8fa-b9ec11d4d102
/dev/sdb2                                                       ext2             GRUB_FILES        (not mounted)                                                       98d3e
```

---

### Post by oldfred on 2012-05-06
Somehow your RAID must be too large for default widths and it messed with formating. Do not know what else other than creating your own. 

Boot info script does its own parsing. You can run it and see or look at the code (its a lot) and see if you can find where it formats it.
```

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        04B05B70B05B6768                       ntfs       WinXP
/dev/sda2        13a684e4-2849-4566-9528-21cd07028a9a   ext3       backup
/dev/sda4        46CD-C9B2                              vfat       SHARE
/dev/sdb2        dd7fece0-88ff-43bd-a83a-93943f57482d   ext4       
/dev/sdb3        4215f5b3-ce4c-4ef8-bc1a-0daac816fb75   ext4       KingstonData
/dev/sdb4        5FE046DD43C03A7C                       ntfs       
/dev/sdc2        0eea4e95-ea0a-4745-80d4-57bf2bbc9d69   ext4       Maverick
/dev/sdc3        00c4e383-cf30-4b54-9a9f-d46953e3966e   swap       
/dev/sdc4        431ba9e5-c72c-41c2-ba82-d8ee052336ff   ext4       MavData
/dev/sdd1        9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f   ext3       grub
/dev/sdd10       b8a7e331-a716-4ac1-bf58-6ac515606c6d   ext4       newhome
/dev/sdd11       09367687-86d1-4fd0-9b81-2787d3196159   swap       
/dev/sdd12       07e2a08d-37ca-4cf1-877b-f02b0eabcbca   ext4       Puppy
/dev/sdd13       318fd41e-4210-4960-a0d9-ee9b48388d69   ext4       natty
/dev/sdd14       2b42c9ad-4304-4a8a-8991-08cfe35717ec   ext4       kubuntu
/dev/sdd15       2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9   swap       
/dev/sdd16       63d146fd-1c63-4b31-95c5-ab52e2892283   ext4       oneiric
/dev/sdd17       63045773-e42a-46eb-9e96-b93428542527   ext4       server
/dev/sdd18       117e0c31-7e16-4e8b-90b7-a3c688a34f26   ext4       
/dev/sdd2        44332FD360AA9657                       ntfs       Shared
/dev/sdd4        bbda6045-bb8a-4666-8bd4-04b3945ca581   ext2       bios_gpt
/dev/sdd5        117412d5-2dbe-4011-8aec-ae310d1ee6c7   ext4       Karmic
/dev/sdd6        a55e6335-616f-4b10-9923-e963559f2b05   ext3       Data
/dev/sdd7        5e25282c-9c54-45df-9e79-514011e98648   ext4       LUCID
/dev/sdd8        af29c61a-34e9-48eb-9c94-afcb4bb61582   ext4       Test
/dev/sdd9        F6A6-705D                              vfat       OLDG
/dev/sde1        7B30-5ACA                              vfat       EFI
/dev/sde3        adc013e9-a23d-4a36-849b-3faeac005667   ext4       Precise
/dev/sde4        44af9906-aa54-4130-9470-5506c83f03e4   ext4       


```

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by masuch on 2012-05-07
:-) there is no reason to make so wide column for device :-)

---

