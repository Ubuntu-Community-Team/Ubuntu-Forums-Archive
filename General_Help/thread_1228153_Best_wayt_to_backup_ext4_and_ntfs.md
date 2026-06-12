---
title: "Best wayt to backup ext4 and ntfs?"
date: 2009-07-31
forum: General Help
---

### Post by SoftwareExplorer on 2009-07-31
What is the best way to backup NTFS and ext4? I'm used to using partimage, but it crashes with NTFS and doesn't support ext4 yet.

---

### Post by CrusaderAD on 2009-07-31
Use keep. You can backup entire networks. Let me know if you need pointers setting it up.

```
sudo apt-get install keep
```

---

### Post by drs305 on 2009-07-31
I use fsarchiver, a command line utility that works a lot like partimage without the visuals. I migrated to it after switching to ext4 and finding out partimage didn't support it yet. I would hardly call it "the best" but I built a couple of scripts and am happy with it.
[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

---

### Post by CrusaderAD on 2009-08-04
I have instructions setup in this thread if you're interested:

[http://ubuntuforums.org/showthread.php?t=902366]("http://ubuntuforums.org/showthread.php?t=902366")

---

### Post by SoftwareExplorer on 2009-08-04
> **raptormanad said:**
> I have instructions setup in this thread if you're interested:

[http://ubuntuforums.org/showthread.php?t=902366]("http://ubuntuforums.org/showthread.php?t=902366")

Thanks, I've been a little busy with 4-H, so that's why i'm so slow to respond. I'm curious, FS archiver backs up at the filesystem level, partimage at partition level except for unused blocks, what does keep backup at?

---

### Post by SoftwareExplorer on 2009-08-04
I just followed the link, it doesn't seem to talk about keep much. Or were you wanting to point out something entirely different?

---

### Post by SoftwareExplorer on 2009-08-09
OK, I'm trying fsarchiver on the system rescue CD. Also, partimage on that CD seems to work with NTFS. I want to test my backups, and I know there is some way to mount a file as a partition, would that work to test them? How hard is it to set up a loop file?

---

### Post by drs305 on 2009-08-09
Both fsarchiver and partimage normally compress the backups. The backup file is not an iso like the LiveCD in which you can view the contents. I don't think you can do what you are proposing.

The way to test it would be to restore the backup to an empty mount point and then just inspect the contents. I've used both and they were very reliable.

---

### Post by SoftwareExplorer on 2009-08-09
I think that since partimage is on the partition level, it wouldn't work to do that. What I'm proposing is to make an empty loop file and then use partimage or fsarchive to do a dry-run restore to that file.

---

### Post by drs305 on 2009-08-09
I didn't chose the right words. I didn't mean mount point, I meant an empty partition - a partition not currently in use. You can restore partimage to a partition of equal or greater size than the original. With fsarchiver, I believe the latest versions even allow you to restore them to a smaller partition as long as the data will fit.

I'll follow the post and see if you can do what you are proposing. :-)

---

### Post by SoftwareExplorer on 2009-08-09
> **drs305 said:**
> I didn't chose the right words. I didn't mean mount point, I meant an empty partition - a partition not currently in use. You can restore partimage to a partition of equal or greater size than the original. With fsarchiver, I believe the latest versions even allow you to restore them to a smaller partition as long as the data will fit.

I'll follow the post and see if you can do what you are proposing. :-)
Basically, could and empty file use loop mounting to act like an empty disk or an empty partition? I would prefer not to have to make a real partition, as that means I would have to Shuffle partitions. One thought:I could use a Virtual Machine, but that might be trying to use a complicated tool when Linux might have a simpler one? I've never used loop mounting, so I don't really understand what its benefits and limitations are.

---

### Post by CrusaderAD on 2009-08-09
> **SoftwareExplorer said:**
> Thanks, I've been a little busy with 4-H, so that's why i'm so slow to respond. I'm curious, FS archiver backs up at the filesystem level, partimage at partition level except for unused blocks, what does keep backup at?

I'm not exactly sure, but I know it will only grab files that have been modified. I've been using it for almost 2 years and it has saved my skin more than once.

---

### Post by SoftwareExplorer on 2009-08-10
Well I did some reading on keep's home page. It sounds like it backs up files that you specify at a specific interval. What I would prefer to use would be a program that backs up the whole partition and when you restore it, it will boot like nothing happend. Partimage does this, but ubuntu's version doesn't do ntfs or ext4. systemrescuecd's version of partimage seems to work with ntfs.  So thanks for your help raptormanad, but I think keep isn't quite the program for me.

---

### Post by CrusaderAD on 2009-08-10
Check this out:

[http://www.linuxquestions.org/questions/ubuntu-63/ghost-for-ubuntu-441797/](http://www.linuxquestions.org/questions/ubuntu-63/ghost-for-ubuntu-441797/)
[http://ubuntuforums.org/archive/index.php/t-63121.html](http://ubuntuforums.org/archive/index.php/t-63121.html)

Norton Ghost sounds like what you're looking for. I'm not sure how it would work with ubuntu.

---

### Post by RedSingularity on 2009-08-10
I have used Clonezilla for a while now.  Works great!

---

### Post by SoftwareExplorer on 2009-10-04
Well, I got it all sorted out. I'm using rsync for data files and dd with [this howto]("http://ubuntuforums.org/showthread.php?t=581680") to make images of OSes.

---

### Post by User Abuser on 2010-07-11
If anyone still struggling to find a solution to this, just use Clonezilla of freeware or any 2010 backup line from Paragon. They have support for ext4 now, load of feats and a gui (whoopee!):KS

---

### Post by SoftwareExplorer on 2010-07-11
Well, I should probably update this thread.
I currently use rsync for both data and OS partitions. As amazing as it is, I can back up Ubuntu on the filesystem level with rsync and then restore it and it works. Even better, if I need a file from my backup and I don't have a spare partition to restore to and don't want to mess with mounting stuff, I just have to go to the folder where I have the backup and copy the correct file. On top of that, rsync only transfers the differences if you are updating a backup, which makes it a lot faster. I usually use the -x (don't cross file system boundaries) -a (archive mode, save all permissions, links, etc) -v (be verbose) and -z (compress data sent across the network). In fact, I can back up a running system successfully when I use -x because it doesn't try to backup everything I have mounted, the /proc /tmp and other things. I'm actually really happy with rsync, now that I know that a filesystem level backup works.

---

### Post by User Abuser on 2010-07-21
Is rsync only for file backup?? It doesn't store your partions or loader, right?
Did you read about Mondo?? [http://articles.techrepublic.com.com/5100-10878_11-1055900.html](http://articles.techrepublic.com.com/5100-10878_11-1055900.html)
Also Acronis 2011 is in beta and ext4 is documented. I was unable to find any intel on what features will it have.
 All this info is making my head spin %( I wish to stumble upon a comprehensive, clear review of ext4 backup software.
Anyway, up till now I have found:
Clonezilla, Rsync, FSarchiver,Paragon HDM2010,Acronis TIH2011 beta and Mondo rescue.
As I presume essential features needed by home users are full file and disk\partion images with compression, incrementals,single-file backup and recovery and the ability to put your loader along with your image hassle free (like ATIH does for MBR). Prolly support for win7 is needed too. Any software meets this?? 
I'm not an specialist in this so don't be grumpy! =) Correct me if needed. I just think that it's about time we make a FAQ out of this cause a lot of people browsing in search of comprehensive info on backing up ext4.
So please post whatever you may find helpful from your user experience or google.

---

### Post by SoftwareExplorer on 2010-07-22
> **User Abuser said:**
> Is rsync only for file backup?? It doesn't store your partions or loader, right?
Yes, it only backs up files (and folders). It doesn't store the partitions or loader. (However, not having the loader isn't that bad when it is now auto generated. The partitions don't have to be the same size as what you are restoring from, as long as the new partition is big enough to hold all the files.) In a way, it can store an "image" of a partition by storing the partitions contents (but not the actual partition)

So, (to try to simplify what I just said) Rsync:Backs up on the file and folder level. You can retrieve single files easily. All of it's features work with ext4. It can back up a running copy of ubuntu. It only transfers the differences from the last time you backed up. On the negative side, it doesn't compress the backup. It doesn't make incremental backups by itself, but you can make a script that uses rsync and 'cp -al' to make an incremental system. It doesn't store the loader or partition layout. Probably wouldn't backup windows in a bootable way.
> **User Abuser said:**
> Did you read about Mondo?? [http://articles.techrepublic.com.com/5100-10878_11-1055900.html](http://articles.techrepublic.com.com/5100-10878_11-1055900.html)
Well, thanks to you, I just did. I'm not sure if it supports backing up to hard drives (which is what I needed), but I sounds like it might have a good number of features otherwise.

> **User Abuser said:**
> Also Acronis 2011 is in beta and ext4 is documented. I was unable to find any intel on what features will it have.
Acronis costs money, right? (I'm not sure. In my situation, I would probably try to find something free instead.)

> **User Abuser said:**
>  All this info is making my head spin %( I wish to stumble upon a comprehensive, clear review of ext4 backup software.
I tried to make my answer about rsync simple and clear this time, but of course, there's the risk that adding more information will just make you more confused. 
> **User Abuser said:**
> As I presume essential features needed by home users are full file and disk\partion images with compression, incrementals,single-file backup and recovery and the ability to put your loader along with your image hassle free (like ATIH does for MBR). Prolly support for win7 is needed too. Any software meets this?? 
Not sure. I kind of think that Ubuntu needs to take all the various backup programs out there and make a single program that has all the various features, has a GUI version (and a non-GUI on for servers)
> **User Abuser said:**
> I'm not an specialist in this so don't be grumpy! =) 
I'm not :) .
> **User Abuser said:**
> Correct me if needed. I just think that it's about time we make a FAQ out of this cause a lot of people browsing in search of comprehensive info on backing up ext4.
So please post whatever you may find helpful from your user experience or google.
Unfortunately, I feel like I'm not being much of a help to you. My problem is solved perfectly for me. Some of the questions you are asking I don't know the answer to, and I'm guessing that only a few other people are reading you questions in this thread because this thread is marked as solved. Maybe you would have more luck getting people who know more than me to help you if you started another thread and then had a link to this thread. I just feel like I'm not being much of a help.(Sorry about that)

---

### Post by User Abuser on 2010-07-22
Thanks! You're answer is great. I got things a little confusing not mentioning that my previous post mostly "goes out to all people out there" =)
 Um, how did you make those separate quotes? =D I couldn't manage to

---

### Post by drs305 on 2010-07-22
> **User Abuser said:**
> 
 Um, how did you make those separate quotes? =D I couldn't manage to

You can press the "QUOTE" button at the lower right of the post you are interested in. It will put the entire post within the "QUOTE" code tags. Pressing "QUOTE" on your post generates this result (between the ***):
***
[noparse]
> **User Abuser said:**
> Thanks! You're answer is great. I got things a little confusing not mentioning that my previous post mostly "goes out to all people out there" =)
 Um, how did you make those separate quotes? =D I couldn't manage to
[/noparse]

***
Notice it starts with [noparse]>  and ends with [/noparse]. 

Note there is a "multiquote" button which is unlabeled but directly to the right of the quote button.

You can also quote any section of any post by starting with the [noparse]> [/noparse] tag and ending with the [noparse][/noparse] tag. For mulitiple quotes, you can just cut and paste what you want and make sure to add the correct tags so there is one at the start and end of each section.

---

