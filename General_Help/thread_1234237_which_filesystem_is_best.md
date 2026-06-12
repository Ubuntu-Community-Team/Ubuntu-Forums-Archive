---
title: "which filesystem is best?"
date: 2009-08-07
forum: General Help
---

### Post by kehon on 2009-08-07
i'm going to move my files from an ntfs partition because i use linux alot and i trust those filesystems more because of the data loss i've had in the past with ntfs.

I want to know which filesystem would be good for what i'm doing.

Basically all the files are svn databases, websites i copied for offline use, music, videos, pictures, large iso dvds and cds for linux plus some i made, and alot more stuff. what i'm saying is there are thousands, if not millions of files in this current ntfs partition and some of them are over 5GB maybe later over 16. So which filesystem would be best and i would like a journaled one for if there are errors because sometimes the power does get cut by me, or an accident.

---

### Post by sasho_zl on 2009-08-07
ext3 is a good choice because it has been around for some time and it is clear from bugs. This is something that can not be said about ext4 because of which I lost all my pictures and documents yesterday due to a system crash from a known ext4 bug.

---

### Post by kehon on 2009-08-07
i heard that there was some sort of max number of files in a directory and max file size on an ext3 filesystem

---

### Post by michy99 on 2009-08-07
ext3 maximum file size depends on the block size, as shown in this chart:

[http://www.crazysquirrel.com/computing/debian/general-commands/ext3-partition-information.jspx](http://www.crazysquirrel.com/computing/debian/general-commands/ext3-partition-information.jspx)

---

### Post by sasho_zl on 2009-08-07
Here is a good article with benchmark tests on some filesystems - [http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)

---

### Post by kehon on 2009-08-07
what about the reiser file system i heard it was good with lots of small files except what about the large files and it said something about not being able to store virtual disk and disk clones on wiki which i sometimes use

---

### Post by lizards2009 on 2009-08-07
The ext3 filesystem. It has been out for a while and [COLOR="Red"]ext4 has some major bugs[/COLOR]!

---

### Post by AoSteve on 2009-08-07
> **kehon said:**
> So which filesystem would be best and i would like a journaled one for if there are errors because sometimes the power does get cut by me, or an accident.

Believe it or not NTFS is a journaling style file system.

[quote=http://en.wikipedia.org/wiki/Journaling_file_system]A **journaling** **file system** is a file system that logs changes to a journal (usually a circular log in a dedicated area of the file system) before committing them to the main file system. Such file systems are less likely to become corrupted in the event of power failure or system crash. [/quote][]("http://en.wikipedia.org/wiki/Journaling_file_system#cite_note-developerworks-1-0")

While ext3 is solid, so is NTFS.   Most file system errors happen from simplistic problems like fragmentation and power failures.   Also failing drives can cause problems as well.   

Personally, I've never had much problem with a well maintained NTFS file system.  That calls for a UPS power supplied system and frequent defragmentation.   Also regular tests on drive integrity are a must.  I've saved plenty of data by learning that a drive was failing before it's finally failed.  One good example was a Quantum Bigfoot drive that was NTFS based.   It was failing, or so the WD/Quantum Tools said, and I got to copy all of the data before it did finally let go.

I've personally never had much problem with ext3 and it's more "extended" journaling system.   NTFS is good, but I trust ext3 a little more.   Either way, the choice is up to you.   I've personally had only one major problem with a non-failing NTFS disk, and it was due to a power failure.  I've never had an ext3 fail on me however.

---

### Post by kavon89 on 2009-08-07
JFS or XFS are the best performing mature file systems as far as I know. Google around for some benchmarks to find out which one is better for your application. I'd use JFS for generally everything.

---

### Post by kehon on 2009-08-07
ok so i copied all of the files form my external drive to the computer then copied them back after formating the external drive but before doing so i noticed that the files on the computer took up more space than they did on an ntfs partion and they weren't compressed. now they won't fit. is there a way to fix this. 

also note: i'm on parted magic live usb(usable) mode with laptop hard drive wiped and now only holding my files from external drive and there are thousands of files i need to copy back to the external

---

### Post by AoSteve on 2009-08-07
Best option is to cut some size by other storage, like a different USB drive or another external drive that way you can get the files where you need them.   Also, you could always cut some pounds by deleting any files you don't want/need anymore.  I have plenty of those and go through my storage drives on a monthly basis just for that size problem.  :)

---

### Post by kehon on 2009-08-07
actually i spent hours yesterday going through crap i downloaded and never got around to looking at. i got tired and moved it to a folder called "Files to Audit" i think i'll put all my music on another drive and just copy those files

---

### Post by AoSteve on 2009-08-08
I have a 32GB flash disk that I keep just for my music.  That's been the most secure and "portable" way of having my music!

---

