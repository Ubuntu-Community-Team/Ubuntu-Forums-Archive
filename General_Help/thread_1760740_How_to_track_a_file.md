---
title: "How to track a file?"
date: 2011-05-17
forum: General Help
---

### Post by enimeizoo on 2011-05-17
Hello,
For learning purposes, I am trying to make a program that will allow me to 'tag' folders and files, allowing search by keywords on documents such as photos, pdf... etc. 
To keep the main file up to date automatically, I need to know whenever a file is moved, suppressed... I have no clue about how to do that. Is there any log for that or something?

Any help is welcome.

---

### Post by __Sun__ on 2011-05-17
It would greatly depend on the programming language you are using.

For starters, try:
```
man stat
```You would, of course, need to loop through files in a directory **stat**ing them one by one and see if they meet your criteria (E.g., check access time, modification time, etc.)

As for checking whence a file was moved, it is tricky. You could try two ways.

(1) maintain a small log
(2) overlap the mv(1) utility (easily done with a shell script) or whatever is the "move" command

---

### Post by enimeizoo on 2011-05-17
Thanks for your reply.
The language I use is python, to be able to manipulate xml files (that is how I want to store tags).
Changes I need to track are files moved, and copied. I have already thought about overlapping the mv command (actually creating an alias), but I was not sure about how to get files managers to use my alias. 

I'm interested about how you would maintain a log, without overlapping mv or cp.

---

### Post by __Sun__ on 2011-05-17
A log is maintained by system by default. See:
```
man mlocate.db
```All the details of which block contains what information is in the manual.

If you don't like mlocate.db you can create your own log, just write values from stat to a file in a structured hierarchy.

So, what you really need to do is find a new file that is not in the database.
Once you find it, there are 3 possiblities:

(1) it was newly created.
(2) it was moved elsewhere or renamed.
(3) it was copied.

You can check if it was newly created by looking at the date of the log and the creation date of the file. Easy.

Check the inode number of the file to see if the file was moved. If the path is different or name is different but inode number is the same as one from the log then that particular file was moved (the one with the exact same inode number). The exception is that hard links share the same inode number as the original file, so you'll have to check paths to see if the old one is still there (if it is, then don't bother to do anything cuz the file wasn't moved). 

*Edit* *improved*
Last part, if it was copied. Clearly, copying is the same as creating a new file. So, the first check will always succeed if file was also copied. I have a slightly inefficient solution to this problem as I can't think of anything else.
Compare this new file with other files, byte by byte and see if it is the same. Only do this when the file size matches, to save time.
It would be better to compare by one **word** (usu. 4 bytes on 32 bit systems) size at a time as this is very very efficient.

I think overlapping mv and cp might be easier and faster.

---

### Post by dragonfly41 on 2011-05-17
see here .. Linux users looking for equivalent of filemon for windows .. [www.sysinternals.com](www.sysinternals.com) (but windows only)

[http://superuser.com/questions/160447/file-monitor-like-sysinternals-filemon-for-linux](http://superuser.com/questions/160447/file-monitor-like-sysinternals-filemon-for-linux)

---

### Post by __Sun__ on 2011-05-17
> see here .. Linux users looking for equivalent of filemon for windows .. [www.sysinternals.com]("http://www.sysinternals.com/") (but windows only)

[http://superuser.com/questions/16044...emon-for-linux]("http://superuser.com/questions/160447/file-monitor-like-sysinternals-filemon-for-linux")

Sweet, there is a perl library too. Really sweet.

The programme would have to be continually run for the duration of the PC session for it to detect any changes. It would help detect real-time changes I suppose.

---

### Post by enimeizoo on 2011-05-17
Thanks, this is very valuable info to me.

I think I have all I need with that. I think I will try both ways!


@dragonfly41 : You sound like the fact windows does have some good features is something huge  :P
Whatever, thanks for the input on audit!

---

### Post by dragonfly41 on 2011-05-17
Further digging around .. just to keep them together ..

[http://stackoverflow.com/questions/420143/making-git-auto-commit](http://stackoverflow.com/questions/420143/making-git-auto-commit)

[EDIT]

> @dragonfly41 : You sound like the fact windows does have some good features is something huge
I will always give windows fair credit where it is due .. and I've found nothing (yet) to match the tools in sysinternals.com.

---

