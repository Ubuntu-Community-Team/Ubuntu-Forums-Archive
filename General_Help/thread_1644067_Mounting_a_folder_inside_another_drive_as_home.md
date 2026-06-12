---
title: "Mounting a folder inside another drive as /home"
date: 2010-12-12
forum: General Help
---

### Post by pranavashok on 2010-12-12
Hello,

I've been trying to move my home directory to a folder in another drive. Since I couldn't find a direct solution, I came up with the last two lines (of the fstab entries given below) after referring a couple of tutorials here and then. I've also added a couple of <options> myself. Please tell me whether this is the most efficient method of doing this.

```
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    proc            /proc           proc    defaults        0       0
    # / was on /dev/sda5 during installation
    UUID=5d57f089-dca0-403b-8d24-f6a5221b9242	/	ext4	errors=remount-ro	0	1
    # swap was on /dev/sda6 during installation
    UUID=b80220c4-85cf-4ec5-88f7-44e1103aa7b8	none	swap	sw	0	0
    /dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
    UUID=d6030338-977c-4b92-90c9-8245386b8cb0	/media/fedora	ext4	auto,nodev,nosuid,rw,user,sync	0	2 
    /media/fedora/ubuntu/home	/home	auto	bind,gid=46,rw,user,suid,dev,exec,sync	0	0
```

What I intended to do is first mount a partition to /media/fedora. Then I mount /media/fedora/ubuntu/home to /home. The contents of my home folder are located inside /dev/sda1/ubuntu/home (Where sda1 is same as the partition with UUID=d6030338-977c-4b92-90c9-8245386b8cb0)

---

