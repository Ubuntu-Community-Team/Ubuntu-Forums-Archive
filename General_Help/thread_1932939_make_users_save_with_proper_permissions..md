---
title: "make users save with proper permissions."
date: 2012-02-28
forum: General Help
---

### Post by toasticles on 2012-02-28
I am trying to get my users to save files to a group share with read/write permissions. They only save with read. The other users can see the file and delete it, but not write. I am not sure what is going on. The shares permissions are (rwsrws---), so everyone in the group should be able to read ans write to everything in the folder, right?

---

### Post by idoitprone on 2012-02-28
> **toasticles said:**
> I am trying to get my users to save files to a group share with read/write permissions. They only save with read. The other users can see the file and delete it, but not write. I am not sure what is going on. The shares permissions are (rwsrws---), so everyone in the group should be able to read ans write to everything in the folder, right?

one stupid question. Did you add them to your group that owns the file?

or the files have proper permission ans umask is 002?
[http://www.nmr.mgh.harvard.edu/martinos/userInfo/computer/perms.php](http://www.nmr.mgh.harvard.edu/martinos/userInfo/computer/perms.php)

---

### Post by toasticles on 2012-02-28
Yes I did add them to the group and did unmask is 002. I didnt think to make the group their main group, and now it works. Would making this the main group mess with other groups they may be  part of?

---

### Post by idoitprone on 2012-02-28
> **toasticles said:**
> Yes I did add them to the group and did unmask is 002. I didnt think to make the group their main group, and now it works. Would making this the main group mess with other groups they may be  part of?

I dont know. You should ask someone else.

---

### Post by bab1 on 2012-02-28
> **toasticles said:**
> Yes I did add them to the group and did unmask is 002. I didnt think to make the group their main group, and now it works. Would making this the main group mess with other groups they may be  part of?

The user is not really the most important identity to the file or directory when sharing files.  With the default setting in Ubuntu sets a group of the same name as the user, but the user is not part of that group (check it out).  Use the group to determine the rw capabilities for the files.  The user that created the file is not important in this context. 

The most efficient way to set this out is to first set the overall umask to 002 in the /etc/profile file (see the bottom of the file).  This sets the creation permissions to 775 for directories and 664 for files.

From the root of the file system in question (i.e /srv) you can set the common group you wish to use.  For example I have a group called smbusers that holds all the users that share files using Samba.

Then we need to set that common group on the root directory and use the sguid bit to force the group on all files and directories below the root directory.  First set the group like this```
sudo chgrp smbusers /srv
```

Then we need to set the sguid and eXecute bit on all directories below the starting point like this```
sudo chmod -R u=rwXs,g=rX,o=rX /srv
```

At this point all files and folders will be created with the group you determined (in my case: smbusers) and the permissions are 755 for dir and 664 for files.

See [**_[COLOR="Blue"]here[/COLOR]_**]("ubuntuforums.org/showthread.php?t=1931995") for a discussion of this last night.

Note: the use of /srv is used for for this discussion only.  By root I mean the beginning of the directory structure you are using.

---

