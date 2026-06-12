---
title: "Copy one file type from my music folder?"
date: 2009-08-11
forum: General Help
---

### Post by S3loth on 2009-08-11
I converted all of my FLAC collection to AAC to play on my Nintendo DSi. The problem is that I forgot to change the folder so now all my FLAC and AAC are mixed together. They're not just in my Music folder, but it is Music>Artist>Album>song.flac and song.m4p. Does anybody know a fast way that I can get all the AACs out and still have the folder system intact? Thanks!

---

### Post by michy99 on 2009-08-11
Do you want to delete the AAC's or move them to another folder?

---

### Post by S3loth on 2009-08-11
I want to have the AACs all organized into their album folders (since the DSi doesn't reconize metadata). I have managed to get all the AACs into one folder. Is there anything I could use that would put the files into folders based on their metadata?

---

### Post by DaithiF on 2009-08-11
Hi,
so you want to have parallel directory structures I think, e.g.
Music-> Artist ->Album, etc  for just your flacs, 
and
Music2->Artist->Album, etc for just your mp4's ?

you can do this with rsync.
open a terminal
create the destination directory
```
mkdir Music2
```
and then run this command:
```
rsync -a --exclude='*.flac' Music Music2
```

this will copy everything except your .flac files into the destination directory, preserving directory structure.

Once you're happy this has worked, you can delete the original .mp4 files in the Music directory by using the find command:
```
find Music -name '*.mp4' -exec rm -f {} \;

```
I would run this first without the -exec rm -f {} \; piece, to make sure it is picking the files you expect to delete.

cheers
d

---

### Post by S3loth on 2009-08-11
Thanks so much! That works perfectly! Man I love the Linux commuinty!

---

