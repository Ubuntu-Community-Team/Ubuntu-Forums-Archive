---
title: "Help copying/verifying files (multi TB)"
date: 2010-05-30
forum: General Help
---

### Post by IMSargon on 2010-05-30
Let's say you want to copy some files from one drive (ext3 over USB) to another (ext4 in local box). You have a few terabytes over a couple million files.

You could just use Nautilus, which is what I did. It seemed to have completed normally (after a few days).

I wanted to verify that everything copied accurately, but I'm not sure the best way to do this. If I used md5sum, the verification would take all week, so that won't do. I used "du -bs *" and compared the sizes of the folders at the root of the drives. Most of the folder sizes were off somewhat - less than 1MB in any case. For each folder whose size was different, the difference was a multiple of 4096 bytes. This makes me suspect that the information du is giving me isn't precisely the information I assume it's giving me.

Baobab gave me different sizes from what du gave me, and it also gave significantly different sizes between my source and destination drives.

I wanted to do a "diff -r source destination", but I don't even have a guess as to how long that would take so I gave up after a couple hours. It wouldn't tell me everything I want to know, anyway (if files are missing vs if files did not copy correctly).

So the help I need is:
1.) Is there a quick way to reassure me that everything copied correctly?
2.) Is there a better way to do such marathon copies? (faster and more reliable?)

---

### Post by dearingj on 2010-05-30
> **IMSargon said:**
> So the help I need is:
1.) Is there a quick way to reassure me that everything copied correctly?
2.) Is there a better way to do such marathon copies? (faster and more reliable?)

You might try adding the "--speed-large-files" option when you use diff. Unfortunately I don't see any way to get a time estimate with diff, but this might speed it up a bit.

As for question number 2, the first utility that comes to my mind is rsync. It can work either locally or over a network and includes automatic hash checking. Just make sure you read the man page before using it to understand the effect of trailing slashes on folder names.

Wish I could help more :)

---

### Post by geirha on 2010-05-30
If you want to do a proper verification, you'd checksum all files and compare. That will of course take a lot of time since it needs to read every byte of every file. 
```

cd /first/drive && find . -type f -exec md5sum {} + > /tmp/md5sums
cd /second/drive && md5sum -c /tmp/md5sums | tee /tmp/verification

```

If you're content with just checking file size (which should be quite fast), you could try something like:
```

cd /first/drive && find . -type f -printf "%s %p\n" > /tmp/first.txt
cd /second/drive && find . -type f -printf "%s %p\n" > /tmp/second.txt
diff -u /tmp/first.txt /tmp/second.txt

```

---

### Post by sdennie on 2010-05-30
In the future, you could use rsync to do this.  It calculates every files checksum as it does the copy.  For example:

```

rsync -avu /source/drive/ /dest/drive/

```

In fact, rsync might be useful for you even in this case.  This will check that all the files are there, the same size and that none of the files in source are newer:

```

rsync -avumn /source/drive/ /dest/drive/

```

And this will do the same thing except list files that have a different checksum (this will be slow):


```

rsync -avumcn /source/drive/ /dest/drive/

```

In the last 2 commands, the "n" option tells rsync to do a dry run so, no files will be copied over.  It just reports what it would copy if you remove the n.

---

### Post by IMSargon on 2010-05-30
> In the future, you could use rsync to do this. It calculates every files checksum as it does the copy. For example:

```
rsync -avu /source/drive/ /dest/drive/
```



Ah, this is what I should have been doing all along. rsync is one of those commands I've be procrastinating on learning.


> If you're content with just checking file size (which should be quite fast), you could try something like:

```
cd /first/drive && find . -type f -printf "%s %p\n" > /tmp/first.txt
cd /second/drive && find . -type f -printf "%s %p\n" > /tmp/second.txt
diff -u /tmp/first.txt /tmp/second.txt
```



I like the speed of this command, but the diff had a bit of trouble. I entered the command as you indicated, but I got a + and a - for over a million lines, even when the lines are clearly identical.
Then I did a sort on each of the output txt files and did a diff on that and only got 6 or 7 differences. I'll do on md5 on each of those files to see what's going on. Is there a way to tell diff to ignore line order? Is there a reason the find command was not consistent in its ordering of the files?

---

### Post by IMSargon on 2010-06-05
So in wanting to assure an accurate copy, I executed sdennie's command:

```
rsync -avumcn /source/drive/ /dest/drive/
```

I was presented with a list of tens of thousands of folders. What am I looking at? Am I to believe that Nautilus botched a significant percentage of the total transfer? I traversed into one of the folders listed and did an MD5 on each of the files in that folder between the source and the destination, and they all matched. 

Am I misinterpreting rsync's output or should I wipe my destination drive and try again with an rsync copy?

---

### Post by sdennie on 2010-06-05
> **IMSargon said:**
> So in wanting to assure an accurate copy, I executed sdennie's command:

```
rsync -avumcn /source/drive/ /dest/drive/
```

I was presented with a list of tens of thousands of folders. What am I looking at? Am I to believe that Nautilus botched a significant percentage of the total transfer? I traversed into one of the folders listed and did an MD5 on each of the files in that folder between the source and the destination, and they all matched. 

Am I misinterpreting rsync's output or should I wipe my destination drive and try again with an rsync copy?

Was it just folders or also files?  I thought I constructed the rsync so that it wouldn't report folders "just for fun" but, rsync is a tricky beast.  If it's just folders and files you know to be newer on the source side, then the test was successful.

Having said that, I work with 10's of thousands of files that add to many terabytes at work.  When I need to transfer them from place A to place B, the only tool I even consider is rsync.  I know you've already done your big copy via Nautilus and you can do some verification on the data but, if you are still worried about the destination files, just start over and use rsync from the beginning.  It will put your mind at ease.

---

### Post by IMSargon on 2010-06-05
rsync is indeed a tricky beast. I forgot the trailing slash for my source on my first go around, and was treated to a multi-million line output.

Perusing my current output, I only ever saw lines ending in "\". If everything executed as I intended, source and destination should be completely identical, as I have prevented any writes during or after my copy. 

I was able to replicate the folder-listing behavior in a small test. Any idea what it does that? Even in a test with a few dozen files, I find the output confusing. It lists all sub-folders? I get that it lists files that are on the source but on on the destination (or need to be updated?), but naturally those entries are mixed in with the folders. Is there anyway way to get an understandable summary like "16 files would need to be copied" or "20 files do not match" or something? 

When I did the same work on another similar system, I did switch to rsync. We can trust "rsync -avu", then? Would you stake your backups on it? A full verification of a copy done by the command would be redundant?

---

### Post by sdennie on 2010-06-05
> **IMSargon said:**
> 
Perusing my current output, I only ever saw lines ending in "\". 


I'm not really sure what you mean by this.  Do you mean ending in "/"?

> 
I was able to replicate the folder-listing behavior in a small test. Any idea what it does that? Even in a test with a few dozen files, I find the output confusing. It lists all sub-folders? I get that it lists files that are on the source but on on the destination (or need to be updated?), but naturally those entries are mixed in with the folders. Is there anyway way to get an understandable summary like "16 files would need to be copied" or "20 files do not match" or something? 


I don't know why you'd see that.  As you've already noticed, trailing slashes make a difference with rsync but, so do dots.  There is a difference between these two commands:

```

rsync -avu foo/ bar/

```

And

```

rsync -avu foo/. bar/

```

A dot "roots" the rsync source.  It's like saying, "Ignore the path until here".

> 
When I did the same work on another similar system, I did switch to rsync. We can trust "rsync -avu", then? Would you stake your backups on it? A full verification of a copy done by the command would be redundant?

Short of hardware failure, an "rsync -avu" is a mirror image because it does on the fly checksum verification on the destination.  A lot of backup systems actually use rsync as their underlying mechanism so, yes, I'd stake my backups on it.

---

### Post by IMSargon on 2010-06-05
Whoops! Of course I meant "/". Sorry for that confusion. I was just saying it appears that rsync only listed folders, without listing any files.

So let's say I mount a couple of drives:

/media/source
/media/dest

say I've copied files such that those two mountpoints should contain identical file trees. 

Are you saying that 
```
rsync -avu /media/source/ /media/dest/
```
is not the same as
```
rsync -avu /media/source/. /media/dest/
```

If I had omitted the "/" from the source, as I found earlier, rsync would look for a folder called "source" in "/media/dest/" and not find it, and then spit out every single file. With the period, I'm not sure what it would be doing differently, even after reading the man page a few times.

I guess I will redo the copy for consistancy's sake, but I would sure like to understand what is happening. I did notice one true difference between source and destination - file and folders on the source are owned by a user and the files and folders on the destination are owned by root. If this is truly the difference that caused the folders to be listed, however, why wouldn't the files be listed as well? Their ownership was also changed. Modified times, permissions, and md5s were all identical.

---

### Post by sdennie on 2010-06-05
> **IMSargon said:**
> 
If I had omitted the "/" from the source, as I found earlier, rsync would look for a folder called "source" in "/media/dest/" and not find it, and then spit out every single file. With the period, I'm not sure what it would be doing differently, even after reading the man page a few times.


I just threw the dot out there because it does make a difference in some cases depending on the arguments you send to rsync.  As I said earlier, rsync is a tricky beast and I'd never fault someone (including myself) for not knowing the intricacies of it but, it's a powerful tool and I'm a fan of spreading knowledge.

> 
I guess I will redo the copy for consistancy's sake, but I would sure like to understand what is happening. I did notice one true difference between source and destination - file and folders on the source are owned by a user and the files and folders on the destination are owned by root. If this is truly the difference that caused the folders to be listed, however, why wouldn't the files be listed as well? Their ownership was also changed. Modified times, permissions, and md5s were all identical.

If all the md5 sums check out, you don't need to re-copy the data.  However, if I had copied terabytes of data via Nautilus and then discovered that there was a better way to do it, I *peronsally* would be inclined to rebuild the data with rsync.  When it comes to that much data, piece of mind is a real concern.  If you know that you've started with rsync and continue to use rsync to update things, you will sleep better at night.

---

