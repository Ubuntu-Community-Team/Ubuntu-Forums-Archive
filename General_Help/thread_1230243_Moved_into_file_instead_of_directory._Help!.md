---
title: "Moved into file instead of directory. Help!"
date: 2009-08-03
forum: General Help
---

### Post by Morat on 2009-08-03
I have just done the following command:

find ~/recordings -name \*.mp3 -exec mv '{}' ~/player \;

Unfortunately, I had previously accidentally deleted the ~/player directory, so the move chucked all the files it found into one file. I now have a single 1gb file called player that contains about 30 concatonated MP3s. Is there a way to get these files back out?

:confused:

--- Morat.

---

### Post by mixmaster on 2009-08-03
I'm very surprised you have a concatinated file.  The find command should have executed a series of 1-file mv commands, so I would expect ~/player to contain the last mp3 copied.  Try renaming player to player.mp3 and see if you can play it.

AFAIK the mv command plays with pointers in the inodes for a move within a single file system, so the actual mp3 data should still be on the disk provided you haven't written anything so I suppose it is possible that one of the various ext3 undelete/recovery programs might be able to find it, but I don't have enough experience of these to recommend one.

---

### Post by t0p on 2009-08-03
If you want to try mixmaster's advice about recovering the mp3 files from your hard disk, there are a number of data recovery apps available through synaptic/apt-get.  Do a synaptic search for **data recovery**.  **But take my advice: stop using the computer's hard disk immediately.  If you need to use that computer to search for/download a data recovery app, boot from the ubuntu live cd and use a live session to do your synaptic stuff.  If you continue using the hard disk, there is more chance of the mp3 data being overwritten.**

Good luck.

**EDIT:**  There are a few programs that can split files up into smaller files.  2 that look half-promising are **split** and **csplit**.  Of the 2, **csplit** is probably the most promising.  It "split[s] a file into sections determined by context lines".  But how it does this, I have no idea.  Consult the csplit manpage for further info.

---

### Post by Morat on 2009-08-03
Oh <expletive>! What a newbie error. I looked at the file size and thought it was around 1gig and therefore contained all the files. I did not realise that find passed each file in turn to the mv command. I thought it had compiled a list of file names and put that list inside the braces.

The file is actually 16mb and, having tried playing it, I find that it just contains the very last of the 30 or so mp3's I had recorded. Looks like I have lost the rest.

Thanks for the help.

--- Morat.

---

### Post by t0p on 2009-08-03
> **Morat said:**
> Oh <expletive>! What a newbie error. I looked at the file size and thought it was around 1gig and therefore contained all the files. I did not realise that find passed each file in turn to the mv command. I thought it had compiled a list of file names and put that list inside the braces.

The file is actually 16mb and, having tried playing it, I find that it just contains the very last of the 30 or so mp3's I had recorded. Looks like I have lost the rest.


Yes, I was puzzled how the 'mv' command could have done what you described.  If you'd used 'cat' and a '>>' operator, it would be possible.  But I didn't think 'mv' could do anything other than overwrite the previous file with the same name.  But I am no guru, and you said the file in question was 1 GB in size, so I decided to accept what you said at face value.

As for the 30-odd mp3 files you lost... data recovery software could help.  But I think that's a little disproportionate just for the sake of some music files.  Learn from your experience, re-download the lost files... and don't do it again! ;)

---

### Post by Morat on 2009-08-04
> **t0p said:**
> Yes, I was puzzled how the 'mv' command could have done what you described.  If you'd used 'cat' and a '>>' operator, it would be possible.  But I didn't think 'mv' could do anything other than overwrite the previous file with the same name.  But I am no guru, and you said the file in question was 1 GB in size, so I decided to accept what you said at face value.

As for the 30-odd mp3 files you lost... data recovery software could help.  But I think that's a little disproportionate just for the sake of some music files.  Learn from your experience, re-download the lost files... and don't do it again! ;)

Yes, I had not paid enough attention to the number of digits in the size field of the ls output and assumed it was 1 gig instead of 10 meg. The files were actually downloaded from BBC IPlayer using iplayer-dl do I could only re-get the more recent ones. As you said, I must take the hit and learn from this.

Thanks for the help.

--- Morat.

---

