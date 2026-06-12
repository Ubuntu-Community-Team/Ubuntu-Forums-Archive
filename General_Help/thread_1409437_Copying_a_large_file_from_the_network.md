---
title: "Copying a large file from the network"
date: 2010-02-17
forum: General Help
---

### Post by madmax.santana on 2010-02-17
I am trying to copy a file from a network resource on my Local Area Network, which is about 4.5 GB. I copy this file through GNOME copying utilities by first going to Places --> Network and then selecting the Windows Share on another computer on my network. I open it and start copying the file to my FAT32 drive by Ctrl+C and Ctrl+V. It copies well up-to 4 GB and then it hangs.

After trying it almost half a dozen times I got really annoyed and left it hung and went to bed. Next morning when I checked a message box saying "file too large to write" has appeared.

I am very annoyed. I desperately need that file. It's an ISO image and it is not damaged at all, it copies well to any windows system. Also, I have sufficient space on the drive in which I am trying to copy that file. What could the problem be? And what is the solution.

Does anyone else have the same or similar problem? If yes then how do you manage it?

---

### Post by robert shearer on 2010-02-17
Fat32 has a 4gb file size limit

[http://www.cknow.com/cms/articles/why-cant-i-copy-a-large-file-despite-having-larger-free-space.html](http://www.cknow.com/cms/articles/why-cant-i-copy-a-large-file-despite-having-larger-free-space.html)

---

### Post by madmax.santana on 2010-02-17
Oh oh!!! So that's the problem. Thank you man. So I must reformat my drive to a ext4 file system?

Also, I am copying the same file now on my desktop, which of course comes under my ubuntu root file system, which is ext4. Does ext have any such anomalies? Will it copy fully?

---

### Post by madmax.santana on 2010-02-17
Man I almost saw that coming, but then I thought, what a stupid idea, how could it possibly a file system rule to prevent large files... Seems FAT32 is really very inflexible and slack file system. It used to be standard file system in older windows, which is a proof of it being useless, :)

---

### Post by robert shearer on 2010-02-17
from the link I posted , scroll to the end and read the  "Converting" fat32 to ntfs.

Ubuntu and ext is fine.
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

> The ext4 filesystem can support volumes with sizes up to 1 Exbibyte[8] and files with sizes up to 16 tebibytes.

---

### Post by madmax.santana on 2010-02-17
Good! Thanks a lot mate... Such a simple solution to my long long post... Hahaha, dunno why, but it looks very funny to me.

---

### Post by madmax.santana on 2010-02-17
Oh, there is some problem with the link you posted. It is for Windows users. I am on linux and been wary of windows for a long time now and do not have any windows version on my system. Is there a way to do that with Linux?

If you know, well and good. If you don't, it's ok. I know this is off-topic and I shall start to resolve that on different lines, in a different process

---

### Post by robert shearer on 2010-02-17
under Windows the conversion is meant to occour without data loss.(a back up before would still be a good idea ;))

I have not tried to convert using the linux partition tool Gparted.
This is on the Ubuntu live cd and if you boot with it and run gparted there may well be an option there.
Otherwise Gparted can reformat the partition or drive to an ext file system but you would lose all the data on the drive/partition!!. 
So back up **first**.

I am presuming that the drive with fat32 is a second drive used for data only ?  
Details would help.

Just cheked my copy of gparted and cannot find a convert option only a reformat option.

May be wise to wait for others to comment.

---

### Post by madmax.santana on 2010-02-17
oh no... about formatting the whole drive, i know that, it's no that tricky. I was looking for, say, just that i run a command and next time I check my drive is not fat32 but ext or ntfs... Lolxx, long shot.

---

