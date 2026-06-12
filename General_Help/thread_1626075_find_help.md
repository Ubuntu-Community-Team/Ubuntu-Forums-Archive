---
title: "find help"
date: 2010-11-19
forum: General Help
---

### Post by mellis95 on 2010-11-19
I have been working on a cronjob to delete backup files that are more than 3 days old. I have found numerous references on various forums that say to do the following:

```
find /var/www/backup -mtime +3 -exec rm {} \;
```

However, it was not deleting all of the files more than three days old. After some research, I discovered the following:
I have five files with the following modification dates:
11-15-2010
11-16-2010
11-17-2010
11-18-2010
11-19-2010
If I run this command from the CLI ON 11-19-2010:

```
find /var/www/backup -mtime +3
``` 

it finds only the 11-15-2010 file. If I change it to -mtime +2, I find the 11-15-2010 and 11-16-2010 files.

Everything that I have read says that the "+3" in -mtime is DAYS, which leads me to believe that -mtime +3 should return all files that were modified MORE than 3 days ago. 
SO, what am I missing? This is happening on Ubuntu 9.10 Server Edition 32 bit and I have not been able to test on another machine.

Thanks,
Matt

---

### Post by papibe on 2010-11-19
From the man's find:
> When  find  figures  out how  many  24-hour  periods  ago the file was last accessed, any fractional part is ignored, so to match -atime +1, a file has to have been accessed at least two days ago.

It looks like the way "find" rounds time is different that the regular common sense. So in your case, it looks like +2 will do the job for "three days".

Good Luck!

---

### Post by asmoore82 on 2010-11-19
`find` can do the job but it makes me nervous.

I would recommend a daily cycle script like logfiles have.

That way you always know the old files are being deleted.

so something like this run daily...

```
[COLOR="Blue"]#Go to Backups[/COLOR]
cd ~/Backups

[COLOR="Blue"]#Drop the oldest[/COLOR]
unlink www.tar.gz.3

[COLOR="Blue"]#Cycle the rest[/COLOR]
mv www.tar.gz.2 www.tar.gz.3
mv www.tar.gz.1 www.tar.gz.2
mv www.tar.gz   www.tar.gz.1

[COLOR="Blue"]#Make today's[/COLOR]
tar -zcf www.tar.gz -C /var/www .

```

---

