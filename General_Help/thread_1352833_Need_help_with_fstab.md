---
title: "Need help with fstab"
date: 2009-12-12
forum: General Help
---

### Post by Uubnewb on 2009-12-12
Ever since I installed Ubuntu 9.10 I'm having trouble with my hard drives.  

My two external drives only mount for the first user to log on, any users after that cannot mount them.  It does not matter which (of the two) accounts I log into first, the second one cannot access the external drives.

Furthermore, one of my internal drives (NTFS) will not mount at all.  When I go to Places I can see it on the left-hand pane, but when I want to access it I get the following error:
```
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/500GB
```

I thought it might be my fstab file that is not configured correctly, but when I opened the fstab file I couldn't understand it at all (I never had to edit the fstab file before).  Can anyone please help me with this?

My fstab file presently looks like this:
```
UUID=bd66edb0-c606-424e-b23a-96d27c3f4e54 swap swap sw 0 0
UUID=2a01b475-a4e8-4190-99a1-592dfded8d8a / ext4 defaults 0 1
UUID=4CA0099DA0098EA0 /media/500GB ntfs-3g noauto 0 0
```

---

### Post by Primefalcon on 2009-12-12
please show the output of 

```
ls -l /etc/fstab
```

---

### Post by Uubnewb on 2009-12-12
I hope I did this right:
```
***@***:~$ ls -l /etc/fstab
-rw-r--r-- 1 root root 173 2009-12-12 10:35 /etc/fstab
```

---

### Post by Primefalcon on 2009-12-12
> **Uubnewb said:**
> I hope I did this right:
```
***@***:~$ ls -l /etc/fstab
-rw-r--r-- 1 root root 173 2009-12-12 10:35 /etc/fstab
```

ok that's correct, go to system -> admin -> users and groups, check the user properties under privledges and make sure the options to access external file systems is active

did you add the entry to your fstab file to automount? if so can you show us the contents of your fstab file?

you can open it by using

```
gksudo gedit /etc/fstab
```

---

### Post by Primefalcon on 2009-12-12
OK try this, first backup your fstab file by using the following command
```
sudo cp --preserve /etc/fstab /etc/fstab-backup
```


then try replacing this line
```
UUID=4CA0099DA0098EA0 /media/500GB ntfs-3g noauto 0 0
```

with this
```
UUID=4CA0099DA0098EA0 /media/500GB  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```

reboot see how things go

---

### Post by Uubnewb on 2009-12-12
OK, the "Access external devices" box was allready checked.  I'm changing the fstab file now.  Will let you know as soon I've restarted.

Thanks for the help so far.

---

### Post by Primefalcon on 2009-12-12
> **Uubnewb said:**
> OK, the "Access external devices" box was allready checked.  I'm changing the fstab file now.  Will let you know as soon I've restarted.

Thanks for the help so far.

Okey dokey

---

### Post by Uubnewb on 2009-12-12
I tried those fstab settings two times, once like this:
```
UUID=4CA0099DA0098EA0 /media/500GB  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```
and once like this:
```
UUID=4CA0099DA0098EA0 /media/500GB ntfs defaults,nls=utf8,umask=007,gid=46 0 0
```

Unfortunately I still cannot access my 500GB drive, I still get the same error.

---

### Post by Primefalcon on 2009-12-12
> **Uubnewb said:**
> I tried those fstab settings two times, once like this:
```
UUID=4CA0099DA0098EA0 /media/500GB  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```
and once like this:
```
UUID=4CA0099DA0098EA0 /media/500GB ntfs defaults,nls=utf8,umask=007,gid=46 0 0
```

Unfortunately I still cannot access my 500GB drive, I still get the same error.
Ok lets just do baby steps here when you first set this up you created a folder right for this at /media/500GB so lets just take a looksey at that

```
ls -l /media | grep 500GB
```

---

### Post by Uubnewb on 2009-12-12
I guess I should also mention how I want my hard drives to be mounted (just for clearance sake).

Like I said earlier, I have two accounts on this computer.  On one account I want all the drives mounted with read/write privileges.  On the other account I want to mount only the external drives (only read access, no write access) together with the CD-Drive.

I don't know if this information will be of much use though.

---

### Post by Uubnewb on 2009-12-12
When I use that command I don't seem to get any response:
```
####@####:~$ ls -l /media | grep 500GB
####@####:~$ 
```

---

### Post by Primefalcon on 2009-12-12
> **Uubnewb said:**
> When I use that command I don't seem to get any response:
```
####@####:~$ ls -l /media | grep 500GB
####@####:~$ 
```
hmmm

```
ls -l /media
```

---

### Post by Uubnewb on 2009-12-12
Using ```
ls -l /media
```
This is what I get:
```
####@####:~$ ls -l /media
total 38
drwx------ 10 user1 user1 16384 1970-01-01 02:00 6A7E-67A8
lrwxrwxrwx  1 root   root       6 2009-11-05 19:10 cdrom -> cdrom0
drwxr-xr-x  2 root   root    4096 2009-11-05 19:10 cdrom0
lrwxrwxrwx  1 root   root       7 2009-11-05 19:10 floppy -> floppy0
drwxr-xr-x  2 root   root    4096 2009-11-05 19:10 floppy0
drwx------  1 user1 user1  4096 2009-12-12 08:44 FreeAgent Drive
drwx------  1 user1 user1  8192 2009-12-11 19:52 FreeAgent Drive_
dr-x------  1 user1 user1  2048 2009-09-01 14:05 Gala 09
```

---

### Post by Primefalcon on 2009-12-12
ok I think we have it, I'll just explain this a little ok

UUID=4CA0099DA0098EA0 /media/500GB

this command is saying take the drive with this ID 4CA0099DA0098EA0 and mount it to the folder /media/500GB, the problem is there is no folder at that location, so let's create one ok

```
sudo mkdir /media/500GB
```

then reboot and see how it goes, you might have to change fstab back to how I told you to have that entry but let's see how that goes ok

---

### Post by Uubnewb on 2009-12-12
Once again, I don't know if this will help, but here is a screenshot of my /media directory (attachment).

---

### Post by Uubnewb on 2009-12-12
OK, I'll do that now, and let you know as soon as I'm logged in again.

---

### Post by Primefalcon on 2009-12-12
> **Uubnewb said:**
> Once again, I don't know if this will help, but here is a screenshot of my /media directory (attachment).
I got that info and more from the ls -l /media ;-)

---

### Post by Uubnewb on 2009-12-12
It worked!  And I didn't even have to restart!  Thank you so much, you've been a wonderful help!  :D

:popcorn:    :popcorn:   :popcorn:

---

### Post by Uubnewb on 2009-12-12
Ah, ok.  I'm still doing most of my work in windows, so using the GUI is still much easier for me to understand.

---

### Post by Primefalcon on 2009-12-12
> **Uubnewb said:**
> It worked!  And I didn't even have to restart!  Thank you so much, you've been a wonderful help!  :D

:popcorn:    :popcorn:   :popcorn:
Your welcome as for the permissions you asked about, you have to handle that with user group and other permissions

basically you choose what permissions you want your account to have, you create a special group (if want one) and give them a seperate set of permissions and then you have others, which you can then give well again permissions for..... I probaly made that sound complicated... it's not though......

you can assign permissions for folders by right clicking folders and setting the permissions there, you can also create groups and add people to those groups under system -> admin -> users and groups

after you've created a group and added what users you want to that group you can choose that group in a folders right click under permissions and group.

of course its quicker with the command line , but that's the gui way for ya ;-)

---

### Post by Uubnewb on 2009-12-12
OK, so I played around with the "Users and Groups" settings, and I tried setting up the permissions.  However, I was not very successful; here is what I have so far:

User1 (administrator)
User2 (unprivileged user)

I created a group called unprivileged and put User2 in that group.  Then I changed the privileges of User2 as can be seen in the attachment.  However, my 500GB drive still mount when User2 logs in.

Oh, and as far as using the terminal goes, please don't stop giving those commands, it's the best way for me to learn in the process. :)

---

### Post by Uubnewb on 2009-12-12
Sorry, I forgot the attachment.

---

### Post by Primefalcon on 2009-12-12
NTFS doesn't store permissions, however you may be able to change the permissions of the mount point itself which is kinda what you want to do anyhow.

do this

go to system -> admin -> users and groups

click the key icon to gain admin powers and enter your password then hit authenticate

select manage groups then add group

as for group name I don't know just enter 500gb_group and tick your user name in the list below that and hit ok

once you've done that enter the following command, (be very careful you are now working with root powers, so be careful)

```
gksudo nautilus /media
```

right click the folder 500GB,and select properties in the group bit click the tab and enter the 500gb_group that you just created and ten give that group the ability to create and delete files as well as read and write in the box just below that..........

now in others well folder access none and file access none

that may do it

---

### Post by Uubnewb on 2009-12-14
Sorry for taking so long to reply.

When I right-click on the 500GB directory and go to properties, the only place I can type anything is in the *Name* area and under the *Notes* tab.

I did find a workaround for part of my problem, but it's far from ideal:  I deleted the /media/500GB directory and created a new one in /home/user_name/500GB.  Then I switched the fstab command to "noauto" so that it doesn't mount at start-up.  Now I just have to mount the hard drive with a sudo command when I need it:
```
sudo mount /dev/sda1 /home/user_name/500GB
```

Like I said: hardly ideal, but it's doing the job for now. :)

My biggest problem at the moment is the two external drives.  Like I said earlier, they only mount with the first user to log in.  This means that I have to do a complete restart when I want to mount them on the other account.

Do you think it could be with my installation that something went wrong?  I wouldn't mind re-installing Ubuntu if there is a chance that it might fix the problem.

I remember in Ubuntu 8.10 it was simple.  When creating a user, I just had to select "unprivileged user" and everything was set up nicely.  If push comes to shove I could always go back to 8.10 (although I would prefer to use 9.10).

---

