---
title: "Running out of disk space -- how can I get more?"
date: 2011-05-07
forum: General Help
---

### Post by Daanii on 2011-05-07
I have a dual boot system that only has about 6.5 GB of total file space for Ubuntu on the disk. Recently I upgraded to 11.04, and have had problems logging on and in downloading and installing programs. Occasionally I get messages that say available memory [edit: I meant disk space, not memory] is too low.

I see from the disk analyzer that a folder called tmp is very large. Can that file be safely deleted? Anything else to clean up and scavenge more space?

---

### Post by doas777 on 2011-05-07
just to clarify, does the message say that "memory" is low, or that "disk space" is low. memory refers to RAM, rather than hard disk space.

don't clear temp on a running system, but it should be safe to clear from a live CD session.

---

### Post by Daanii on 2011-05-07
It says disk space. Not memory (sorry for the mistake). Both the total file space and now the root seem to be bumping right up against the limit.

---

### Post by Daanii on 2011-05-07
For example, I get the following at the end of a long string of downloading and unpacking statements when I tried to add a package:

```

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.38-8-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Grisk13 on 2011-05-07
Well, this comes down to partitioning.  One possible solution is to shrink your Windows (I'm assuming) partition and adding a new partition for programs/documents.  

You can shrink your windows partition in Computer Management -> Disk Analyzer, and you can use a FOSS tool like gParted to format a new linux partition.  Honestly, it might be easier to just re-install Ubuntu, though.

---

### Post by drs305 on 2011-05-07
I wrote this guide for finding files and folders that are taking up more space than is normal. You might get some ideas from it.
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by oracle2b on 2011-05-07
Saving valuable hard disk space
Each time you install an application using apt-get, the package is actually cached in a location on your hard disk. It is usually stored in the location /var/cache/apt/archives/ . Over a period of time, all the cached packages will eat up your valuable hard disk space. You can clear the cache and release hard disk space by using the following command:

> sudo apt-get clean

---

### Post by Daanii on 2011-05-07
Thanks for all the comments and suggestions. I cleaned up several things, per various suggestions, and got my free space to 666 MB. That gave me a little breathing room. 

Then as suggested by drs305 in his excellent post on cleaning up, I looked for big files. The results amazed me by my own stupidity. I had downloaded a 2.0 GB file so I could put it on a flash drive to install Linux on a BeagleBoard. When extracted the file expands to 3.5 GB. That is space I do not have. 

So I deleted the bloated file, and now have 3.1 GB available out of 6.5 GB. That's plenty. 

Again, thanks for all comments and suggestions.

---

