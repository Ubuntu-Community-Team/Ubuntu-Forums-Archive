---
title: "Using fsck to check Windows partition"
date: 2010-03-21
forum: General Help
---

### Post by santosh3 on 2010-03-21
My windows partition isn't starting up, gives an error and suggests using chkdsk. However, I cant even reach safe mode or command prompt. I can still access my Windows hard drive through Ubuntu.

I am wondering I can use a Linux tool to perform a check on this Windows partition? I found the fsck command, but I am confused about the warning about running it on a mounted system and about what exactly is a mounted system.

Can someone please tell me how exactly I would go about doing a check on this partition? Its currently located in /media/disk. 

I can right click on the partition and unmount it.  But if I do this, will Ubuntu still be able to see this partition?

What command do I use to do fsck only on this Windows partition (and not the whole system and other mounted places)? 

How do I remount the Windows partition so that I can atleast salvage my data easily in case doing a disk check does not help?


Thanks

---

### Post by srs5694 on 2010-03-21
The Linux fsck tool is the rough equivalent of CHKDSK in Windows; however, fsck works best on Linux-native filesystems. Although it can work on NTFS partitions (via the fsck.ntfs helper program), that support is very limited; it just runs a few very basic tests and then marks the partition as requiring a more thorough check, which the Windows tools are supposed to provide. This *might* be enough in your case, but it might be completely ineffective and it might even cause more problems. Thus, I don't recommend you use fsck on an NTFS partition unless you understand your specific problem and all the tools involved much more than you do (or more than I do or even would if I had physical access to your computer).

My best advice is to use a Linux installation/recovery CD/DVD. These discs should be able to perform a CHKDSK, even if they can't boot all the way to a Windows GUI login. You may need to run this process two or three times. With any luck, doing this will correct the problems and enable Windows to boot. Even if Windows will no longer boot, though, they should at least enable Linux to mount the NTFS partition(s) so you can recover your files.

Failing that, you might try the Linux ntfsls and ntfscat programs, which enable access to unmounted NTFS partitions. (Type "man ntfsls" and "man ntfscat" to learn about them.) I've never used them, though; I just know they exist, and from their man pages they look like they *might* be useful in some recovery situations.

---

### Post by santosh3 on 2010-03-21
Thanks. I couldn't get the Ubuntu installer to do a disk check, so I just used the Windows XP one to run Chkdsk. That worked, I am not sure why I didn't think about that.

---

