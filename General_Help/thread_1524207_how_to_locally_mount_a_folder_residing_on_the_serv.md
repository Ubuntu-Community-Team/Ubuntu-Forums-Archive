---
title: "how to locally mount a folder residing on the server"
date: 2010-07-04
forum: General Help
---

### Post by raymondvillain on 2010-07-04
I have been able to do this before but somehow it quit working.

I have 2 linux machines, one running Ubuntu Server.  A particular folder, /srv/common_folder, resides on the server.

So on the other (not the server) machine, I edited the file /etc/fstab to include this line:

SERVER_NAME:/srv/common_folder /mnt/local_folder_name nfs _netdev,rsize=8192, wsize=8192,soft 0 0

When I boot everything up, there is indeed a folder on the other machine, /mnt/local_folder_name, but it is empty.  I cannot see the files that are in the folder on the server.

Is there something else I need to be doing?

---

### Post by anglican on 2010-07-05
> **raymondvillain said:**
> I have been able to do this before but somehow it quit working.

I have 2 linux machines, one running Ubuntu Server.  A particular folder, /srv/common_folder, resides on the server.

So on the other (not the server) machine, I edited the file /etc/fstab to include this line:

SERVER_NAME:/srv/common_folder /mnt/local_folder_name nfs _netdev,rsize=8192, wsize=8192,soft 0 0

When I boot everything up, there is indeed a folder on the other machine, /mnt/local_folder_name, but it is empty.  I cannot see the files that are in the folder on the server.

Is there something else I need to be doing?
The folder /mnt/local_folder_name is just the mount point for your nfs mount, and if it isn't mounted then all you will see is an empty folder. It looks like the mount is failing for some reason. What do you see if you try to mount it manually:
```
sudo mount /mnt/local_folder_name
```My guess is that you're not exporting it from the server. On the server you need to make sure the package nfs-kernel-server is installed (otherwise run "sudo apt-get install nfs-kernel-server") then add an entry in /etc/exports for the directrory:
```
/srv/common_folder CLIENT_NAME (rw,no_subtree_check,sync)
```then run "exportfs -ra" to export it and try mounting again.

H

---

### Post by raymondvillain on 2010-07-05
Thanks very much, anglican.

I tried those things, pretty much.  When I issued the "mount" command from a terminal window, I received an error message:

"DNS resolution failed for SERVER_NAME: No address associated with hostname"

But I had successfully pinged the server using the ip address, so I knew that the server was visible.

So I replaced SERVER_NAME with the numerical address, 192.168.0.252, and it worked.  Then I edited the fstab file and did the same thing, and, Voila!  I can automatically mount the folder contents to the local machine.

I don't know why this should happen, but at least I'm up and running now, and I'll mark this thread solved.

---

### Post by anglican on 2010-07-06
> **raymondvillain said:**
> Thanks very much, anglican.

I tried those things, pretty much.  When I issued the "mount" command from a terminal window, I received an error message:

"DNS resolution failed for SERVER_NAME: No address associated with hostname"

But I had successfully pinged the server using the ip address, so I knew that the server was visible.

So I replaced SERVER_NAME with the numerical address, 192.168.0.252, and it worked.  Then I edited the fstab file and did the same thing, and, Voila!  I can automatically mount the folder contents to the local machine.

I don't know why this should happen, but at least I'm up and running now, and I'll mark this thread solved.
Maybe adding an entry in /etc/hosts on the client would have solved this:

```
192.168.0.252        SERVER_NAME
```Anyway, glad it's sorted now.

H

---

