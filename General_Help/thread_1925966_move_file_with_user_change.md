---
title: "move file with user change"
date: 2012-02-15
forum: General Help
---

### Post by geohei on 2012-02-15
Hi.

I have 2 users:

UserA
UserB

I have no root access:

I'd like to move a file from /home/UserA to /home/UserB.
After mv command is executed, I would like to that the moved file is owned by UserB.

Is that possible?

Before move:
```
-rw-r--r-- 1 UserA group 0 Feb 15 06:12 file
```

Should look like this after move:
```
-rw-r--r-- 1 UserB group 0 Feb 15 06:12 file
```

---

### Post by drmrgd on 2012-02-15
I don't believe you can chown without root privileges.  It would be a big security flaw if limited users could chown files that didn't belong to them!

---

### Post by geohei on 2012-02-16
Yes, you are right. I expected this answer.

I explain what I would like to do.

UserA is a user of AccountA (upload account) on a server.

UserB is a user who is supposed to manage uploads done my UserA on AccountA. UserA and UserB are part of the same group. A cron script copies uploaded files from AccountA to AccountB.

The problem is that, when I move the files from AccountA to AccountB, the uploaded files keep ownership UserA. Hence, UserB can't move, or delete (w permission is missing) the files since the ownership is UserA instead of UserB.

Now ... UserB could copy the files from AccountA to AccountB (this would change the ownership from UserA to UserB), but then I face another problem. When an upload is in progress, the mv command moves the file and continues the upload until treminated. The cp command copies the file and doesn't wait until finished. Therefore, the file might be corrupt (since upload not finished).

Basically:

mv command
+ upload continues while file is moved
- wrong permissions

cp command
- copied files are corrupt during upload
+ permissions correct

Might be, I need to attack the problem completely differently, but I'm slowly running out of ideas.

Thanks,

---

### Post by LewisTM on 2012-02-16
The easiest would be to set the group to have write access since both users are in the same group. I assume UserB is a member of the UserA group.

Enter umask, which sets the permissions for newly created files. In Ubuntu the default umask is 022 meaning the owner has full file access (6-0=6=rw) while the group has only read access (6-2=4=r-). You want to change it to 002.

This is kind of tricky since the way to set it will vary between Ubuntu versions and whether umask should be set for a single process or systemwide.

Running [FONT="Courier New"]umask 002[/FONT] before a command or at the beginning of a script will set it for the process.

For systemwide the easiest would be to modify the PAM authentication config in /etc/pam.d/common-session. 
Add a line with
```
session optional     pam_umask.so umask=002
```

Cheers!

---

