---
title: "Backing up 500GB to a smaller place?"
date: 2009-08-07
forum: General Help
---

### Post by Dark Aspect on 2009-08-07
Does anyone know of a way to backup 500GB to maybe around 300GB with some form of data compression? I have a 1TB hard drive that I have used half of it and a 320GB hard drive with nothing on it. I am wanting to backup my home folder and it has gotten rather large.

[IMG]http://img329.imageshack.us/img329/4011/homev.png[/IMG]

Also, if I do compress something that much, is it close to error proof when I decompress it?

---

### Post by kayvortex on 2009-08-07
The strongest one that I know of is 7-zip. I don't know whether it'll be able to shrink ~500Gb to ~300Gb though since I think it is somewhat dependent on the data it's being told to compress. It's in the repos as "p7zip-full".
Also, don't forget about max file sizes, though anything that's not vfat should be fine.

---

### Post by Dark Aspect on 2009-08-07
> **kayvortex said:**
> The strongest one that I know of is 7-zip. I don't know whether it'll be able to shrink ~500Gb to ~300Gb though since I think it is somewhat dependent on the data it's being told to compress. It's in the repos as "p7zip-full".
Also, don't forget about max file sizes, though anything that's not vfat should be fine.

Whats the maximum file size for ext3?

About 100Gb of the data is flac rips from my own audio collection and my parent's audio collection from the 70s and early 80s. Not sure how that will compress, probably another 80GB is virtual machines. Games I suppose I could delete and reinstall to trim on the over all file size.

---

### Post by kayvortex on 2009-08-07
Not sure about the ext3 file size, but it's not really a problem anyway since you can pipe to split, which will separate the data into fixed-size files.

Audio won't compress too well, if much at all, since they've already been compressed into their respective formats. This'll be true for any file: if it's already been compressed, it'll probably not compress much further regardless of the tools used.

Virtual machines probably will compress OK, but you might want to look into that in more detail (like will defraging the guest OS help?).

Games will probably compress OK too, I guess; but you might also want to look into compressing .iso files in more detail -- there could be better ways of doing it or something.

In any case, you could give the compressions a go for isolated files to check how good the compression is. 7-zip will not overwrite/delete the files it is compressing, so you don't have to worry about that.

---

### Post by init1 on 2009-08-07
> **Dark Aspect said:**
> Whats the maximum file size for ext3?

About 100Gb of the data is flac rips from my own audio collection and my parent's audio collection from the 70s and early 80s. Not sure how that will compress, probably another 80GB is virtual machines. Games I suppose I could delete and reinstall to trim on the over all file size.
Don't think you'll have any trouble with file sizes for ext3.
Compressed audio (such as Flac and MP3) won't compress much more. You should probably get descent compression ratios from your virtual machines though. You might be able to get down to 300GB, all depends on the file types of your other files. 
I took a 145MB MP3 at 256Kb/s and compressed it with 7zip. The compressed size was 139MB. That's only a 0.05% gain. Of course, I really have no idea how well Flac would compress with 7zip.

---

### Post by kayvortex on 2009-08-07
7z can be a little confusing, so you'll need to run something like this:
```
tar cf - *data_to_compress* | 7z a -t7z -m0=lzma -mx=9 -md=32m -mfb=64 -ms=on -si -v50g */save_to_dir/name_of_archive.tar.7z*
```

That will tar your files and then compress that tar file at "ultra settings". Note also the "-v50g" flag, which will tell 7z to create 50Gb files: it's probably not needed, though; but you can add it if you like.

To uncompress, the command will be, if you didn't use the "-v" flag,
```
7z x *your_archive.tar.7z* -so | tar xf - -C */extract/to/this/directory*
```
and,
```
7z x *your_archive.tar.7z.001* -so | tar xf - -C */extract/to/this/directory*
```
if you did.

Although, having said all this, I'm sure you can get pretty good deals on memory storage (especially if you're OK with hooking up internal hard-drives: a little research and it's not that difficult): you'll probably need it at some point anyway.

---

### Post by Dark Aspect on 2009-08-07
> **kayvortex said:**
> 7z can be a little confusing, so you'll need to run something like this:
```
tar cf - *data_to_compress* | 7z a -t7z -m0=lzma -mx=9 -md=32m -mfb=64 -ms=on -si -v50g */save_to_dir/name_of_archive.tar.7z*
```

That will tar your files and then compress that tar file at "ultra settings". Note also the "-v50g" flag, which will tell 7z to create 50Gb files: it's probably not needed, though; but you can add it if you like.

To uncompress, the command will be, if you didn't use the "-v" flag,
```
7z x *your_archive.tar.7z* -so | tar xf - -C */extract/to/this/directory*
```
and,
```
7z x *your_archive.tar.7z.001* -so | tar xf - -C */extract/to/this/directory*
```
if you did.


Thank you, thats helpful. I compressed a few GB for a test and it came out about 15% smaller. I'll try on a large scale over night on the 320GB and see if it runs out of space.

> **kayvortex said:**
> 
Although, having said all this, I'm sure you can get pretty good deals on memory storage (especially if you're OK with hooking up internal hard-drives: a little research and it's not that difficult): you'll probably need it at some point anyway.

Yeah I can hook up internal hard-drives, if fact my computer came with the 320GB internal hard drive but I hardly ever use it. Your probably right I need another memory upgrade soon but with any luck I can wait until I get money for a 2 or 3 TB file storage.

I have 250GB external hard drive but it only has 6 GB free, I am eating memory :)

---

### Post by asmoore82 on 2009-08-07
I would suggest either Clonezilla [http://clonezilla.org/](http://clonezilla.org/) to capture a sparse compressed image at the partition layer
-OR- rsync to selectively back up only the most important data to the 320 GB drive.

---

### Post by kayvortex on 2009-08-08
> I have 250GB external hard drive but it only has 6 GB free, I am eating memory

Yeah, I know that! 500Gb on my PC totally filled up, a 400Gb external HD almost filled up, and I *really* need to upgrade the 120Gb on my laptop. Quite frankly I blame the internet. Damn techno-sociological progress.

Still, you should be able to compress most of your files and move them over to the 320Gb HD, right? That's something at least.

Edit:
> I would suggest either Clonezilla [http://clonezilla.org/](http://clonezilla.org/) to capture a sparse compressed image at the partition layer
-OR- rsync to selectively back up only the most important data to the 320 GB drive.

Wouldn't a disk clone introduce more data to compress? Maybe not much more, I suppose; but still. Would it be more space-economical than just tarring the files and compressing them? As for rsync, wouldn't it just be overkill for copying data from one disk to another? Then again, having never used it, maybe it has benefits that I'm not aware of...

---

### Post by TenPlus1 on 2009-08-08
Flac's are the main culprit here it seems and for an audiophile the sound quality is essential...  Try converting one flac song to ogg using SoundConverter (ogg, veyr high quality @ 256kbps or 512kbps) and see how that sounds in comparison, but I'll bet you can shrink your audio files down so they fit on the 300gb limit doing this and they will still sound amazing :P

---

### Post by jahvascriptmaniac on 2011-01-29
I know this thread is old, but I think this info might be useful to other people that land here after a search :

flac doesn't compress data very well, and xz (lzma) does a much better job, so one might want to extract all flac files to wav, and compress that with xz (this could be done via a script of course).

The only problem is that the flac metadata (artist, genre, …) is lost this way, so one might want to bundle a dump of the metadata with each wav and compress them with tar + xz.

---

