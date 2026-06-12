---
title: "Can't get write permissions on FAT32 share"
date: 2006-02-22
forum: General Help
---

### Post by Freddie.Ruddick on 2006-02-22
Hi everyone,

I have a shared folder on my Windows PC, containing my MP3s and vids. I can mount it on my ubuntu box with ```
sudo mount /mnt/Freddie-hp 
```with this line in the fstab:

```
//192.168.0.158/media   /mnt/Freddie-hp smbfs rw,_netdev,auto,username=Guest,password=[ITS A SECRET]       0       0
```. However, if I add the "users" or "user" option to the fstab line, when I try and mount with ```
mount /mnt/Freddie-hp
```, it doesn't mount and returns ```
smbmnt must be installed suid root for direct user mounts (1000,1000)
smbmnt failed: 1

``` Which I don't understand, even after reading the man pages on fstab, mount, smbmnt and smbmount. But I can handle using sudo to mount it. My main problem is, I can't write to the drive, even with sudo or gksudo nautilus. I've chowned /mnt/Freddie-hp to freddie:freddie, and 777'd, but when I mount the drive, everything is owned by root, and 755'd.

Can anyone help me get write permission on the share?

---

### Post by SqdnGuns on 2006-02-22
nevermind.......................didn't read it all...........

---

### Post by dcstar on 2006-02-23
[QUOTE=Freddie.Ruddick]Hi everyone,

I have a shared folder on my Windows PC, containing my MP3s and vids. I can mount it on my ubuntu box with ```
sudo mount /mnt/Freddie-hp 
```with this line in the fstab:

```
//192.168.0.158/media   /mnt/Freddie-hp smbfs rw,_netdev,auto,username=Guest,password=[ITS A SECRET]       0       0
```. However, if I add the "users" or "user" option to the fstab line, when I try and mount with ```
mount /mnt/Freddie-hp
```, it doesn't mount and returns ```
smbmnt must be installed suid root for direct user mounts (1000,1000)
smbmnt failed: 1

``` Which I don't understand, even after reading the man pages on fstab, mount, smbmnt and smbmount. But I can handle using sudo to mount it. My main problem is, I can't write to the drive, even with sudo or gksudo nautilus. I've chowned /mnt/Freddie-hp to freddie:freddie, and 777'd, but when I mount the drive, everything is owned by root, and 755'd.

Can anyone help me get write permission on the share?[/QUOTE]
Try adding this to the fstab options:

umask=000

---

### Post by Freddie.Ruddick on 2006-02-23
Thanks ,David. I tried that, but it still doesn't work.

---

### Post by lamego on 2006-02-23
I don't get your problem, does it works with the "username=" option ? You shouldn't need user or users options for a samba mount...

---

### Post by Freddie.Ruddick on 2006-02-23
[QUOTE=lamego]I don't get your problem, does it works with the "username=" option ? You shouldn't need user or users options for a samba mount...[/QUOTE]

With username it works after a fashion. I can mount it as root, but I'd like to be able to mount it myself, without root. But if I can't, I can't.

My main problem is not being able to get write access, even with the mount point (/mnt/Freddie-hp) chowned to me and 777'd. But if I mount the drive, it reverts to owned by root and 755'd.

---

### Post by Sutekh on 2006-02-23
- You need to add an extra flag to the samba mount fstab entry; **uid**

 - This is a good link for explaining the use of uid.

[Just Linux - Mounting smbfs Shares Permanently Help File]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")

 - Look for the section **Providing Security** and then 'Providing Read/Write Access to the Share'

[QUOTE=JustLinux]Providing Read/Write Access to the Share

Another problem with mounting the Windows share as shown in the /etc/fstab file above is that only the root user would have read/write access to the share. All other users would have read only access to it. If you wanted read/write access to it for yourself, you need to specify your userid or groupid. That would change the line in /etc/fstab to look like this:

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,uid=mylinuxusername,gid=mylinuxgroupname 0 0

Whatever user and or group you specified in the line would have read/write access to the mounted share. You can use either the user or group name or the user or group numerical ID. Either should work.

If you had several users you wanted to have read/write access to it, create a group and add those users to the group. Then specify just that groupid in the /etc/fstab file. You wouldn't need to specify a userid. The line in etc/fstab would look like this:

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,gid=sambausersgroup 0 0
[/QUOTE]

 - You can determine your user's id using the command ```
id
```

 - Usually the first user on the system has a uid=1000 and gid=1000.

---

### Post by Freddie.Ruddick on 2006-02-24
Thanks a lot sutekh! Its working now, with uid=1000 and gid=1000 added nto the fstab.

EDIT: Or maybe not. It now recognises me as the owner of all the files, but if I try and Create a folder or whatever on it in Nautilus, I get an error (See attached), and if I try from the terminal, I get:```
mkdir: cannot create directory `test': Input/output error
```

Anyone?

---

### Post by Freddie.Ruddick on 2006-02-25
Ahhh. I think its a hardware problem. I can't write to it from the local windows machine either. I think I'll reformat it.

---

### Post by zilkha on 2007-06-03
chmod +s /usr/bin/smbmnt fixed the problem for me but this might also create a security problem does anyone know?

---

