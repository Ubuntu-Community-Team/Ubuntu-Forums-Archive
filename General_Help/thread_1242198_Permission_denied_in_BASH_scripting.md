---
title: "Permission denied in BASH scripting"
date: 2009-08-16
forum: General Help
---

### Post by billdotson on 2009-08-16
When I run a command, say for example:

sudo clamscan -i -r backup_partitiondata > stdout | grep -w "FOUND"

it says: bash: stdout: Permission denied

I am running this as sudo, so why is this happening?

This happens if I try to run a script to copy something or do something to a file that is in a root only folder or mount point. I have found a workaround for this by creating a bash script, putting the command I want to run in it and then typing sudo ./COMMAND but to have to do this all the time is getting annoying. Any ideas? I don't know if I have to add something to a path somewhere or what.

Thank you.

---

### Post by dlmarti on 2009-08-16
sudo clamscan -i -r backup_partitiondata | grep -w "FOUND"

Is what you want, I believe.

---

### Post by llamabr on 2009-08-16
```
sudo clamscan -i -r backup_partitiondata > stdout | grep -w "FOUND"
```

maybe.  or the directory you're in when you run the command is one you don't have write permissions for.  do

```
pwd
```

before you run the command, and post

---

### Post by billdotson on 2009-08-17
this happens with lots of things. You would think I have access to my own home folder.

Yeah, changing the > stdout to just a pipe would work I guess but I have seen other commands be done that way to make the output for to stdout. I guess for commands that normally don't go to stdout you would have to do that? I had linked a few commands earlier using > stdout and no issues whatsoever, so why was clamscan different?

I don't completely understand the pwd command, does it do something different or does it show the same folder that I can see I am in from the terminal (bill@bill:/media/Windows_backups$ that is in the terminal but pwd is /media/Windows_backups/XP, the same)

Regardless though, if I put sudo before any command this shouldn't be happening should it? I know I get permission denied when running as bill, but sudo has access to everything.

Thanks.

---

### Post by ibuclaw on 2009-08-17
> **billdotson said:**
> this happens with lots of things. You would think I have access to my own home folder.

Yeah, changing the > stdout to just a pipe would work I guess but I have seen other commands be done that way to make the output for to stdout. I guess for commands that normally don't go to stdout you would have to do that?

I don't completely understand the pwd command, does it do something different or does it show the same folder that I can see I am in from the terminal (bill@bill:/media/Windows_backups$ that is in the terminal but pwd is /media/Windows_backups/XP, the same)

Regardless though, if I put sudo before any command this shouldn't be happening should it? I know I get permission denied when running as bill, but sudo has access to everything.

If you want to direct all output to stdout in bash, you use the rather cryptic:
```
sudo clamscan -i -r backup_partitiondata **2>&1** | grep -w "FOUND"
```
Which redirects all stderr (2) to stdout (1).

Regards
Iain

---

