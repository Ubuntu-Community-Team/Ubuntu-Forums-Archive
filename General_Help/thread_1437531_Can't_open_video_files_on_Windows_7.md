---
title: "Can't open video files on Windows 7"
date: 2010-03-24
forum: General Help
---

### Post by jibun on 2010-03-24
Hi everyone ! I have a problem. I have some video files (.mkv) wich I downloaded and I can open (watch) them easily. But when I tried to open them on my Windows 7 after I moved them in a NTFS drive (from Ubuntu 9.10 to Wndows 7) I couldn't play them at all. "Can't open or find the file" that pops up when I try to open them. I already tryed with other player but it was the same.

Is there anyone who can solve my problem? 

Thanks in advance.

---

### Post by Bradtek on 2010-03-24
Isn't this a question for a Windows forum ? :p

Most likely you do not have the codec installed.

try this

[http://www.free-codecs.com/Matroska_Pack_download.htm](http://www.free-codecs.com/Matroska_Pack_download.htm)

---

### Post by wilee-nilee on 2010-03-24
If it's playable this pack should do it just watch the install and make sure you get everything.
[http://www.codecguide.com/download_kl.htm](http://www.codecguide.com/download_kl.htm)

---

### Post by jibun on 2010-03-24
Thanks guys. But I already had codecs installed (K-lite Codec Pack).
I think it's a problem about Windows who can't open file after they are opened into Ubuntu ...

[@Bradtek]("http://ubuntuforums.org/member.php?u=566742") Sorry I didn't see the Windows section. My bad

---

### Post by Aped on 2010-03-24
Not likely, since Ubuntu doesn't CHANGE the files it opens in any way; go download VLC and open them with that. It'll work and when it does, that means that you just don't have the right codecs installed. 

It's possible, though hugely unlikely, that whatever media center/player you used in ubuntu DID cause some change in the file; what did you use? 

Consider changing to the CCCP over K-Lite, too; far more robust and well-supported iirc.

---

### Post by jibun on 2010-03-24
@Aped : I was thinking the same way you thinked about the fact that an Ubuntu player may change the file... likely not . I use VLC on Ubuntu 9.10 and on Windows 7 too. 

But Oh My God !! I somehow resolved the problem !! It's a problem about EXT3/4 file system and NTFS ! Windows can't read nor open where a file copied from an EXT3/4 partition to an NTFS one. Plus when you try to delete the file (copied from EXt4 to NTFS) it's stated as "Not found" or "0 Kbyte" or "Can't open". 

This is how you must deal with this problem .. lol auto solving..

       => Get a FLASH DRIVE USB and FORMAT it to FAT32 system (on Windows or Linux)
       => Boot into Ubuntu (Linux) and COPY the file weither it's on EXt3/4 or NTFS 
       => And PAST it to that FLASH DRIVE
       => Then restart and go to Windows (7) then COPY and PAST the file to your Windows Folder (again if you had already the file in Windows)
       => Then restart into Ubuntu and DELETE the ORIGINAL file 
       => And you are done !!! 

NOW you can open it from Windows or from Linux.
Unfortunately I have a 1 GB flash drive so I repeated the method 5 times to finish my 4.3 GB files!!

Isn't it weird....??? I was so surprised when I did it . lol

Thanks guys for your replies.

Linux rocks !! Windows sucks !!

---

### Post by Aped on 2010-03-24
Very interesting, but that *shouldn't* be the case...

---

### Post by jibun on 2010-03-24
I'm sorry but it's almostly the case :( ..

---

### Post by gordintoronto on 2010-03-24
> **jibun said:**
> But Oh My God !! I somehow resolved the problem !! It's a problem about EXT3/4 file system and NTFS ! Windows can't read nor open where a file copied from an EXT3/4 partition to an NTFS one. Plus when you try to delete the file (copied from EXt4 to NTFS) it's stated as "Not found" or "0 Kbyte" or "Can't open". 


This is not at all true.  I routinely copy multimedia files from my EXT3 partition to a Windows 7 NTFS partition and play the files in media player.

---

### Post by jibun on 2010-03-24
I misunderstand it ! Sorry! I meant in my case it was the case. Oh and I can play very well some files copied from EXT4 to NTFS. Maybe different hard drives + file system problem.

EXT4 file system with an old SAMSUNG SP0842N IDE 80 GB on 20 GB second partition (first one with Windows)
NTFS for the Windows + another HDD SAMSUNG HD322HJ 320 GB NTFS where I copied my files.

PS: Mine is an EXT4 not EXT3 ..

---

### Post by Mark Phelps on 2010-03-25
Are you by any chance mounting your Win7 partition read/write in Ubuntu?  If so, THAT could be part of the problem.

I only mount my MS Win partitions read-only, because although NTFS-3G is SUPPOSED to be able to mount them read/write without any difficulties, I have run into problems in the past when I automatically mounted NTFS partitions.

However, when I created separate data partitions, formatted some VFAT and some NTFS, I didn't have those problems anymore.

Appears to be something related to mounting Vista/Win7 OS partitions in Ubuntu.

---

