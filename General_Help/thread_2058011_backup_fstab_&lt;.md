---
title: "backup fstab? :&lt;"
date: 2012-09-14
forum: General Help
---

### Post by clo17 on 2012-09-14
[FONT=Century Gothic]Hello,

I have seen some phrases "backup fstab" everywhere but I couldn't find a single thread telling me how to do this, and I figured I should ask.

Please do not tell me to read another thread/page. I am tired of seeing that. Please copy down the know-how instead.

In case you are wondering, yes I am new to ubuntu.
[/FONT]

---

### Post by steeldriver on 2012-09-14
Hello and welcome

The fstab file is just an ordinary text file - so backing it up is as simple as copying it. Most people choose to do that to the same directory as the original (which is the /etc directory) hence requiring 'sudo' authority - e.g. from a terminal you could do

```
sudo cp /etc/fstab /etc/fstab.bak
```but that's not actually required - you could copy it to your home dir (although that will make it slightly more complicated to restore in the event that you need to do so)

---

### Post by clo17 on 2012-09-14
[FONT=Century Gothic]https://help.ubuntu.com/community/MountingWindowsPartitions

Alright, er... so I am trying to follow the steps listed in that link and I am kind of stuck at "mount point." Can that just be anything? What are the codes for each location anyway? I'm new to ubuntu so I am kind of overwhelmed by all of this and that.

[/FONT]**Manual Configuration**

 [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconGNOMETerminal.png[/IMG] First you need to find the device location of the NTFS partition(s) you want to mount.  In terminal, run: 

[LIST]
[*]sudo fdisk -l | grep NTFS | awk '{print $1}'
[/LIST]
The name of each partition should be something like /dev/hd**xn** or /dev/sd**xn**, where **x** is an alphabetical letter (ranges from a to z) and **n** is a number (e.g. /dev/hda1). 
If the drive is internal, you will now need to edit your [file systems table]("https://help.ubuntu.com/community/Fstab") configuration file, /etc/fstab.   If the drive is an external USB or firewire drive, hal should  automount it.  Now, be sure to save a backup of fstab first, then open  the file for editing: 

[LIST]
[*]sudo cp /etc/fstab /etc/fstab.orig gksudo gedit /etc/fstab
[/LIST]
After  entering your password, find the line that matches the device location  you just found and change it to the following. If there is no entry yet,  add a new line like the following: 

[LIST]
[*]<your partition> /media/<mount point> ntfs-3g defaults,user,locale=en_US.utf8 0 0
[/LIST]
NOTE: If it displays your NTFS partition with a [UUID]("https://help.ubuntu.com/community/UsingUUID"),  you can check the relevant device location by running one of the  following commands.  It is OK (and even advisable) to keep the UUID  setup if that is what already exists. 

[LIST]
[*]sudo blkid ls -l /dev/disk/by-uuid/
[/LIST]
Replace  <your partition> with the name of the partition you identified  earlier. Replace <mount point> with the location you would like  the partition to be mounted at, so you have something like /media/windows or /media/documents for that column. 
Note: you can also change your locale option (ex: locale=fr_FR.utf8). Execute locale -a in a terminal to know which ones are supported on your system. 
Save  and close the file.  You will now need to create the mount point for  each NTFS partition before you can actually mount them: 

[LIST]
[*]sudo mkdir -p /media/<mount point>
[/LIST]
Now remount each partition with 

[LIST]
[*]sudo umount <your partition> sudo mount -a
[/LIST]
If you want to revert to your previous configuration, run: 
sudo mv /etc/fstab.orig /etc/fstab sudo umount /media/<mount point>

---

### Post by clo17 on 2012-09-14
[FONT=Century Gothic]Oh what does this mean? :<

umount: /host: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
[/FONT]

---

### Post by whatthefunk on 2012-09-14
What are you trying to mount?  Harddrive?

---

### Post by clo17 on 2012-09-14
> **whatthefunk said:**
> What are you trying to mount?  Harddrive?

[FONT=Century Gothic][FONT=Century Gothic]Naw, trying to mount my Windows 7 data so I can access everything on ubuntu. I didn't know it could be another OS when I installed it. Someone told me to install ubuntu to create a MineCraft server, and I ended up in this conundrum. What I like about it, though, is that I can use my own password now (my stepparents hacked into my Windows 7 account, preventing me any permanent access). Also, ubuntu is not that bad.

Oh, I also need a solution really fast because I really need Cubase 5 and Overwolf (along with plenty more important files) back. I can't afford installing those things again.

The problem is that I need all my things on Windows 7 back with me on ubuntu and somehow audio is not working anymore. I even tried AlsaMixer. I kind of regret installing ubuntu but the fact that I can regain full access to my laptop is nice, so I'm not really thinking of uninstalling.
[/FONT][/FONT]

---

### Post by Bashing-om on 2012-09-14
clo17; Hi !

  Let me see if I can help.

Mount point: Everything and anything in linux is a file! (yes devices are files)..In this file system is the root (/) ..the head of the file system...all files are under root. So you need to attach "something" to this tree. One does that from a "mount point". This is the common reference between you and root.  My example ... I keep my backup files on a seperate hard drive. Simply enough I call my reference "backup". Now to attach "backup" to the file system I make root aware of it by 
```
sudo mkdir /mnt/backup
```In answer to your question, yes this can be anything . You may make the "mount point" to any established directory. However there are benefits to using either the directory "mnt" or "media".
Anyway, so now we want to use our device....Tell the system you want to use it thus:
```
sudo mount /dev/sdb1 /mnt/backup
```this ^is a manual mount.

If you want to auto mount the "device" so you have access to it ...fstab (file system table) is the way to do it. Now comes the thinking part...setting up the entry in fstab is no small matter ,,,access rights, mounting options, file checking options (your reference is good) How you set up the mount options is a personal preference.
-----------------
the < character.....out of context can not be specific,
  hint: <expression> just a indicator that something takes the place of expression
           < could also be used as a redirection symbol ..like --take input from a file rather    than the terminal.
could be a arithmetic comparator ....
The point being ... it is a symbol that is case dependent.

Umount host is busy///well something (an open file most likely) has the device in use,
 close everything out and back out of it gracefully...
then:
```
sudo umount /mnt/backup
```(in my example)

This is a steep learning curve, but I assure you the effort is well worth it ..returns in ways beyond imagination.                    BDQ ==> said that

---

### Post by clo17 on 2012-09-14
> **Bashing-om said:**
> clo17; Hi !

  Let me see if I can help.

Mount point: Everything and anything in linux is a file! (yes devices are files)..In this file system is the root (/) ..the head of the file system...all files are under root. So you need to attach "something" to this tree. One does that from a "mount point". This is the common reference between you and root.  My example ... I keep my backup files on a seperate hard drive. Simply enough I call my reference "backup". Now to attach "backup" to the file system I make root aware of it by 
```
sudo mkdir /mnt/backup
```In answer to your question, yes this can be anything . You may make the "mount point" to any established directory. However there are benefits to using either the directory "mnt" or "media".
Anyway, so now we want to use our device....Tell the system you want to use it thus:
```
sudo mount /dev/sdb1 /mnt/backup
```this ^is a manual mount.

If you want to auto mount the "device" so you have access to it ...fstab (file system table) is the way to do it. Now comes the thinking part...setting up the entry in fstab is no small matter ,,,access rights, mounting options, file checking options (your reference is good) How you set up the mount options is a personal preference.
-----------------
the < character.....out of context can not be specific,
  hint: <expression> just a indicator that something takes the place of expression
           < could also be used as a redirection symbol ..like --take input from a file rather    than the terminal.
could be a arithmetic comparator ....
The point being ... it is a symbol that is case dependent.

Umount host is busy///well something (an open file most likely) has the device in use,
 close everything out and back out of it gracefully...
then:
```
sudo umount /mnt/backup
```(in my example)

This is a steep learning curve, but I assure you the effort is well worth it ..returns in ways beyond imagination.                    BDQ ==> said that

[FONT=Century Gothic]Well I keep getting the "busy" something-like-that even when I don't have anything open. If there is a way to get that barrier out of the way, or there is another way to access and use everything from Windows 7 directly from ubuntu, for that matter, that would be great. The reason why I cannot afford just trying to reboot the computer with Windows 7 is not only do I have no clue how, my account in Windows 7 has been hacked, as I mentioned earlier.[/FONT]

---

### Post by cjhabs on 2012-09-14
I am running 10.04 and do:
Places -> Network -> Windows Network
and it'll show all the shared windows folders - you can simply navigate to them - not sure if you'll need to authenticate or not

---

### Post by clo17 on 2012-09-14
> **cjhabs said:**
> I am running 10.04 and do:
Places -> Network -> Windows Network
and it'll show all the shared windows folders - you can simply navigate to them - not sure if you'll need to authenticate or not

[FONT=Century Gothic]No, that would apply when it's between two different computers. I've already tried that. In my case it would be the same laptop, just with two different operating systems. Yes, I will pretty much need to merge both of them altogether.

I highly doubt if this problem will ever be solved.
[/FONT]

---

### Post by cjhabs on 2012-09-14
> **clo17 said:**
> [FONT=Century Gothic]No, that would apply when it's between two different computers. I've already tried that. In my case it would be the same laptop, just with two different operating systems. Yes, I will pretty much need to merge both of them altogether.

I highly doubt if this problem will ever be solved.
[/FONT]
To find out what is making it busy use:
```
sudo fuser -m /dev/sdb1
```It will list the pids - then use 
```
ps -elf | grep pidnumber
```to find out what the offending actually is. Then you may be able to kill it.

---

