---
title: "Is it possible to free up the ext3 journal space?"
date: 2010-12-17
forum: General Help
---

### Post by tanoloco on 2010-12-17
Hello,

I'm still quite new on linux .. so please accept my question, even if I'm asking something stupid :)
The fact is that I created some months ago a partition of 50 Gb to store my data and I used an ext3 
filesystem with journal .. and the journal was about 1 Gb I think
Now after a few months of usage I moved all my data to a new device and I noticed that when the
partition was completly emptied, in fact there was still about 10 Gb occupied.
All  data was moved away, so I think this might be the journal.

Now a few questions:
1) Is it normal for a journal to occupy 1/5 of a device? 
2) Is there a command or another way to free up the space occupied by the journal?
3) Is there a better option in order of filesystem? Maybe it's better to use another one?
I usually use ext3 for the system partition and for data storage partition,
then I have a partition into where I store clonezilla images for backup purposes
and I decided to use reiserfs for it in order to have more space available,
even because it's always unmounted and I access onto it only for backup activities
once or twice a month.
Which are your recomendation?

Thank you for any reply
Cheers

---

### Post by NightwishFan on 2010-12-17
I believe that the filesystem has a max reserved space of 5%, though I could be wrong. You might have hidden files on there. Though someone else can correct me if I am wrong.

As for ext3 its great, very stable. If you want something newer try ext4.

---

### Post by tanoloco on 2010-12-17
thank you very much!
I had some hidden folders I forgot! ... I feel stupid for not having thought about that by myself!
I moved this staff and the partition it's now occupied by 1 Gb again on 50 Gb available .. which
is not 5% but that's more or less what I remember when I formatted the partition.

Maybe I made some mistake, but that's the proportion.

Thank you for your suggestion, too: I think I'll stay on ext3, even if ext4 seems to be the default file system for karmic and beyond, but I read somewhere ext4 crashed somehow and ext3 is still more recommendable.

Finally I never had a problem with it: only now I thought 1/5 of a device for journal is too much but I was wrong :)

Thanks again!

---

### Post by NightwishFan on 2010-12-17
Sure no problem. Personally I think ext4 is safe, but ext3 is certainly much more well tested. ;)

---

### Post by cgroza on 2010-12-18
If tou don't want a journal you can disable or use ext2.

---

### Post by tanoloco on 2010-12-22
> **cgroza said:**
> If tou don't want a journal you can disable or use ext2.

Hi cgroza!

I don't know if this only a personal impression, but I noticed that moving or copying files between different types of file systems is slower than between the same type, especially if one of these is ntfs!

My choice to use reiserfs is in fact due to the fact I don't want to waste space for journal to store data I only use from time to time, but I always have the doubt that maybe I loose time moving or copying or synchronizing .. so maybe it's better to use the same type of file system (ext3) disabling journal?

And how could I do that?

And then, is there any evidence in loosing time moving data between two different type of fs, or is it exactly the same?

Thank you

---

