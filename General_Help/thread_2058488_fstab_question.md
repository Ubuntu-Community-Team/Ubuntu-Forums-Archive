---
title: "fstab question"
date: 2012-09-15
forum: General Help
---

### Post by bobman321123 on 2012-09-15
UUID=44EBC5660C2616FA /mnt/data ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0


I have this line in my fstab to mount a data partition.
However, I can't seem to extract archives to it. 
Is there a way to make it read/write? 

(bonus points for explaining every part of the fstab entry)

---

### Post by oldos2er on 2012-09-15
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Are you getting permission errors, or something else? A screenshot or text cut-and-paste of the actual error might help.

---

### Post by bobman321123 on 2012-09-15
The screenshot utility seems to hate me today, but here's the text output.
```
tar: Darcey's Website/index3.html: Cannot utime: Operation not permitted
tar: Darcey's Website/index.html: Cannot utime: Operation not permitted
tar: Darcey's Website/index2.html: Cannot utime: Operation not permitted
tar: Darcey's Website/index4.html: Cannot utime: Operation not permitted
tar: Darcey's Website: Cannot utime: Operation not permitted
tar: Darcey's Website: Cannot change mode to rwxrwxr-x: Operation not permitted
tar: Exiting with failure status due to previous errors

```

---

### Post by cjhabs on 2012-09-15
> **bobman321123 said:**
> UUID=44EBC5660C2616FA /mnt/data ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0


I have this line in my fstab to mount a data partition.
However, I can't seem to extract archives to it. 
Is there a way to make it read/write? 

(bonus points for explaining every part of the fstab entry)

This is mounting with uid 1000 - check the /etc/passwd file to see which user id you are - if you are not 1000 this may be the problem.
defaults makes the partition r/w by default
umask 000 creates new files with 777 permissions
I don't know what "windows_names 0 0" does - sorry.

---

### Post by bobman321123 on 2012-09-15
```
joshua@Nero:~$ cat /etc/passwd | grep joshua
joshua:x:1001:1001:Joshua,,,:/home/joshua:/bin/bash

```

This would mean that I'm 1001, not 1000, right?

---

### Post by dcstar on 2012-09-16
> **bobman321123 said:**
> ```
UUID=44EBC5660C2616FA /mnt/data ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```
I have this line in my fstab to mount a data partition.
However, I can't seem to extract archives to it. 
Is there a way to make it read/write? 

```
UUID=44EBC5660C2616FA /mnt/data **ntfs-3g** defaults,nls=utf8,umask=000,windows_names 0 0
```

---

### Post by bobman321123 on 2012-09-16
> **dcstar said:**
> ```
UUID=44EBC5660C2616FA /mnt/data **ntfs-3g** defaults,nls=utf8,umask=000,windows_names 0 0
```

Changing it to 1001 instead of 1000 fixed the problem :) but I'll do the above if I have any more issues.

Thanks,
Josh

---

### Post by Morbius1 on 2012-09-16
Just for clarity,  in Ubuntu and I think in every current distribution ntfs is ntfs-3g:
> >> ls -l /sbin/mount.ntfs
[COLOR=Blue]**l**[/COLOR]rwxrwxrwx 1 root root 13 Apr 30 13:57 /sbin/mount.ntfs -> **[COLOR=Blue]mount.ntfs-3g[/COLOR]**When you specify "ntfs" it automatically links to "ntfs-3g". Been that way since Hardy I believe.

---

