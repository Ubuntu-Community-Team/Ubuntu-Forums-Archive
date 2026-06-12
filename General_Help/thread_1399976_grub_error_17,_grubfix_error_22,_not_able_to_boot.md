---
title: "grub error 17, grubfix error 22, not able to boot"
date: 2010-02-06
forum: General Help
---

### Post by cholericfun on 2010-02-06
Hi

not sure what happened, yesterday i installed the new kernel and played around a bit by uninstalling some older kernels. Everything was fine but now i cant boot into ubuntu any more. I have a Dual boot and Grub let me boot into windows. for linux grub gave error 17 (if i remember correctly).
So i popped in the LiveCD and tryed gparted to check for errors (nothing changed). I tried rewriting grub from the live cd and that made matters worse.

```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,3)
grub> root (hd0,3)
root (hd0,3)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,3)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition

```

now all i get upon booting is "loading grub stage 1.5" flying down the screen

no grub to boot even windows off.
will be searching for hints on the web now but help is appreciated!
(btw. its 8.04, and i'm on a 9.10 LiveCD - but just installed "legacyGrub")

---

### Post by cholericfun on 2010-02-06
theres the RESULTS from the bootinfoscript if thats of any help

one thing i noticed is a problem i had before in that using "grup-update" after removing and installing kernels the menu.lst entry pointed at the wrong partition (the swap partition - hd0,2 instead of the hd0,3) maybe that was the initial problem but now it seems to be of no use anymore since grub stage 1_5 is broken.

(i did edit the menu.lst and changed all the (hd0,2) entries to the correct one but grub setup still didnt proceed normally)

---

### Post by cholericfun on 2010-02-06
just played around as root from the liveCD - not too knowledgebal bout root status but something odd struck me
from first post - grub does find the HD, finds stage2 (on the partition as far as i can recognise), everything ok,
then it turns around and says the partition does not exist when trying to write to it...
so heres what i found as root: the HD is seen as sda in the /dev/sd* entry
but theres no sda1 - sda4 as there should be - actually theres no sda1-4 in normal user mode either which is odd since i have all 3 (not the swap) partitions mounted.
and when i try:
```
root@ubuntu:/dev# mount /dev/sda /media/bunt
mount: unknown filesystem type 'nvidia_raid_member'

```

raid?
theres no raid? or is that just some generic errormessage?



Some more trial and error :
```
sudo grub-install --root-directory=/media/1f40b14c-2182-4582-90fc-c4ee97607211/ /dev/sda 
/dev/mapper/nvidia_fbjhgiaj4 does not have any corresponding BIOS drive.

```

what does that mean now?

```
sudo grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```

the entry in the /boot/grub/device.map file is
```
(hd0)   /dev/sda

```

---

### Post by cholericfun on 2010-02-06
AHA!

problem was trying to use a karmic CD to repair a hardy install!

i dug out the old hardy liveCD and all went smoothly!

no funny errors.

---

