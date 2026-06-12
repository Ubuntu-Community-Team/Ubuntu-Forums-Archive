---
title: "mountpoint command in ubuntu ( /bin/mountpoint)"
date: 2009-11-26
forum: General Help
---

### Post by musarraf172 on 2009-11-26
Can anybody tell me about the command "mountpoint" which is located in /bin. 

It is not working in my system. If I try "mountpoint --help" in terminal it says "bash: /bin/mountpoint: cannot execute binary file"

I am having problem to configure uswsusp . It tells me the mountpoint command error...

---

### Post by audiomick on 2009-11-26
try 
```
man mountpoint
```

---

### Post by solar george on 2009-11-26
```

# man mountpoint
MOUNTPOINT(1)                                                                  Linux System Administrator's Manual                                                                 MOUNTPOINT(1)

NAME
       mountpoint - see if a directory is a mountpoint

SYNOPSIS
       /bin/mountpoint [-q] [-d] /path/to/directory
       /bin/mountpoint -x /dev/device

DESCRIPTION
       Mountpoint checks if the directory is a mountpoint.

OPTIONS
       -q     Be quiet - don't print anything.

       -d     Print major/minor device number of the filesystem on stdout.

       -x     Print major/minor device number of the blockdevice on stdout.

EXIT STATUS
       Zero if the directory is a mountpoint, non-zero if not.

```
as for your error, maybe try to reinstall the package containin mountpoint
```
sudo  aptitude reinstall initscripts
```

---

### Post by musarraf172 on 2009-11-26
> **solar george said:**
> ```

# man mountpoint
MOUNTPOINT(1)                                                                  Linux System Administrator's Manual                                                                 MOUNTPOINT(1)

NAME
       mountpoint - see if a directory is a mountpoint

SYNOPSIS
       /bin/mountpoint [-q] [-d] /path/to/directory
       /bin/mountpoint -x /dev/device

DESCRIPTION
       Mountpoint checks if the directory is a mountpoint.

OPTIONS
       -q     Be quiet - don't print anything.

       -d     Print major/minor device number of the filesystem on stdout.

       -x     Print major/minor device number of the blockdevice on stdout.

EXIT STATUS
       Zero if the directory is a mountpoint, non-zero if not.

```
as for your error, maybe try to reinstall the package containin mountpoint
```
sudo  aptitude reinstall initscripts
```

Thanks solar george or your prompt and valuable reply. This solved my problem. Ubuntu forum rocks...........:D:D:D

---

### Post by solar george on 2009-11-26
> Thanks solar george or your prompt and valuable reply. This solved my problem. Ubuntu forum rocks...........

No problem, have fun

---

