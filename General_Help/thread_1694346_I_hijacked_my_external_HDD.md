---
title: "I hijacked my external HDD"
date: 2011-02-24
forum: General Help
---

### Post by Fryie on 2011-02-24
Hello there,

So I was playing around with dd and I did something really stupid. I wanted to write to my USB stick, but I wrote to my external hard disk instead.
[B]This is very unfortunate!
[/B]My external hard disk contains all my music, movies, series, backups, a lot of uni stuff, etc.

Now I only wrote 1,44MB to the disk (since I was trying to write a floppy image to the USB stick), and I reckon this completely destroyed the filesystem information. The data are most probably still there. I could still access the data, but then I unmounted the partition (perhaps I shouldn't have done that? But I would have had to anyway at some point...) and now of course all seems gone. But I don't think all that data has really been deleted. The problem is that I cannot easily make a backup of that data since its like 160GB and I don't have that space available on my laptop.

Now I don't even remember whether I had a FAT or a NTFS system on that hard disk (I believe it was the latter, but I'm not 100% sure). Is there any way I could possibly find out and if yes, is it possible to get back at that data?

Please soften my unbearable pain and tell me there is a possibility to do something!

Thank you all

---

### Post by seawolf167 on 2011-02-24
I would try [TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")and see if it can recover your partition table (if you scroll down on the front page, it has a download & how to)

---

### Post by psusi on 2011-02-24
Photorec and pray.

---

### Post by Fryie on 2011-02-24
Thank you very much. I tried testdisk and it appears it worked. At least I can see all my data.

Whoever made that tool has my eternal gratitude. :)

---

### Post by Fryie on 2011-02-25
Just a post scriptum, in case anybody experiences the same problem:

It seems TestDisk hadn't been able to recover all the files, my whole music folder seemed to be gone. I was able to solve that problem by booting Windows and running chkdsk on my hard drive.

---

### Post by seawolf167 on 2011-02-25
Glad to hear it worked :) 

Now that you have been thoroughly worried... make sure you back everything up! [Clonezilla ]("http://clonezilla.org/")is wonderful for backing up entire drives &/or partitions.

---

