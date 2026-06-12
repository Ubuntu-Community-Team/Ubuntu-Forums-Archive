---
title: "Partimage and ext4"
date: 2011-01-14
forum: General Help
---

### Post by ceperman on 2011-01-14
I've been using PING (which I understand uses Partimage under the covers) for a little while to back up an ext4 partition. I've just become aware that Partimage doesn't support ext4, so I'm confused as to why it appears to be working (although I've not tried to restore it).

The Disk Utility (version 2.30.1) on Ubuntu 10.10 reports the partition as Ext4 (version 1.0). However, PING and GParted report it as ext3fs, which may explain why Partimage is processing it. As far as I'm concerned it should be ext4 as that's what I selected during installation.

What's going on?

---

### Post by indytim on 2011-01-14
The last time I checked the Partimage website, it was plainly stated that Partimage does not support ext4 or NTFS.  As I recall, there is no plans to move to this support.

I have been using fsarchiver quite successfully for about 9 months.  I supports most common file system types (including ntfs and ext4).  Even though it is still classified as "in development" I have found it both stable and reliable.  I have restored numerous ext4 and ntfs partitions with no lingering issues.

If you're interested, I've authored a small "white paper" on the subject.  See the Backup Strategy Ver 2 link in my sig.  Also not the comment attached to the paper for an important update.

Hope this helps.

IndyTim / DataMan

---

### Post by Slim Odds on 2011-01-14
> **indytim said:**
> The last time I checked the Partimage website, it was plainly stated that Partimage does not support ext4 or NTFS.  As I recall, there is no plans to move to this support
....

I think that you're confusing file systems. From the website:
> Partimage does not support **ext4** or **btrfs** filesystems. It does support NTFS

---

### Post by Slim Odds on 2011-01-14
<system glitch>

---

### Post by indytim on 2011-01-14
[http://www.partimage.org/Supported-Filesystems]("http://www.partimage.org/Supported-Filesystems")

NTFS is listed as "experimental"

-IndyTim / DataMan

---

### Post by ceperman on 2011-01-16
The main reason for the original post was to try to find out why GParted/Partimage/PING see this partition as ext3fs when it is actually ext4. If necessary I will convert the partition to ext3 so I can continue using Partimage, but I'm really confused that it appears to think it already is.

---

### Post by ceperman on 2011-12-09
Just to wrap this thread up, I discovered CLONEZILLA which seems to do everything I want, so I'm using this successfully for all my backups/restores.

Thanks to all for your comments.

---

