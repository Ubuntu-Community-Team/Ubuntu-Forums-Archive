---
title: "Checking backed up data for corruption?"
date: 2009-12-11
forum: General Help
---

### Post by blueshiftoverwatch on 2009-12-11
I have a lot of information stored on an external hard drive which I periodically back up onto my computer's hard drive.

When I say backup I mean I just delete all the current files and copy+paste the new ones. But this kind of worries me because of the possibility of some data being corrupted in the process.

What's a simple way to backup my data but also have it check to make sure none of the files have been corrupted while in the process transferring?

Creating a compressed archive of my external HD and then uncompressing it to check for errors sounds like it might work, but I want something that I can just hit a button to start backing it up and walk away without much effort on my part.

It seems like there should be a checkable box in the file transfer progress bar that says something like "compare original and copied versions bit for bit" or something.

---

### Post by StuartN on 2009-12-11
> **blueshiftoverwatch said:**
> What's a simple way to backup my data but also have it check to make sure none of the files have been corrupted while in the process transferring?

The hardware and OS will inform you of any error with an IO Error warning. I assume (and have never seen evidence to convince me otherwise) that the destination is a correct copy if I do not receive an error.

If you want to run a proper verification then you can

- run rsync with the -n (or --dry-run) flag to report any differences between source and destination

- use Meld for graphical directory comparison

- use Krusader's synchronise tool with compare by content

- run diff, which has no output when the files match

(and many more ways). My preference is rsync if I expect an absolute match, as with backup, and Krusader when I expect some differences, as with synchronising music or photo collections.

---

### Post by blueshiftoverwatch on 2009-12-12
> **StuartN said:**
> 
- run rsync with the -n (or --dry-run) flag to report any differences between source and destination
I get errors when trying to compare directories, even after adding quotations around files with spaces in the names it just says "skipping directory .".
> **StuartN said:**
> 
- use Meld for graphical directory comparison
Meld will only compare files, not directories. I have over 20,000 files and the only way I'd ever be able to compare them would be to make them zip archives and compare those files. But that's too much work. Also, everytime I go to compare two files (not directories) I get an error saying that my files "contain ascii nulls or perhaps it is a binary file".
> **StuartN said:**
> 
- use Krusader's synchronise tool with compare by content
I keep getting "could not parse output" errors. But I used Kdiff and it seemed to work, although it would not compare directories either.
> **StuartN said:**
> 
- run diff, which has no output when the files match

(and many more ways). My preference is rsync if I expect an absolute match, as with backup, and Krusader when I expect some differences, as with synchronising music or photo collections.
When comparing small directories it seems to work, when comparing large directories I just get a bunch of messages about common subdirectories.

---

### Post by StuartN on 2009-12-12
> **blueshiftoverwatch said:**
> I get errors ...

I get a detailed list of every different file, plus the type of change required, using this:
```
rsync --dry-run -avi source/ destination/
```

Meld has a compare directories function that will compare a large file hierarchy and present a tree showing where different files occur, like a graphical version of the rsync command. Krusader's synchronise presents the same list, but allows you to operate on the list contents to correct differences, or to save the synchronisation as a profile for reuse. Diff, as I said, gives no output when files match.

All these commands have good manual pages or online help.

---

### Post by blueshiftoverwatch on 2009-12-13
I just spent the last 7 hours using the GTK frontend for Meld to copy 190GB worth of data from my external hard drive to the backup partition of my computer. If this were done by just copying the files it would have taken much less time, so I'm assuming this is because it not only copied the data but verified it bit for bit. Although I haven't read any of the detailed manual pages for any of the apps you listed as this process used up 100% of my RAM, so doing anything else while that was running was pretty much out of the question.
> **StuartN said:**
> The hardware and OS will inform you of any error with an IO Error warning. I assume (and have never seen evidence to convince me otherwise) that the destination is a correct copy if I do not receive an error.
I have reason to believe that isn't the case. A few months ago I was copying my music collection from my external hard drive onto my PS3. After the transfer was complete I had instances where I would go to select an album and if there were 12 songs, the first song would be listed 4 times, erasing songs 2-4 in the process. After looking through the music that had been transferred that happened more than a few times.

---

