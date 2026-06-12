---
title: "Is this good home server practice?"
date: 2009-10-27
forum: General Help
---

### Post by sirsmegalot105 on 2009-10-27
Hi

Just want to get some feedback on this, make sure I'm going down the right road...

I set up a headless Ubuntu Server 9.04 at home recently and am ssh'ing in to it from my laptop. It's going to be the main server used for storage of files, music, and also some deamon services running on it (some NAS drives will be mounted on the server as well as it having its own shares)

Amoung other NTFS paritions being used for Windows, Linux is installed across 2 paritions. Here is my df:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             10080520    900792   8667660  10% /
tmpfs                   512640         0    512640   0% /lib/init/rw
varrun                  512640       304    512336   1% /var/run
varlock                 512640         0    512640   0% /var/lock
udev                    512640       144    512496   1% /dev
tmpfs                   512640         0    512640   0% /dev/shm
lrm                     512640      2392    510248   1% /lib/modules/2.6.28-11-server/volatile
/dev/sda4             53233432    435820  50093472   1% /storage
```

So /dev/sda2 is mounted on / and /dev/sda4 is mounted on /storage (the parition I want to use for central storage). Now as things stand, I ssh into a standard user account when accessing the server (the one I made when I installed it), and sudo anytime I need to do it. Am I right in my understanding of the following (bare with me here, this should be over soon lol):

1) A ls -la from my root directory shows: 

```
drwxr-xr-x  5 root root  4096 2009-10-28 01:08 storage 
```

with all other folders/mounts showing the same root:root permissions. I am currently only changing permissions on folders (in /storage) so that I can access / write to them remotely under the non-root account, and assigning daemons their own user accounts (or my standard one I setup when installing) for when they need to write to say /storage/downloads/

Is this the right things to do I assume, keep root access only until I need other wise on specific folders? 

2) Since I am later going to be setting up samba server (to share /storage/folders across network) and smbclient (so that I can access a NAS samba share and share /mnt/nas possibly), plus generally doing backups and wanting write access to /storage from a lot of stuff, should I be making the whole /storage writable under my own user account? 

Thanks if you managed to read this far, and I appreciate any help you can provide :p

And BTW keep up the great work, ubuntuforums.org is an invaluable resource for me - I'm learning more daily and will soon be able to contribute back and start filing bug reports :-({|=

---

### Post by jbrown96 on 2009-10-27
You could make yourself the owner; there's nothing really wrong with that. It really depends on what daemons are running and how much access they need. It's usually a good principle to limit access to files as much as possible, especially when they are network-accessible. 
Here's what I would do
1) /storage is already readable by everyone, so your daemons won't have any trouble reading from the folder; however, they won't be able to write to it. This should work in many situations; most of the time users don't need write access, especially with large media volumes -- it's just read. So I would leave the "other" permissions alone.
2) Create a storage group. ```
sudo groupadd storage
``` Then, give the group ownership of /storage ```
sudo chown -R root:storage /storage
``` Then give the group write access ```
sudo chown -R g+w /storage
```
3) add yourself to the storage group ```
sudo usermod -aG storage $USER
``` Now let's say you want samba (I imagine that's the user, but not sure) to be able to write, you can give it permission with ```
sudo usermod -aG storage samba
``` You can do this with any daemon as long as you know its user. 
This is a really good way to manage access because you have to explicitly grant write permissions. If you want to be really secure, then you could revoke read permissions for "others" and only allow root and the storage group access ```
sudo chmod -R o-rx /storage
```


Here's something that I just noticed. I'm part of a sambashare group without ever configuring samba, so you may want to look into what that group does. you can check your groups or another user's groups (need sudo) ```
groups $USER
``` and you can replace $USER with the desired user. $USER is a variable that is automatically set for the current user, so you can always use that in commands to specify the user running the command.

---

### Post by sirsmegalot105 on 2009-10-28
Thanks for the reply I'll take it on board and see how it goes...

---

