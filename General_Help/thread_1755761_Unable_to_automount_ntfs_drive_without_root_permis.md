---
title: "Unable to automount ntfs drive without root permission"
date: 2011-05-11
forum: General Help
---

### Post by josephellengar on 2011-05-11
Hi. I have the following line in my fstab:

```

# external hard drive
UUID=4DDD273633F3859D /home/ross/external ntfs-3g auto,exec,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

```

When I plug in the drive with this UUID, I get the following error:
```

Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```

Is there any way that I can mount this drive (which must be ntfs-formatted) without root permissions? I have googled this error and it seems that many other people are having this same problem, but I can't find a real solution. Most people suggest just reformatting the drive.

---

### Post by blind2314 on 2011-05-11
> **josephellengar said:**
> Hi. I have the following line in my fstab:
 
```

# external hard drive
UUID=4DDD273633F3859D /home/ross/external ntfs-3g auto,exec,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

```
 
When I plug in the drive with this UUID, I get the following error:
```

Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```
 
Is there any way that I can mount this drive (which must be ntfs-formatted) without root permissions? I have googled this error and it seems that many other people are having this same problem, but I can't find a real solution. Most people suggest just reformatting the drive.
 
I know this seems like a "duh" question, but have you tried to re-install NTFS-3G under your normal account? The link it gives shows how to make it a setuid binary, so if you can get it compiled with FUSE integrated and run those two commands, it should allow you to mount it as yourself. Otherwise, I don't know of a way other than using root privileges :/

---

### Post by josephellengar on 2011-05-11
> **blind2314 said:**
> I know this seems like a "duh" question, but have you tried to re-install NTFS-3G under your normal account? The link it gives shows how to make it a setuid binary, so if you can get it compiled with FUSE integrated and run those two commands, it should allow you to mount it as yourself. Otherwise, I don't know of a way other than using root privileges :/

Is there a way to simply allow myself to mount/unmount things using sudoers?

---

### Post by blind2314 on 2011-05-11
> **josephellengar said:**
> Is there a way to simply allow myself to mount/unmount things using sudoers?
 
I'm fairly certain sudoers is setup to allow that by default..```
sudo mount <options> <drive> <mountpoint>
``` should work just fine.

---

### Post by ajgreeny on 2011-05-11
This may be seeming like teaching grandmother to suck eggs, to use an old British saying, but does ** /home/ross/external**  exist?  I would expect a different error if it did not, but thought it worth the question.

Just to try something else, what happens if you use the disk mounter applet in the panel to mount the partition?

---

### Post by josephellengar on 2011-05-11
> **ajgreeny said:**
> This may be seeming like teaching grandmother to suck eggs, to use an old British saying, but does ** /home/ross/external**  exist?  I would expect a different error if it did not, but thought it worth the question.

Just to try something else, what happens if you use the disk mounter applet in the panel to mount the partition?

Yes the directory exists, and if I use the disk mounter applet I get the same error.

---

### Post by drammock on 2011-06-19
> **blind2314 said:**
> I know this seems like a "duh" question, but have you tried to re-install NTFS-3G under your normal account? The link it gives shows how to make it a setuid binary, so if you can get it compiled with FUSE integrated and run those two commands, it should allow you to mount it as yourself. Otherwise, I don't know of a way other than using root privileges :/

I'd just like to point out that the link given in the error message now redirects to the TUXERA homepage, and there is no obvious corresponding page in that domain that gives the information referenced above.  So if someone who knows how could reproduce that information here (i.e., how to rebuild ntfs-3g with FUSE and with uid=root), it would be appreciated.

---

