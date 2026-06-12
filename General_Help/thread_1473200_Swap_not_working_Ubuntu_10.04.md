---
title: "Swap not working Ubuntu 10.04"
date: 2010-05-05
forum: General Help
---

### Post by Saeger on 2010-05-05
The swap partition is not working on my computer, I just upgraded from 9.10 to 10.04.  I don't remember whether it was working or not in 9.10.  Here is the output from TOP:

top - 23:40:29 up 2 min,  2 users,  load average: 2.69, 1.37, 0.52
Tasks: 150 total,   1 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.0%us,  2.0%sy,  0.0%ni,  0.0%id, 93.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    315168k total,   302344k used,    12824k free,    35264k buffers
Swap:        0k total,        0k used,        0k free,   127912k cached

I am new to Ubuntu so I am not quite familiar with UNIX commands yet.  I would like to know how to find the ID of my swap partition (I am positive the there is one) and what lines to add or change in my FSTAB to activate the swap partition.  Thanks!

---

### Post by Ginsu543 on 2010-05-05
It's funny that your swap file doesn't appear to be mounted. Do you have an entry in your /etc/fstab file for your swap partition? If not, you can add it. You need to find out what the address is to your swap file. On my computer, my swap file is /dev/sda3 (it is the third partition on the first SATA hard drive). So it should look something like this:
```

<file system>     <mount point>     <type>     <options>     <dump>     <pass>
/dev/sda3           none                   swap         sw                0                0

```It would be even better if you used the UUID for the swap partition:
```

<file system>     <mount point>     <type>      <options>     <dump>     <pass>
UUID=xxxxxx      none                   swap         sw                 0                0

```To find out what the UUID for all your partitions are, just open Terminal and type this:
```

ls -l /dev/disk/by-uuid

```

---

