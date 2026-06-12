---
title: "post-install grub config, 2 ide drives, win2k + ubuntu"
date: 2006-04-07
forum: General Help
---

### Post by caporaso on 2006-04-07
Hello:
Can anyone point me to some information on how to configure grub to allow me to choose between booting off of two hard drives that I have installed? One has win 2k on it, and the other has ubuntu. I just installed the win2k on an old drive that i had around (only had ubuntu on the system before that), and have so far used the system in a 'manual-dual-boot' fashion (i.e. both are set as MASTER and I only supply power to the one I want to boot from).  These are two ide drives on the same cable.

Thanks for any help, I did a bit of looking around in the forums, but couldn't find anything that helped.

--Greg

---

### Post by lha on 2006-04-10
Open terminal (Applications->Accessories->Terminal) and type in following commands
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
Then add
```
title Windows 2000
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
to the end of the file you just opened. Save, shut down and set your drive with Windows as slave.

---

