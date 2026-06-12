---
title: "file format"
date: 2010-01-29
forum: General Help
---

### Post by raymondh on 2010-01-29
Am looking for advice/suggestions/recommendations on a file format that can be accessed by windows, linux and OSX. 

Read & write capabilities.  Able to handle large media files as intend to use this in a NAS I am configuring in my home.  

Pro's and con's much appreciated.

NTFS? 

Thanks,

Raymond

---

### Post by cjhabs on 2010-01-29
You could also look at HFS+ - BUT - you need to buy Macdrive 7 for the PC for read/write support.
I believe HFS+ is supported out of the box under Ubuntu but I haven't tried it.

---

### Post by raymondh on 2010-01-29
> **cjhabs said:**
> You could also look at HFS+ - BUT - you need to buy Macdrive 7 for the PC for read/write support.
I believe HFS+ is supported out of the box under Ubuntu but I haven't tried it.

Thanks ... will look into that.  Was hoping though not to spend 'anymore'  :)

Thanks anyway.

Raymond

---

### Post by akshay.sulakhe on 2010-01-29
to enable write support on HFS on Ubuntu,u need to disable journalising...also windows wont write on that(read smoothly),best option,make two partitions,make on XFS,other NTFS..or go for NTFS...but it sucks...its upon u now...

---

### Post by louieb on 2010-01-29
Maybe I'm missing something here. But it does not sound like your wanting to triple boot.
If this is to be accessed by other computers over a network - use a file system native to the host operating system  - the other computers will not know or care what file-system is used by the NAS - all I/O will be handled by the host OS.

---

### Post by raymondh on 2010-01-29
This is what I'm playing around/learning with

[http://www.pcmag.com/article2/0,2817,2351970,00.asp](http://www.pcmag.com/article2/0,2817,2351970,00.asp)

I want to hold my family's "common" media in this unit ... to be accessed by our households' mac/s (HFS+), my wife's windows (NTFS) and my ubuntu (EXT3).  I also want to be able to write unto it using either/any machine in the house, whether it be from the mac, the win7 or my ubuntu.  I also plan to link the appleTV to this for additional storage.

I tried your suggestions (akshay and LouieB) using the host OSX format and putting in 1 mp3 file to test.  The macs' and the appleTV were able to see and retrieve from it.  No joy on the windows laptop.  Have not tried ubuntu netbook yet as I'm currently googling around for a window solution.

Will keep the XFS + NTFS solution in mind.  Was hoping for a more common, 1 format solution.

Your inputs much appreciated.

Raymond

---

