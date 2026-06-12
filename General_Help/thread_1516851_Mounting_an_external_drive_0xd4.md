---
title: "Mounting an external drive 0xd4"
date: 2010-06-24
forum: General Help
---

### Post by soma_rich on 2010-06-24
I have a HDD from a CCTV system  that I suspect to be Linux based. I cannot see it in Ubuntu. I can see the partitions in the Disk Utility. All it says is Partition type: Unknown(0xd4).

I need to access this CCTV footage any help received would be grateful.

---

### Post by dabl on 2010-06-24
Looks like DOS/FAT16, if I'm understanding [[COLOR="Green"]**this**[/COLOR]](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html) correctly.

---

### Post by soma_rich on 2010-06-24
OK thanks for the prompt reply. Can I just change the type in the Disk Utility and the disk will mount? If not how do I mount it?

Thanks

---

### Post by dabl on 2010-06-24
Because it is saying "unrecognized", I think you are going to have to boot something like a Super Grub Disk (SGD) or Hiren's Boot CD or something like that, to work with it.  I assume one of those will have utilities that will recognize it.

You could try to mount it as a VFAT filesystem, but I'm not real optimistic that it will be recognized:

```
sudo mount -t vfat /dev/sdx /mnt/target
```

and see if there's anything to see at /mnt/target.

---

