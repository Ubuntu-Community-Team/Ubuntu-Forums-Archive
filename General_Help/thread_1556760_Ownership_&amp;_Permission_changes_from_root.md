---
title: "Ownership &amp; Permission changes from root"
date: 2010-08-19
forum: General Help
---

### Post by j22 on 2010-08-19
Short version - terminal commands to change ownership & permissions from root to my user name/group (john/john) aren't working even though I get a confirmation that they were changed.

Long version - After getting samba to finally work, I want to be able to copy files from a Windows machine to Ubuntu 10.04 x64 machine for backup.  Before trying the smbclient/smbf (?) commands in terminal, I try to copy or move via drag & drop to be sure I can, in fact, copy and move.  Get error message that I don't have ownership so copy/move denied.  Checking the file properties I find ownership and permission's as root.  I find all other files in the directory are root also.  I then check file ownership/permission of files on the Ubuntu machine but that are located in a Windows partition.   They are root also.  I decide to change these from root to my user/group and then use that knowledge on the Windows machine files.  So on the Ubuntu machine, windows partition, and changing to the parent directory of the file I enter to change the owner to my user/group for the file Augustine.doc --

sudo chown john:john Augustine.doc

No error message returned but checking properties of the file it still is shown as root.

I then try it as root by entering su, the root passwork, and then entering the following command:

root@johndesk:~# chown -c john:john /media/C:/"Documents and Settings"/John/"My Documents"/Word/John/Augustine.doc

to which I receive the following confirmation -
changed ownership of `/media/C:/Documents and Settings/John/My Documents/Word/John/Augustine.doc' to john:john

However, again the properties/permissions tab of the file show owner & group as both root along with the footnote "You are not the owner; so you cannot change these permissions.".

Can someone with more experience than me point out what's going on and how to go about changing these permissions?  Why do I get a confirmation but it doesn't change?

Thanks.

---

### Post by j22 on 2010-08-28
Filed as bug; responses to bug posting indicate that ownership/permissions are set when some drives/disks are mounted at least for some anyway.  Part of the mounting process.  I will look into that and call this thread solved.

---

