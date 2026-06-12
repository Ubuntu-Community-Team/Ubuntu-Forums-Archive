---
title: "backing up files with &quot;invalid encoding&quot; in the filename"
date: 2010-05-10
forum: General Help
---

### Post by Tjampman on 2010-05-10
Hi

I wish to install ubuntu 10.04 on my desktop PC, but before I do that I need to back up my HDD.
Due to alot of filenames show as having a wrong encoding, ubuntu will not let me copy the files.
We are talking hundres of files in many sub folders.

The way I see it, I either have to:
1. have ubuntu back up my files in annother way (and not simply dragging and dropping as I have tried)
2.use some sort of tool to convert/fix the filenames so I wil then be able to back them up.

I've tried the following using convmv [as mentioned here]("http://ubuntuforums.org/showthread.php?t=1236012"), but with no succes. 
```
convmv -r --notest -f windows-1255 -t UTF-8 *
```

I'm using a live cd, thus the files are not located in my home folder, but on a separate parrtition.

What would you advice me to do in order to back up these file.

TIA

---

### Post by Old *ix Geek on 2010-05-10
> **Tjampman said:**
> Hi

I wish to install ubuntu 10.04 on my desktop PC, but before I do that I need to back up my HDD.
Due to alot of filenames show as having a wrong encoding, ubuntu will not let me copy the files.
We are talking hundres of files in many sub folders.

The way I see it, I either have to:
1. have ubuntu back up my files in annother way (and not simply dragging and dropping as I have tried)
2.use some sort of tool to convert/fix the filenames so I wil then be able to back them up.

I've tried the following using convmv [as mentioned here]("http://ubuntuforums.org/showthread.php?t=1236012"), but with no succes. 
```
convmv -r --notest -f windows-1255 -t UTF-8 *
```

I'm using a live cd, thus the files are not located in my home folder, but on a separate parrtition.

What would you advice me to do in order to back up these file.

TIAThese files are on a windoze box?  How about zipping each folder? You say that a lot of filenames show as having wrong encoding--do you mean because they have spaces in their names, or what?  If so, that won't cause any problems zipping them.  Then you could just unzip them after installing Ubuntu--I know I've unarchived files that contained filenames with spaces and did NOT have issues. YMMV.

---

### Post by StuartN on 2010-05-10
> **Tjampman said:**
> I'm using a live cd, thus the files are not located in my home folder, but on a separate parrtition.

You could try mounting the partition with the iocharset= option and see if you can find an appropriate encoding that the files show up correctly.

---

### Post by Tjampman on 2010-05-10
No, the files with the "invalid encoding" were originally named or created on a windows box. The reason they are invalid is because they have localized characters, fx æ, ø and å. These letters are replaced by a question-mark with the "invalid encoding"-string added to the end of the file name.
Pretty much the same problem as in the other thread I linked to.
[http://ubuntuforums.org/showthread.php?t=1236012](http://ubuntuforums.org/showthread.php?t=1236012)

The files are located on a HDD with a ext-4 file system, and as I would like to install Ubuntu (as well as windows) on this HDD, I need to copy all the files from the HDD to my external one.
When I try to copy the affected files, I get an error message and the choice to skip the file or cancel the entire operation.


I apologies for not being clearer on this, but I had spent so much time on the topic and i guess i got tunnel vision. I hope it is clear now, though.

---

### Post by Tjampman on 2010-05-10
> **StuartN said:**
> You could try mounting the partition with the iocharset= option and see if you can find an appropriate encoding that the files show up correctly.

How do I do that?
I'm sorry but I never tried to mount a partition with the command line.

I believe the charset is windows-1252

---

### Post by StuartN on 2010-05-11
> **Tjampman said:**
> How do I do that?

I am not sure - in a recent post you state that the partition is formatted ext4, but that the problematic files were created with Windows. Normally you would mount a foreign filesystem with:

```
mkdir ~/my_partition
mount /dev/sdb1 ~/my_partition -t ntfs -o iocharset=iso8859-1
```

where ~/my_partition is a location where you wish to mount the partition, -t is the type of filesystem and -o is mount options separated by "," with no intervening spaces. The option iocharset=iso8859-1 reads filenames with unusual characters as being Western European. (iocharset is in keeping with most other filesystems, but strictly, this option is now nls= for ntfs).

**man mount** does not indicate that **-t ext4** can take an iocharset option.

---

### Post by Tjampman on 2010-05-11
Yep, you're right that didn't work...
I discovered that my disk is ext3 but it still did not work.
I discovered that I can copy/paste the affected files on the my drive, I just cannot copy them to another drive, so I tried to mount this partition onto my external HDD, but that I did not succeed in... Perhaps because my external HDD is NTFS?
I also tried to compress a few files and transfer the archive, that seemed promising, until I tried to decompress the files...

---

### Post by Tjampman on 2010-05-11
I think my only sollution is to make convmv work, does anyone have any experience in using that program/command? 
As I mentioned earlier I have tried it already, but did not succeed. The last time I tried I got some weird output in the terminal that I did not quite understand:
> ubuntu@ubuntu~$ convmv -r --notest -f windows-1252 -t utf8 *
Your perl version as fleas #37757 #49830
ready
ubuntu@ubuntu~$

What does it mean and how can I make it work as intended?

TIA

---

### Post by Tjampman on 2010-05-13
I ended deleting many of the files, and then renaming the rest manually, but thanks for trying to help me.

---

### Post by areskz on 2011-06-16
You can also try using *recode* command.

---

