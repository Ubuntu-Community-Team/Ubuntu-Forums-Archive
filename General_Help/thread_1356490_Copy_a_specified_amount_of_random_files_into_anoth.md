---
title: "Copy a specified amount of random files into another directory"
date: 2009-12-16
forum: General Help
---

### Post by infinitejones on 2009-12-16
I have a NAS with a few hundred gigabytes of movie and music files, and I have a laptop with about 40GB of empty hard-drive.

I'm going away for a couple of weeks, taking my laptop with me, and I'd like to fill the 40GB with some movies to watch and music to listen to.

Is there a simple way to tell Ubuntu to randomly chose (let's say) 20GB of MP3s from the directory where all my MP3s are? I guess I should say the directory full of subdirectories where all my MP3s are.

It doesn't have to be full albums - in fact I kind of like the idea of having a completely random mix of songs, albums, artists etc. Just 20GB of random files.

Then obviously I'd point Ubuntu at the directory on my NAS full of movies and tell it to copy across 20GB of movie files selected at random too.

I'm not bothered if it's a command line, a script, a GUI application... just point me in the right direction, I'm sure I'll work it out.

Couple of things - unlikely to have useful internet access where I'm going, so a solution that involves streaming stuff from the NAS won't work.

Also, I know it's unadvisable to completely 100% fill up the space, and I know that 20GB of movie files might not be an exact number of files. The numbers are just examples... ;)

---

### Post by infinitejones on 2009-12-18
Bump!

---

### Post by kaibob on 2009-12-19
I do not have any experience with an NAS or have any idea how they work. Also, you are going to transfer large amounts of data, and I do not have anything similar that I can use for testing purposes. So, my suggestion may be of little direct help, but I wanted to give it a try for learning purposes. 

The following shell script will recursively copy randomized files from a source directory to a target directory until the specified maximum is reached. I used kilobytes for testing purposes; you would want to use something larger. 

```
#!/bin/bash

total=0

maximum=200

find /source/directory -type f | sort -R | while read file ; do 
   size=$(stat -c%s "$file")
   size=$((size/1024))
   total=$((total + size))
   [ "$total" -gt $maximum ] && exit 0
   cp "$file" /target/directory
done
```

I tested this shell script with a limited number of relatively small files on my hard drive, and it did seem to work.

---

### Post by infinitejones on 2009-12-19
This looks fantastic - thanks very much.

For the record, the NAS is just mounted over NFS so the source directory can just be treated as any other directory would be - in my case it's /mnt/NAS/music.

I wanted to treat this as a learning process too (I'm a total beginner with scripting) so can I check a couple of things:

[LIST]
[*]'total' keeps track of the amount of data transferred so far
[*]'maximum' is where you specify how much data you want to transfer altogether - in this case, 200kb. So if I wanted to transfer 20gb, I'd change that number to 20000000.
[*]The actual command that randomises the chosen files is sort -R
[/LIST]

Then it just loops through, finding the size of each file chosen using stat -c%s, adds that to the total and compares it to the maximum to know when to stop.

Is that all correct? Anyway, I'll give it a go now and report back any weirdness caused by larger volumes of data or files.

Thanks!

---

### Post by kaibob on 2009-12-19
> **infinitejones said:**
> ...I wanted to treat this as a learning process too (I'm a total beginner with scripting) so can I check a couple of things:

[LIST]
[*]'total' keeps track of the amount of data transferred so far
[*]'maximum' is where you specify how much data you want to transfer altogether - in this case, 200kb. So if I wanted to transfer 20gb, I'd change that number to 20000000.
[*]The actual command that randomises the chosen files is sort -R
[/LIST]

Then it just loops through, finding the size of each file chosen using stat -c%s, adds that to the total and compares it to the maximum to know when to stop.

Is that all correct?

That is all correct including the figure to use to transfer 20 gb. I just ran a test transferring 20 mb of files from an external hard drive, and everything worked OK. So, I think the shell script is sound in principle. As noted, the large quantity of data and perhaps the devices involved is the concern.

---

### Post by infinitejones on 2009-12-19
OK, this seems to be working just fine - I've started off with transferring 1gb so that I don't have to wait too long to make sure it stops, but I'm assuming that if it works for 1gb it'll work for higher numbers.

I made one small adjustment to the 'find' line - I added in the argument --mindepth 1 to make find work recursively, because the directory structure is more or less ./Music/Artist name/Album name. So now it's:

```
find /source/dir -mindepth 1 -type f | sort -R | while read file ; do
```
Actually while I've been typing, it seems to have finished - Nautilus is reporting only 973.2mb of files in the folder but that's not a big deal. At least the script did what it was supposed to and then exited. Now let's crank up the data volume!

Thanks again for your help.

---

