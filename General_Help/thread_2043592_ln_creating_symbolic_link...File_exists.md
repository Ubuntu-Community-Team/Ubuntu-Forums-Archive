---
title: "ln: creating symbolic link...File exists"
date: 2012-08-16
forum: General Help
---

### Post by Ballzac on 2012-08-16
Hi,

I'm using Ubuntu Server 10.04. I have two drives that have the same type of content, and I want to be able to view all the files in one directory.

The most logical way would be to use raid array, but I don't have enough free space at the moment to store the data while I set up the array, so I need a different option.

The next best option seemed to me to be using symbolic links. I have my two drives mounted at locations that look like this:

```
/home/username/Drives/Drive1
/home/username/Drives/Drive2
```

each drive contains multiple files and folders.

I've changed the names for readability, but basically I did

```

sudo mkdir /home/username/content
cd /home/username/content
sudo ln -s /home/username/Drives/Drive1/*
sudo ln -s /home/username/Drives/Drive2/*
```

The thing is that only a link for the contents of Drive2 (currently only one folder and its subdirectories). I cannot see the content from Drive1 when I ls inside /home/username/content.

I tried running

```
sudo ln -s /home/username/Drives/Drive1/*
```

again, but I get

```
ln: creating symbolic link `/home/username/Drives/Drive1/path/to/file': File exists

```

for every "path/to/file" on Drive1.

so it looks like the links have been created, but I can't see them with ls. Nor can I remove them using rm, because they aren't detected. Just wondering if anyone has any ideas what's going on with this.

Also, this is not an ideal way of doing it because if I add a file or directory to Drive1 or Drive2, I will have to create a new link every time. So if anyone has any suggestions of how to achieve what I want without using RAID, that would be appreciated, but mainly I'm interested in solving this problem with the links not showing up. Cheers :)

---

### Post by oldfred on 2012-08-17
You cannot link two folders with the same name into the same place.

My links show up ok

```
fred@fred-Precise:~$ ls -l
total 3128
drwxr-xr-x 2 root root    4096 Jun 14 13:08 bin
-rw------- 1 fred fred 1290151 Jul 20 14:38 bookmarks.html
-rwxrwxr-x 1 fred fred  113072 Dec 21  2011 bootinfoscript
-rw-rw-r-- 1 fred fred    3590 Apr 20 15:50 bug.crash
drwxrwxr-x 4 fred fred    4096 Jul 19 23:24 Calibre Library
drwxr-xr-x 2 fred fred    4096 Apr 18 15:48 Desktop
lrwxrwxrwx 1 root root      19 Mar 24 15:23 Documents -> /mnt/data/Documents
lrwxrwxrwx 1 root root      19 Mar 24 15:23 Downloads -> /mnt/data/Downloads
lrwxrwxrwx 1 root root      23 Mar 24 15:23 eclipsetrader -> /mnt/data/eclipsetrader

```

I use this to link all my folders, but I use the same names for many as the default install, so I have to delete those folders first.

I use this to mount all my folders, it does give an error if I rerun it on all the one's that already exist, but does not do anything other than give the error.
for i in `echo /mnt/data/*`;do ln -s $i; done

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Ballzac on 2012-08-17
Thanks for your reply.

> You cannot link two folders with the same name into the same place.

I don't think this could be the issue, because there is nothing on Drive1 with the same name as anything on Drive2.

Though I did make a mistake with what I posted above. It is more of the form

```
sudo mkdir /home/username/content
cd /home/username/content
sudo ln -s /home/username/Drives/Drive1/content/*
sudo ln -s /home/username/Drives/Drive2/content/*
```
so there *is* a folder (content) on each drive with the same name, but I'm linking to the *contents* of those two folders, and there are no directories or files of the same name in those two locations.

I realised that there is a lost+found directory on both, and have deleted them to see if that helps, but it didn't I tried using
```
sudo ln -sf /home/username/Drives/Drive1/content/*
```
to overcome the error that says they already exist, but it's not helping. I just don't understand why the links would not be visible if they are there.

Thanks for providing those links, but from what I can tell, they all cover using separate partitions for separate folders, whereas I want every link to show up as though they are dirs and files in a single folder.

---

### Post by diesch on 2012-08-17
The commands doesn't do what you expect if there's more than one file or folder in a  drive.

If you do something like 
```
ln -s *
```the "*" first gets expanded by the shell.

If "*" only expands to just one file the shell runs
```
ln -s name1
``` which means "Create a symlink pointing to *name1* in the current working folder." - which is fine.

But if the "*" expands to more than one file the shell actually runs something like
```
ln -s name1 name2 name3
```That means "Create symlinks pointing to *name1*, *name2* in folder *name3*" - which is not what you want.

To create all the symlinks in the current folder use
```
ln -s * .
```

---

### Post by Ballzac on 2012-08-17
Oh wow, that explains it. Thanks for the info.

So if I'm in the directory that I want the links in, can I just type

```
sudo ln -s /home/username/Drives/Drive1/content/* .
```

to make a link for each file and directory in /home/username/Drives/Drive1/content ?

Otherwise, if I navigate to /home/username/Drives/Drive1/content
is there something similar to
```
ln -s * .
```
that I can run to cause the links to be made in
/home/username/content

?

Thanks for your help :)


EDIT: Just tried the first option and it worked fine. Thanks again for your help. I don't think I would have ever worked that out by myself :)

---

### Post by diesch on 2012-08-17
You just have to give the target folder as the last option to *ln*.

So if you want to symlink the files from the current folder into */home/username/content/* use

```
ln -s * /home/username/content/
```

---

### Post by Ballzac on 2012-08-17
> **diesch said:**
> You just have to give the target folder as the last option to *ln*.

So if you want to symlink the files from the current folder into */home/username/content/* use

```
ln -s * /home/username/content/
```

Okay, thanks. Just one last question...

I would preferably like to write a shell script to do this, which means I wouldn't want to have to be in a particular folder. I'm sure there would be a way to do this with a for loop, but is it possible to do it in a single line with something like

```
ln -s /home/username/Drives/Drive1/content/* . /home/username/content/
```

I'm assuming, based on your example, that this would work. But everything I've read says that the last option has to be the name of the *link* itself, which I don't know until the wildcard (*) find the name of the source. So what I'm guessing you're saying is that using the path to the directory *ending in a forward slash* will create the names of the links themselves inside that directory?

Also, I noticed that, in your last example, you didn't include the period (.) Was that an oversight, or is there something I'm missing?

Cheers :)

---

### Post by diesch on 2012-08-17
What do you want the shell script to do?

---

### Post by Ballzac on 2012-08-17
> **diesch said:**
> What do you want the shell script to do?

Just to automate this process. I have 8 drives in this server, and will probably add more at a later date. So let's say at some point I have two types of content, so I create a folder for each, then maybe I want one of them to have links to the contents of 3 different drives, and the other to have links to five of them, then I have to manually add the links every time I add new files to any of the eight drives. If I had a script that would automate all this, then I could even set it as a cron job so that it periodically creates the links and I don't actually have to do anything.

---

