---
title: "What have I done?"
date: 2010-05-08
forum: General Help
---

### Post by Rillow on 2010-05-08
I booted from live CD so I could reformat my drive to ext3 so I could access it from Win XP.

The only thing I get upon boot is a grub error and I can only access anything from the boot CD... :mad::mad::mad::mad::mad::mad:

What do I do?

---

### Post by stinkeye on 2010-05-08
Reinstall ubuntu or repair your mbr with xp disc.

---

### Post by bryanhogan on 2010-05-08
> **Rillow said:**
> I booted from live CD so I could reformat my drive to ext3 so I could access it from Win XP.

The only thing I get upon boot is a grub error and I can only access anything from the boot CD... :mad::mad::mad::mad::mad::mad:

What do I do?


Can you provide more details? 

Is your system dual boot? or are you running linux on an external drive? 

If you system is dual boot, where was grub?

Did you start the install process for ubuntu from the live cd? 

Which live cd did you use?

Do you have a windows recovery partition? or windows xp install cd?

Have you tried the windows recovery mode? that can fix boot loaders

Any other relevant info?

---

### Post by QLee on 2010-05-08
[QUOTE=Rillow]I booted from live CD so I could reformat my drive to ext3 so I could access it from Win XP.

The only thing I get upon boot is a grub error and I can only access anything from the boot CD... :mad::mad::mad::mad::mad::mad:

What do I do?[/QUOTE]

I'm going to make a guess at the subject you stated, "What have I done".

Presumably, you had ext4 for Ubuntu when you started.

Grub in the MBR was pointing to the partition you formatted as ext3, after formatting the UUID on the partition was changed as well as all files gone and thus the MBR was trying to send GRUB to someplace that no longer existed. 

As stated by stinkeye, I think easiest way at this point would be to reinstall to that ext3 partition and when GRUB2 installs to the MBR and creates a new grub.cfg it will have the correct UUID for your boot partition.

It's always a good idea to state the exact error message, they often lead you in the right direction.

---

### Post by dino99 on 2010-05-08
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

