---
title: "An error occured while mounting 0"
date: 2011-03-02
forum: General Help
---

### Post by krushaaa on 2011-03-02
hey 

i just installed ubuntu 10.10 64bit and used all the tips from this [http://ubuntuforums.org/showpost.php?p=9328344&postcount=110](http://ubuntuforums.org/showpost.php?p=9328344&postcount=110)

now i get the following error everytime i boot up: An error occured while mounting 0

my fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
# Commented out by Dropbox
# UUID=d6e7fea4-8d5c-4641-a68f-dfe96acd18fb /               ext4    commit=100,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7acd0c09-68f9-4ecf-9792-0868c543f86c none            swap    
sw              0       0

#tmp su ram
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
UUID=d6e7fea4-8d5c-4641-a68f-dfe96acd18fb / ext4 commit=100,errors=remount-ro,user_xattr 0 1

```i followed some steps from here [http://ubuntuforums.org/showthread.php?t=1474478](http://ubuntuforums.org/showthread.php?t=1474478)
sudo blkid
```

/dev/sda1: UUID="d6e7fea4-8d5c-4641-a68f-dfe96acd18fb" TYPE="ext4" 
/dev/sda5: UUID="7acd0c09-68f9-4ecf-9792-0868c543f86c" TYPE="swap"

```so could you tell me what is wrong with my system?

---

