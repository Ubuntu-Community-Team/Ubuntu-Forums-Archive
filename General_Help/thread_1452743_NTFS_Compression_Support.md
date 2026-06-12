---
title: "NTFS Compression Support"
date: 2010-04-12
forum: General Help
---

### Post by grnorris on 2010-04-12
I've done some searching both on the forums here and with scroogle (google minus the spam).  I recently decided to compress my two NTFS partitions using Windows (in this case 7) NTFS compression.  Unfortunately it seems that although NTFS-3G says it has some support for NTFS Compression all it really seems able to do is read a few documents files.  It's completely unable to work with my torrents (uTorrent via Wine) and my email (Thunderbird-shared profiles via the --profilemanager method).

My question in short (or at least as short as I'm capable of making it) is:  Is there any way to gain full compatibility for NTFS compression.  Even if it means taking the windows driver and wrapping it somehow to work with linux (currently Ubuntu 9.10, planning to upgrade as soon as 10.04 comes out).

As I hinted at earlier I am dual booting Windows 7 with Ubuntu and I really can't get rid of any more data off my drive.  I'd consider switching to another FS if I could somehow get the compression capabilities of NTFS compression wherein I can still use the files almost (less than a second difference) as fast as without compression.

My current drive setup is as follows(grub 2 representation):
(hd0,1) is Windows System Reserved (obviously doesn't matter)

(hd0,2) is my Windows (ntfs) Partition (I don't really share to much between that partion and linux)

(hd0,3) is Ubuntu (ext4)

(hd0,4) is my Data Drive (ntfs-extended) (This is the one I keep my torrent and email on).

(hd0,5) is my linux swap (swap-extended)

Note that 4 and 5 are extended, also note that I've not actually read them all from grub so I'm going by the known scheme (HD starts with 0, partitions start with 1).

---

### Post by Slim Odds on 2010-04-12
If you're tight on disk space, I'd recommend a larger drive.

File system compression is just more of a headache than it's worth.

(opinions may vary).

In my opinion, disks are big and cheap these days, so save your self some trouble and get a bigger one (or two).

---

### Post by grnorris on 2010-04-12
> **Slim Odds said:**
> If you're tight on disk space, I'd recommend a larger drive.

File system compression is just more of a headache than it's worth.

(opinions may vary).

In my opinion, disks are big and cheap these days, so save your self some trouble and get a bigger one (or two).

As true as that may be the fact of the matter is that I'm already spending money I don't have.  Therefor a just buying a larger drive is completely out of the question.  Besides, since I've only got one hard drive slot in my laptop it would be extremely difficult for me to transfer everything without losing all functionality of my laptop.  This is especially true for dual booters.  Also note that it's impossible for me to get along with just Ubuntu as the corporate world and the world of college all work for Microsoft and wine just isn't enough.

---

### Post by szaka on 2010-04-12
> **grnorris said:**
> I've done some searching both on the forums here and with scroogle (google minus the spam).  I recently decided to compress my two NTFS partitions using Windows (in this case 7) NTFS compression.  Unfortunately it seems that although NTFS-3G says it has some support for NTFS Compression all it really seems able to do is read a few documents files.  It's completely unable to work with my torrents (uTorrent via Wine) and my email (Thunderbird-shared profiles via the --profilemanager method).

There are a few special cases where compression doesn't work yet. We are working on them. Compression works for most other cases as you can also confirm by doing e.g. file copies, etc.

---

### Post by Slim Odds on 2010-04-12
> **grnorris said:**
> As true as that may be the fact of the matter is that I'm already spending money I don't have.  Therefor a just buying a larger drive is completely out of the question.  Besides, since I've only got one hard drive slot in my laptop it would be extremely difficult for me to transfer everything without losing all functionality of my laptop.  This is especially true for dual booters.  Also note that it's impossible for me to get along with just Ubuntu as the corporate world and the world of college all work for Microsoft and wine just isn't enough.

In that case, why don't you run Ubuntu in a virtual machine like VirtualBox. It works quite well. By using shared folders Ubuntu would have no problem with any part of the NTFS file system being compressed.

Just a thought.

---

### Post by grnorris on 2010-04-13
> **Slim Odds said:**
> In that case, why don't you run Ubuntu in a virtual machine like VirtualBox. It works quite well. By using shared folders Ubuntu would have no problem with any part of the NTFS file system being compressed.

Just a thought.

I'm running 32-bit windows and 64-bit Ubuntu.  I also use Ubuntu as a backup.  If windows crashes and won't boot I can attempt repair by booting into Ubuntu.  Lastly, the performance hit of running all of my windows app (Firewall, updaters, uTorrent, Your-Freedom [proxy]) + a full Ubuntu environment (minus the common apps) would be a major drain on my batteries and might be a bit too much for my Turions.

---

### Post by Slim Odds on 2010-04-13
> **grnorris said:**
> I'm running 32-bit windows and 64-bit Ubuntu.  I also use Ubuntu as a backup.  If windows crashes and won't boot I can attempt repair by booting into Ubuntu.  Lastly, the performance hit of running all of my windows app (Firewall, updaters, uTorrent, Your-Freedom [proxy]) + a full Ubuntu environment (minus the common apps) would be a major drain on my batteries and might be a bit too much for my Turions.

Understood....

I always keep a LiveCD with me. You never know when you won't be able to boot anything from the hard drive but might still be able to copy some files using the LiveCD.

Regarding your first issue:> 
3.2 64-bit guests
Starting with version 2.0, VirtualBox supports 64-bit guest operating systems. Starting
with version 2.1, you can even run 64-bit guests on a 32-bit host operating system.Also, I find it funny that you're worried about battery live while running "updaters and uTorrents". If you have both OS's very busy, sure. But if you're busy using linux, you problem won't be doing much in window (just like you won't be doing anything in windows at all if you dual boot).

---

### Post by grnorris on 2010-04-14
> **Slim Odds said:**
> Understood....

I always keep a LiveCD with me. You never know when you won't be able to boot anything from the hard drive but might still be able to copy some files using the LiveCD.

Regarding your first issue:Also, I find it funny that you're worried about battery live while running "updaters and uTorrents". If you have both OS's very busy, sure. But if you're busy using linux, you problem won't be doing much in window (just like you won't be doing anything in windows at all if you dual boot).

Most virtual machines will use a minimal amount of power even when they are not in focus and unlike your machine which is apparently quite powerful I'm only running an upper middle of the line laptop.  One of the biggest factors is RAM.  I have 3GB DDR2 PC6400 RAM in my laptop which isn't a particularly small amount but, just having another Gig (especially if it meant gaining Dual Channel) would make a huge difference.  Of course that is again a matter of money I don't really have.

None the less, I've read that Ubuntu 10.04 is supposed to have KVM built into it so when it comes out I may see about trying seemless virtualization.  Especially if I can find a way to use it as a go between for my NTFS partitions.

---

