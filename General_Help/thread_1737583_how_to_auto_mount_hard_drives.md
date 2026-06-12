---
title: "how to auto mount hard drives?"
date: 2011-04-23
forum: General Help
---

### Post by lime4x4 on 2011-04-23
Just installed natty 64 bit. fully updated the system. i need to hard drives to automaticaly mount when starting the computer. What is the easiest way to do this in natty?

---

### Post by Harry33 on 2011-04-23
> **lime4x4 said:**
> Just installed natty 64 bit. fully updated the system. i need to hard drives to automaticaly mount when starting the computer. What is the easiest way to do this in natty?

Put the hard drive UUID in the /etc/fstab.

---

### Post by Morbius1 on 2011-04-23
The easiest way to have done this was to have it done by the installer when you first installed Ubuntu. 

Why not post the output of the following commands so we can see how your partitions are set up:
```
sudo blkid -c /dev/null
cat /etc/fstab
```

---

### Post by lime4x4 on 2011-04-23
john@john-linux:~$ sudo blkid -c /dev/null
[sudo] password for john: 
/dev/sda1: UUID="3c9d1b14-8617-4331-954c-08c46fe3de8b" TYPE="swap" 
/dev/sda2: UUID="ff8a7744-8746-4566-b17f-9465d6b0cb3a" TYPE="ext4" 
/dev/sdb1: UUID="fa5d3414-acfb-4a6a-afa3-b4e0d3e9f49e" TYPE="ext4" 
/dev/sdc1: UUID="b4a35da0-6a7e-40ff-9d70-79d05acb43c0" TYPE="ext4" 
/dev/sdd1: LABEL="storage" UUID="50E062301B62E3A0" TYPE="ntfs" 
/dev/sde1: UUID="d612c3f3-9ad9-4e27-97fd-87248f97f073" TYPE="ext3" 
/dev/sdf1: LABEL="vwdideos" UUID="08aa92e8-d7ed-4e20-9eba-705539d276d0" TYPE="ext4" 
john@john-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=fa5d3414-acfb-4a6a-afa3-b4e0d3e9f49e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=ff8a7744-8746-4566-b17f-9465d6b0cb3a /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=3c9d1b14-8617-4331-954c-08c46fe3de8b none            swap    sw              0       0
john@john-linux:~$

---

### Post by Morbius1 on 2011-04-23
Lets take two partitions as examples of how to do this:
[B]
First,[/B] if you have any of these non system partitions in a temporary mount unmount them.

**[1] An ext4 partition**
> /dev/sdc1: UUID="b4a35da0-6a7e-40ff-9d70-79d05acb43c0" TYPE="ext4"Make a permanent mount point with a name that is meaningful to you, For example:
```
sudo mkdir /media/Data
```Add a line to /etc/fstab that will automount that partition to that mountpoint:
```
UUID=b4a35da0-6a7e-40ff-9d70-79d05acb43c0 /media/Data ext4 defaults,noatime 0 2
```Save fstab and then run the following command to test for errors and mount the new partition:
```
sudo mount -a
```**[2] An NTFS partition**
> /dev/sdd1: LABEL="storage" UUID="50E062301B62E3A0" TYPE="ntfs"Make another mount point:
```
sudo mkdir /media/Storage
```Add a line to fstab:
```
UUID=50E062301B62E3A0 /media/Storage ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0
```Then run the mount command again:
```
sudo mount -a
```The form and syntax for a Linux filesystem and a Windows filesystem are different so use the above examples as templates for the remaining partition you want to mount.

---

### Post by karmila on 2011-04-26
Hi Morbius1,

I want to thank you first for answering my question at *bodhi.zazen* "how to fstab" thread. 
Now, I have a same question about automount an ext4 data partition. At another thread I found a suggestion for /etc/fstab entry is
```
/dev/sda8 /media/data ext4 user,auto 0 0
```what is the difference with
```
/dev/sda8 /media/data ext4 defaults,noatime 0 2
```

---

### Post by Morbius1 on 2011-04-26
> /dev/sda8 /media/data ext4 user,auto 0 0"auto" is included in "defaults"
"user" is a rather curious option that you see a lot in this forum in particular and I'm not sure why.

Lets' look at the definition of that parameter:
> user
    Allow an ordinary user to mount the file system. The name of the mounting user is written to mtab so that he can unmount the file system again.OK, um .... :
(1) Why would you want that to happen? If you're automounting the partition you want it to be available to the user without requiring him to mount it himself.

(2) Now let's look at in the context of fstab. At the moment in the boot process where the instructions in fstab are being executed there is only one user. Root.

Root mounts the partition and only root can unmount the partition. If you have user as an option in fstab and an ordinary user tries to mount it again you'll get an "only root can do that". If an ordinary user tries to unmount it you will get an "only root can unmount". If root unmounts the partition first and an ordinary user tries to mount it you will get an "only root....". You get the idea. The addition of user in fstab will do nothing.

---

### Post by dino99 on 2011-04-26
mountmanager (from synaptic) is a nice tool to set properly the needed settings

---

### Post by cariboo on 2011-04-26
This really isn't a Natty specific question, moved to General Help so that more people can benefit from this thread.

---

### Post by VMC on 2011-04-26
I'm glad this topic was moved. Once natty goes public the topics are closed.
Some real informative info here.

 I also wondered about using the "user" qualifier, and have in the past had the root errors, after the share was unmounted. Now I know.

---

### Post by karmila on 2011-04-26
> **Morbius1 said:**
> Root mounts the partition and only root can unmount the partition. If you have user as an option in fstab and an ordinary user tries to mount it again you'll get an "only root can do that". If an ordinary user tries to unmount it you will get an "only root can unmount". If root unmounts the partition first and an ordinary user tries to mount it you will get an "only root....". You get the idea. The addition of user in fstab will do nothing.

Thanks, that is clear. I've got the idea.
Now that I already have my ext4 data partition auto mounted at /media/data but then I found if I can't create file/directory there. Is that means I should set permission for /media/data? If yes what is the proper value for that directory permission.

Edit: this is output from ls:
```
[ari@ari-desktop:~$ ls -l /media
total 8
drwxr-xr-x 3 root root 4096 2011-04-25 19:44 data
```
Or maybe I should change the owner?

> **dino99 said:**
> mountmanager (from synaptic) is a nice tool to set properly the needed settings

Thanks, i will take a look at that. :)

---

### Post by Morbius1 on 2011-04-26
I should point out that despite the way I made it sound in my last rant  there is a place for the user option. But it's a rather uncommon use.

It only makes sense in my mind when you also add it's little brother "noauto". If I create a line on fstab that looks like this:
```
 /dev/sda8 /media/data ext4 defaults,noatime,user,noauto 0 2
```Then it will not mount at boot ( noauto ) but a regular user can mount it but using a rather odd syntax.

If I try to mount it with a regular mount statement:
```
mount /dev/sda8 /home/morbius/Data
```I'll get the "only root" error message.

But I can mount it with eithr one of these commands:
```
mount /dev/sda8
mount /media/data
```What the system will do before throwing you the "only root" message is check fstab for a corresponding line that mentions either sda8 or /media/data. If it finds it then it will mount per the instructions in fstab.

Don't know how useful that is in common usage but it is a possibility.

---

### Post by Morbius1 on 2011-04-26
> Now that I already have my ext4 data partition auto mounted at  /media/data but then I found if I can't create file/directory there. Is  that means I should set permission for /media/data? If yes what is the  proper value for that directory permission.
That depends on how you want to use it and if you have multiple users on your system. If it's only you then take possession of the partition:
```
sudo chown karmila /media/data
```BTW, to each his own of course, but I wouldn't use mountmanager on a drunken bet :D  It's an odd little utility that requires of the user so much knowledge of mounting paramters that he would probably just use gedit to change fstab directly. Just my opinion. But I do enjoy the challenge of fixing the mistakes that mountmanager can make.

---

### Post by karmila on 2011-04-26
> **Morbius1 said:**
> That depends on how you want to use it and if you have multiple users on your system. If it's only you then take possession of the partition:
```
sudo chown karmila /media/data
```BTW, to each his own of course, but I wouldn't use mountmanager on a drunken bet :D  It's an odd little utility that requires of the user so much knowledge of mounting paramters that he would probably just use gedit to change fstab directly. Just my opinion. But I do enjoy the challenge of fixing the mistakes that mountmanager can make.
Yes, that's only me use this PC. The 
```
sudo chown karmila /media/data
```solved permission problem :D

Since you are here, i want to ask about ntfs partition automount too.
What is the difference of this:
```
UUID=50E062301B62E3A0 /media/Storage ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0
```and this:
```
UUID=50E062301B62E3A0 /media/Storage ntfs-3g defaults,uid=1000 0 0
``` ?

Actually, the
```
UUID=50E062301B62E3A0 /media/Storage ntfs-3g defaults,uid=1000 0 0
```
works fine but the other one may be better.

---

### Post by Morbius1 on 2011-04-26
I feel like this is a final exam :D

(1) UUID=50E062301B62E3A0 /media/Storage ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0
(2) UUID=50E062301B62E3A0 /media/Storage ntfs-3g defaults,uid=1000 0 0

In Ubuntu ntfs = ntfs-3g
"defaults" in Ubuntu has an embedded umask=000 in it. But it can be overridden with an explicit umask value.

The first expression will mount the partition with:
user = you (uid=1000)
group = plugdev ( gid=46 )
With permissions for you to read / write ( the first "0" in umask ), for plugdev to read / write ( the second "0" ) and with no permissions for anyone else.
If you added new users to your system using "Users and Groups" then all users are members of plugdev.

The second expression will mount with:
owner = you
and with permissions for everyone to read / write.

Again this is just personal preferences on my part but I prefer to explicitly state the umask value because you never know when someone will change the definition of "defaults".

If you're the only user then one is not better than the other.

**[COLOR=Blue]OOPS:[/COLOR]** Missed the utf8 reference that's missing in the second expression. It has to do with character encodeing - special characters. Don't really know enough about it to explain it further than that but I always add it out of habit.

---

### Post by karmila on 2011-04-26
> **Morbius1 said:**
> I feel like this is a final exam :D

(1) UUID=50E062301B62E3A0 /media/Storage ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0
(2) UUID=50E062301B62E3A0 /media/Storage ntfs-3g defaults,uid=1000 0 0

In Ubuntu ntfs = ntfs-3g
"defaults" in Ubuntu has an embedded umask=000 in it. But it can be overridden with an explicit umask value.

The first expression will mount the partition with:
user = you (uid=1000)
group = plugdev ( gid=46 )
With permissions for you to read / write ( the first "0" in umask ), for plugdev to read / write ( the second "0" ) and with no permissions for anyone else.
If you added new users to your system using "Users and Groups" then all users are members of plugdev.

The second expression will mount with:
owner = you
and with permissions for everyone to read / write.

Again this is just personal preferences on my part but I prefer to explicitly state the umask value because you never know when someone will change the definition of "defaults".

If you're the only user then one is not better than the other.

**[COLOR=Blue]OOPS:[/COLOR]** Missed the utf8 reference that's missing in the second expression. It has to do with character encodeing - special characters. Don't really know enough about it to explain it further than that but I always add it out of habit.
Hi Morbius1,

Really thanks for this complete yet simple explanation. I have subscribed to this thread in case me or my friends need help about /etc/fstab entry for auto mount partitions.

If this is an exams, you will get A++ :D

Thanks.

---

