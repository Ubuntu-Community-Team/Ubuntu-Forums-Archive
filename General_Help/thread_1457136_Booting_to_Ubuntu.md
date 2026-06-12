---
title: "Booting to Ubuntu"
date: 2010-04-18
forum: General Help
---

### Post by Shinka.S on 2010-04-18
I have 3 hard drives; 

- The first one has Ubuntu 10.04 x86_64
- The second one has Kubuntu 10.04 Beta 2 x86_64
- The third one was empty

I wanted to try CentOS (the OS installed at my job), but now I can only boot to CentOS. I know my data from the first two hard drives is still there, I used the ubuntu live CD to check, but can I also use the live CD to reinstall the ubuntu booting system (I'm pretty sure it would detect the 3 OS, it always does) ?

---

### Post by wojox on 2010-04-18
Sure try this [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Shinka.S on 2010-04-18
Thanks, but I'm an absolute newbie at this: 

Where do I reinstall Grub2 ? I guess I can't reinstall it on CentOS, but if I reinstall it on one of my ubuntu partition, will my computer use it instead of CentOS boot system ?

---

### Post by nerdtron on 2010-04-18
Yes thats true. You can install GRUB2 on your Ubuntu partition. The Ubuntu GRUB should detect CentOS. It will also be used as the default bootloader of your computer.

---

