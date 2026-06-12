---
title: "Linux - problem in repairing/recreating ext3 filesystem"
date: 2012-10-11
forum: General Help
---

### Post by gr@ss_h@pper on 2012-10-11
Hi,

This might not be the correct place to ask this question as it's more of a generic Linux filesystem question. But anyway as I am not in any other forum, i thought of asking the Ubunutu Family :)

Ok. So I am on kernel 2.6.32.58-26 with MIPS arch. It's an embedded environment and I can't do desktop like experiments on this.

mount shows:
[COLOR=Green]/dev/sda1 on /xxx type ext3 (rw,sync,relatime,errors=continue,data=ordered)
[/COLOR]
On this partition /xxx some important binaries like kernel image and uboot etc resides. I am not totally sure who mounts it at boot up but it's unmountable on a running system.

[COLOR=Green]>umount /xxx
umount: can't umount /xxx: Device or resource busy[/COLOR]

Now due to something, this filesystem on this partition got corrupted. Now filesystem operations are giving errors:

[COLOR=Green]root@YYY:~ >cd /xxx
root@YYY:/xxx >du -sh
EXT3-fs error (device sda1): htree_dirblock_to_tree: bad entry in directory #137125: inode out of bounds - offset=0, inode=50462976, rec_len=1284, name_len=6
EXT3-fs error (device sda1): ext3_lookup: deleted inode referenced: 137122
du: ./zzz/logs/aaa: Input/output errorEXT3-fs error (device sda1): ext3_lookup:
deleted inode referenced: 137121
du: ./zzz/logs/bbb: Input/output error
...
...
306.3M  .
root@YYY:/xxx >
[/COLOR]
Also during bootup I see this message:

 [COLOR=Green]EXT3-fs warning: mounting fs with errors, running e2fsck is recommended[/COLOR]
  
As I am not able to unmount it, [COLOR=Navy]how can I run e2fsck or fsck.ext3 utilities to repair/recreate this filesystem? Or is there any other way I can recreate the filesystem on /dev/sda1.[/COLOR]

On this system I think I don't have any other option (like desktop) to boot from other media (usb/CD) to mount and repair this partition there.

Please help me in solving this issue.

Many Thanks,
[COLOR=SeaGreen]gr@ss_h@pper[/COLOR]

---

### Post by 2F4U on 2012-10-11
You could try to bring the system into single user mode. As root perform the following steps:

```

[B]init 1
[/B][B]mount -o ro,remount /dev/sda1
[/B][B]e2fsck -f /dev/sda1
[/B]**mount -o remount /dev/sda1**

```

---

### Post by gr@ss_h@pper on 2012-10-12
Thanks 2F4U... This worked for me...

I did
mount -o ro,remount /xxx
 fsck.ext3 /dev/sda1


Then allowed it to repair the filesystem. And it worked.


Many Thanks :)

---

