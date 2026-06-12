---
title: "Full HDD encrypted LVM grub failure error out of partition grub rescue"
date: 2011-01-20
forum: General Help
---

### Post by Ex_Machina on 2011-01-20
Hello folks,

I have a LVM encrypted HDD and running into the problem now that the boot partition is damaged or whatever, it's tripping anyway.

The error is:
```
error: out of partition.
grub rescue>

```

Been trying a lot of things, I can succesfully mounted the encrypted partition from a live usb, fsck told me that there is a lot wrong with /dev/sda1 where grub is installed but everything seems fine with the encrypted space.

I have been looking into tutorials how to fix this and I came across this:
[http://forums.aria.co.uk/showthread.php?t=16377](http://forums.aria.co.uk/showthread.php?t=16377)

I have been hovering above the install button for some time but I was too scared to lose any data, I did however tried the `normal` things which had no success like trying to install grub on it.

I think I need some grub2 with lvm support, how can I install this manually or shall I use the install button anyway?

I have been head banging my head against the wall for some time now and my work starts in ~7 hours and it all has to be fixed by then and I prefer to sleep for some hours before I have to work.

Please help me out a hand if you can, would be greatly appreciated.

---

### Post by psusi on 2011-01-20
Please run this script and post the output:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Ex_Machina on 2011-01-21
> **psusi said:**
> Please run this script and post the output:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

# cat Error_Log 
boot_info_script.sh: 307: declare: not found
boot_info_script.sh: 311: declare: not found
boot_info_script.sh: 314: declare: not found
boot_info_script.sh: 323: Syntax error: "(" unexpected

# cat Trash 
ls: cannot access /dev/hd?: No such file or directory
dmraid is /sbin/dmraid

---

### Post by psusi on 2011-01-21
I don't know what you did, but it doesn't look like running the script.  You also need to run it with sudo.

---

