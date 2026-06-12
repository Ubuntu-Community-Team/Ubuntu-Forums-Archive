---
title: "2nd hard drive fat32"
date: 2009-07-03
forum: General Help
---

### Post by unsung hero on 2009-07-03
first im three weeks into using ubuntu and like it so much im sticking with it, however i am going to partition my first hard drive to have xp on it as well, now heres what else i plan on doing...
i want to get a second hard drive formated to fat32, the reason for this is that i want both ubuntu and xp able to read and write to this hard drive, has anyone else done this?

i got this idea when i noticed that ubuntu does a great job at recognizing both my usb flash drive and ipod shuffle which i used  on xp.

i plan on storing all media files (pics, music, or any important docs) on my second much larger hard drive and it would be great to be able to access everything regardless of what os im running

so again i just want to know if anyone else is doing this, has done this, or if this will even work, so please give me some input :p

---

### Post by Idefix82 on 2009-07-03
Glad you like Ubuntu.

What you are describing is in fact quite a common setup. You can also format the data drive as ntfs, Ubuntu should be able to read it and write to it without problems as well.

---

### Post by unsung hero on 2009-07-03
thanx for the quick reply
and yes i like ubuntu so much the only reason im keeping xp is for a few programs that seem to only run flawlessly under windows,

one of them being winamp which ive used since 98 and to this day have not seen a substitute that comes close to all its features, its ability to organize your ipod has only made it that much better,  i tried a number of ubuntu music and ipod programs and still have not found anything close to winamp, bottom line is winamp allows me to organize all my media with ease

but getting back to formats u mentioned i can do ntfs, if thats the case then i suppose i should format to ntfs...? also can the second hard drive be the slave or does it need to be an external hard drive?

---

### Post by attiliok on 2009-07-03
Idefix is right, it's an usual situation.
I have the same configuration. I listen to my music with ITUNES from Win and with Quodlibet or Gtkpod from ubuntu.

You can use both fat32 o ntfs beacause new versions of ubuntu can write to ntfs partition too. Choose one of them and format your harddisk with the filesystem you want.
It can be external or internal slave, no problems about that.

Probably you know that a winamp-like program in linux is XMMS. It doesn't suite to your needs?

---

### Post by unsung hero on 2009-07-03
i would use xmmx if it was still being supported and developed
im happy to know that this is a common set up
i looked into different ways of doing this from emulating windows to have 2os on 2 hd
but partitioning one hd and using a second hd for storage seems to be the best way
thanks for the replies

---

### Post by HermanAB on 2009-07-03
FAT is not good for media:
Unreliable
Maximum file size of 2GB
Windows has a bad Ext3 file system available
Linux has a good NTFS file system available

So you best solution is NTFS.

---

