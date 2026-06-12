---
title: "Search Long file names and non Windows characters"
date: 2010-12-21
forum: General Help
---

### Post by lucast on 2010-12-21
Hi,

Could anyone help me with a search question.

I had all my data on a EXT4 formatted drive.  I decided to switch to NTFS and Fat32 to share files with windows and so copied all my files across.

I have now discovered that some files will not open in Windows because they have non Windows characters in them.

Is there are way to search for all the characters which are not compatible with Windows and also FAT32.  Also Is there a way to search for files with names which are too long for FAT32

Tim

---

### Post by dandnsmith on 2010-12-21
You haven't given any examples, so it may need someone who's solved this problem.
I comment that Windows can sometimes benefit from quoting filenames to overcome problems - a space in the middle is one that comes to mind.
Are your FAT filesystems mounted as 'vfat' - this can make a difference to the way it treats long names?
I cannot get my head round looking for the objectional characters or length of name without more clues.

---

### Post by lucast on 2010-12-21
Hi,

As an example, when I rip music to MP3 in Linux I use the Artist, album and track name to name the file.  Because the program I use gets the track data, sometimes the name might have ¿ ? : * ? " < > |) in the name and this then gets written to the filename.

Linux appears to allow files with these characters to be written to my NTFS partition, but then windows can't open them until I have renamed them in Linux.

Im not sure if these are the only characters which Windows doesn't like, but I would like to search my drive to find these.

Also is it possible to force linux to not allow these characters when writing to NTFS or FAT?

---

### Post by Vaphell on 2010-12-21
```
find . -type f -regextype posix-extended -regex "^.*/[^/]{256,}$"
```

[^/]{256,} = 256 or more not-/'s
256 is the restriction of ntfs, if there is some different value for fat just find out and put it there

windows explorer disallows \ / : * ? " < > |, so it would be something along the lines of
```
find . -type f -regextype posix-extended -regex "^.*/[^/]*[:*?\"<>|][^/]*$"
``` though i haven't tested it so some chars may not work because of necessary escaping or something

---

### Post by ThePooh on 2012-03-07
> **Vaphell said:**
> 
```
find . -type f -regextype posix-extended -regex "^.*/[^/]*[:*?\"<>|][^/]*$"
```

I altered the above code to include $ and ^.  Also the "\" above needed a preceding "\".
I removed "-type f" to find folders as well.

The result is:
```
find .  -regextype posix-extended -regex "^.*/[^/]*[:*?^$<>|\"\\][^/]*$"
```

---

### Post by Akovia on 2012-07-02
This was very helpful but for some reason in my case, I didn't need to include the "$" or the "^" characters. Windows recognized them fine. 

Thnx for the code

---

