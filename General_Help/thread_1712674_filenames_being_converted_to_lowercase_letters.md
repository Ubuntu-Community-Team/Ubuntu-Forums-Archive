---
title: "filenames being converted to lowercase letters"
date: 2011-03-23
forum: General Help
---

### Post by ***J*** on 2011-03-23
Every time I create a directory with eight characters or less in all capital letters (AAAAAAAA) on an external hard drive on my local network the filename is then converted to lowercase letters (aaaaaaaa). If the filename has both capital and lowercase letters (Aaaaaaaa) this doesn't happen. How can I stop this from happening? After doing some research a common suggestion is to add an option called shortname=winnt to fstab but it didn't work in my case (might have to do with me using cifs). 

The external hard drive's file system is FAT32 and plugged into a HD Media Player (WD TV Live Media Player) which is plugged into a router (ASUS RT-N16 with TomatoUSB firmware). I am using Ubuntu 10.10 with an EXT4 file system. I am forced to have either a NTFS, FAT32 or HFS (non-journaled) file system on my external hard drive because those are the only ones that my HD Media Player supports. I am trying to create these directories wirelessly on my local network. The line that I tried adding to fstab (which didn't solve my problem) is ```
//netbiosname/sharename    /mnt/sharename        cifs    guest,rw,iocharset=utf8,shortname=winnt,file_mode=0777,dir_mode=0777 0 0
```If you need any more information let me know. :shock:

---

### Post by jocko on 2011-03-23
> *****J*** said:**
> Every time I create a directory with eight characters or less in all capital letters (AAAAAAAA) on an external hard drive on my local network the filename is then converted to lowercase letters (aaaaaaaa). If the filename has both capital and lowercase letters (Aaaaaaaa) this doesn't happen. How can I stop this from happening? After doing some research a common suggestion is to add an option called shortname=winnt to fstab but it didn't work in my case (might have to do with me using cifs). 

The external hard drive's file system is FAT32...


Fat32 is not case sensitive, but can preserve the case in file names with mixed upper and lower case. There's nothing you can do about it.

---

