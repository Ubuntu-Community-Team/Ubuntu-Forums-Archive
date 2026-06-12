---
title: "rearranging grub2"
date: 2010-03-20
forum: General Help
---

### Post by yon2501 on 2010-03-20
ok so i need to know just how to rearrange grub2 to have win7 as the first entry because on this box i use that more then ubuntu, this is my gaming box i rarely turn it on to do anything other then game so id like to have grub set up to boot automatically to windows 7 rather then ubuntu. normally id do this myself but i still dont quite understand how to change the order of the menu entries on grub 2 yet :\ from what ive read i just have to change the number on the boot scripts name? or is it something else, i feel like a total newb >.<

---

### Post by sisco311 on 2010-03-20
> **yon2501 said:**
> ok so i need to know just how to rearrange grub2 to have win7 as the first entry because on this box i use that more then ubuntu, this is my gaming box i rarely turn it on to do anything other then game so id like to have grub set up to boot automatically to windows 7 rather then ubuntu. normally id do this myself but i still dont quite understand how to change the order of the menu entries on grub 2 yet :\ from what ive read i just have to change the number on the boot scripts name? or is it something else, i feel like a total newb >.<

Yes, you have to change the number...:
```
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober
```
Then run:
```
sudo update-grub
```
to generate a new grub.cfg file.

---

### Post by oldfred on 2010-03-20
If all you want is the default to be windows this is another way:

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by yon2501 on 2010-03-20
> **sisco311 said:**
> Yes, you have to change the number...:
```
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober
```
Then run:
```
sudo update-grub
```
to generate a new grub.cfg file.

awesome thanks just what i was looking for

---

