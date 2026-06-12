---
title: "How can I find and DELETE directories  uding -exec rm?"
date: 2009-08-04
forum: General Help
---

### Post by malarie on 2009-08-04
Hi there, 

I want to erase old backup files on my laptop every 15 days using a cronjob.

Here is my command:


find /var/backup -type d -mtime +15 -exec rm {} \;

This does not work, because i have to pass arguments to the command. (rm -r or rmdir -r)

How do I pass an option to the command that is called by -exec?


I know i can find  -type f -exec rm{} \; then run the same command with type d -exec rmdir but im curious to know if we can pass arguments to a command called by -exec.

Thanks much

---

### Post by warp99 on 2009-08-04
```
find /var/backup -type d -mtime +15 | xargs rm -r
```

If you need root you can place sudo in-front of the xargs command.

---

### Post by pizmooz on 2009-08-04
Here are some examples of find usage [here]("http://www.wagoneers.com/UNIX/FIND/find-usage.html").  There is probably something going on with the parameter expansion that is tripping you up.  for instance:
```
find / -exec echo {} \;
``` works
```
find / -exec 'echo {} ;'
``` does not work
```
find / -exec 'echo' '{}' ';'
``` works

Also find is recursive automatically, I am guessing you know that and want to use rm -r to remove the directories.  It would probably simplify things to use tar to backup, then you will only have to worry about one file when you rotate the backups.

---

### Post by malarie on 2009-08-04
> **warp99 said:**
> ```
find /var/backup -type d -mtime +15 | xargs rm -r
```

If you need root you can place sudo in-front of the xargs command.

The command piped to xargs does not work:
find /var/backup -type d -mtime +15 | xargs rm -r
rm: missing operand
Try `rm --help' for more information.


I made it work, its really not elegant, but i did a 
#!/bin/bash

find  /var/backup -type f  -mtime+15 -exec rm {} \;
sleep 5
find  /var/backup -type d  -mtime +15 -exec rm {} \;

---

### Post by warp99 on 2009-08-04
> **malarie said:**
> The command piped to xargs does not work:
find /var/backup -type d -mtime +15 | xargs rm -r
rm: missing operand
Try `rm --help' for more information

It does work, the reason you received the missing operand error is because the find command did not locate any files of that type. Prove of concept:

```
:~/Public$ mkdir 1 2 3 4 5
:~/Public$ ls
1  2  3  4  5
:~/Public$ find ./ -type d | xargs rm -r
rm: cannot remove directory `./'
:~/Public$ ls 
```

---

### Post by malarie on 2009-08-04
-1 for me.

I was expecting no return at all because i already erased the files when testing the script.

Merci

---

### Post by geirha on 2009-08-04
```
find /var/backup -type d -mtime +15 -delete
```

Though, that will only remove empty dirs, so you might want
```

find /var/backup -depth -type d -mtime +15 -exec rm -r {} +
# or
find /var/backup -depth -type d -mtime +15 -print0 | xargs -0 -- rm -r

```
Never ever use find|xargs with out -print0 and -0

---

