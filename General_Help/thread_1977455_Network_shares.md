---
title: "Network shares"
date: 2012-05-10
forum: General Help
---

### Post by columbo1977 on 2012-05-10
Hey

I have ubuntu 12.04 installed on one of my machines. I have mounted via fstab some windows shares from my file server. Problem is it will not let me create anything g in these folders.

How do I sort the permissions so i can change and create in these folders.

I hav e the same user and pass on both machines.

Thanks

Graham

---

### Post by Peter09 on 2012-05-10
I believe windows shares are mounted default as read-only.
 
I think there is a tool box in the repositories called something like
 
>  
nfstools (cannot remember the exact name)

 
see if you can find them in the software center.

---

### Post by columbo1977 on 2012-05-10
Hey

I installed Ntfs-Config tool and although I have selected to enable write support for internal and external devices I still cannot edit what is on my shares.

Also it is crashing all the time, does anything work with 12.04?

Anymore ideas?

G

---

### Post by Peter09 on 2012-05-10
Have you mounted and unmounted the share since you changed the settings?

---

### Post by columbo1977 on 2012-05-10
Yes, and restarted the system.

---

### Post by bab1 on 2012-05-10
> **columbo1977 said:**
> Hey

I have ubuntu 12.04 installed on one of my machines. I have mounted via fstab some windows shares from my file server. Problem is it will not let me create anything g in these folders.

How do I sort the permissions so i can change and create in these folders.

I hav e the same user and pass on both machines.

Thanks

Graham

You have to explicitly name the owner and group in the mount command.  For the various options see ```
man mount.cifs 
```

---

### Post by columbo1977 on 2012-05-10
From looking at the man file I can see that I neede to add the rw but when I try this I get an error saying the line is bad.

Any ideas what I need to add to this to make it work?

//192.168.1.100/Writing	/mnt/Writing	smbfs credentials=/home/MyHomDir/.credentials/SHARE_CREDS	0	0

Thanks

Graham

---

### Post by Morbius1 on 2012-05-10
Make sure the following package in installed:
```
sudo apt-get install cifs-utils
```Change the line line in fstab to this:

//192.168.1.100/Writing    /mnt/Writing [COLOR=Blue]**cifs**[/COLOR] credentials=/home/MyHomDir/.credentials/SHARE_CREDS,[COLOR=Blue]**uid=1000**[/COLOR]    0    0

Then mount the share with this comand:
```
sudo mount -a
```OR, for a completely different method:
```
gvfs-mount smb://192.168.1.100/Writing
```Then:
```
nautilus $HOME/.gvfs
```

---

### Post by columbo1977 on 2012-05-10
Hey

Got it working, thanks for all the help. Here is the commands I put in the fstab :

//Universe/Writing	/mnt/Writing	cifs rw,uid=user,gid=user,file_mode=0777,dir_mode=0777,cred=/home/columbo/.credentials/SHARE_CREDS	0	0

Cheers

Graham

---

