---
title: "Where to house fileserver shared data directories?"
date: 2010-02-14
forum: General Help
---

### Post by noyzy on 2010-02-14
Hi,
In the linux directory structure where, as a best practice should I store fileserver files for access to network users?
Is there a best practice location or would you simply create directories directly above the root like so:

/<Company Name>/Shared/Software/...
/<Company Name>/Data/Administration/Accounts Payable/...

---

### Post by bab1 on 2010-02-14
> **noyzy said:**
> Hi,
In the linux directory structure where, as a best practice should I store fileserver files for access to network users?
Is there a best practice location or would you simply create directories directly above the root like so:

/<Company Name>/Shared/Software/...
/<Company Name>/Data/Administration/Accounts Payable/...

There is a basic guide to the Linux file system [**_[COLOR="Navy"]here[/COLOR]_**]("http://www.pathname.com/fhs/").  My feeling is to make it short.  Originally NFS files were at [FONT="Courier New"]/export[/FONT] and they are described as *exported*.  I have always kept Samba shares at [FONT="Courier New"]/smb[/FONT].  The use of [FONT="Courier New"]/mnt [/FONT]is generally considered the mount point of removable media (e.g. USB drves and flash nmedia).

Why do you need the the structure?```
/<Company Name>/Shared/Software/...
/<Company Name>/Data/Administration/Accounts Payable/...
```

---

### Post by madverb on 2010-02-14
Do whatever you think is best. It doesn't really matter where you put them.

---

### Post by noyzy on 2010-02-14
Thanks,
I think I will house them at /smb/<Company Name>/Data/Administration/Accounts Payable/...

As I will be using samba to share them and therefore it would be a logical location.

bab1; In regards to the structure I had: That's just an example of how I usually setup company filesystems and was only added as an additional explaination of the type of content within the shares.

Thanks again for the guidance guys.

---

### Post by bab1 on 2010-02-14
My point was more toward the need of:```
[COLOR="Red"]**/Data/Administration/Accounts Payable/...**[/COLOR]
```

Do you intend to have any sub directories under ```
<Company Name>
```or ```
/Data
```or ```
/Administration
```etc.

If not then they are not needed.  I my opinion the shared file system should be a simple as possible.  Just my experience.  On one of my servers I have /smb and mount 2 drives (partitions) at [FONT="Courier New"]</smb>/backup[/FONT] and [FONT="Courier New"]</smb>/data[/FONT].  The drive for /smb/backup is mounted only when I backup and it has sub directories for 10 hosts.  This setup holds 2TB of data spread across 1000's of directories.  Remember these are **not** the shares, but rather the mount points for the block devices (partitions).  

Edit: Upon a little reflection I must say that I never think of adding a filesystem without it being on a new partition.  So my comments are in that regard.  I would still use the /smb starting point for flexibility.  This will allow you to add disk space in the future.

---

