---
title: "Newbie Help Please - Changing File Permissons"
date: 2009-11-08
forum: General Help
---

### Post by Quarkrad on 2009-11-08
I have a file called sbackupd in etc/init.d - which is a script.  I need to set file ownership to root:root and file permissions to: rwx-r-xr-x. 

Hmmmm...

Not easy for a newbie/me.  I can go **gksudo nautilus** so I can navigate/see the file and if I right click and go Properties/Permissions it looks like I can change the owner to root (it already is at root) but all the Access attributes are listed in words (Read-only, Read and Write). Not sure at this level how I change to rwx-r-xr-x.

I have googled to try and see how it is done but I'm thrown into unknown waters. Is there a simple way to change this files permissions?

---

### Post by HiImTye on 2009-11-08
rwx-r-xr-x

read/write/execute
read/execute
read/execute
:D

---

### Post by Primefalcon on 2009-11-08
> **Quarkrad said:**
> I have a file called sbackupd in etc/init.d - which is a script.  I need to set file ownership to root:root and file permissions to: rwx-r-xr-x. 

Hmmmm...

Not easy for a newbie/me.  I can go **gksudo nautilus** so I can navigate/see the file and if I right click and go Properties/Permissions it looks like I can change the owner to root (it already is at root) but all the Access attributes are listed in words (Read-only, Read and Write). Not sure at this level how I change to rwx-r-xr-x.

I have googled to try and see how it is done but I'm thrown into unknown waters. Is there a simple way to change this files permissions?
easiest way is chmod via the cli, and your probaly better off using a numeric style

0 = no permissions (aka denied)
1 = execute
2 = write
4 = read

you combine them to get various permissions, for example read and write is 6, while just read and execute is 5

ok now you have a triple permissions system, owner(aka user), group and others...

for example to give the owner read write and execute permissions, group read, and everything else nothing it would be

640

the syntax to run this on a file is as such

```
chmod 640 filename
```

note: remember to cd to the directory first by running

```
cd /path/to/directory/
```

---

### Post by Quarkrad on 2009-11-08
Ah - thank you.  I thought it might be this.  So the order is:

Owner        read/write/execute
Group        read/execute
Others       read/execute

---

### Post by Primefalcon on 2009-11-08
> **Quarkrad said:**
> Ah - thank you.  I thought it might be this.  So the order is:

Owner        read/write/execute
Group        read/execute
Others       read/execute
which would be chmod 755 filename, I know a lot of newcomers don't like the cli but it really is easier for tasks like this

---

### Post by scouser73 on 2009-11-08
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your file/folder or drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by Quarkrad on 2009-11-08
Ok - I'm nearly there but not quite.  Sorry.

rwx-r-xr-x

**rwx**  I can see read/write/execute
**r**    read
**xr**   execute/read
**x**    execute

Four settings for three settings  Owner/Access, Group/Access, Others/Access ???

So using the numbers I'm guessing  rwx-r-xr-x  is 7-4-5-1  so is the command chmod 7451 filename?   Probably not!

---

### Post by Lateralis on 2009-11-08
There are three different sets of permissions:  user/owner, others and groups.  When you see the permissions of a file, you might see something like this: -rw-r--r--

The first dash is to designate whether the "thing" is a file (-), directory (d) or link (l).  The next three characters relate to read-write-execute for the owner, next three for others and next three for groups.  So for the particular example I have given above, it relates to a file where the owner (me) is able to read and write to the file, whilst everyone else and special groups are read only.

---

### Post by Quarkrad on 2009-11-08
Thank you all - I now understand.

---

