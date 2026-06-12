---
title: "Formatting USB Drive w/ Label"
date: 2009-12-15
forum: General Help
---

### Post by CarlosinFL on 2009-12-15
I have a new USB flash drive and need to format this. My main question is, I am using Ubuntu 9.10 and **DO NOT** have X Windows installed and or configured. I am simply using CLI only. I would like to know how I can format this USB flash drive as FAT32 and also place a label during the formatting command. When I use this USB flash drive in machines that do have a GUI, I want the drive to be recognised as "data" via the label I assign. Can someone please help me with the command I would need to run in order to create a label on my flash drive?

Can anyone help me? I tried the following and it didn't work:

```
root@tunafish:~# umount /dev/sdc1
umount: /dev/sdc1: not mounted
root@tunafish:~# mlabel -i /dev/sdc1 ::usb
Total number of sectors (31879958) not a multiple of sectors per track (32)!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test
```

---

### Post by andrewc6l on 2009-12-15
If you edit your ~/.mtoolsrc file and add the line:
mtools_skip_check=1

does it work?

More details are here:
[http://www.informatik.uni-hamburg.de/RZ/software/mtools/mtools_5.html](http://www.informatik.uni-hamburg.de/RZ/software/mtools/mtools_5.html)

---

