---
title: "Unremovable File"
date: 2011-05-30
forum: General Help
---

### Post by jim_deadlock on 2011-05-30
I was messing around with tar and I've ended up with this file on my USB drive (NTFS) with no ownership or permissions or anything:

```
-????????? ? ?   ?            ?                ? backup1.tgz
```

I can't do anything with it

```
$ sudo rm backup1.tgz
rm: cannot remove `backup1.tgz': Input/output error

```

Apart from this the drive is working normally, no problems with any other files.

---

### Post by AlphaLexman on 2011-05-30
You may have a non-printing escape character in the filename. Try this:
```
sudo rm -f ./*backup1.tgz*
```

---

### Post by jim_deadlock on 2011-05-30
Good idea thanks, but still no joy

```
sudo rm -f ./*backup1.tgz*
rm: cannot remove `./backup1.tgz': Input/output error
```

---

### Post by AlphaLexman on 2011-05-30
In your first post with all the question marks was that the output of 'ls -l' ? If so what else can you do to check the file exists and is valid?
```
file backup1.tgz
if [ -a backup1.tgz ]; then echo true; fi
if [ -f backup1.tgz ]; then echo true; fi
```

---

### Post by jim_deadlock on 2011-05-30
Yes that was output from ls -l

```
file backup1.tgz
backup1.tgz: ERROR: cannot open `backup1.tgz' (Input/output error)

if [-f backup1.tgz ]; then echo true; fi
[-f: command not found

```

---

### Post by AlphaLexman on 2011-05-30
You need a **space** between the square bracket **[** and the **-f**

---

### Post by jim_deadlock on 2011-05-30
OK, no output for -a or -f

---

### Post by AlphaLexman on 2011-05-30
Can you un-mount and re-mount successfully? I think the problem may lie with the ntfs-3g driver. It may not be reading file allocation table correctly. Or it could be a user-mapping issue.

---

### Post by jim_deadlock on 2011-05-30
Yes I can mount/unmount no problem. Everything is working normally apart from this stupid file.

Edit: should I try unintalling ntfs-3g and reinstall? It looks pretty severe, I wouldn't want to make matters worse...

---

### Post by AlphaLexman on 2011-05-30
I don't have a ntfs partition, but look at the ntfs-3g man page see if any of the options can fix your file.

You may want to try 'chkdsk' from MS-Win if you have one.

EDIT: I think a re-install is quite drastic.

---

### Post by glene77is on 2011-05-30
> **AlphaLexman said:**
>      .

Alpha,
guess what ? 
I have some 

-????????? ? ?   ?            ?                ?  
showing up in these little test subdir. 
[FONT=monospace]Interesting. 
Maybe I should do more reading, 
and less mucking.  :(
[/FONT]

---

### Post by AlphaLexman on 2011-05-30
@ glene77is, are you also on an ntfs partition?

---

### Post by glene77is on 2011-05-30
> **AlphaLexman said:**
> @ glene77is, are you also on an ntfs partition?

Alpha
No.  Ubuntu, ext2. 
Maybe I did a     chmod 111 filename    . 

So, 
Nautilus shows /ta as glene77is 666.    and test.txt as unknown  unknown unknown .   Not OK.
PCMan   shows /ta as glene77is 666.    and test.txt as glene77is 666.   OK. 
I was getting bored, now there is something to work on.   :popcorn:
Guests are here now, for dinner.

---

### Post by AlphaLexman on 2011-05-30
@ glene77is, did you try these tests?

> **AlphaLexman said:**
> ...can you check the file exists and is valid?
```
file backup1.tgz
if [ -a backup1.tgz ]; then echo true; fi
if [ -f backup1.tgz ]; then echo true; fi
```

---

### Post by glene77is on 2011-05-30
> **AlphaLexman said:**
> @ glene77is, did you try these tests?

Alpha
No.  I jumped right in with PCMan file manager and "tools"  and "open as root".
PCMan was able to delete them.
PCMan was unable to copy / paste the original file.txt back into the folders. 
Used PCMan to delete the folders, and then Create folders as before.
Then PCMan did a copy / paste back into the new folders. 

Nautilus showed the bad files as unloadable and showed nothing in the folders. 
PCMan at user level (glene77is) showed the files as unreadable.
PCMan at root level (root)           showed the files as readable, as glene77is, 666.   OK. 

Only solution was to have PCMan delete the subdir, and re-create subdir, then copy files back in. 
So, advice is to download PCMan and clear the trashed subdir. 
Guess it would have been more interesting to have done it with scripting, 
but I did not do it that way.  

Got to go, guests are here.

---

### Post by jim_deadlock on 2011-05-30
I'm back to report on my adventures with chkdsk. I have Win7 in a VM so I went ahead and ran chkdsk /b

Short answer: problem solved! Good call Alpha!

Long answer: steps 1-3 (of 5) went well, it seemed to fix all kinds of indexing issues, I had no idea my drive was in such a dreadful state. Then came step 4 (verifying file data) and it took 10 hours to process 10% of the filesystem and was hogging an unholy amount of RAM, at which point I finally lost patience and shut the VM down and saved the image, half expecting my drive to be inaccessible, but it turned out fine and the problem file is gone. It's left behind a found.000 folder full of temp files so I might fire up the VM again later and see if it'll continue, if I can be bothered.

Anyway thanks Alpha. SOLVED.

---

### Post by AlphaLexman on 2011-05-30
> **jim_deadlock said:**
> Anyway thanks Alpha. SOLVED.
Thank you, for marking the thread as [SOLVED].

---

