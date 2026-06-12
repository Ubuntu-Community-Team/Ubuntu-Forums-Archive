---
title: "lost files copying from ext4 to ntfs"
date: 2011-11-25
forum: General Help
---

### Post by ponto18 on 2011-11-25
Hi guys,

I have a big problem... i copied around 10GB of data from my linux partition to my Data partition that is NTFS, and looking with nautilus the data was successfully copied, but when I booted into windows i checked and the data was not there anymore... sh..t

So in linux i used foremost to try and recover it but no joy, so i thought the data was already in the NTFS partition, when i got lost somehow...
Back in windows, i started the recovery program and guess what, couldn't find it either...

Where is my data??

Can anyone help me on how to recover it?

Thanks.
Carlos

---

### Post by Mark Phelps on 2011-11-26
Was Windows hibernated during the time you copied the files?

IF so, this will NEVER work -- as Windows saves away a copy of the partition tables when it hibernates, and when it awakens, it rewrites the partition tables.

Any changes made to the Windows filesystem while Windows was hibernated are removed -- which is exactly how Hibernation is supposed to work.

---

### Post by bluexrider on 2011-11-26
use testdisk with photorec.

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by blueridgedog on 2011-11-26
Please clarify...if you copied the source and the copy failed, then the source still exists and can be copied again. Perhaps I have miss-read your post, but if you tried to copy from A to B and it failed, then you can try another method.  Using Linux to write to NTFS is a bit of a gamble at this point for a variety of reasons.

---

### Post by Slim Odds on 2011-11-26
> **blueridgedog said:**
> Please clarify...if you copied the source and the copy failed, then the source still exists and can be copied again. Perhaps I have miss-read your post, but if you tried to copy from A to B and it failed, the you can try another method.  Using Linux to write to NTFS is a bit of a gamble at this point for a variety of reasons.

Actually, the latest NTFS filesystem drivers work quite well. But you still have to close file systems properly. That usually where people make mistakes and "lose" files.

---

### Post by ponto18 on 2011-12-02
> **Mark Phelps said:**
> Was Windows hibernated during the time you copied the files?

IF so, this will NEVER work -- as Windows saves away a copy of the partition tables when it hibernates, and when it awakens, it rewrites the partition tables.

Any changes made to the Windows filesystem while Windows was hibernated are removed -- which is exactly how Hibernation is supposed to work.


Yes it was, like it always is...
So there is no way of getting it back? That's a shame...
Thank you.

---

### Post by ponto18 on 2011-12-02
> **Slim Odds said:**
> Actually, the latest NTFS filesystem drivers work quite well. But you still have to close file systems properly. That usually where people make mistakes and "lose" files.

Well I thought that as well, that's why I was never worried about this operation since I have done it lots, lots of time before, but maybe not with the Windows in hibernate mode.

And to clarify you:
1- Windows was hibernated; 
2- I booted into Ubuntu;
3- I moved (not copied - sorry for my confusion) the data from the Ubuntu partition (ext4) to my data partititon (NTFS - does not contain the windows binaries - it is data only);
4- I checked that the data was in fact on the NTFS partition and not in the ext4 anymore. So far so good.
5- Later on I booted into windows and the data was gone...
6- I tried several methods to retrieve it, both in windows as in linux;
 Conclusion - my data is lost in the air..

Thanks guys.
Carlos

---

### Post by Slim Odds on 2011-12-02
Just to be clear, it's NOT the partition table that Windows overwrites when returning from hibernation... it's the file allocation tables. That's why files do not appear even though you wrote them to that partition.

It should be noted that Windows never, ever expects any other OS to touch a machine here it is installed.

---

### Post by alphaamanitin on 2011-12-02
PhotoRec or TestDisk should be able to recover the files on the linux side of things.  Just to be clear it is not, as stated above, "TestDisk with PhotoRec."  PhotoRec and TestDisk are two separate programs that are bundled together and are best used in different situations.  I would run PhotoRec on the linux HD that originally had the data.  I doubt that linux does a destructive delete when moving data.  

AlphaA

---

