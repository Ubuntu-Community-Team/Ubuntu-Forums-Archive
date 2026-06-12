---
title: "Making sure everything backed up correctly"
date: 2010-03-11
forum: General Help
---

### Post by teKro on 2010-03-11
Hey. I finally bought a second hard drive to back up all my files since I'm planning on wiping my hard drive completely clean and reinstalling Windows and Ubuntu once Lucid comes out. I'm just wondering, how common is it for files to become corrupt when transferring from one hard drive to another? I ask this because I usually have trouble when transferring (usually large files) onto my flash drive. I know that actual hard drives are different but I just want to make sure. Also, is there a way I can confirm that everything transferred correctly? Most of my files are music so it would be a pain to check every single one to see if it works.

Thanks in advanced :)

---

### Post by nemilar on 2010-03-12
Are you doing the transfer under Linux or under Windows?

You should not have data integrity problems transferring data between drives.  If you consistently see this issue, perhaps you have a hardware problem (although admittedly, I don't at all trust the low-end USB sticks with my data).

If you are transferring under Linux, you could rsync twice (make sure you use -c); the second time you run it, nothing should be transfered.

---

### Post by teKro on 2010-03-12
I was just drag and dropping in Ubuntu. Would the terminal be better? If so how would I go about doing this because I'm still kind of new. This is my set up: I have two hard drives. My main hard drive has a partition named Files which has my document folder, music folder, etc. My backup drive is named Backup.

---

### Post by nemilar on 2010-03-12
You could do something like this:

Assuming:
source = /media/Files
destination = /media/Backup

```

mkdir /media/Backup/Files
rsync --progress -avc /media/Files /media/Backup/Files
rsync --progress -avc /media/Files /media/Backup/Files

```

By repeating the rsync command twice, you are forcing it to calculate the checksum of the file again.  If there is corruption, this should detect it.  If there is no corruption, the second "rsync" command should not transfer any data (unless data has changed in /media/Files).

---

### Post by teKro on 2010-03-12
I tested it on the folder that has my books for quick testing. I did put the command the second time right after the first and it gave me this: sent 3791 bytes  received 15 bytes  362.48 bytes/sec

Tried it a third time and it gave me pretty much something similar: sent 3791 bytes  received 15 bytes  507.47 bytes/sec

It didn't send anything substantial but you said it wouldn't send any data. Is that fine?

Just for clarification, the rsync command tells the first directory to copy itself onto the second directory only if there is a difference in the two directories correct? Also, what does -avc do?

Thanks for your help so far by the way.

---

### Post by nemilar on 2010-03-12
Do the two devices have the same filesystem?

Can you try doing an md5sum of the source and destination files:

```
md5sum /media/Files/some_file
md5sum /media/Backup/the_same_file
```

the md5sum had better be identical...

---

### Post by teKro on 2010-03-12
I couldn't get the md5sum command to work. It kept saying the files did not exist. I tried rsync again and continued to say that x amount of bytes were sent. I looked around the web some more and found about grsync. It tried it and it said that x amount of bytes were sent the second time as well. Then I went on youtube and looked up a tutorial on rsync and saw that they had the same results. I'm guessing the x amount of bytes aren't a big deal then. First because it's only a few thousand and second because it didn't not actually copy any files since there were none listed.

---

