---
title: "rsync and permissions driving me nuts"
date: 2009-08-04
forum: General Help
---

### Post by jmirick on 2009-08-04
I'm trying to backup users' Maildir folders from the mail server to an on-network backup server.  I want cron to launch every day a process that grabs them, incrementally updates the destination, and just parks them in one place so then I can further go offsite with them.  But I'm constantly getting stopped by permission violations of one kind or another.  I'm logged into the server as user ns02-temp, and my current command is:
> 
rsync -av 192.168.10.24:home/jrm/Maildir/* /home/ns02-temp/testbackup/jrm

and the system returns: 

> receiving incremental file list
rsync: mkdir "/home/ns02-temp/testbackup/jrm" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(594) [receiver=3.0.5]

But there IS that directory, and the permissions are wide open.  It makes no difference if I set the options to -av or anything else.  Also, if I delete the "jrm" directory, it won't create it.

I've tried to run rsync with sudo but then it asks for root password on the source machine which of course I can't supply.

I'm sure there is something very simple wrong here, and I keep hearing that rsync is very simple and great, but I'm stopped dead.  Any suggestions would be greatly appreciated.

---

### Post by kpkeerthi on 2009-08-04
Can you post the output of?
```
ls -ld /home/ns02-temp/testbackup/jrm 
```

---

### Post by jmirick on 2009-08-04
OK, so I'm officially blind, the directory was test-backup, not testbackup, which goes to show you that if you look at something long enough, you'll see what you expect to see, especially after about 8 hours.

What I also had to do was to create a "backup user" on the mail machine, and add this user as a member of the group of each of the Maildir directories, "apply to the enclosed files", and then it has access to them all.  If I don't do this, the source machine throws an error that my user has no access.

I assume that there's a way to get the ssh password to be auto-inserted into the script when I get it written, I'll have to look at that.  But at least I can get to the files.

Thanks for prying my eyes open.

---

### Post by kpkeerthi on 2009-08-04
You could use TAB autocomplete to autocomplete filenames while working at the command prompt.

---

