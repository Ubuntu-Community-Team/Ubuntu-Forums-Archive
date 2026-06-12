---
title: "Shared partition between win 7 and ubuntu 11.04"
date: 2011-08-22
forum: General Help
---

### Post by vincedba on 2011-08-22
Hi All,


I'm planning to build dual boot on my laptops (win7 and ubuntu 11.04). My idea is to have one partition for win7, one partition for ubuntu 11.04 and one partition for shared (will be accessible from both win7 and ubuntu)

So my question is which one is better for shared partition?
- shared partition formatted with ext4 and install application on win7 to be able read and write ext4 partition
- shared partition formatted with NTFS and have ubuntu 11.04 read and write on it?

I've researched around and found some suggestion to use ntfs-3g for ubuntu to be able read NTFS, my question is this ntfs-3g mandatory to be installed? Can't ubuntu 11.04 natively able to read and write NTFS  like put on /etc/fstab mount point like /sdb1 /shared ntfs x x x x ??


Please kindly help me on this


Many Thanks

P.S it wasn't my intention to get the thread with red evil look like face icon, not sure why it can be like that

---

### Post by oldfred on 2011-08-22
The ntfs-3g has been standard for several years with the default install of Ubuntu.

I suggest using NTFS. I have used this with my XP install since just before they included the NTFS driver. Before that I had FAT but found I was damaging any file over 4GB since FAT32 does not support that. I have my Firefox & Thunderbird profiles & all photos for Picasa in my shared.

There is no current driver for ext4 from windows and some have had success and some not so much with the ext3 or ext2 drivers in windows.

---

### Post by vincedba on 2011-08-22
> **oldfred said:**
> The ntfs-3g has been standard for several years with the default install of Ubuntu.

I suggest using NTFS. I have used this with my XP install since just before they included the NTFS driver. Before that I had FAT but found I was damaging any file over 4GB since FAT32 does not support that. I have my Firefox & Thunderbird profiles & all photos for Picasa in my shared.

There is no current driver for ext4 from windows and some have had success and some not so much with the ext3 or ext2 drivers in windows.

Thanks for the input, really appreciate it.

So presumably ntfs-3g is came out-of-box on ubuntu 11.04?

---

### Post by Mark Phelps on 2011-08-23
> **vincedba said:**
> Thanks for the input, really appreciate it.

So presumably ntfs-3g is came out-of-box on ubuntu 11.04?

IF you mean, installed by default, I believe it is.

If not, you can get it using the Software Center or Synaptic.

---

