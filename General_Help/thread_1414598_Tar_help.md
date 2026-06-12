---
title: "Tar help"
date: 2010-02-23
forum: General Help
---

### Post by skeeterxb on 2010-02-23
I have a script which runs on my machine to backup one directory to another, I setup cron to do this at a particular time each night.  This is working perfectly, pretty straight forward.  I am now looking to write another which will run daily after the script above has run and produce a tar.gz file to another folder with a following naming convention JDoe-2Feb2009.tar.gz or something like that.    At a loss on this one how to begin.   Any guidance would be appreciative. 
 
Thanks
Rob

---

### Post by skeeterxb on 2010-02-23
Think i might be onto a start.  Please let me know if i am getting close. 
 
I can configure this as a script to backup the follow directory and create a tar.gz of it and dump it into the following directory, i believe, i havent tested it yet.  I am just not sure on the date stamp piece. 
 
tar cf /home/rob/backups | gzip -c > /home/backups/archive/Rob-$datestamp.tar.gz

---

### Post by jobix on 2010-02-23
tar has a "z" option. That will allow you to get rid of the gzip.

---

### Post by skeeterxb on 2010-02-23
Here is what i am trying to do, going to create a script which
tar's a folder and gzip's it to another location with a date stamp.  I thought i was close below but, i got the following error -  
 
Doesnt seem to work, says it refuses to create empty archive

tar cf /home/rob/backups | gzip -c > /home/rob/backups/archive/Rob-$datestamp.tar.gz
 
Any further help but be much appreciated.

---

### Post by n0dix on 2010-02-23
> **skeeterxb said:**
> Here is what i am trying to do, going to create a script which
tar's a folder and gzip's it to another location with a date stamp.  I thought i was close below but, i got the following error -  
 
Doesnt seem to work, says it refuses to create empty archive

tar cf /home/rob/backups | gzip -c > /home/rob/backups/archive/Rob-$datestamp.tar.gz
 
Any further help but be much appreciated.

Try 
```
tar czfv /home/rob/backups /home/rob/backups/archive/Rob-$datestamp.tar.gz
```

---

### Post by jobix on 2010-02-24
> **skeeterxb said:**
> Here is what i am trying to do, going to create a script which
tar's a folder and gzip's it to another location with a date stamp.  I thought i was close below but, i got the following error -  
 
Doesnt seem to work, says it refuses to create empty archive

tar cf /home/rob/backups | gzip -c > /home/rob/backups/archive/Rob-$datestamp.tar.gz
 
Any further help but be much appreciated.

It should've complained and also suggested using 'tar --help' or 'tar --usage'. man tar should also have shown you what you're doing wrong. The problem in your command above is that you use the f option but then try to redirect the output to gzip. The man page will tell you that the "f" option needs you to specify a file. In your example you are not specifying a file to the first tar command.

```
tar c /home/rob/backups | gzip -c > /home/rob/backups/archive/Rob-$datestamp.tar.gz 
```

will work. Or better yet:

```
tar zc /home/rob/backups -f /home/rob/backups/archive/Rob-$datestamp.tar.gz

```

There is another problem however. You're storing the tar.gz file in the archive directory which is in the backups directory. This means the next time you try to create a backup, it will create a tar of all the stuff in the archive directory too including the previous tar.gz file. Not sure if that is what you want.

---

### Post by skeeterxb on 2010-02-24
Thank you that is doing what i was looking for.  I took your advice and moved the archive folder out of the backup folder.  Worked great except one last issue, i am hoping to have the new file name appear in this format "Rob-24Feb20109.tar.gz"
 
Here is my new script
 
tar zc /home/rob/backups -f /home/rob/archive/Rob-'date+%m-%d-%y'.tar.gz
 
All that i am getting is Rob-'date+%m-%d-%y'.tar.gz
 
Any other ideas, thanks again in advance.

---

### Post by skeeterxb on 2010-02-24
See you leave me long enough and i figure it out.  
 
tar zc /home/rob/backups -f /home/rob/archive/Rob-`date+%d%m%y`.tar.gz
 
Is there anyway to delete files from a directory after a they are a week old?

---

### Post by jobix on 2010-02-26
> **skeeterxb said:**
> See you leave me long enough and i figure it out.  
 
tar zc /home/rob/backups -f /home/rob/archive/Rob-`date+%d%m%y`.tar.gz
 
Is there anyway to delete files from a directory after a they are a week old?

The best way to learn is by figuring it out yourself, like you did. You seem like a smart guy. So, I'll give you a pointer, not the complete answer. :)

Use the "find" command. "man find" for more help. It has the option you need. Once you determine which files are a week old, you can use "rm" to remove them.

Good luck.

---

