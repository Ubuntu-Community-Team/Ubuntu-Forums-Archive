---
title: "Permissions on NTSF partition - Problems"
date: 2009-08-01
forum: General Help
---

### Post by fasti on 2009-08-01
Hello everyone,

I've recently had many weird problems with one of 3 partitions I have on my HDD.
All 3 partitions are formatted as NTFS file systems, since I was a windows user a couple years ago.

The biggest problem appears to be that I am unable to add or remove files in ONE folder on that partition.
Trying to remove or add files or folders in that folder result with error messages from nautilus, of this kind:
> There was an error deleting untitled folder 8.
Error removing file: Input/output error
> Error while creating directory untitled folder 9.
There was an error creating the directory in /media/Partition3/Azureus.
Error creating directory: Input/output error
> There was an error copying the file into /media/Partition3/Azureus.
Error opening file '/media/Partition3/Azureus/file.txt': Input/output error

As you may have noticed, it wasn't my intention to have _9 untitled folders_. (:))
Nautilus apparently creates them despite the error messages.

Another problem, which I had brought up in another [thread (link)]("http://ubuntuforums.org/showthread.php?t=1222162") when I thought the problem was smaller,
is that there are a couple of files that exist on the root of the partition (not in a folder), that I cannot delete.
I think that maybe there was in interruption while they were moved from a different partition.
For the first file, the error message is similar to errors in the folder I mentioned before:
> There was an error deleting 072707.wmv.
Error removing file: Input/output error.
I even tried "sudo rm -f 072707.wmv", but I get the same result.

The second file, I can't actually see unless I do "ls -la" interminal for the partition,
and I see that one of the files has question marks instead of file properties:
> -rwxrwxrwx 1 root root 241945145 2009-05-19 01:55 prisonbreaks03e04.wmv
-rwxrwxrwx 1 root root 0 2009-07-25 13:20 072707.wmv
-rwxrwxrwx 1 root root 1559072154 2008-09-27 09:39 080507.wmv
-????????? ? ? ? ? ? Aidn2.wmv
-rwxrwxrwx 1 root root 259937421 2009-05-19 01:52 prisonbreaks03e05.wmv
drwxrwxrwx 1 root root 65536 2009-07-25 21:00 Azureus
-rwxrwxrwx 1 root root 1574459 2009-04-26 02:13 Azureus_Stats.xml
drwxrwxrwx 1 root root 0 2009-06-10 19:38 backup ff3.5 stuff 


I do think the partition is loaded correctly with ntfs-3g, because most folders work properly,
and in /etc/fstab the partition is mounted this way:
> /dev/sdb6 /media/Partition3 ntfs-3g rw,locale=en_US.utf8,uid=1000 0 0 

I would appreciate any help. Thanks in advance.

p.s. - I'm using Ubuntu Jaunty. (I used the "different OS" prefix because of the whole NTFS topic).

---

### Post by michy99 on 2009-08-01
Have you tried deleting the files from Windows?

---

### Post by fasti on 2009-08-01
> Have you tried deleting the files from Windows? 

Thanks for your reply, but I removed that horrible OS from my computer.


Do you have any linux based solutions?

---

### Post by fasti on 2009-08-02
please, guys... I really need your help...

this problem is paralyzing my torrent folder...


:-(

---

### Post by credobyte on 2009-08-02
```
sudo chown -R user:user /media/Partition3
```
Replace user:user with your username & let us know if it helps.

---

### Post by fasti on 2009-08-03
wow, it did something...

well, by doing "sudo chown -R user:user /media/Partition3" I got:
> chown: changing ownership of `/media/Partition3/Aidn2.wmv': Input/output error
which impressed me.  ...but,
still, no success with deleting these files.
I still get-
rm: cannot remove `Aidn2.wmv': Input/output error
rm: cannot remove `072707.wmv': Input/output error

---

### Post by Lavaeagle on 2009-08-03
Depending on how long you have had this install do you think that something might have gotten in you're computer and messed things up?

---

### Post by asmoore82 on 2009-08-03
sounds like failing hardware, test with badblocks ...
```
sudo badblocks -sv /dev/sd?
```

---

### Post by ppirilla on 2009-08-03
It may be overkill; I don't know how big the partition is, or how much file space you have elsewhere, but did you consider backing up the important data and reformatting the partition in a Linux-friendly file system?

---

### Post by fasti on 2009-08-03
for - "sudo badblocks -sv /dev/sdb6"
I get:
> Checking blocks 0 to 106393878
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.


ppirilla-
> It may be overkill; I don't know how big the partition is, or how much file space you have elsewhere, but did you consider backing up the important data and reformatting the partition in a Linux-friendly file system?
Actually, I'm starting to think ubuntu has no solutions for NTFS problems,
so I might have to buy a new HDD, transfer the data and format the old HDD.
(to the ext3 or ext4 file-system, which Ubuntu supports better).

But that's not why I came looking for help with you guys, right?
(I could have just quit trying to fix it without posting here).

Please, anyone? suggestions?

---

### Post by merlinus on 2009-08-03
Have you tried running an antivirus check on the partition?  I assume you tried running nautilus with

```
gksu nautilus
```

---

### Post by Primefalcon on 2009-08-03
> **fasti said:**
> for - "sudo badblocks -sv /dev/sdb6"
I get:



ppirilla-

Actually, I'm starting to think ubuntu has no solutions for NTFS problems,
so I might have to buy a new HDD, transfer the data and format the old HDD.
(to the ext3 or ext4 file-system, which Ubuntu supports better).

But that's not why I came looking for help with you guys, right?
(I could have just quit trying to fix it without posting here).

Please, anyone? suggestions?
there is a tool you can use if no one else answers within about 10 minutes I'll see what I'll check back and post if no one else has

---

### Post by ppirilla on 2009-08-03
> **fasti said:**
> Actually, I'm starting to think ubuntu has no solutions for NTFS problems,
so I might have to buy a new HDD, transfer the data and format the old HDD.
(to the ext3 or ext4 file-system, which Ubuntu supports better).

That's probably the biggest of your problems.  Microsoft invented the NTFS, intending for it to only ever work with windows computers.  The open source community has had to reverse-engineer everything.  When I last dealt with a Linux/Windows dual-boot system three years ago, writing to an NTFS partition from linux was simply not possible, though reading data worked more often than not.


In short, Linux just doesn't play well with Microsoft's NTFS, and probably never will.

---

### Post by Primefalcon on 2009-08-04
Ok sorry for taking so long but use synaptic and install ntfsprogs

then run the command along these lines

```
sudo ntfsfix /dev/sda1
```

make sure your windows partition is unmounted when you do this and change the drive sda1 for your type of drive such as hda1 and also for the check with a program such as gparted to find out the specifics

for example
[IMG]http://i30.tinypic.com/5perro.jpg[/IMG]

you can see above from the ntfs part that my windows partition is /dev/sda1, for notes sake even if you don't have ubuntu installed you can do a live disk for this

Also for reference Ubuntu ntfs support has come a long way it writes natively now, and with 0 issues

---

### Post by skillllllz on 2009-08-04
Your best bet is to borrow a Windows XP CD to boot up and run chkdsk from the built-in recovery console.

As far as I know ntfsfix (as recommended by another user above) often fails to repair NTFS file-system errors such as this. NTFS truly is a hunk-o-junk and the only tool that really knows how to help it limp along is MS's own chkdsk utlity.

---

### Post by Primefalcon on 2009-08-04
> **skillllllz said:**
> Your best bet is to borrow a Windows XP CD to boot up and run chkdsk from the built-in recovery console.

As far as I know ntfsfix (as recommended by another user above) often fails to repair NTFS file-system errors such as this. NTFS truly is a hunk-o-junk and the only tool that really knows how to help it limp along is MS's own chkdsk utlity.
Hunk of junk is an understatment, it's suppose to be a journaling filesystem yet somehow it still messes everything up enough that it's just as bad at fragmenting as the fat systems

---

### Post by skillllllz on 2009-08-04
> **Primefalcon said:**
> Hunk of junk is an understatment, it's suppose to be a journaling filesystem yet somehow it still messes everything up enough that it's just as bad at fragmenting as the fat systems

Oh, believe me, after ~15yrs of using NTFS, I know all about its shortcomings. I have utter disdain for NTFS.

---

### Post by fasti on 2009-08-06
Well, I want to thank all you guys for advising me.

So, that settles it, I'll give up on trying to fix the file system.
I'll buy a new HDD, transfer all my files to it and format the old HDD as ext3 (or ext 4). (or would you recommend a better file system?).

Thanx.

---

