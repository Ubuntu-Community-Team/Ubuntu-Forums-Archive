---
title: "symbolic links  vs bind mounts"
date: 2012-09-17
forum: General Help
---

### Post by roy.nico on 2012-09-17
Hello Community, 

I would like to ask your opinion about the differences in practice between the following two methods:
* mount with option "bind"
* symbolic link

Reason of my question  : My data (documents, music, photos, etc...) lie on different partitions that are mounted at startup, and from each user account, I refer to htese mounted directories with one of the above mentionned methods. For example :

* my /home lies in the partition sda1. It contains subdirectories /home/user1 and /home/user2.
* Data for all users are in the partition sda2, which is mounted at startup in /data. It contains /data/user1 and /data/user2 which respectively contain directoris "Documents", "Images" ...

Method 1 (for user1):
* There is a directory /home/user1/Documents which is empty
* I have e bind mount (in fstab)
 /data/user1/Documents /home/Documents none  rw,bind 0 0 

Method 2 (for user2)
* There is a symbolic link /home/user2/Documents pointing to /data/user2/Documents

What is in your opinion the advantages/drawbacks of each method ? 
Thanks

nicolas

---

### Post by Morbius1 on 2012-09-17
I use bind mostly because I use Samba to share folders across the network and Samba does not allow a client to follow symlinks. There is a way to override this default setting but Samba regards it as a security issue. 

The other thing for me is that I truly don't like symlinks although there's no logical reason for that. I don't use fstab for bind instead opting for having it mounted in a Upstart job at boot but either way you can look at fstab or the Upstart job and always see the complete list of folders that you are linking together.

---

