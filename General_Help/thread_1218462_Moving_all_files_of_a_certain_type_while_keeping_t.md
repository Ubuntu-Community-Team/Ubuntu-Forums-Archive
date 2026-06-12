---
title: "Moving all files of a certain type while keeping the hierarchy of folders."
date: 2009-07-20
forum: General Help
---

### Post by boballen55 on 2009-07-20
Ok, so I'm sure there is a better forum to put this but I've always found help here.  There is probably a few simple commands that can solve this but I don't know them...  So here is the situation:

I have a lot of photo files that are intermixed with video files.  I've used a program to help organize the picture files.  In fact it has copied all picture files and made a by date organization of them in folders.  I like that, but the problem is that it ignores the video files.  So to save hours of time I want to run a simple program to extract or copy all the video files and have the folder hierarchy stay in place.  Then I can get rid of the duplicate photo files on my computer.

Thanks for your help!

---

### Post by quixote on 2009-07-21
I'm a rank amateur at this, so test my suggestion first on a small subset of your directory tree.

I'd suggest using rsync.  It will recreate directories on the fly, and limiting it to specific filetypes, it'll copy only those and leave the others. For more info than you probably want :D, use **man rsync**.

As a possible command line, maybe something like this.  Assuming your photo files are, say .jpg & .png and you want all the other files in those directories:```
rsync -avu --exclude "*.jpg" --exclude "*.png" /home/path/to/your/video-photo-file-directories/ /path/to/where/you/want/to/copy-to 
```

Or, let's say all your videos are .flv, and there are several different photo formats: ```
rsync -avu --include "*.flv" /home/path/to/your/video-photo-file-directories/ /path/to/where/you/want/to/copy-to 
```

Couple of notes: a means "archive" = preserve permissions, time stamps, etc.  v = verbose  i.e. it echoes what it's doing to the screen.  u means update, ie add new files to what's there, don't delete anything. The backslash at the end of the SOURCE dir and *none* at the end of the TARGET dir is important.  Otherwise it will create an extra layer of subdirectories.

You can also add -n to have it do just a simulation, although sometimes the simulation seems to work and then the real run doesn't.

You can add a --delete if you want files that have been removed in the source to also be removed on the target.

Hope this helps.

---

### Post by boballen55 on 2009-07-22
That sounds very promising, I'll have to play around with that tomorrow after I get some sleep.  Thanks, I'll type up how it goes later.

---

### Post by boballen55 on 2009-07-23
That works great!  Thanks!  The last detail I haven't figured out is an easy way to find the couple dozen folders out of a hundred that were copied to a new location but are now empty because they contain nothing.  I could manually do that without too much time of a time investment but maybe for future reference does anyone know a quick command line way to do that?  I bet there is some option in rsync that will get the job done some how (so many options).  Thanks.

---

### Post by niteshifter on 2009-07-23
Hi,

Finding empty directories:

```
find *path-to-start-from* -depth -type d -empty
```

Replace *path-to-start-from* as per your needs.

---

### Post by boballen55 on 2009-07-25
> **niteshifter said:**
> Hi,

Finding empty directories:

```
find *path-to-start-from* -depth -type d -empty
```

Replace *path-to-start-from* as per your needs.

That did help find exactly which ones are empty so I could have manually deleted slightly faster than before but it did not help with deleted them with one line of code.  I ended up using FSlint to find and delete empty directories.  It works quite well.

Thanks to both of you that helped.

---

### Post by quixote on 2009-07-26
Cheers.  Glad it worked!

FSLint is a great program and probably the safest way to remove empties.  You can also take the output of one command and send it to another, like so:  (test first, this is off the top of my head)```
find *path-to-start-from* -depth -type d -empty -exec rm {} \;
```

---

### Post by boballen55 on 2009-07-27
> **quixote said:**
> Cheers.  Glad it worked!

FSLint is a great program and probably the safest way to remove empties.  You can also take the output of one command and send it to another, like so:  (test first, this is off the top of my head)```
find *path-to-start-from* -depth -type d -empty -exec rm {} \;
```

Yea, I was hoping to do something like that but I couldn't figure it out.  I thought I needed to use rmdir to delete directories but looking at the rm manual I see it is possible to force a directory to delete with a "-r" or something like that.  I could have gotten by with rmdir if most of my directory names didn't have spaces.  "find" didn't report them with the necessary \ at the spaces for rmdir, so my attempt at copy and pasting the find results didn't work.  After the 15 min it took me to figure all that out I looked for a gui program instead and found fslint real fast.

---

