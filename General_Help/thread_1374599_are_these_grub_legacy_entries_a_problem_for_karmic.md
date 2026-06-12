---
title: "are these grub legacy entries a problem for karmic?"
date: 2010-01-07
forum: General Help
---

### Post by pythonscript on 2010-01-07
I just installed karmic on my netbook, and for the sake of simplicity, I'd like to stick with grub legacy for the time being. Would these grub entries provide any problems to boot both windows and linux?
```

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        bf3bb895-ce78-4f5d-a5f2-cbad3f6b1950
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=bf3bb895-ce78-4f5d-a5f2-cbad3f6b1950 ro quiet 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Windows XP Professional x86
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1
```Windows XP is installed on /dev/sda2, and karmic is on /dev/sda3. I tried to set this up to boot linux without the splash screen (but showing the text). Does all of this look appropriate? I want to make sure it's correct before I overwrite my MBR. Thanks for the help!

EDIT:  I did verify the uuid entries, kernel version, etc, so all of that information is correct. I'm just worried about the formatting and the boot options, in case these have changed with karmic. Thanks!

---

### Post by juancarlospaco on 2010-01-07
It seems OK 
:)

---

### Post by pythonscript on 2010-01-07
Thanks; these are working great, and karmic is running quite well on my netbook. Thanks again for the help.

---

