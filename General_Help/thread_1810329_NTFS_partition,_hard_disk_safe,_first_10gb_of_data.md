---
title: "NTFS partition, hard disk safe, first 10gb of data OVERWRITTEN - help (notes inside)"
date: 2011-07-22
forum: General Help
---

### Post by AlecTeal on 2011-07-22
So the first 10Gb of a 450GB NTFS partition have just accidently been written over with an Ext4 filesystem that spans the entire partition instead. all foolishness asside, what can be repaired.

Now i know Ext4 likes to jot bits of meta-data down (inodes blocks) along the way, and this can be about 5% of drive capacity, that said, there's alot of small text files and stuff, coe files so forth that can surely be recovered

i've looked into magicrescue, and testdisk, but they fall into the only two groups to exist:
1) filesystem independant, that is search almost like a patern - well exactly like a pattern match, to find the header and footer of files.
2) filesystem recovery tools, like, damanged bootsector, so forth

I need one, that will be able to extract files, i understand this will be a hard task, but.... text files; surely that'll be easy, anyway, please help! 

Alec

this is my backup drive, they''re both WD you see, anyway. yes i'm a fool, but this is important, given the coding is ASCII surely..... i mean

please help

Alec

---

### Post by 2F4U on 2011-07-23
I would try one of the Linux distributions dedicated to computer forensics, such as BackTrack or CAINE. You can find more of them by using the search function of distrowatch. Most of them are available as a liveCD, so no need to install them on your machine.

---

### Post by MARP1961 on 2011-07-23
I think Testdisk might be your answer. Install it via:

```
sudo apt-get install testdisk
```

Once installed you need to launch via the terminal as it is not a GUI application.

```
sudo testdisk
```

or for recovery of all sorts of files:

```
sudo photorec
```

---

### Post by Mark Phelps on 2011-07-23
As they say, experiences vary ... but the last time I tried file recovery using TestDisk, it gave me a useless list of arbitrary filenames.  Maybe your experience will be better.

If not, and if you really need to get the files back from the NTFS partition, I highly recommend using GetDataBack from Runtime Software.

To use it, you will have to disconnect your drive, connect it to a Windows PC, download and install the trial version of GetDataBack, run it in it's deepest discovery mode (best run overnight), and then see if it finds the files you want.  If it does, you will need to purchase it to do the actual file recovery.

---

### Post by AlecTeal on 2011-07-23
programs don't like doing this because all the meta-data, the header of the partition is GONE, does anyone know where NTFS keeps the name of files and whatnot? and does it used linked-lists to know what's going on.

---

