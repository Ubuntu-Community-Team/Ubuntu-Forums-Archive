---
title: "Gparted claims an unmounted drive is mounted?"
date: 2009-08-08
forum: General Help
---

### Post by killpotts on 2009-08-08
Hey all, I have been trying to convert an external hardrive to ntfs so it can be used by a windows machine with Gparted. It gets far enough, however I am given this output:
```
GParted 0.3.8

Libparted 1.8.9

Create Primary Partition #1 (ntfs, 149.05 GiB) on /dev/sdc  00:00:00    ( ERROR )
     	
create empty partition  00:00:00    ( SUCCESS )
     	
path: /dev/sdc1
start: 63
end: 312576704
size: 312576642 (149.05 GiB)
set partitiontype on /dev/sdc1  00:00:00    ( SUCCESS )
     	
new partitiontype: ntfs
create new ntfs filesystem  00:00:00    ( ERROR )
     	
mkntfs -Q -vv -L "" /dev/sdc1
     	
/dev/sdc1 is mounted.
Refusing to make a filesystem here!
```

Which makes sense...except one big problem! sdc1 is not mounted. For some reason Gparted believes it is and will not complete it's task, leaving me with an "unknown" type filesystem. Is there any way around this?

---

### Post by ju2wheels on 2009-08-08
Open a terminal and type:
```

mount

```

And post the result.

Edit: Also are you running on a live cd? Or are you logged into an installed system.

---

### Post by killpotts on 2009-08-08
I was on an actual linux machine ( a laptop that only has ubuntu installed )...which never had any problems till now. Tested it on a different blank external and it worked fine.

I had already tried going into the terminal with "mount" and trying to check it's status\umount it that way all claimed it wasn't mounted.

SO...rather then get my head in a spin, I connected the external to a windows desktop, booted up a Fedora Core 10 Live CD and used that to convert the external to ntfs. Worked fine.:popcorn:

Well now that it's finished and tested I guess this will have to remain a mystery. :KS

---

### Post by dcstar on 2009-08-08
> **killpotts said:**
> 
.......
Well now that it's finished and tested I guess this will have to remain a mystery. :KS

It probably isn't.

When you have your desktop set to automount drives as soon as you create a new partition it is mounted before it can be formatted.

---

