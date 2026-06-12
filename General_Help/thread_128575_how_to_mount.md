---
title: "how to mount"
date: 2006-02-11
forum: General Help
---

### Post by Disastorm on 2006-02-11
how do i mount my first hd (ntfs) , so that i can access it.  I need some files from there to get my broadcom wlan working.  I use to know how to use the mount command but i forgot since then lol.

---

### Post by taurus on 2006-02-11
sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows
sudo cd /mnt/windows
sudo ls -la

---

### Post by Disastorm on 2006-02-11
ok this might be stupid but when i do sudo /mnt/windows it says 
cd: command not found

yet when i just do cd /mnt/windows it says 
permission denied

*edit* oh i just got in by doing 
sudo -i
then cd /mnt/windows

---

### Post by taurus on 2006-02-11
[QUOTE=Disastorm]ok this might be stupid but when i do sudo /mnt/windows it says 
cd: command not found[/QUOTE]
My post said

sudo cd /mnt/windows

:rolleyes:

---

