---
title: "mdadm help"
date: 2010-12-31
forum: General Help
---

### Post by cinohpa on 2010-12-31
I recently reinstalled ubuntu to try out 10.10.

I previously was running 10.04 lts with 2 mdadm arrays.

I am trying to reassemble the arrays now and having some trouble.

For example:

```

mdadm --assemble /dev/md0 <the partitions that form the array>

```

gives me 

mdadm: failed to create /dev/md0

I am wondering if assemble is usually used to reassemble an array previously used on a system that would already have information stored about it in the mdadm config file. I'm digging through the mdadm documentation to try to figure out what I should do, but any help, ideas, or pointers to particularly helpful resources would be appreciated.

Thanks.

SOLVED: Lol. Just needed sudo.

```

sudo mdadm --assmeble /dev/md0 devices

```

Works just fine.

Still looking for good resources though. The resource I used when first using mdadm was great. It showed me how to save the information about my arrays to a config file so that they would be ready at boot for me to mount in /etc/fstab.

Still trying to find that particularly helpful resources again.

EDIT: 
I think the resource I was looking for from before can be found here:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

Thanks!

---

