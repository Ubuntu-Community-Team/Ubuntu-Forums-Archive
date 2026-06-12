---
title: "Share NTFS in Ubuntu 9.10"
date: 2009-12-05
forum: General Help
---

### Post by lucast on 2009-12-05
Could anyone give me some guidance on how to share a drive formatted as NTFS in Ubuntu 9.10 please (read and Write with no password required)

I would like to access it from another computer running Windows.  It is currently mounted and I can read and write to it.

---

### Post by StuartN on 2009-12-05
> **lucast said:**
> Could anyone give me some guidance on how to share a drive formatted as NTFS in Ubuntu 9.10 please (read and Write with no password required)

If you locate the mount path (in /media if automatically mounted) in Nautilus, then right-click on it, you will be able to modify the sharing options.

You will be prompted to install samba if it isn't installed already.

---

### Post by lucast on 2009-12-06
Hi,

Thank you for the reply.

I have done that, but can't see the share from Windows.  Also when I go back into Nautilus the share has gone.  I also get access denied when trying to change the permissions.

After some research I found out that this is because its formatted NTFS which doesn't have the same file level security.

Any idea what I have to do now?

Thanks for your help!

---

### Post by StuartN on 2009-12-06
Perhaps you do not have permission to share the resource. Also, the owner, group, permissions etc of all the folders and files within a mounted NTFS volume are derived from the mount point.

You could add the partition to your /etc/fstab or mount it with a command like:

```
mkdir ~/NTFS
sudo mount -t ntfs -o uid=stuart,gid=stuart /dev/sda2 /home/stuart/NTFS
```

Now the partition contained on the partition /dev/sda2 has been mounted to a folder called NTFS in my home directory, with me as owner, and can be shared.

It is also possible to alter the default sharing behaviour - if I try to share a root-owned share, a message says *"we are restricted to only sharing directories we own. Ask the administrator to add the line _"usershare owner only = False"_ to the [global] section of the smb.conf to allow this."*

---

### Post by lucast on 2009-12-07
Hi,

I have done a bit of research and I guess the correct option is to change my 'fstab'  and I believe I need to change the umask.  Do you know how this line should read?  I have read that I can compromise my security depending on how I change this?

Here is the line that mounts my ntfs drive:

```
# /windows/D was on /dev/sdb1 during installation
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```

And here is the complete fstab:

```
 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=9efcde3a-cdc5-4ecb-92e2-1d263511d2e4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=5a54f549-b2a8-4dc2-a308-327c0f47f9b8 /home           ext4    defaults        0       2
# /windows/C was on /dev/sda1 during installation
UUID=64848FC3848F95E8 /windows/C      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /windows/D was on /dev/sdb1 during installation
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /windows/E was on /dev/sda2 during installation
UUID=1028579828577C22 /windows/E      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=23c69a5e-cd23-4f18-bed1-1c687043240c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


I have also added 'usershare owner only = False' to my smb.conf in the Global section.

---

### Post by StuartN on 2009-12-07
> **lucast said:**
> ```
# /windows/D was on /dev/sdb1 during installation
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```

umask is denial of read (4) + write (2) + execute (1) permission for user, group and others. A umask of 007 denies nothing to user and group, but denies others all permissions. 022 might be useful, denying group and others write permission, but allowing read and execute. (Google returns a good page for "man umask", though Ubuntu has no man umask page).

I would change gid=46 to the group name to make it more readable, add uid=<your username>, and mount to ~/windows/D (unless you want to share the mount with other users). I am assuming it is a single-user desktop PC, and not a server.

---

### Post by lucast on 2009-12-12
Hi Stuart,

SOLVED :-D  Thank you for all your help.

So to summarise I...

I have two internal disks.  One has Windows XP x64 and Ubuntu 9.10.  The other is a NTFS formatted disk with all my documents on it.

After installing Ubuntu 9.10 I was able to read and write to the NTFS disk by default but not share any of the folders on my home network.

Firstly I tried sharing a folder which prompted me to install the sharing tools, which I did.

I then ran in a terminal:
```
sudo gedit /etc/fstab
```

I chaged my FSTAB entry for the NTFS disk to include:
umask=022
uid=<my username>

```
# /windows/D was on /dev/sdb1 during installation
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,umask=022,gid=46,uid=imagine 0       0
```

After making this change and rebooting I made a change to the smb.conf file to include the following under the [Global] section:
```
sudo gedit /etc/samba/smb.conf
```
   workgroup = WORKGROUP
   netbios name = Imagine-ubuntu
   usershare owner only = false

I then did the following in a terminal:
```
sudo /etc/init.d/samba restart
```

Now I could go to the folder I want to share and right click on it, properties, and share.

I'm not sure if there is a easier way of doing this, or even if this is the correct way, but it worked for me.

Thank you again for all your help!

---

### Post by lucast on 2009-12-13
I have also been chatting about this problem with sys-admin and they said in a situation like this where the disk is in a machine at home and there is no security risk.  Start by giving complete access then slowly secure it one bit at a time until its not usable and then go back one step so that it is usable.

So I started with

```
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8 0       0
```

This allowed me to share the drive Read/Write, so then I did this:

```
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,gid=46,uid=imagine 0       0
```

and this still worked for me so I added a umask:

```
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,umask=777,gid=46,uid=imagine 0       0
```

this still worked  so I changed the umask to 022 which still shared the drive but read only. so I changed it to 222 which now seems to work for me.

I only have one user on my home computer so adding uid=imagine is a good idea I believe.  

I am new to Linux and what I have written maybe not be the best way or correct way to do this as I am not a SysAdmin. 

Hope this has helped a few people.

---

### Post by inkhorn on 2009-12-27
I was having the same problem trying to share my external NTFS formatted hard drive with  a windows XP machine ([[COLOR="Blue"]_see the full story here_[/COLOR]]("http://nixliving.blogspot.com/2009/12/permissions-samba-sharing-external-ntfs.html")).  To make a long story short a program for ubuntu called pysdm (Python Storage Device Manager) helped me choose the right fstab options for sharing my drive over the network.  Word of warning though, the program I mention links up your external drive's current partition with the mount point.  So, you have to go into your fstab file and replace your external drive's current partition title (let's say it was /dev/sdb1) with your external drive's UUID (e.g. "UUID=010C7CC23301CA6C").

To download pysdm:

```
sudo apt-get install pysdm
```

Access it by clicking: System > Administration > Storage Device Manager

To find out your connected external hard drive's UUID:

```
sudo blkid
```

And look for the UUID on the line beginning with your external drive's partition title (mine is /dev/sdb1 currently).

---

### Post by percheron on 2010-03-07
Hi Everyone.
I tried all the above without success. What worked for me eventually was to add myself to the root user group, then share the drive in /media.

Before adding myself to the root group, I was able to share the drive but still couldn't access it from a windows share. 

I'm not sure about the security issues this brings up, I am on a home network so it isn't a problem.

---

### Post by percheron on 2010-03-07
Hi Everyone.
I tried all the above without success. What worked for me eventually was to add myself to the root user group, then share the drive in /media.

Before adding myself to the root group, I was able to share the drive but still couldn't access it from a windows share. 

I'm not sure about the security issues this brings up, I am on a home network so it isn't a problem.

---

