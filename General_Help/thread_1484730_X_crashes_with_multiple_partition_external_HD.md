---
title: "X crashes with multiple partition external HD"
date: 2010-05-16
forum: General Help
---

### Post by user_cero on 2010-05-16
Hi folks, I'm running 10.04 X86_64. I have this 650 GB External Hard Drive With three partitions: one fat32 and two ext4. Sometimes when I plug the drive in X crashes. I get no response at all from the keyboard but the pointer works. I am able to minimize and maximize windows but i cant close them and i cant click on the top bar. Today the error occurred after I transfered some files from one of the ext4 partitions to a 320 GB External HD(single partition FAT32). I pressed the ctrl + alt+ f1 ( to go to the shell :-/) and this strange lines of code where showing up over and over again:

[XXXXX.XXXXXX] ata1.00:status: {DRDY ERR}

Also the following exception:

[XXXXX.XXXXXX] ata1.00:status: Exception Emask 0x00 SAct 0x0 SErr 0x0 action 0x0

When i came back to X (ctrl + alt + f7) and unmounted the drives every worked fine.

Any ideas of why this might be happening?

---

### Post by DawieS on 2010-05-16
I had a similar problem. One of my 3 PC's froze whenever I plugged in an external USB drive, or even a flash drive. Since the same didn't happen on the other two PC's, I knew it must be a setting somewhere on this PC.

It turned out a BIOS setting on this PC  (Something about reserved memory space for USB). After selecting another option in the BIOS, the freezing stopped. It works perfectly now.:smile:

---

