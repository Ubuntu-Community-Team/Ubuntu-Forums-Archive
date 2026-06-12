---
title: "Recursive Hard Links"
date: 2011-09-12
forum: General Help
---

### Post by Fishbowler on 2011-09-12
I've got a backup of the mother-in-law's hard drive and it's a chuffing mess.
I'd like to run some fun scripts to put the files in some semblance of order, but before I do, I'd like to take a backup.
Since I'm not touching file content, hard links seem like a good way to save space.

I've duplicated the folder holding the backup using 
```
cp -rl
```

Is that enough?

---

### Post by An Sanct on 2011-09-12
If you wish to make a 100% backup without touching the files, you can use dd ;)

okay, joke aside ... dd is not nicknamed DiskDestroyer for nothing ... try using some ghosting utility and make a "perfect" image, then manipulate the disk (you can also destroy it and then later revert it ... without your mother in law noticing)

---

### Post by Fishbowler on 2011-09-12
Thanks for the reply!

I don't need a perfect byte-for-byte copy (and even if I did, I don't think I've got the disk space!)

I'm looking for a way to test some scripty methods of organising her digital chaos into some sensible folder structure - the files themselves should be untouched, and all I really need is the folder structure and filenames to be intact. 

Assuming I don't actually edit any of the physical files, have I now got what I wanted? Do I have a separate structure that I can rename, remove, shuffle, amalgamate and de-dupe from? Were hard links a valid and sensible choice? Is there anything I could do in this setup to alter the originals? I don't care about file timestamps, but I assume renaming is fair game?

---

### Post by haqking on 2011-09-12
> **Fishbowler said:**
> Thanks for the reply!

I don't need a perfect byte-for-byte copy (and even if I did, I don't think I've got the disk space!)

I'm looking for a way to test some scripty methods of organising her digital chaos into some sensible folder structure - the files themselves should be untouched, and all I really need is the folder structure and filenames to be intact. 

Assuming I don't actually edit any of the physical files, have I now got what I wanted? Do I have a separate structure that I can rename, remove, shuffle, amalgamate and de-dupe from? Were hard links a valid and sensible choice? Is there anything I could do in this setup to alter the originals? I don't care about file timestamps, but I assume renaming is fair game?


dd or rsync

or [clonezilla]("http://ubuntuforums.org/www.clonezilla.org") to take an image of it.

---

### Post by Fishbowler on 2011-09-13
Thanks for your reply, but I'm not sure I'm fully grasping your answer.

What are the limitations in what I've achieved through cp?
If I don't intend to directly edit the files, do I really need to duplicate all the files themselves?

---

### Post by SecretCode on 2011-09-13
A "backup" using hard links is not what most people think of as a backup, because it doesn't give any protection against file contents changing - but you say you aren't worried about that. Also it has to be on the same filesystem so it gives no protection against hardware failures or filesystem corruption.

What it will do is preserve a link to each inode in a copy of the original directory structure.

Is that all you want?

---

### Post by Fishbowler on 2011-09-13
I need to completely fark about with the directory structure and the file names whilst being able to preserve or revert to the original. I'd also like to be able to delete suspected duplicates without affecting the original backup either. From my reading, this all sounds easily achievable with hard links.

My question is more: Have I done it right?

---

### Post by SecretCode on 2011-09-13
What was the complete copy command you used?

You'll preserve the original and you would be able to revert part or all of the structure, as long as the copy is in another directory and you don't touch it again.

If you delete duplicates you won't actually free up any space because the backup hard links will still be there ... I presume eventually you'll delete the backup, as long as you are happy with your restructuring?

---

### Post by aeiah on 2011-09-13
hard links will only work on supported filesystems, and hard linking only works within the same filesystem. its probably best to shove all the data onto an ext partition. id do this:

```

rsync -aP /path/to/source/ /path/to/backup/

```
that'll copy everything over to /path/to/backup/

then id just do
```

cp -al /path/to/target/ /path/to/playarea/

```

and work on renaming files in the /playarea/. since its hard linked, it'll preserve the directory structure of /backup/ even though you make changes to /playarea/. your ideas about hard links are correct, they wont take up any more space, and when you've got a neat and tidy /playarea/ you can remove /backup/ without risk of injury.

---

### Post by Fishbowler on 2011-09-13
> **SecretCode said:**
> What was the complete copy command you used?

cd /media/DATA0/Backups
cp -rl Maxtor Maxtor2

Not the best descriptive name in the world...
DATA0 is an ext3 drive. Maxtor is a folder I created, into which then copied the contents of the mum-in-law's NTFS formatted external drive using Nautilus.

> **aeiah said:**
> then id just do```
cp -al /path/to/target/ /path/to/playarea/
```

By my reading of the man pages, since I've copied from an NTFS drive, there's no difference between -al and -rl, right?

---

### Post by aeiah on 2011-09-13
> **Fishbowler said:**
> cd /media/DATA0/Backups
cp -rl Maxtor Maxtor2

Not the best descriptive name in the world...
DATA0 is an ext3 drive. Maxtor is a folder I created, into which then copied the contents of the mum-in-law's NTFS formatted external drive using Nautilus.



By my reading of the man pages, since I've copied from an NTFS drive, there's no difference between -al and -rl, right?

more or less, yea. 'a' is for archive, so its usually best for this sort of thing. just do cp --help to see what '-a' is short for.


but yes, what you did seems fine. its what id have done. you should be able to move things around in Maxtor2 and/or delete things without it affecting Maxtor1. likewise, once you're happy with Maxtor2 you can remove Maxtor1 without losing any data (given that the data still exists as a link in Maxtor2 of course)

---

