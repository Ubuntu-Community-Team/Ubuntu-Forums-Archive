---
title: "plz help with fstab problem"
date: 2009-07-08
forum: General Help
---

### Post by codered1444 on 2009-07-08
i went to edit fstab with the usb code for virtual box and the real fstab got removed now in the fstab its just a document with the usb code and nothing else how do i fix it or can i get another one or something (i'm a n00b) plz help

---

### Post by 67GTA on 2009-07-08
/etc/mtab holds a temporary copy of the drives that are currently mounted. You can copy them to fstab. Open a terminal and run 
```
sudo cp /etc/mtab /etc/fstab
``` You will have to add your CDROM, etc. Another easy way would be to boot a live CD and copy the fstab file from it.

---

### Post by codered1444 on 2009-07-08
what do you mean i will have to add my cdrom i did the other thing you told and that got me the fstab file now how would i go about editing that. everytime i type ```
gksudo gedit etc/ftab
``` it comes up with a blank file named fstab

---

### Post by spibou on 2009-07-08
It's /etc/fstab not etc/ftab

---

### Post by 67GTA on 2009-07-08
Make sure the fstab was generated. What does ```
cat /etc/fstab
``` show? Make sure the command spelling is correct. ```
gksudo gedit /etc/fstab
```

---

### Post by codered1444 on 2009-07-08
oh god thanks soooooo much you saved me a lot of hassle thank you so much god i am such a noob

---

### Post by darolu on 2009-07-08
You need to understand how the fstab file works if you want to manually fix it; read these links, should help you solve your problem:

[http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by 67GTA on 2009-07-08
If your not comfortable editing the fstab by hand, just boot a live CD on the machine in question, and copy it. It should be exactly the same as what you had. Be sure to always back up stuff. ```
sudo mv /etc/fstab /etc/fstab.bak
``` then if something like this happens, ```
sudo cp /etc/fstab.bak /etc/fstab
```

---

### Post by codered1444 on 2009-07-09
Thanks guys for all your help really appreciate it

---

