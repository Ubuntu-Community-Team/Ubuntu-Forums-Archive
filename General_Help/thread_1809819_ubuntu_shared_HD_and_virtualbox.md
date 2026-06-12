---
title: "ubuntu shared HD and virtualbox"
date: 2011-07-22
forum: General Help
---

### Post by g_lev on 2011-07-22
Hello, 
on my Ubuntu I have virtualbox installed. 
I also have a secondary hard drive (FAT) which I share across the network (seen on all windows and mac machines). 
the thing is I need to access the HD from inside the ubuntu server running from virtualbox (without x. only command line).
I tried this tutorial >  [http://youtu.be/BSg-_3OFlrQ](http://youtu.be/BSg-_3OFlrQ) but I got several errors. 
I fixed some by updating the Guestadditions updating the server and installing Build and Kernel Header. 
However still no luck with viewing my HD from inside the server. 
could anybody help me how can I do this?  

thank you.  

p.s. for some reason I see inside the media folder my sf_hdhome but can't access it 
"cd: sf_hdhome: Permission denied". 
my current error is when I try the command 
sudo mount -t vboxsf hdhome /mnt/hdsh 
I get 
/sbin/mount.vboxsf: mounting failed with the error: Invalid argument 
I also tried  
sudo mount.vboxsf hdhome /mnt/hdsh 
but got the same result 
mounting failed with the error: Invalid argument

---

### Post by YesWeCan on 2011-07-22
Hi. You are running Ubuntu as guest OS on Windows as Host OS?
In general,
You need GusetAdditions installed
You need to create a shared folder (folder icon bottom right in VB window)
Then use the mount command and make sure the mount point exists

You might want to run 'mount' to check that the shared folder is not  already mounted. I'm not sure why you have that directory in /media.

---

### Post by Morbius1 on 2011-07-22
Version 4 of Virtual Box automatically mounts the shared folder created in VBox on the host. It places the mount point in /media/sh_share-name.

The reason you cannot access may be because you are not a member of the vboxsf group. Run the following command to see if you are a memeber:
```
id
```If you are not then add yourself:
```
sudo gpasswd -a user-name vboxsf
```You will have to logout and login again on the guest for the group membership to change.

There is no longer a need for any mount commands.

---

### Post by g_lev on 2011-07-22
> **Morbius1 said:**
> Version 4 of Virtual Box automatically mounts the shared folder created in VBox on the host. It places the mount point in /media/sh_share-name.

The reason you cannot access may be because you are not a member of the vboxsf group. Run the following command to see if you are a memeber:
```
id
```If you are not then add yourself:
```
sudo gpasswd -a user-name vboxsf
```You will have to logout and login again on the guest for the group membership to change.

There is no longer a need for any mount commands.

EXCELLENT !!! 
thank you very very much =D>

---

