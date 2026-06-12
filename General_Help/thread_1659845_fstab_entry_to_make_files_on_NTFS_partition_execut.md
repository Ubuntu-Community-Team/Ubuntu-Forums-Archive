---
title: "fstab entry to make files on NTFS partition executable?"
date: 2011-01-04
forum: General Help
---

### Post by silenceofnight on 2011-01-04
Hi. 
I'm dual-booting windows and Ubuntu 10.04 (there's always a few things that won't work under WINE). I have a NTFS partition that for my documents and what have you that is shared between the two operating systems. 

My problem is, whenever I try to run an executable that is on that partition, it says:
```
permission denied: <executable name>
```

Which is odd, because when I look at ls -l, everything has the permissions set to 777. I think the problem is likely my fstab entry, as I partially made it myself without really knowing what I was doing. The line for that partition is as follows:
```
/dev/sda5     /home/jeremy/Documents       ntfs         relatime,nls=iso8859-1,rw,users,exec,umask=000,gid=1000,user,owner,uid=1000  0  0
```

Can anyone help me sort this out? Thanks.

---

### Post by bodhi.zazen on 2011-01-04
Linux is not windows and in general will not run windows .exe

You can run some with wine.

---

### Post by silenceofnight on 2011-01-04
Oh, sorry. I guess I didn't explain things very well. When I said that some things wouldn't run under WINE, I was just complaining about having to use Windows :p

Anyway, the problem is that linux executables (including ones that I compile myself) won't run. They don't have any compatibility issues, I just don't seem to have permissions to run them, even though it shows that I do.

**Edit**: Let me also say that these files have been copied from a ext4 partition where they run properly. They also run when copied from the ntfs partition back to the ext4 partition; the only time the executables won't run is when they are actually stored on the ntfs partition. Python scripts will run on that partition, though.

---

