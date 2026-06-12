---
title: "Trying to clone unallocated space to an .img - any experience?"
date: 2012-04-08
forum: General Help
---

### Post by janisgeiger on 2012-04-08
Hey - I have a question.
I accidentily erased a partition of my hard drive and testdisk cannot recover the partition entry.
It is the very first 12 GB of the drive, outside of an extended partition (alone on itself), it is now shown as "unallocated space"

- now I read through this manual [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) , caming to the conclusion:
- I have to make an image of the space to examine it (as testdisk failed, parted also).

As this space has never had any "new" data written to it, doesn't this mean the the files are still in there and could be recovered "somehow" ?

How could I make an image of these 12GB, as though they can't be adressed from a directory tree?
I thought about making  an image of the whole drive, but let it stop after the last sector of the 12GB - but how to do that? Haven't found any options about it in gddrescue or dd_rescue... (the whole drive is 300 GB, by the way)

Here's the information about the unallocated space from GParted

First sector: 0
Last sector: 25703999
Total sectors: 25704000

I tried to put the space back into the following extended partition, hoping testdisk would see the partition again. (now shown first sector: 63, but in general the same as above.)

F.y.i:
The partition got deleted after I ran testdisk to restore another partition (sucessfully), but appearently I made a mistake, or testdisk made one, and "re-mapped" the partition to a size I had given it some time before (5GB), it then could not be mounted again, GParted showed an exlamation mark beside of it, I let it "check & fix the file system", returned in 5GB of empty space, I then deleted the partition... The original size of the partition was ~12GB.

Well, anyways, I will now try to run photorec again to see if it advances further than last time, now that I got the space back in the extended partition, if I'll find no further clues I might just create a new partition of the 12GB and "investigate" if there's a way to recover the data in a better way than from unallocated space... But, I assume this is all just trial & error ;) the data ist not 100 % life important to me...

But, I'm confused that acessing unallocated space is appearantly difficult? Haven't found much on the web... except mostly windows forensis software (which I tried, just gave me a parade of 100MB files with no file type...). Well, thanks anyways!

---

### Post by Basher101 on 2012-04-08
unallocated space usually indicates that the file system is messed up ===> meaning your data is beyond saving. 

Someone correct me if I am wrong on this one, I got some expirience with partitions, but recovery is one of the things where i have none.

---

### Post by oldfred on 2012-04-08
If testdisk will not show partition nor files in partition, did you try photorec? But if the tool you used did not find much photorec may not either.

I have used photorec and it recovered many files. It only gives file extension based on what it thinks data was on drive. Some text files were recovered many times as it found the older deleted versions. And some text files were just segments or combinations of deleted files. It is a long slow process and even longer sorting thru files to figure out what they were.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by janisgeiger on 2012-04-08
> **Basher101 said:**
> unallocated space usually indicates that the  file system is messed up ===> meaning your data is beyond saving. 
Someone correct me if I am wrong on this one, I got some expirience with  partitions, but recovery is one of the things where i have  none.

No, I think you're wrong... in the best scenario it just means the partition entry got deleted, not necessarily the data inside... - not really an expert what the correct terms are -
in my case, no new file data had been really written to it, so,
i was hoping to just extract this thing and examine it as a directory, but couldn't find any information about accessing unallocated space, nowhere.

read [this]("http://www.computer-forensics.net/what-is-the-different-between-unallocated-space-and-active-or-allocated-space?/") ;) ? [SIZE=1]just show me *those* [/SIZE]*specialized computer forensic*[SIZE=1]* tools*, man....[/SIZE]

if someone stumbles acroos this thread looking for a similiar thing, this was among the sites of interest I found [http://www.4n6k.com/2012/02/forensics-quickie-extracting.html](http://www.4n6k.com/2012/02/forensics-quickie-extracting.html)
about your comment here's a guy sucessfully recovering unallocated space [http://www.youtube.com/watch?v=EncqYP1ijFg](http://www.youtube.com/watch?v=EncqYP1ijFg)





> **oldfred said:**
> If testdisk will not show partition nor files in  partition, did you try photorec? [...] 
I have used photorec and it recovered many files. It only gives file  extension based on what it thinks data was on drive.

thanks about the information that photo-rec "guesses" the extension! Yes, I'v tried it, and actually I have saved 3.4 GB, but it ended with an error and didn't advance. The output files are very messed up as you said, but it's better than nothing and still, I've tried my best :) !

---

### Post by rmil on 2012-04-08
You deleted partition so many times. The chances are not on your side. 
It would be good if you remember what kind of partition it was ext3,ext4 or something else

Anyway the last hope can be recreation of the disk using command fdisk. You can create new partition by trying to guess the first and last sector using +12G option. 

Then try to mount disk and see if it is possible

---

### Post by oldfred on 2012-04-08
If it just was the partition entry testdisk finds it and lets you recreate it.

I think this works using the same data testdisk does.

Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

I think this is just a gui version of manually using parted above.
GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted

---

### Post by janisgeiger on 2012-04-08
> **rmil said:**
> You deleted partition so many times. The chances are not on your side. 
It would be good if you remember what kind of partition it was ext3,ext4 or something else

Anyway the last hope can be recreation of the disk using command fdisk. You can create new partition by trying to guess the first and last sector using +12G option. 

Then try to mount disk and see if it is possible

Ok, that's maybe more going for a direction I was maybe looking for. Didn't know about fdisk really
But you're right that I played with and deleted the partition too much. Well, what can you do if you have no real clue and try to optimize it for some ways or tutorials you've read about ? ;)
By the way, the partition was ext4
it was labelled "Working"
it had ardour project / audio files in it, I think photorec has no implementation yet for the recreation of .ardour files ;)

---

### Post by janisgeiger on 2012-04-08
> **oldfred said:**
> If it just was the partition entry testdisk finds it and lets you recreate it.

I think this works using the same data testdisk does.

Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

I think this is just a gui version of manually using parted above.
GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted

thanks a lot for your reply, the others too.
you know, testdisk didn't recover the partition entry or so in the correct way, it always showed me a partition entry for those 5GB, which turned out to be empty when I fixed them with GParted... Did it only one time, then deleted it and tried to search around. But I know it's crazy how much I played with the partition, especially now, haha.

Well, I will use FTK Imager now once more inside Windows and just try to make an image, load that image and look what I'll find. Then I'll try out that fdisk way, after that, I have my photorec recovered stuff at least.

Ah: parted did find the same thing as testdisk
that's why thought there was a way to access the data more directly, before trying to recreate that old partition.

ps: ubuntu 10.04, gparted doesn't show me that device option. wow! maybe that would've helped, I was already wondering why gparted didn't have that kind of an option.

---

### Post by janisgeiger on 2012-04-08
I decided the stuff is gone, I'll start from scratch... I have some backups, but not of the recent things.

It's not very dramatic, it was just sound experiments anyway, even though some good ones, the most recent backup is this file I uploaded on soundcloud 2 days ago :KS [http://soundcloud.com/mojapogi/zobra](http://soundcloud.com/mojapogi/zobra)
so,you see ;) more of experimentation, via ardour digitally archived.

anyways, thanks for the help! if I was more impatient, maybe I could've recovered more, or if I came here in the first place ;)

Cheers.

---

### Post by janisgeiger on 2012-04-08
PS:

While browsing through that photorec recovered stuff, I'm coming across stuff I have never ever seen!! It's hilarious. Some desktop and folder pictures of a guy appearantly called "mario", using some slavic language or something on his operating system, showing screenshots of some excerpts of his synaptic contents, his home folder...
did I buy this hard drive unknowingly in a used state? or maybe these are some help tutorial pictures of a previously installed gnome desktop I didn't come across before?

crazy,spooky,whooo.

---

