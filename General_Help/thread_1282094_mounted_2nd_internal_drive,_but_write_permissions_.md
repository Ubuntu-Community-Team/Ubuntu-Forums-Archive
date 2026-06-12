---
title: "mounted 2nd internal drive, but write permissions wrong"
date: 2009-10-03
forum: General Help
---

### Post by missmoondog on 2009-10-03
# FAT32 drive for common Windows/Linux application data
/dev/sdb1 /media/SATA320FAT32 vfat iocharset=utf8,umask=000 0 0

after searching around the better part of all day today, i finally found some info that is easy enough for even me to do. now i can write to second internal drive (fat32). sheesh! what a pain. 

how come i read so many posts about this being auto detected for a while now, but obviously not working yet?

i found the answer here, in an archived thread. all i had to do was add "iocharset=utf8,umask=000" in place of "default" and reboot.

[http://ubuntuforums.org/showthread.php?p=2107144](http://ubuntuforums.org/showthread.php?p=2107144)

thought i'd post this as a fresh thread so i could subscribe to it and find it later, when i do another computer. maybe by people replying/viewing, this will get integrated sooner!

edit:
i guess i do still have a question about this too. 
do i need to enable sharing of that hard drive under windows also, to continue making this work. i did that as a brain fart thinking that would solve the problem. i don't really want to do that, if not necessary.

thanks

---

### Post by SoftwareExplorer on 2009-10-03
OK, let me get this strait: you want to share files between ubuntu and windows on the same machine. You want to know if you need to share the drive over the network on windows. If both of my guesses are correct, then you don't need to share the drive over the network on windows.

---

### Post by missmoondog on 2009-10-04
> **SoftwareExplorer said:**
> OK, let me get this strait: you want to share files between ubuntu and windows on the same machine. You want to know if you need to share the drive over the network on windows. If both of my guesses are correct, then you don't need to share the drive over the network on windows.

you understood me perfectly! that doesn't happen often!!

that is exactly what i thought about not having to share also, but first time i've ever tried to share anything between windows and linux.

thank you
thread is totally solved now  :)

---

### Post by SoftwareExplorer on 2009-10-04
> **missmoondog said:**
> you understood me perfectly! that doesn't happen often!!

that is exactly what i thought about not having to share also, but first time i've ever tried to share anything between windows and linux.

thank you
thread is totally solved now  :)

You're welcome. :)

---

