---
title: "Backup Over-all User Changes"
date: 2009-08-28
forum: General Help
---

### Post by thepalsrus on 2009-08-28
I am trying to figure out a way to backup any changes made by the user on a Ubuntu system. 
I want to isolate the installed packages from the user data and backup only the user data.
The user may not have kept the files exclusively in the home directory and so I need to be able to find the changes and create a backup of just user created files.
I do not have a backup of the initial system installation and do not want to backup packages files.
The user is a python programmer and stores files in various locations outside the home directory.
I was thinking some rendition of rsync any thoughts?

I was thinking of trying to pull a list of all installed packages and their dependencies into a text file and excluding them during a backup.  Is there an easier way to do this?  Can I pull the list into the command without having to dump it to a file first?

Thanks

---

### Post by thepalsrus on 2009-08-28
I am looking for a multi-platform solution.  I was thinking about using the find command to find all the files used by that user, but it would not work since the user can use sudo to create files or install apps.  I thought I could use:

for ENT in $(rpm -qa --filesbypkg | tr -s  '[:blank:]' ' ' | sed 's:^[^ ]* ::' | sort -u); do if [ ! -d "${ENT}" ]; then echo "${ENT}" >> /tmp/rsync.exclude; fi; done

and them just exclude the files listed in the rsync.exclude file during backup.  Is there an easier way to do this?

---

