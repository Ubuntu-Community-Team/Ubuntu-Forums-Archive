---
title: "Karmic can't find optical drive"
date: 2010-01-03
forum: General Help
---

### Post by Aurora on 2010-01-03
Hello,

I cannot play or rip CDs or DVD's, or install updates because of this.

The device is listed in fstab (edited for brevity):

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
            0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

cdrom0 is listed under "Places" in the menu.  When I try to open it, here's the error:

**Unable to mount cdrom0**
mount: special device /dev/scd0 does not exist

I used the error as a search term in these fora, but did not come up with the same problem, at least not in a solved posting.

Running updates fails; Synaptic and aptitude ask for the DVD, but can't read it when I put it in.  It also asks for the DVD when I install packages, but sometimes can install them from the network anyway; other times the files don't download.

I can boot the computer from this drive with a live DVD.  When booted from the HDD, it disappears:confused:

I eagerly await a solution.

Thanks,

Paul in Seattle

---

