---
title: "uninstall win7 (dual boot with ubuntu)"
date: 2010-06-05
forum: General Help
---

### Post by chchew90 on 2010-06-05
Currently i am dual boot win7 and ubuntu, and the win7 is installed first in C drive, then ubuntu 10.04 is installed in D drive, my question is can i uninstall win7 and just keep the ubuntu on my machine?

---

### Post by TeoBigusGeekus on 2010-06-05
Of course. Just run gparted from ubuntu and format the windows partition.

---

### Post by chchew90 on 2010-06-05
oh..i will try it..thx

---

### Post by chchew90 on 2010-06-05
erm..i am not understand what is mean by gparted?can anyone explain it?

---

### Post by wilee-nilee on 2010-06-05
> **chchew90 said:**
> erm..i am not understand what is mean by gparted?can anyone explain it?

Is this a true dual boot or a wubi install? The use of lettered drives is confusing, in Linux speak.

---

### Post by Jakiejake on 2010-06-05
> **chchew90 said:**
> erm..i am not understand what is mean by gparted?can anyone explain it?

Download Gparted [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Burn and boot
Unistall the windows part (Partition)

---

### Post by Leppie on 2010-06-05
> **Jakiejake said:**
> Download Gparted [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Burn and boot
Unistall the windows part (Partition)

gparted is in the ubuntu repos:
```
sudo apt-get install gparted
```

please be aware that as wilee-nilee said, removing windows from a wubi install cannot be done by just simply formatting the windows partition.

---

### Post by chchew90 on 2010-06-05
currently this is a real dual boot

---

### Post by elliotn on 2010-06-05
Sudo apt-get install gparted  

Then in terminal type

sudo gparted

---

### Post by wilee-nilee on 2010-06-05
> **chchew90 said:**
> currently this is a real dual boot

Just wanted to check many think a install inside of windows is a dualboot, so if you have installed with separate partitions with separate bootloaders gparted as suggested is how to remove windows, you just want to make sure your using the grub to boot, otherwise you will just have to reload it to the mbr.

---

### Post by Leppie on 2010-06-05
> **chchew90 said:**
> currently this is a real dual boot
then once you have removed windows from your system, run update-grub to have it removed from the startup menu as well:
```
sudo update-grub
```
after installing gparted, it's in the menu as well: System>Administration>Gparted

---

### Post by wojox on 2010-06-05
You could always use a LiveCD to use G-Parted.

---

### Post by wojox on 2010-06-05
> **elliotn said:**
> Sudo apt-get install gparted  

Then in terminal type

sudo gparted

You can't use G-Parted when the Filesystem is mounted. :)

---

### Post by Leppie on 2010-06-05
> **wojox said:**
> You can't use G-Parted when the Filesystem is mounted. :)
as it's the windows drive, you can simply unmount it in gparted as well ;)

---

### Post by wojox on 2010-06-05
> **Leppie said:**
> as it's the windows drive, you can simply unmount it in gparted as well ;)

Can you? I didn't think you could do that. I learn something new every day. :P

Sorry elliotn. :)

---

