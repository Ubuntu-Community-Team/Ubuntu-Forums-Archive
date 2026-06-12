---
title: "how to umount  the disk?"
date: 2010-04-01
forum: General Help
---

### Post by luofeiyu on 2010-04-01
i want to copy the VCD  to  my disk
what i do  is :
cd /usr/src/modules/cdfs/2.6
sudo insmod cdfs.ko
sudo mount -t cdfs -o ro /dev/cdrom /mnt/cdfs
cp -a  /mnt/cdfs/  /home/pt
but i can't umount it !

pt@pt-laptop:~$ sudo umount /mnt/cdfs
umount: /mnt/cdfs: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

i have to restart it,can i umount it with correct command?

---

### Post by capscrew on 2010-04-02
> **luofeiyu said:**
> i want to copy the VCD  to  my disk
what i do  is :
cd /usr/src/modules/cdfs/2.6
sudo insmod cdfs.ko
sudo mount -t cdfs -o ro /dev/cdrom /mnt/cdfs
cp -a  /mnt/cdfs/  /home/pt
but i can't umount it !

pt@pt-laptop:~$ sudo umount /mnt/cdfs
umount: /mnt/cdfs: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

i have to restart it,can i umount it with correct command?

Try issuing a [FONT="Courier New"][SIZE="3"]cd[/SIZE][/FONT] command at the prompt before you use the [FONT="Courier New"][SIZE="3"]umount [/SIZE][/FONT]command.

The command [FONT="Courier New"][SIZE="3"]cd [/SIZE][/FONT]by itself will put you in your home directory.

---

