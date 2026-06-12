---
title: "Can't read text files"
date: 2010-03-31
forum: General Help
---

### Post by cabman46 on 2010-03-31
I recently installed Ubuntu 9.10 on a spare PC. Unfortunately, it's in a location without internet access for the time being. I'm trying to transfer text files from an XP machine to this Linux machine via a flash drive. I can open the text files in Gedit but they are all unreadable. All of the text is lower case y's with lines above them. I've tried several different text editors on the windows machine and they all do the same thing. However, if I create a test text file from Gedit on the Linux box, I can read it correctly on the Windows machine. When I first noticed this was when I attempted to copy an address book (.csv file) from xp Thunderbird the tried to import it, via the flash drive, to Evolution. 

I'm new to Ubuntu and learning.

Thanks

---

### Post by bobcollard on 2010-03-31
> **cabman46 said:**
> I recently installed Ubuntu 9.10 on a spare PC. Unfortunately, it's in a location without internet access for the time being. I'm trying to transfer text files from an XP machine to this Linux machine via a flash drive. I can open the text files in Gedit but they are all unreadable. All of the text is lower case y's with lines above them. I've tried several different text editors on the windows machine and they all do the same thing. However, if I create a test text file from Gedit on the Linux box, I can read it correctly on the Windows machine. When I first noticed this was when I attempted to copy an address book (.csv file) from xp Thunderbird the tried to import it, via the flash drive, to Evolution. 

I'm new to Ubuntu and learning.

Thanks
Try opening your text files with Open Office Writer.

---

### Post by cabman46 on 2010-03-31
> **bobcollard said:**
> Try opening your text files with Open Office Writer.

I tried this also. The characters display the same way.

---

### Post by burton247 on 2010-03-31
probably a silly question but youre sure theyre .txt?

---

### Post by cabman46 on 2010-03-31
> **burton247 said:**
> probably a silly question but youre sure theyre .txt?

Yes, I saved them as .txt. I'm going to try to save as .doc and see if that will work? 


Could I have done something wrong during the install to create this problem? Everything else appears to work from the thumb drive. I don't have much on there but other file types seem to work OK.

---

### Post by cabman46 on 2010-03-31
I just created a test .doc file and it displays the exact same characters in both Gedit and Open Office on the Linux machine.

I have a couple extra hard drives to play with so I'm going to install 9.10 on one and see if I somehow screwed up the encoding during the install.

---

### Post by dwarfolo on 2010-03-31
Check the dimension of these files. I suspect it could be some sort of virus. If the virus has managed to sthealt itself inside notepad it may be trying to replicate.

---

### Post by cabman46 on 2010-03-31
> **dwarfolo said:**
> Check the dimension of these files. I suspect it could be some sort of virus. If the virus has managed to sthealt itself inside notepad it may be trying to replicate.
I don't understand what you're asking??

---

### Post by cabman46 on 2010-03-31
I installed 9.10 on a different hard drive to see if I screwed up the install but it does exactly the same thing. I'm going to put some of these files on a CD and see what happens.

---

### Post by dwarfolo on 2010-03-31
I was suggesting to check the size of the files. If the size is meaningfully different from what it should be, it could be a clue about the presence of a virus.

---

### Post by bobcollard on 2010-03-31
If you still have Windows, try saving the files in *.rtf  (Rich Text Format)

---

### Post by cabman46 on 2010-03-31
> **dwarfolo said:**
> I was suggesting to check the size of the files. If the size is meaningfully different from what it should be, it could be a clue about the presence of a virus.
Oh I see what you were asking. I think it's ok? I just wrote a short sentence and it reports 1k in size. I don't think it goes any lower than 1k? BTW, I used Open Office writer, notepad, and Wordpad to make these .txt and.doc files. They all do the same thing. As I mentioned, I'm going to try some text files from a CD and see what happens. Maybe it don't like my thumb drive?

---

### Post by cabman46 on 2010-03-31
> **bobcollard said:**
> If you still have Windows, try saving the files in *.rtf  (Rich Text Format)
I'll try this and get back asap.

---

### Post by cabman46 on 2010-03-31
Well, this is interesting, I can read text files ok from a CD with the Linux PC. Just for general drill I tried to copy the test files I had on the thumb drive to the CD and they still don't read. I believe the problem is with the flash drive somehow? It works fine in the Windows PC reading and writing. I've been using it in 5 or 6 different Windows machines for months with no problem. Apparently Linux don't like it though. I checked the format and it's FAT32.  I don't know what else to check.

---

### Post by cabman46 on 2010-03-31
> **cabman46 said:**
> I'll try this and get back asap.
I created a .rtf file and copied it to the CD and thumb drive. Again, the Linux machine reads the CD but not the thumb drive. I'm convinced something is unique with the thumb drive causing this problem. Just text files though! I have other files on there like .avi's that work fine on Linux and Windows.

---

### Post by bobcollard on 2010-03-31
> **cabman46 said:**
> I created a .rtf file and copied it to the CD and thumb drive. Again, the Linux machine reads the CD but not the thumb drive. I'm convinced something is unique with the thumb drive causing this problem. Just text files though! I have other files on there like .avi's that work fine on Linux and Windows.
What is the format of the thumb drive?  They are normally FAT 16 or 32.

---

### Post by cabman46 on 2010-03-31
> **bobcollard said:**
> What is the format of the thumb drive?  They are normally FAT 16 or 32.
It's FAT32 32 gig.

I plugged this thumb drive into the XP machine and did dskchk (with repair checked) and defragged it. Nothing different. I copied some files to a DIFFERENT thumb drive and all the file types work fine on the Linux box. I actually migrated my address book from XP Thunderbird to Evolution! Not bad for a nOOb huh? I don't have a clue what's wrong with the original thumb drive? Once I dump everything on it to the XP machine I'm going to try to format it and and go through these test again and see what happens. Id give up if it wasn't 32 gig and kinda pricey!

---

### Post by bobcollard on 2010-03-31
> **cabman46 said:**
> It's FAT32 32 gig.

I plugged this thumb drive into the XP machine and did dskchk (with repair checked) and defragged it. Nothing different. I copied some files to a DIFFERENT thumb drive and all the file types work fine on the Linux box. I actually migrated my address book from XP Thunderbird to Evolution! Not bad for a nOOb huh? I don't have a clue what's wrong with the original thumb drive? Once I dump everything on it to the XP machine I'm going to try to format it and and go through these test again and see what happens. Id give up if it wasn't 32 gig and kinda pricey!
Format it on your Linux Machine.  If this solves your problem please Edit your first post in this thread and add [Solved] to the Title so someone else may benefit from your experience.

---

### Post by cabman46 on 2010-03-31
This should close this thread.

I would like to thank each of you for your help with this noob.

I formatted this thumb drive and apparently did the trick. I can now write and read most file types on both Windows and Ubuntu.

Thanks again

---

### Post by blur xc on 2010-03-31
How were the text file in xp created?

BM

---

