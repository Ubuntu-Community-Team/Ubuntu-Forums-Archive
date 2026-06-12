---
title: "copy ubuntu to a other harddrive"
date: 2009-11-02
forum: General Help
---

### Post by starcraftmaster on 2009-11-02
hey guys
i just want to copy my ubuntu drive to a other drive 

the way i want to do this is to make a image of ubuntu and put it on the other drive thats on the computer

how can i do this? simple way i mean

so copy / to /media/disk


norton ghost 2003 copys the ext3 partition but the image file is 6 kb LOL

---

### Post by Giblet5 on 2009-11-02
For purposes of example, we'll assume that Ubuntu is now on /dev/sda1 and you want to move it to /dev/sdb3:

1: Make an extX filesystem on /dev/sdb3 that is big enough, using your favorite partitioning tool. Then format that partion: ```
sudo mkfs /dev/sdb3
```

2: Mount /dev/sdb3: ```
sudo mount /dev/sdb3 /mnt -text
```

3: Copy everything, preserving timestamps, permissions, and links: ```
cd /
sudo bash ## VERY DANGEROUS!!! ENTER COMMANDS EXACTLY!
find . | grep -ve '^./mnt/' | cpio -op | (cd /mnt ; cpio -ip)
exit
```

That will take awhile. Go get a bagel.

4: Do a quick verify that everything seems to be copied.

5: Install the bootloader: ```
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo chroot /mnt bash ## Gangerous! Follow commands exactly!
update-grub
grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
exit
sudo umount /dev/sdb3
```

6: Reboot. Verify correct operation carefully and thoroughly.

7: Wipe out /dev/sda1 if you don't need it anymore.

---

### Post by Aero-Z on 2009-11-02
Maybe my thread can help you: [http://ubuntuforums.org/showthread.php?t=1305999]("http://ubuntuforums.org/showthread.php?t=1305999")

---

### Post by starcraftmaster on 2009-11-02
> **Giblet5 said:**
> For purposes of example, we'll assume that Ubuntu is now on /dev/sda1 and you want to move it to /dev/sdb3:

1: Make an extX filesystem on /dev/sdb3 that is big enough, using your favorite partitioning tool. Then format that partion: ```
sudo mkfs /dev/sdb3
```

2: Mount /dev/sdb3: ```
sudo mount /dev/sdb3 /mnt -text
```

3: Copy everything, preserving timestamps, permissions, and links: ```
cd /
sudo bash ## VERY DANGEROUS!!! ENTER COMMANDS EXACTLY!
find . | grep -ve '^./mnt/' | cpio -op | (cd /mnt ; cpio -ip)
exit
```

That will take awhile. Go get a bagel.

4: Do a quick verify that everything seems to be copied.

5: Install the bootloader: ```
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo chroot /mnt bash ## Gangerous! Follow commands exactly!
update-grub
grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
exit
sudo umount /dev/sdb3
```

6: Reboot. Verify correct operation carefully and thoroughly.

7: Wipe out /dev/sda1 if you don't need it anymore.



any way i can just do it like norton ghost ? becasue i really dont feel like/have the time to format drives

and i will look at that Aero-Z

---

### Post by ranch hand on 2009-11-02
Or you could just fire up gparted and click on copy and then on paste for each partition you need to move.

---

### Post by outback jack on 2009-11-10
> **ranch hand said:**
> Or you could just fire up gparted and click on copy and then on paste for each partition you need to move.

Nice and simple, thanks for the post.

---

