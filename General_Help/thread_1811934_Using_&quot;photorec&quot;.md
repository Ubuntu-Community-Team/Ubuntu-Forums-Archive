---
title: "Using &quot;photorec&quot;"
date: 2011-07-25
forum: General Help
---

### Post by Bigneil on 2011-07-25
Hi every one.  I have used photorec to recover files from an external drive that i accidentally formatted ( don't ask#-o ).

The recovery was successful but.... I can't open any of the office documents. any ideas?


thanks in advance

Bigneil

---

### Post by pqwoerituytrueiwoq on 2011-07-25
can you upload a sample document (assuming you have one that does not have sensitive data in it)

---

### Post by Mark Phelps on 2011-07-25
When you say "office", you mean Microsoft Office, or Open Office?

If the former, were these the newer "docx" (XML) files? OR were they the older "doc" files?

Also, what was the filesystem that got reformatted -- Ext4, or NTFS?

---

### Post by alphaamanitin on 2011-07-25
Please tell me you have kept the drive that you reformated and have done nothing else to it besides photorec.  I have personally deleted my every partition on my Windows XP hard drive, and then reformatted it to FAT32 using gparted.  I used testdisk to completely recover the drive.  After I used SuperGRUB to repair the windows XP boot loader I booted into my XP like nothing had happened.  

So, is your drive still around, unbothered?  If so clone it using the dd command and then we can work on it.  

AlphaA

---

### Post by Bigneil on 2011-07-26
Thanks for your Help guys. 
 Ok, here is a little background. I was repairing an old dell lappy for a friend, but couldn't bring it back to life, It's running XP so, using my 'buntu live CD I retrieved the data from the "documents and settings" folder to an external hard drive..ok so far, but then i totally goofed up. when I was re-installing his XP I left the external drive plugged in and formatted it by accident (Doh!). well i figured all was not lost and fired up photorec and retrieved the data from the external drive. I spoke to my friend and i told him that i may have lost some of his data,...He was a little upset but said that there was nothing really important to him except some of the office stuff and typically the only files i am struggling with are the office files. 

They are MS office mostly word, I don't know what version. so far I have tried to open them with "Libre", "Open office" and "MS word 2007".

I can upload one, the data is not sensitive in any way.

P.S the external drive was FAT32

---

### Post by Mark Phelps on 2011-07-26
Can't help you with Photorec.  Have found it to be generally useless in recovering damaged MS Windows filesystems.

If you can hook the drive up to a Windows PC, you can try the following:
1) Go to the Runtime Software website and download the trial version of GetDataBack for FAT
2) Instll it to the PC
3) Run GetDataBack in the deepest search mode -- probably overnight would be best
4) See if it finds the files you need
5) If it does, you will have to purchase it to do the actual file recovery (the trial only does the search).

---

### Post by Bigneil on 2011-07-26
here's one

---

### Post by Bigneil on 2011-07-26
> **Mark Phelps said:**
> Can't help you with Photorec.  Have found it to be generally useless in recovering damaged MS Windows filesystems.

If you can hook the drive up to a Windows PC, you can try the following:
1) Go to the Runtime Software website and download the trial version of GetDataBack for FAT
2) Instll it to the PC
3) Run GetDataBack in the deepest search mode -- probably overnight would be best
4) See if it finds the files you need
5) If it does, you will have to purchase it to do the actual file recovery (the trial only does the search).

Cool, i will give that a go...I'm not surprised, having to pay for stuff is a recurring issue in windows systems..tut tut.  lol

---

