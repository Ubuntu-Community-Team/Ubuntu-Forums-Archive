---
title: "ubuntu won,t boot"
date: 2011-04-16
forum: General Help
---

### Post by ewientje on 2011-04-16
My computer won,t boot up anymore, i keep getting the following mistake message:
Unable to enumarate usb device on port 2. Don,t know how to skip that, and continue to desktop.
Please help.

---

### Post by suduntu on 2011-04-17
well, did you try to boot after unplugging the usb device?

---

### Post by ewientje on 2011-04-17
no, I tried reinstalling ubuntu with the aid of a livecd, and he wouldn,t write a bootmanager to the first harddrive. That problem is solved now, but i still get unable to enumerate usb device. I think it is looping, and sometimes ubuntu gets through and starts up, but It is still in the background in that loop.

---

### Post by Leppie on 2011-04-17
is this a dual boot or is ubuntu the only system installed?

---

### Post by ewientje on 2011-04-17
ubuntu is the only system. Has been for years.

---

### Post by Leppie on 2011-04-17
then boot off the livecd without any usb drive attached to your system, open a terminal and issue these commands (assuming you do not have a seperate /boot partition):
```
sudo -i
mkdir /mnt/temp
mount /dev/sda1 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub
exit
```

reboot and see if it's working.

---

### Post by ewientje on 2011-04-25
my computer is repaired, and booting again, so i think this thread can be closed.
thank you all for your help. 
i didn't try the command, i just reinstalled ubuntu again, and this time it worked.
I was afraid to use tje above commands,because I have several harddrives attached, and i didn't want to lose the data on the other drives.

---

