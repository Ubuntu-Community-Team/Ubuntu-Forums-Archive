---
title: "sudo problems"
date: 2010-01-04
forum: General Help
---

### Post by cucuru on 2010-01-04
hello, I have a problem, I changed the own of all the etc folder, it was a mistake, but I can't change it again, now, I cant use "sudo" because root is not the own.

When I try to use "sudo" this is the error:

sudo: /etc/sudoers is owned by uid 1000, should be 0

so, the own is my user instead of the root. How can I change it again?

Thanks. Regards

---

### Post by DasEi on 2010-01-04
use a live-cd and chmod it back

here are mine, non altered ones : [http://pastebin.com/f3eac4c8c](http://pastebin.com/f3eac4c8c)

---

### Post by cucuru on 2010-01-04
Is that the only way? I have to change it in a server, and I can't go there. I'm trying:

chown root:root /etc/sudoers


but it says that it isn't allowed.


Thanks. Regards

---

### Post by prshah on 2010-01-04
> **cucuru said:**
> I changed the own of all the etc folder, it was a mistake, 

sudo: /etc/sudoers is owned by uid 1000, should be 0

so, the own is my user instead of the root. How can I change it again?


You can use either recovery mode (from GRUB startup menu) or a live CD.

If you can boot into recovery mode, you will get a maintenance menu. Choose "Root Terminal" (or similar) option. Then at the command line give the command```
chown root:root /etc/sudoers
``` (Note no need to use sudo). Then reboot with the command```
reboot
```.

If that doesn't work, boot with a live CD. Open the terminal (Applications-Accessories-Terminal) and give the following commands```
sudo mount /dev/sdX9 /mnt -o defaults,rw
sudo chown root:root /etc/sudoers
sudo umount /mnt
sudo reboot
```

(Replace /dev/sdX9 with the actual partition that contains the "/etc" file system)

Note that these will fix ONLY your sudoers files. You should also fix the other files/directories in /etc to have the correct owner. Most files are root:root (user:group) but some files are different. You will have to study a regular installation to know what files belong to what user:group. 

Please post back here if you want more help on this matter.

---

### Post by cucuru on 2010-01-04
Thank you for your reply, I tried the first one, but it didn't work.9.10

I have ubuntu server 9.10.

I'm not sure I understand the CD option. I start with the CD with the probe Ubuntu Server without any changes in your computer?

and, after change what you say?

Thank. Regards

---

### Post by rnerwein on 2010-01-04
hi
even if you can change it --> be careful not all files in the folder /etc belongs to the group root
ciao

---

### Post by cucuru on 2010-01-05
Thank you! finally I could solve it! I don't know why it allowed me but I have it!, I put the values as the DasEi ones.

Regards

---

