---
title: "No harddrive detected during installation"
date: 2010-05-05
forum: General Help
---

### Post by nextraa on 2010-05-05
Hello,

During the installation of Ubuntu from a LiveCD my harddrive doesn't seem to be detected. I cannot create partitions. I used Gparted to shrink my Windows partition. There's 23 GiB of unallocated space, but it's not being detected. I have tried some suggestions that were posted in this forum but nothing seems to help.

Regards,

Nextraa

---

### Post by dremation on 2010-05-05
I'm not 100% sure why, but I has this same problem and I had to unplug all USB devices except my keyboard & mouse and the problem went away. Not sure if this will be the same fix for you, but it's worth a try.

---

### Post by nextraa on 2010-05-05
I'll try it. Thanks.

---

### Post by dino99 on 2010-05-05
with gparted:
format the unallocated space into:
- 10 go and format it as a bootable root / with ext3 or ext4
- 1 go for swap
- all the unused as /home with ext3 or ext4 to put your data

when formatting, you need to take note of the system path (ie /, should be /dev/sd?, "?" is a letter) because you will be asked by grub to install on it (not over the windows bootloader).

the easiest and secured way is to install with the "alternate" image with unetbootin.

when installation is done, you reboot on ubuntu, then into a console:

sudo grub-mkconfig && update-grub

---

### Post by nextraa on 2010-05-05
Dremation, tried it. Doesn't work. Thanks anyway.

Dino, I'm going to try your suggestion. I already had an ext2 partition, but it wasn't bootable. But this wasn't detected by the install program. I'll get back with results shortly.

Regards,

Nextraa

---

### Post by amlife on 2010-05-05
> **nextraa said:**
> Hello,

During the installation of Ubuntu from a LiveCD my harddrive doesn't seem to be detected. I cannot create partitions. I used Gparted to shrink my Windows partition. There's 23 GiB of unallocated space, but it's not being detected. I have tried some suggestions that were posted in this forum but nothing seems to help.

Regards,

Nextraa

I think your ubuntu CD is unable to detect required drivers to talk to your hard drive, therefore it is unable to see it. 

I'm not sure what to do next! I experienced this few times when installing *windows*, and the solution is to add drivers to windows disk then it would install normally. but I'm not sure how to go about that in ubuntu.

---

### Post by nextraa on 2010-05-05
Dino,

Created with Gparted the following partitions:

20 GB partition /dev/sda3 primary bootable (for / partition and everything else)
3 GB swap /dev/sda4

Started the installation from LiveCD. Still no partions visible in partion portion of install (step 4 of 7).

Do I have to mount the /dev/sda3 partition and what mointpoint should I use?

Regards,

Nextraa

---

### Post by nextraa on 2010-05-05
PS The partitions are ext3 partitions.

---

### Post by nextraa on 2010-05-05
I tried a Mandriva 2009 LiveCD and that goes completely nuts. It doesn't make it through the startup of the LiveCD. There's somekind of error message, but it scrolls by so fast I can't see it. It keeps repeating that error message ad infinitum and the only thing I can do is turn off my computer physically. I think there must be something wrong with my computer, but I don't know what it is. The only thing different is that 1 of my DVD-drives is broken and I detached it from the motherboard. I don't think that's it, but I don't know what else it could be.

Regards,

Nextraa

---

### Post by nextraa on 2010-05-07
Problem solved. I was using a 7.10 LiveCD. A colleague of mine burned the latest version 10.04 for me. I tried that and I could see partitions immediately. Thanks everyone for your help.

Regards,

Nextraa :)

---

