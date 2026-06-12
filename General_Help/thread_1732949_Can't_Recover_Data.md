---
title: "Can't Recover Data?"
date: 2011-04-18
forum: General Help
---

### Post by ken0069 on 2011-04-18
Dual boot system with Windows XP and Ubuntu 9.xx on different drives.  Ubuntu was updated via internet last week to 10.04 because of some "minor" problems.  Then I got another problem in that I had the windows drive in two different partitions and with Ubuntu 9.xx it was setup to auto mount those windows partitions at boot.  The upgrade to 10.04 broke that and while I was trying to fix that I've managed to hork up Ubuntu to where it won't boot past the splash screen?  Just sits there with the dots going from left to right continuously.  

That Ubuntu load has 6.6GB of data in the downloads folder that I'd like to save but every time I try to recover it I get the "you don't have permission" crap.  I've booted with Ubuntu live version, I can see those files but they've got a lock on them and I'm not able to figure out how to unlock them so I can transfer them to one of those windows partitions before I reload with 10.10?

Can someone point me to a step by step method of saving that data to either another internal drive or an external USB flash drive?

Thanks,

Ken

---

### Post by TeoBigusGeekus on 2011-04-18
Have you tried 
```
gksu nautilus
```
from the live cd?

---

### Post by ken0069 on 2011-04-18
> **TeoBigusGeekus said:**
> Have you tried 
```
gksu nautilus
```from the live cd?

No I haven't.  What is that suppose to do?

---

### Post by ken0069 on 2011-04-18
OK so the nautilus thingie didn't work either and looks like no one else seems to have any suggestions that I can use so far so how about this one.

What if I go ahead and install
 10.10 on another hard drive with updates and all the samba and network sharing stuff.  Will I be able to access my data from the old ubuntu drive then?  I got to have that data as there's some critical backups for my forum there!

Anyone??

Thanks,


ken

---

### Post by fatherted on 2011-04-19
It sounds like just a permissions issue? 

If you open up Terminal and navigate to the directory in question, see who actually owns the files and what the file permissions are. Note that for some of the below commands you might need to use sudo depending on who now owns the directory. 

```
cd /path/to/files (probably /home/username/Downloads)

ls -lha 
```

You should see several columns of information like so: 

```

drwxr-xr-x  3 user user 4.0K 2011-04-14 19:35 .
drwxr-xr-x 33 user user 4.0K 2011-04-18 21:06 ..
drwxr-xr-x  3 user user 4.0K 2011-04-14 19:37 dd_rhelp-0.1.2
-rw-r--r--  1 root root 2.3M 2011-04-18 22:43 wholedisk.log

```

The leftmost columns are the read/write/execute permissions on the files, and there are three sets of three attributes - owner's ability to r/w/x, group members' ability to r/w/x, and everyone else's ability to r/w/x. If you don't see at least "r" in the first column, you won't be able to read the files. 

The third and fourth columns are the username of the owner and the name of the group that user is part of. In most cases in Ubuntu they're the same for user files.  Fifth column is size, then date created, then file name. 

So, a couple things to try:  

If your files are not owned by your username, you won't be able to do much with 'em.  Find out what groups you're part of by typing, from the terminal, "groups".  At least one of the things that's printed should match the "groups" column on the directory listing. 

Change user and group ownership using: 

chown username:groupname ./filename

So if I wanted to take ownership of the "wholedisk.log" file as above, I'd have to type (sudo is needed because files are not owned by me): 

chown user:user ./wholedisk.log

Then, to make sure I can read, write, and execute the files, I'd do: 

chmod 744 ./wholedisk.log

This would make the file read/write/execute for me (the owner), and read-only for everyone else. 

Hope that helps, I'm just guessing as to what the trouble might be.

---

### Post by ken0069 on 2011-04-19
To simplify things somewhat, I'm going to do a fresh install on another drive using 10.10 and I'll use the exact same username and password so question is, if that nonbootable drive is also connected to the same computer, will my permissions on the new software load also be the same on that other drive?  If they are then I should be able to copy those files without any problems, yes/no?

I'm not much of a command line person as I'm a partial Windows convert.  

Thanks,

Ken

---

### Post by oldfred on 2011-04-19
It still depends on how you mount it. 

And if the gksu Nautilus did not work you may have other issues. gksu made you root so you can do anything, which should always work.

More info:
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ken0069 on 2011-04-19
SOLVED

First I want to thank those who tried to help.  I'm not a noob but I'm not nor do I want to be a linux guru either.  Linux is a tool that I use mainly because of its security and I do NOTHING online with a Windows computer that I want to be secure!  

Second, there is joy in mudville today.  I installed 10.10 on another drive then connected that nonbootable drive and copied those files off with zero problems.  I guess using the same username and password helped.  

Thanks again,

Ken

---

