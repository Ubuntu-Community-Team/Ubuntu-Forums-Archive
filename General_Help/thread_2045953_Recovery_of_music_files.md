---
title: "Recovery of music files?"
date: 2012-08-22
forum: General Help
---

### Post by jadranka on 2012-08-22
Hello,

I've been searching the whole morning for some answer, read so many posts and forums and nothing helped. 
I accidentally erased all of my music from my HD and I did it in Rythmbox. What I wanted to do is to remove music from Rythmbox, and not being aware of, "moved all my music to rubbish bin". No doublecheck, no "Are you sure?" questions (seriously Linux?). By the second I realised it, it was gone. Now all that is left in my Music folder are empty folders. The good thing is that all subfolders are still there as well (also empty), but hey, at least I know what I had. 
Anyway, as I'm sure that the app. 100GB of music is still somewhere there, and couldn't manage myself how to recover it, can anyone help me on this? I'm currently using Ubuntu 12.04.

Thanks, Jay

---

### Post by greenpeace on 2012-08-22
I'm sure you've checked already, but has it been moved to the trash folder?

check in here: ```
 ~/.local/share/Trash/files
```

---

### Post by TheFu on 2012-08-22
Just restore from your last backup.  

After all, this is exactly what backups are for.

If you don't have a backup, you really want to pull this HDD out and never mount it read-write again if you want any chance of getting the data back.  If I were you, I'd find another HDD and mirror the source (be certain it is read-only) quickly using **dd** or **ddrescue** at the partition level (for example /dev/sda6).  Then I'd look for data recovery tools that work at the file system and device levels - some file systems aren't supported by those tools, so you might be screwed.

[http://www.linuxlinks.com/article/20100226122928107/DataRecovery.html](http://www.linuxlinks.com/article/20100226122928107/DataRecovery.html) has some tools listed. **PhotoRec** seems very popular.  Again, if you are running on the same system and install anything, you risk over writing the data you want to recover.  I've used **ddrescue** and** dd_rescue** extensively to recover corrupt files, but not deleted files - they won't help except to mirror the partition at the bit level. 

If you've been using the HDD partition (i.e. even had it booted, every log file written, every temp file written has been over writing your data since that instance.

If you get much of the data back, I think you'll agree that having a good backup methodology would be much easier to restore.

---- Update
I happen to have a HDD that was reformatted this morning from NTFS to EXT4.  Grabbed PhotoRec (part of the GPLv2 TestDisk suite) and ran it against the 1TB formatted disk.  After about an hour, I stopped it - it wanted 10 hrs for the run.  It only writes files to a different partition, never to the same one.    The recovered filenames have nothing to do with the originals. Some examples:
```
f0074040.mpg  f4762992.mpg  f4824664.mpg  f4875536.mpg  f4888960.mpg  report.xml
f4731688.mpg  f4794432.mpg  f4852496.mpg  f4883192.mpg  f5106560.mpg
```  That partition was where TV recordings for later viewing were stored.  PhotoRec has no clue about directory structure from what I could see.

Getting back anything for large, multi-sector files is impressive. It didn't pull back any MKV files, however. MP3 is a supported format.

Anyway, I can't imagine trying to restore the file names for 100G of files.

---

### Post by jadranka on 2012-08-25
As I couldn't do it myself (had even problem with installing and running **ddrescue**) I gave my laptop to a friend - it's all back. Honestly, I don't know what she did and at this point it doesn't even matter to me.

As of back-ups, I know what they are for, but I didn't delete a single file accidentally in last 13 years. I did it once with system files and from there on I always double checked what I deleted. 
What pisses me off is that in Ubuntu I have to give my password for everything, every new program, every update etc, but when it comes to deleting my whole music files from Rythmbox (!!), there is no precaution.

Anyway, thanks for your help.

---

### Post by TheFu on 2012-08-25
**I'm happy that everything was recovered.**

> **jadranka said:**
> As of back-ups, I know what they are for, but I didn't delete a single file accidentally in last 13 years. I did it once with system files and from there on I always double checked what I deleted. 
Backups are not just for accidentally deleted files. They help recover from:
* Failed hardware
* Failed software
* Security attacks

> **jadranka said:**
> 
What pisses me off is that in Ubuntu I have to give my password for everything, every new program, every update etc, but when it comes to deleting my whole music files from Rythmbox (!!), there is no precaution.

Anyway, thanks for your help.

You can change whether you are asked for a password or not or how long the period is that the password is remembered/cached, if you like.  **man sudoers **will explain everything.

Being mad at Rythmbox is fine, but UNIX-like systems have a do-what-I-tell-you, don't ask questions philosophy. You didn't understand that before. Now you do.

If you don't want files deleted, then setup the file permissions so that your userid cannot delete them.  I'll ask you, when you selected all the files and said delete, can you imagine someone else being mad if it didn't remove them all?

I'm happy that everything was recovered.

---

