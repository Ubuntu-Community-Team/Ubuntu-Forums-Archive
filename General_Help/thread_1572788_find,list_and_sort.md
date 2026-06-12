---
title: "find,list and sort"
date: 2010-09-11
forum: General Help
---

### Post by bowens44 on 2010-09-11
I have tried to find a way to do this but have been unsuccessful.....

Heres the situation:

I have  hard drive with several thousand photos. These photos are in different formats, some are tif some jpg some raw (cr2). These  files are in dozens of directories.

What I want to do is produce a list of all the files, in all of the directories, sorted by the file name (not sorting on the path), listing the location, file name, size and date  created.

For instance I may have a file called photo1.jpg in /photos/pics/
I may also have a file called photo1.cr2 in /photos/misc/ and a file called photo1.tif in /photos/processed/summer/.

I would like a text file that would look like this:
/photos/misc/photo1.cr2               2536658 2010-07-09 13:17
/photos/pics/photo1.jpg                320046 2010-07-07 14:47 
/photos/processed/summer/photo1.tif 234456689 2010-07-10 09:22

Of course I want it to do this for all of the photos.

I pretty sure that there is a way to do this with a minimum amount of work.

I have no problem with using the command line. 

Any suggestions as to the best way to accomplish this will be greatly appreciated. thanks

---

### Post by zigmo on 2010-09-11
You could try the find command and send the output to a text file.
Perhaps something like:

```
find /photos -name *.jpg > jpg_photos.txt
```

Repeat with different search strings and filetype text files.

---

### Post by llamabr on 2010-09-11
Fine will work, for this I'd use locate:

```
locate .jpg | xargs ls -lh > file.txt
```

you'll want to mess around with it at that point, but it'll get you started.  Depending on how many directories you're working with, find might be better.  Locate may turn up much more than you want.

---

### Post by lloyd_b on 2010-09-11
> **bowens44 said:**
> I have tried to find a way to do this but have been unsuccessful.....

Heres the situation:

I have  hard drive with several thousand photos. These photos are in different formats, some are tif some jpg some raw (cr2). These  files are in dozens of directories.

What I want to do is produce a list of all the files, in all of the directories, sorted by the file name (not sorting on the path), listing the location, file name, size and date  created.

For instance I may have a file called photo1.jpg in /photos/pics/
I may also have a file called photo1.cr2 in /photos/misc/ and a file called photo1.tif in /photos/processed/summer/.

I would like a text file that would look like this:
/photos/misc/photo1.cr2               2536658 2010-07-09 13:17
/photos/pics/photo1.jpg                320046 2010-07-07 14:47 
/photos/processed/summer/photo1.tif 234456689 2010-07-10 09:22

Of course I want it to do this for all of the photos.

I pretty sure that there is a way to do this with a minimum amount of work.

I have no problem with using the command line. 

Any suggestions as to the best way to accomplish this will be greatly appreciated. thanks

'find' and 'sort', when combined, will do this:```
find . \( -name "*.jpg" -o -name "*.tif" -o -name "*.cr2" \) -printf "%h %f %k %t\n" | sort -k 2 > pictures.txt
``` should do the trick.  The "-o" parts should be read as "or", so it translates to "find from the current directory all files matching *.jpg or *.tif or *.cr2".  The printf is used to control the output format, forcing a space between the path and the filename (which sort needs to be able to sort on the filename).

Note that in this example, 'sort' will not do what you want if there are spaces in the path or file names...

Lloyd B

---

