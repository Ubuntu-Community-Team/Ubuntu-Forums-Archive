---
title: "Where c$ is monted?"
date: 2009-08-11
forum: General Help
---

### Post by Thomas_Klaus2 on 2009-08-11
Hi,

by mounting a Windows Network, for example $c on 192.168.178.43,
I receive a link on the Desktop called like this.
But I cant find it in :~/Desktop$ ls
I want to know where this item is mounted originally?
Or is there anything to make show ls this link, f.e. ls -L?

Thank you,

---

### Post by Charlietje on 2009-08-11
How did you mount the windows share?

To mount a windows share try the following command:
```
smbmount //192.168.1.2/*shared_path* /*path_to_mountpoint* -o username=*your_username*

```

---

### Post by Thomas_Klaus2 on 2009-08-11
thanks.
I mounted with nautilus smb://192.168.178.20/c$/ with the built in "samba"
(smbmount is not included) of 8.04

---

### Post by synapsys on 2009-08-11
You must specify a mount point when mounting any kind of media. ```
smb://192.168.178.20/c$/ (space) /path/to/mount/point/
```

The default mount point is /media or /mnt

---

### Post by Thomas_Klaus2 on 2009-08-11
thomas@frunobulax:~$ smb://192.168.178.21/c$  /home/thomas/Desktop/mnt
bash: smb://192.168.178.21/c$: No such file or directory
thomas@frunobulax:~$ 

on the other side nautilus creates a link 'c$ on 192.168.178.21'
on the Desktop . Maybe nautilus puts automatically a mount point
to this link (invisible with ls?), but I don't know where.

Its not in /media or /mnt

---

### Post by Charlietje on 2009-08-12
First install:

```
apt-get install samba-common smbfs
```


then you can mount the smb share like this:

```
mount -t smbfs -o username=*username*,password=*password* //192.168.178.20/c$/  /*mount_point*
```


or

```
smbmount //192.168.178.20/c$ /*path_to_mountpoint* -o username=*your_username*
```

---

### Post by 3rdalbum on 2009-08-12
When you mount an SMB share within Gnome, it actually appears inside ~/.gvfs. That is, it's inside a hidden folder called ".gvfs" in your home directory.

I keep it in my Bookmarks list in Gnome and KDE for easy access.

---

### Post by Thomas_Klaus2 on 2009-08-12
Thank you very much 3rdalbum , thats it! I tried sometimes in the german forum, but I never got an answer. And I had no right idea where to look in
the search engines.

First I used the well known method of Charlietje to mount my brothers Windows machine, to explore it with the terminal (Count certain pattens).
But smbmount is not included in the 8.04 version. After I installed smbmount, etc... the Windows printer "Windows printer via samba" has disappeared from the printer configuration.The only printer here. Soon, after changing the harddisk, I made a new installation. Now it works again, and I dont want to use too much from outside the standart installation. Even if it cames from standart repositories. In this case it not necessary too. It was just a fast way to mount c$.

PS: I have had to search hidden files for 192.168.178.20. OK. I forget always, because they are displayed, except in "search for files". Until now ; )

---

### Post by mperrin on 2009-08-12
Refer to thread
[http://ubuntuforums.org/showthread.php?t=1176404](http://ubuntuforums.org/showthread.php?t=1176404)

It answers your original question and I posted a share mounting management system, written in shell script, that you may find useful.

---

### Post by synapsys on 2009-08-14
Next time try doing a search for c$

---

### Post by Thomas_Klaus2 on 2009-08-18
yes, and choose "search for files" > "select more options" > add "show hidden and backup files" before or do
thomas@frunobulax:/$ find -name *192.168.178.20*   
*c$*is rare enough too
I was too gnome easydoing

cifsmanage is going to be processed

Regards

---

