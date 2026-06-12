---
title: "Grsync error code - help required"
date: 2011-10-24
forum: General Help
---

### Post by Frogster on 2011-10-24
Evening All, 

This message is driving me mad! It seems like all is working well but completing with errors in the simulation. I think its the syntax I am using for "smb://nas-6c-c7-f4.local/media/"

Any help

*** Launching RSYNC command (simulation mode):
rsync -r -n -t -v --progress --ignore-existing -s /media/Big Empty/All Music ://nas-6c-c7-f4.local/media/

ssh: Could not resolve hostname : Name or service not known

rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(601) [sender=3.0.7]
Rsync process exit status: 255

---

### Post by papibe on 2011-10-24
Your guess seems correct. (G)rsync doesn't support smb urls, so you need to use server name that can be resolve.

Does the machine nas-6c-c7-f4 have OpenSSH server installed?

If so, you can use something like:
```
rsync -r -n -t -v --progress --ignore-existing -s '/media/Big Empty/All Music'   nas-6c-c7-f4.local:/media/
```
Hope it helps,
Regards.

---

### Post by Frogster on 2011-10-24
Thanks for the quick response papibe

"Does the machine nas-6c-c7-f4 have OpenSSH server installed?" I have to admit to not knowing if it does. How could I tell?

---

### Post by papibe on 2011-10-24
Another solution would be to mount the shares on a temp location. And then using rsync referring local directories.

In order to mount a samba share you need to install this first:
```
sudo apt-get  install smbfs 
```
Then you can mount your share using a command like:
```
mkdir mnt
sudo mount -t cifs  //nas-6c-c7-f4/media/ mnt/ 
```
After that you can rsync like this:
```
rsync -r -n -t -v --progress --ignore-existing -s '/media/Big Empty/All Music'   mnt/
```
To unmount the share:
```
sudo umount mnt/
```
I Hope it helps,
Regards.

---

### Post by Frogster on 2011-10-24
Thank you.

I got this

> keith@Ernie:~$ sudo mount -t cifs  //nas-6c-c7-f4/media/music/ mnt
Password: 
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


The learning curve grows :-)

---

### Post by papibe on 2011-10-24
What brand and model is you nas-6c-c7-f4?
It is an actual computer or a NAS box?
How do you admin the machine? (Web UI?)

Does this work?
```
sudo mount -t cifs  //nas-6c-c7-f4.local/media/ mnt/
```
Regards.

---

### Post by Frogster on 2011-10-24
The box is a Netgear ReadyNas Duo, normal admin is done via firefox.

I normally access for adding files etc via Places, Network.

> sudo mount -t cifs  //nas-6c-c7-f4.local/media/ mnt/ worked, I got a disk on my desktop

Yay thanks papibe. that "mnt" now shows up in Grsync and I can select the music folder to I want to update. Grsync completed successfully on the simulation. Time to give it a try.

One final question. Do I need to run "sudo mount -t cifs  //nas-6c-c7-f4.local/media/ mnt/" every time I wish to mount the drive?

So so grateful for your help

---

### Post by papibe on 2011-10-24
If having the share mounted all the time works best for you, you have a couple of alternatives:

- Permanently mounted by creating an entry on /etc/fstab (check [this]("https://help.ubuntu.com/community/Fstab")), or
- Use autofs so that it gets mounted automatically only when you access the folder (read [this]("https://help.ubuntu.com/community/Autofs")).

Let us know if you need any help setting those solutions,
Regards.

---

### Post by Frogster on 2011-10-24
Thank you for the pointers, I will check them out this evening and see what is the best solution.

Thank you for your help, its been invaluable in solving this one for me. I have learnt and had a problem solved. A good day

---

