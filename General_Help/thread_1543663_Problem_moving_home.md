---
title: "Problem moving /home"
date: 2010-08-01
forum: General Help
---

### Post by TXpaniolo on 2010-08-01
New user.  Tried to move /home following the community guide at [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)  all commands seem to have worked.  At the point in the guide "Checking Copying Worked" I went to the new home but it is a blank structure, like a new install, without any of my existing data there.  

After the steps in the guide failed I tried doing another sudo rsync -aS /home/. /media/home.  (media home was defined by putting the UUID of sda7 into FStab as directed in the community guide, and mounted) and got the following error:
[INDENT] rsync: readlink_stat("/home/ubuntu/.gvfs") failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]
[/INDENT]Ubuntu 10.04 installed from LiveCD.  I repartitioned the hard drive sda  from LiveCD with everything as ext4 and sda1 primary with /, then the  others set up as extended logical; sda5 3gb swap, sda6 10gb for new  installs, and the rest 400+gb as /home on sda7.  

I am wondering if setting up multiple users is part of my problem?  I set up a system:admin user with adminstrator privileges and a user david:david with more limited access.  Obviously, I would like to move both /home/admin and /home/david to the new /home partition.  I have noticed that admin did not have access to david's files like I expected.  Ubuntu would tell me I did not have permission on some file activities, which I was going to research later.

---

### Post by oldfred on 2010-08-01
Welcome to the forums.

the instructions do say this:
The --exclude='/*/.gvfs' prevents rsync from complaining about not being able to copy .gvfs, but I believe it optional. 

To set permissions & ownership see this which also has help on another common problem related to dmrc errors.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by TXpaniolo on 2010-08-01
Hi OldFred, Thank you for the welcome and the help!

The first time I did it I did do the exclude, when that seemed to fail I didn't put the exclude in the 2nd time.

SOLVED!  But in going over your advice and the instructions again I saw what I was doing wrong!  After I used LiveCD to repartition I never booted back up from the HD!  So the whole time I was running in LiveCD ... thats the reason the new /home I was trying to set up looked like a new install ... duh #-o  I'm going to blame it on lack of sleep last night at 1am.

So I rebooted from HD with my new partitions and everything went smooth with moving my home directory to the new partition.

However, I did notice something while editing FStab with the UUID of the new /home partition.  Namely that FSTab identified Swap with the UUID from the initial install.  Now that I have repartitioned, the UUID of the Swap partition has changed.  Should I update FStab with the current UUID of the Swap partition?

Now on to permissions to figure out how my admin user can change/delete user files.

---

### Post by oldfred on 2010-08-01
You are not using swap if the UUID changed. Some say you do not need swap if you have lots of memory so system may work without it. But if you want to hibernate you have to have swap and it is good to have just incase. After any changes to fstab always run this. If it just returns you to the terminal is is ok, or it will give error messages from your fstab.

```
sudo mount -a
```I do not know much about sharing as I only boot as me and my wife uses it as such. But I did save these links.

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

---

### Post by TXpaniolo on 2010-08-01
OK, I revised the UUID for swap to the repartitioned value and did a
```
sudo mount -a
```
Nothing came back so I guess that's good.

Thank you for your help OldFred, and I will check out those links on sharing.

David

---

