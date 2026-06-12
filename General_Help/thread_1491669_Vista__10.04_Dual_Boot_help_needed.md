---
title: "Vista / 10.04 Dual Boot help needed"
date: 2010-05-23
forum: General Help
---

### Post by ratagain on 2010-05-23
Hey All, 

I am having some trouble finding a post that deals with what I've got going on so sorry if it is covered else where.

I have 3 hard drives: one with vista installed on it working fine, one with 10.04 installed on it and working fine and the last is just a media storage drive.

Currently I have been unplugging the windows or ubuntu drive depending on which OS I want to boot. What do I need to do so that I don't have to physically disconnect the drives and can just pick which OS to boot on power up? Do you all need any other info to help answer the question?

Thanks in advance!
Dave

---

### Post by alexpwnsn00b2 on 2010-05-23
mmm I'm no expert, but this should work. Plug both and when you boot up get into the BIOS menu and set which hard drive you want to use as the first thing to boot.

---

### Post by techunit on 2010-05-24
ok you need to plug in both hardrives and boot into the bios. then find where to set which to be booted from first. select the ubuntu one and give it the highest priority. exit from the bios. you should be loaded into ubuntu... 

from here open a terminal and type

```
sudo update-grub
```

now reboot.. you should now have a menu to select which os you want to use

---

### Post by ratagain on 2010-05-24
Awesome, that did the trick. I had done the Bios option but it was the update-grub that was the missing link.

Thanks for the help!

---

