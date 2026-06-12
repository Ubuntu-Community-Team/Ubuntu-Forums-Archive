---
title: "luckybackup: how to &quot;echo&quot; a folder from hdd 1 on hdd2"
date: 2010-04-27
forum: General Help
---

### Post by Pifilatakanemu on 2010-04-27
Ok,
sounds trivial but I don't manage to make a "one-way-sync" from my backintime folder on hdd 1 on hdd 2. 

I just want luckybackup to copy everything from hdd 1 to hdd 2 and delete every file on hdd 2 that is not on hdd 1. 

I tried all different backup-patterns but hdd 2 ends up filled with stuff that was already deleted on hdd 1.


any suggestions or nice alternatives?

---

### Post by geirha on 2010-04-27
rsync can do that.
```
man rsync
```

There's also a gui front-end; [grsync](apt:grsync).

---

### Post by Pifilatakanemu on 2010-04-27
I used to do it with grsync, too.


What I miss is to create and run a list of tasks.

In luckybackup I have a list of operations that are subsequently run:
/home -> /Dropbox
/home -> /Ubuntu One
/hdd1/backintime - /hdd2
/hdd1/backintime - /hdd3
/hdd1/movies -> /hdd2
/hdd1/photos -> /hdd3
/hdd1/music -> /hdd3


I don't want to miss that automatization. With Grsync I can only run them one by one.

---

### Post by Pifilatakanemu on 2010-05-04
*push*


I'd love to see a solution to this.

Thanks!

---

### Post by StuartN on 2010-05-04
> **flohmann said:**
> I used to do it with grsync, too.
What I miss is to create and run a list of tasks.

Grsync will display the rsync command that will be run, which you can cut and paste into a file. Once you have cut and pasted all your tasks, you can make the file executable and run it as a script.

The rsync --dry-run option is very useful too to check what would be backed up.

---

### Post by dcstar on 2010-05-05
**luckybackup**

rsync-based GUI data backup utility

---

### Post by Pifilatakanemu on 2010-05-12
luckybackup failed in my case.

now i'm thinking about writing a script for this purpose.
as I want to sync several folders at once, Grsync is no solution for me.

What about a script like this:

```
#!/bin/bash
# Backupscript

sudo rsync -a --delete /quellpfad1 /zielpfad1
sudo rsync -a --delete /quellpfad2 /zielpfad2
sudo rsync -a --delete /quellpfad3 /zielpfad3

exit 0
```

---

### Post by Pifilatakanemu on 2010-05-13
would it work that way after making the script executable?

please help me.

thanks.

---

### Post by StuartN on 2010-05-14
> **Pifilatakanemu said:**
> would it work that way after making the script executable?

please help me.

thanks.

I do not think you need to use sudo, and the exit is superfluous because the script will end at that point. You need a trailing / on your paths. Otherwise it looks like it will work.

The -i option is useful to itemize all the changes, and the output can be saved in a file, e.g. rsync -ia --delete [source/] [dest/] > Backupscript.log

You can also use --dry-run to generate the output without copying any files, to test what will happen - very useful when you also have --delete.

---

