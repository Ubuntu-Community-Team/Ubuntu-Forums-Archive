---
title: "Urgent: Do not have permission to save file"
date: 2010-07-08
forum: General Help
---

### Post by Robbyx on 2010-07-08
I downloaded a government form in pdf. It had a note in it indicating that to save it I should press CTRL -S (or save as). When I try to save the file from with Acrobat 9 a box pops up stating "The document could not be saved. You do not have permission to write to this  file."

The permissions show the file  User and group as Root with read/write / execute ticked for owner, group, other users.

I am logged in as Robin and group: rob.

Using sudo mode I tried to change the owner and group to Robin / rob. The response is that it is an invalid user. 

It seems that all my documents are root/ root.

I need to save the pdf and do not know how to do it. Any ideas please?

---

### Post by mikewhatever on 2010-07-08
It looks like either the downloading program or Acroread was run as root, which made the downloaded file owned by root. Run the chown command again and post the output.

---

### Post by dabl on 2010-07-08
> **Robbyx said:**
> I downloaded a government form in pdf.

Downloaded how? Were you logged in as "robin" at the time?

> 
 It had a note in it indicating that to save it I should press CTRL -S (or save as). 

Since when would you pay attention to what the downloaded doc says about how to save it?  If you already downloaded it, then it _is_ saved already.

> 

When I try to save the file from with Acrobat 9 it says I do not have permission to save the file.



You are running Acrobat 9 with Ubuntu?  Interesting!  :)


> 

The permissions show the file  User and group as Root with read/write / execute ticked for owner, group, other users.



The only way the files could be saved with root permissions, on a Linux system, is if root saved it, or Robin saved it using "sudo".


>  

It seems that all my documents are root/ root.



Sounds like a very hosed-up Ubuntu system.  The user will be able to read them, but never modify them, unless and until the permissions are all changed to the user.

Are you trying to work between Windows and Ubuntu?  Do you understand that _every_ Windows user is "root" as far as that OS is concerned?

---

### Post by Robbyx on 2010-07-08
> **mikewhatever said:**
> It looks like either the downloading program or Acroread was run as root, which made the downloaded file owned by root. Run the chown command again and post the output.

Could you please give me the syntax for chown. I have been looking at the permissions via a file manager.

---

### Post by kiddykoff on 2010-07-08
```
chown robin:rob file.pdf
```

run that, but your post seems odd. Why are you running adobe in ubuntu are you using WINE?

why would you need to save it again if it's already open?

why!!!! heheh

i should say that "file.pdf" is the file that is in question as well as whatever directory it's in.

---

### Post by Robbyx on 2010-07-08
> **dabl said:**
> Downloaded how? Were you logged in as "robin" at the time?



Since when would you pay attention to what the downloaded doc says about how to save it?  If you already downloaded it, then it _is_ saved already.

It is a tax return form and I need to save the form with the information in it. I can not save or save  as the file.

> The only way the files could be saved with root permissions, on a Linux system, is if root saved it, or Robin saved it using "sudo".

I saved it the normal way via a download from the website. I was not in sudo or root. To me that makes it strange that I can not save the file under any user name. The file is called CT600(SECURED).pdf


> Sounds like a very hosed-up Ubuntu system.  The user will be able to read them, but never modify them, unless and until the permissions are all changed to the user.

Note that the permissions are that everyone can read, write and execute the files even though the owner is root.

> Are you trying to work between Windows and Ubuntu?  Do you understand that _every_ Windows user is "root" as far as that OS is concerned?


Not really. I do occassionaly use Virtualbox but I was not accessing the downloaded file through VB. I downloaded it via Firefox and using Nautilus opened the file using Acrobat.

I have noticed that my PCman file manager will not open subdirectories unless I have changed the user to super user. I may have to do that for each subdirectory.

Robin

---

### Post by Robbyx on 2010-07-08
> > **kiddykoff said:**
> ```
chown robin:rob file.pdf
```

I get invalid user : 'robin:rob' I also tried Robin:rob with same effect.

[QUOTE]run that, but your post seems odd. Why are you running adobe in ubuntu are you using WINE?

I am not using wine to run adobe reader 9.

> why would you need to save it again if it's already open?

Because it is a form.

> i should say that "file.pdf" is the file that is in question as well as whatever directory it's in.

I ran terminal from the directory containing the file.

Robin

---

### Post by NCLI on 2010-07-08
STOP.

You are complicating a very simple problem. The file is most likely saved in /tmp, the place where temporary files go, owned by root. This is where Firefox saves files when you use the "Open with" option.

Simply do what the program suggests, and use Save As to save it to your home folder.

---

### Post by Robbyx on 2010-07-08
> **NCLI said:**
> STOP.

You are complicating a very simple problem. The file is most likely saved in /tmp, the place where temporary files go, owned by root. This is where Firefox saves files when you use the "Open with" option.

Simply do what the program suggests, and use Save As to save it to your home folder.

When  I downloaded the file I used the my documents area that I use for all my files. This area is on a separate HD and is not tmp. It is accessed through media.

Although I have the file open I can not save it either via save as or Ctrl S.


Robin

---

### Post by mikewhatever on 2010-07-08
Try saving the file to your home folder for now. If needed, you can later move it you whatever documents area you wish.
The syntax for chown is as follows:
sudo chown user:group /some-file

If you don't know your user and group, run the **whoami** command.

---

### Post by Robbyx on 2010-07-08
> QUOTE=mikewhatever;9565163]Try saving the file to your home folder for now. If needed, you can later move it you whatever documents area you wish.

That worked. 

Should I be thinking about changing the owner of my data files?


> The syntax for chown is as follows:
sudo chown user:group /some-file

If you don't know your user and group, run the **whoami** command.

Whoami is showing user rob but not a group.

---

### Post by mikewhatever on 2010-07-08
> **Robbyx said:**
> That worked. 

Should I be thinking about changing the owner of my data files?
Possibly. It's far from optimal to have your files owned by another user.

> Whoami is showing user rob but not a group.
By default, the group should be the same as the user, unless you had changed it.

---

### Post by Ibidem on 2010-07-08
First, I think you've solved the core problem.  I'd try changing the way the external drive is mounted.
Second, if you want to know what group you're in:
Try
```

id   #Gives you a big list of groups, etc. that you're in.

```
Look for "gid=<number>(group)"; the part in parentheses is your group.

Is the hard drive internal or external?  It sounds like a FAT/NTFS external drive, or some such thing.

---

### Post by Robbyx on 2010-07-09
> Ibidem First, I think you've solved the core problem.  I'd try changing the way the external drive is mounted.
It is solved but in a very temporary fashion because I can not keep saving files to the home directory. I would like to resolve the saving of files to the my docs directory.


> Second, if you want to know what group you're in:
Try
```

id   #Gives you a big list of groups, etc. that you're in.

```
Look for "gid=<number>(group)"; the part in parentheses is your group.
The group is rob.
I looked at the user groups and found that there is a user rob with one member Robin.

If I try to change a file owner from root/ root to Robin/ rob I get an error message Invalid User.




> Is the hard drive internal or external?  It sounds like a FAT/NTFS external drive, or some such thing.

Internal: NTFS 3Ware Linux Raid.

---

### Post by Robbyx on 2010-07-09
Thank you all for your help so far. I was able to work with the pdf and submit the returns in time today. 

I would now like to sort out my files. Most programs will allow me to save to the my docs directory. Adobe Reader is picking up some restraints that other programs are ignoring. The same applies to pcman and nautilus, both will not let me drill down to subdirectories within the my doc area.

I think the answer is to change the owner to my normal login user name but when I try to change the file permissions the user and group is not being recognised as valid. Is there a way forward?

---

### Post by Rawrmage on 2010-07-09
I think that there is some confusion about your "normal login username" and your actual username. If the output of whoami is rob, that should be your actual username, so you would chown to rob:rob. I log in as Ryan, but my username is rawr, and my prompt is "rawr@popcorn:~$ ".
When you open up the terminal, what is the prompt (the text before the cursor) ?

---

### Post by Robbyx on 2010-07-09
> **Rawrmage said:**
> I think that there is some confusion about your "normal login username" and your actual username. If the output of whoami is rob, that should be your actual username, so you would chown to rob:rob. I log in as Ryan, but my username is rawr, and my prompt is "rawr@popcorn:~$ ".
When you open up the terminal, what is the prompt (the text before the cursor) ?

This is the prompt

rob@rob-desktop

I do not get an error message when I change the owner and group using sudo chown rob:rob  Directory name. When I look at the file and directory properties they are not changing. They still remain as root root.

I have also tried su nautilus and this gives me options to change the owner but none of them are rob. There is a rob - Robin. When I try to change the user from within nautilus it immediately reverts to root. Same problem with changing the group.

---

### Post by mikewhatever on 2010-07-09
To chown a directory with everything inside, use the recursive flag, -R.
```
sudo chown -R rob:rob /directory
```

---

### Post by Robbyx on 2010-07-09
> **mikewhatever said:**
> To chown a directory with everything inside, use the recursive flag, -R.
```
sudo chown -R rob:rob /directory
```

Although I do not get an error message it does not change the permissions. The owner stays as root and the group as root.

This is the entry in fstab:

```
UUID=724E07853D78E7A8  /media/mydocs  ntfs         user,rw,auto,exec,nls=utf8,unmask=007  0  2  
```

I assume it has nothing to do with the inability to change the owner.

---

### Post by mikewhatever on 2010-07-10
Right, so what's the output of **mount** then?

---

### Post by Robbyx on 2010-07-10
> **mikewhatever said:**
> Right, so what's the output of **mount** then?

Looking at the particular partition I can not see any reason why I can not change the owner of a directory or file. I tried to check if mode =0755 was a cause, but could not find a reference explaining it.  Assuming you agree the mount is not the problem, where else should I look?

```
rob@rob-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdc1 on /media/mydocs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/g type reiserfs (rw,noexec,nosuid,nodev,noatime,notail)
/dev/sda6 on /media/video type reiserfs (rw,noexec,nosuid,nodev,noatime,notail)
/dev/sda2 on /home type ext3 (rw,nosuid,nodev,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rob)
/dev/sdb5 on /media/7C8E-F0C6 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1 on /media/5C84-AE54 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```

---

### Post by mikewhatever on 2010-07-10
What if you just chown the files and not the mount point?
```
sudo chown -R rob:rob /media/mydocs/*
```

---

### Post by Robbyx on 2010-07-10
> **mikewhatever said:**
> What if you just chown the files and not the mount point?
```
sudo chown -R rob:rob /media/mydocs/*
```

```
rob@rob-desktop:~$ sudo chown -R rob:rob /media/mydocs/*
[sudo] password for rob: 
chown: changing ownership of `/media/mydocs/FFprofile/4tl537wk.default/SDold/thumbnail-24-1255220006530.png': Input/output error
rob@rob-desktop:~$ 

```

I have looked for the thumbnail and it is not in the location mentioned in the error message.

Should I try check filesystem and repair (in disk utility)? Will it work on a raid drive?

---

### Post by mikewhatever on 2010-07-10
That's odd indeed. Are you saying there is no Firefox profile there at all? Anyway, if that was the only error, then the rest of the files may have been changed. I don't know if checking the file system is the way to go. No experience with raids here.

---

### Post by Robbyx on 2010-07-10
> **mikewhatever said:**
> That's odd indeed. Are you saying there is no Firefox profile there at all? Anyway, if that was the only error, then the rest of the files may have been changed. I don't know if checking the file system is the way to go. No experience with raids here.

The firefox profile is there, but that thumbnail is not.

I have looked at the file permissions using nautilus and they are still set to root root!

---

