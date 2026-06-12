---
title: "File Permissions"
date: 2009-08-28
forum: General Help
---

### Post by dmcdaniel on 2009-08-28
Hello everyone,

Pre-word: I'm using command line to do this and I can't get it to work. 

I have a folder that I need to give Write permissions too. 

This is what I have tried so far:

```
sudo chmod 777 /media/intouch
sudo chown 500.user intouch 
```

neither has worked. This is how I mounted the file:

```
sudo mount -t cifs -o username=mcdaniel //10.0.11.4/intouch /media/intouch
```


This is the error I receive:

```
changing permissions of `intouch': Permission denied
```

Any Ideas on how to give it permission?

---

### Post by dmcdaniel on 2009-08-28
No one can help?

---

### Post by Zill on 2009-08-28
The following code should confirm that your mount directory has your required permissions.
```
ls -l /media/intouch
```
If these permissions are correct then I suggest that your source directory permissions may need to be changed similarly.

ps.  You may need to try "sudo chmod 755" rather than 777.

---

### Post by dmcdaniel on 2009-09-01
> **Zill said:**
> The following code should confirm that your mount directory has your required permissions.
```
ls -l /media/intouch
```
If these permissions are correct then I suggest that your source directory permissions may need to be changed similarly.

ps.  You may need to try "sudo chmod 755" rather than 777.

Hello,

Thanks for the response. I tried what you suggested and this is the error I received. 

```
agent@szeto110:~$ sudo chmod 755 /media/intouch
[sudo] password for agent: 
chmod: changing permissions of `/media/intouch': Permission denied

```

---

### Post by Zill on 2009-09-01
dmcdaniel:  Please post the outputs of
```
ls -l /media
```
and
```
ls -l /media/intouch
```

---

### Post by dmcdaniel on 2009-09-01
ls -l /media

```
total 2052
lrwxrwxrwx  1 root root     6 2008-12-09 15:39 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-12-09 15:39 cdrom0
drwxrwxr-x  6  513   515    0 2009-08-28 12:02 intouch
drwxrwxrwx 14  500 users    0 2009-09-01 12:40 shared

```


ls -l /media/intouch

```
total 43008
-rwxrwxr-x 1 513 515  3002074 2009-08-31 23:37 accounts.txt
-rwxrwxr-x 1 501 503  5341982 2009-08-28 11:42 acctdtl.txt
-rwxrwxr-x 1 501 503  3420262 2009-07-27 08:47 allinvoices-Old.txt
-rwxrwxr-x 1 501 503  3126147 2009-08-24 21:54 allinvoices.txt
drwxrwxr-x 2 513 515        0 2009-09-01 01:54 backup
-rwxrwxr-x 1 513 515  6764025 2009-08-31 23:37 handles.txt
-rwxrwxr-x 1 513 515 12999915 2009-08-31 23:37 handmast.txt
drwxrwxr-x 2 513 515        0 2006-05-26 08:51 intouch
drwxrwxr-x 9 513 515        0 2005-12-13 07:38 IntouchBu-Old
drwxrwxr-x 2 513 515        0 2007-09-28 10:34 MaxData
-rwxrwxr-x 1 502 511   415232 2009-08-28 12:06 QA_Form.doc
-rwxrwxr-x 1 513 515   651110 2009-08-31 23:37 tele.txt

```

---

### Post by Zill on 2009-09-01
dmcdaniel:  Well, I think I can see what is happening but I am not quite sure how to resolve it!

When you run "ls -l" this shows the owner and the group for each file/directory.  As you can see, the cdrom (correctly!) belongs to the user and group root.  However, your directory "intouch" belongs to the user 513 and the group 515.  As your PC should normally display the *name* of the user and group (not the UID/GID numbers), this means that they are not listed in your system.

If you type the following two commands you should see all your users and groups listed:
```
cat /etc/passwd
cat /etc/group
```
Against each name in /etc/passwd you will see two numbers; the first is the User ID (UID) and the second is the Group ID (GID).
It seems that your user 513 and the group 515 are not in this list!

You could edit the files /etc/passwd and /etc/group to ensure that your required user(s) are in the lists.  However, I do not understand how this situation has arisen, or if you intended this.

The reason you could not change the permissions is, I believe, due to the "curious" ownership of the directory "intouch".  You should be able to change this with the chown command, but you will first have to decide who *should* own the directory: root or a named user?  Once the ownership has been established then the owner (root or a named user) should be able to change the permissions as required.  If the file is owned by root then, of course, changes should be made with the sudo prefix.

A further confusion is apparent by your second "ls -l", which shows that the ownership of files *within* the directory "intouch" is also inconsistent as they are also owned by different UID/GID numbers, rather than *real* user names.

I hope this helps clarify what has happened but we need some more input from you as to where these mysterious un-named users have come from!  If you intended to work with UID/GIDs rather than names then please advise.

ps. Regarding your original post, it is clear that UID 513 and GID 515 both *do* have write access to the "intouch" directory (and *some* files within it)!  I suspect that the real matter is to define "who" you want to have write access. ;-)

---

### Post by dmcdaniel on 2009-09-02
Zill,

Maybe if I explain my network set-up. 

We have a PDC (Windows based) that has all of our users on a network

We then have a Samba Server that these files are attached too

I browsed my network using Ubuntu and put in my network password to connect to the server and mounted the drive to Ubuntu. I then used a command to link it as a file system so I could use it in my Virtual Box OSE. 

Do you think I need to add the user agent to my PDC?

---

### Post by Zill on 2009-09-02
dmcdaniel:  Thanks for the clarification.  However, I abandoned Windows years ago so can't really go much further with specific help.

As certain users and groups *do* appear to have write access to your "intouch" directory it does seem that the problem relates to the user/group IDs.  When mounting directories in a Linux network I always ensure that the user names and IDs on server and clients match up.  This eliminates many problems at source!

I would *guess* that a Samba setup including Windows PCs will also require similar ID matching.  Hopefully others will now be able to help with this one. :-)

So, are there any Samba gurus reading this thread???

---

