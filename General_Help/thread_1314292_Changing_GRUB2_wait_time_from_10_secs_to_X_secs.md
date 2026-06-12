---
title: "Changing GRUB2 wait time from 10 secs to X secs"
date: 2009-11-04
forum: General Help
---

### Post by MC707 on 2009-11-04
Hello Linux users. I am having a little issue (actually a lot of them, but I'll wait for updates ;)). My grub menu has vista apart from Ubuntu, so it waits 10 seconds instead of just going directly to Ubuntu like other machines I have with Ubuntu. I tried using the command [in this post]("http://ubuntuforums.org/showthread.php?t=318933"), however that only opens a blank menu.1st file, as well as the fact it is two years old. Thus, karmic has the new grub2, so maybe the directory has changed or something... anyway I want to make it so it chooses Ubuntu in 2 secs instead of 10. Thanks in advance.

Regards

---

### Post by tuwe on 2009-11-04
The setting you are looking for can be found in /etc/default/grub.

Edit the line GRUB_TIMEOUT=10 to your needs, and run sudo update-grub afterwards.

---

### Post by MC707 on 2009-11-04
To complete your answer (and anyone else that has this problem), run in terminal 
```
sudo gedit /etc/default/grub
```
edit the "GRUB_TIMEOUT=10" line and then save and exit. Finally, run 
```
sudo update-grub
```
Thanks for pointing out the new grub file and its new location.

Regards

---

### Post by Huss on 2010-12-26
Thanks ;)

---

