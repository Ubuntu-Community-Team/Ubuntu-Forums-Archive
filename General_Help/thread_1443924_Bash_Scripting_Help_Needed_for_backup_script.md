---
title: "Bash Scripting Help Needed for backup script"
date: 2010-03-31
forum: General Help
---

### Post by spliner on 2010-03-31
I am trying to write a bash script that will tar the contents of the /home directory to back up users files.  Problem is, I have a server with a ton of home directories and the files have become quite large with my script that simply tars them all in one file.  What I would like to accomplish is a script that would tar the contents of the home directory with a separate tar file for each home folder.

For instance if I had /home/user1 and /home/user2 I would end up with user1.tar and user2.tar instead of a huge users.tar file.

That way restoring files would be quicker and easier for a single user.

Any help is appreciated.  I've been trying to list the contents of the /home directory to a file, then use that file to create the tar files.  For instance using ls -1 /home > homedirs would give me a file called 'homedirs' that would list each folder on a single line.  How would I then use that file to create the individual tar files?

Any ideas?  I had to restore a single user's home directory the other day and my 27 gig backup file with over 70 user's files took forever to extract that one user's folder.

---

### Post by derrick81787 on 2010-03-31
> **spliner said:**
> I am trying to write a bash script that will tar the contents of the /home directory to back up users files.  Problem is, I have a server with a ton of home directories and the files have become quite large with my script that simply tars them all in one file.  What I would like to accomplish is a script that would tar the contents of the home directory with a separate tar file for each home folder.

For instance if I had /home/user1 and /home/user2 I would end up with user1.tar and user2.tar instead of a huge users.tar file.

That way restoring files would be quicker and easier for a single user.

Any help is appreciated.  I've been trying to list the contents of the /home directory to a file, then use that file to create the tar files.  For instance using ls -1 /home > homedirs would give me a file called 'homedirs' that would list each folder on a single line.  How would I then use that file to create the individual tar files?

Any ideas?  I had to restore a single user's home directory the other day and my 27 gig backup file with over 70 user's files took forever to extract that one user's folder.

Try something like this:
```
#!/usr/bin/env bash
for folder in $(ls /home); do
   tar -czf "/path/to/backup/dir/$folder.tar.gz" "$folder"
done
exit
```

That way, for each folder in your /home directory, you will create a folder.tar.gz in whatever location you specify in the script.  For example, if you have a user1 and a user2, then you will have user1.tar.gz and user2.tar.gz, just like I think you wanted.

I hope this helps.

- Derrick

*****Edit:**
If your home directory is on a separate partition than the rest of your system, you might have a folder called lost+found.  If you do, you will want to exclude that.  In that case, just make the script like this:
```
#!/usr/bin/env bash
for folder in $(ls /home); do
   if [ "$folder" != "lost+found" ]; then
      tar -czf "/path/to/backup/dir/$folder.tar.gz" "$folder"
   fi
done
exit
```

---

### Post by spliner on 2010-03-31
I'll give that a try, thanks for the help!

Spliner

---

### Post by spliner on 2010-03-31
Ok, that seems to work.  I modified it a bit so the script could be run from somewhere else other than the home dir and added the verbose switch for logging purposes:

#!/usr/bin/env bash
#Loop for each folder in the /home dir
for folder in $(ls /home); do
     tar -cvzf "/backupdir/$folder.tar.gz" /home/"$folder"
done
exit

But.. I also need to log everything that is tar'd to a text file so I tried adding a redirect > backup.log like:

#!/usr/bin/env bash
#Loop for each folder in the /home dir
for folder in $(ls /home); do
     tar -cvzf "/backupdir/$folder.tar.gz" /home/"$folder" > /backup.log
done
exit

However, it only writes the last directory it backs up to the log.  Any idea how to fix that?

Edit: Figured that part out.. helps if you redirect it correctly (append):
tar -cvzf "/backupdir/$folder.tar.gz" /home/"$folder" >> /backup.log

It was overwriting the backup.log file each time it did a new folder.

Thanks again, I'll post my progress here for the rest of my script.  Might be helpful to someone other than me.

Spliner

---

### Post by derrick81787 on 2010-03-31
Yeah, I accidentally forgot to add the "/home/" to the tar command, so I'm glad you figured that out.  Also, using >> to redirect should work for the logging, I would think.  Let me know if you need anything else, but it sounds like you're on the right track.

---

### Post by spliner on 2010-04-09
This worked great, thanks much for the help.  My original script simply threw all of the home folders in a single tar.  Parsing that tar file from a removable drive was taking F O R E V E R when I needed to restore just one folder.  This is a much more elegant solution for me.

It has been a while since I logged a script, I had forgotten that > created a file (over-wrote), while >> appends.  Worked like a charm.

Spliner

---

### Post by derrick81787 on 2010-04-10
> **spliner said:**
> This worked great, thanks much for the help.  My original script simply threw all of the home folders in a single tar.  Parsing that tar file from a removable drive was taking F O R E V E R when I needed to restore just one folder.  This is a much more elegant solution for me.

It has been a while since I logged a script, I had forgotten that > created a file (over-wrote), while >> appends.  Worked like a charm.

Spliner

Awesome! I'm glad I could help.

- Derrick

---

