---
title: "Samba problem - cannot delete files"
date: 2012-07-11
forum: General Help
---

### Post by woodyg on 2012-07-11
I am using a computer running Lubuntu 11.10 as a backup for my main computer. One of the things that is being backed up is the entire .mozilla folder, so that I can keep my old Firefox data intact after future OS re-installations. As I have been having problem copying part of the .mozilla folder over (I get error messages running LuckyBackup) I have decided to not backup the cache folder. The problem I face now is however that I cannot delete the cache folder in .mozilla on my backup HDD. I get the error message:
> 
Some files cannot be moved to the rubbish bin because the underlying file systems don't support this operation. Do you want to delete them instead?What is the problem? What does this message mean? The permissions for the entire .mozilla folder is 775. I am trying to delete as root, but get the error message mentioned above.

---

### Post by coffeecat on 2012-07-11
> **woodyg said:**
> I am trying to delete as root

Why are you trying to delete as root? From what you've told us, invoking root privileges shouldn't be necessary. If you try to delete as root using a root-owned file manager, any deleted files would be moved to root's trash. I'm speculating here, but my guess is that the backup HD is formatted with a Microsoft filesystem such as NTFS or FAT32, and that you have automounted it from the GUI. Automounting it from the GUI causes it to be mounted with the UID=1000 option, effectively owning it by yourself.

With the backup HD plugged in and mounted the way it was when you encountered these problems, post the terminal output of:

```
mount
```

Now cd in the terminal to the cache folder and post the output of this command:

```
ls -l
```

---

### Post by woodyg on 2012-07-12
> **coffeecat said:**
> Why are you trying to delete as root? 
I couldn't delete as normal user, so I tried with root as well... that's all.


> **coffeecat said:**
>  I'm speculating here, but my guess  is that the backup HD is formatted with a Microsoft filesystem such as  NTFS or FAT32
It is a separate computer, Lubuntu 11.10, and it is ext4. I automount by having the following in etc/fstab

//192.168.1.88/michael-2012        /media/remote_lubuntu  smbfs   credentials=/root/.smbcredentials,noperm,file_mode=0777,dir_mode=0777   0       0



> **coffeecat said:**
> 
```
mount
```

It gives me

```
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda9 on /home type ext4 (rw)
//192.168.1.88/michael-2012 on /media/remote_lubuntu type cifs (rw)
gvfs-fuse-daemon on /home/michael-lxde/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael-lxde)
```> **coffeecat said:**
> Now cd in the terminal to the cache folder and post the output of this command:

```
ls -l
```

Which cache folder is this? Is it .cache in my home directory?

---

### Post by coffeecat on 2012-07-12
Apologies, re-reading your OP it's now apparent that you are trying to delete over the network - I missed that - but it's only clear from your latest post that this is with a samba share:

> **woodyg said:**
> 
//192.168.1.88/michael-2012        /media/remote_lubuntu  smbfs   credentials=/root/.smbcredentials,noperm,file_mode=0777,dir_mode=0777   0       0

I think you need to look at your samba permissions - I don't think invoking root in the local machine will help. I'll defer to someone who knows more about samba/smb. You'll need a thread title that mentions that to get the attention of someone with appropriate expertise. I can edit your thread title for you - what would you like?

---

### Post by woodyg on 2012-07-12
> **coffeecat said:**
> You'll need a thread title that mentions that to get the attention of someone with appropriate expertise. I can edit your thread title for you - what would you like?

Modifying the thread title would be great. Please enter whatever you think is suitable (I'm kinda lost...). Thanks!

On a side note... I have had other issues with my samba share, where LuckyBackup was unable to set permissions on the files that were copied across. So perhaps there is a general problem with this samba share.

---

### Post by coffeecat on 2012-07-12
> **woodyg said:**
> Modifying the thread title would be great. Please enter whatever you think is suitable (I'm kinda lost...). Thanks!

Done! :)

If that doesn't attract a samba guru, and you want the thread moved to another sub-forum, you can send a request to the staff area with the report button. Don't worry that it says "report abuse". You can use it for thread move requests as well.

---

