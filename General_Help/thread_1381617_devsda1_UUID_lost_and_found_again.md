---
title: "/dev/sda1 UUID lost and found again"
date: 2010-01-15
forum: General Help
---

### Post by karg on 2010-01-15
Hello, I'm using Ubuntu 9.10. It happened 2 times so that my /dev/sda1 lost its UUID for some reason or another. This led to the problem that the Ubuntu no longer booted but only said these things:

"Waiting for root filesystem.."

and then complained that the disk specified by ROOT=UUID=.... was not found and then it just failed to shell.

Sounds familiar to anyone? 

The first time I spent too many hours to figure out the problem with Google -> got angry and reinstalled the Ubuntu. Luckily it was only the day 2 for the current 9.10 installation.

The second time I tried to cool down at first and then did this after thinking a bit:

1. I changed Grub startup parameters in Grub menu for the latest kernel a bit:
    - removed the line that starts with "search"
    - changed ROOT=UUID=.... to ROOT=/dev/sda1

   * after those changes I could boot up the Ubuntu again!

2. update-grub2 -> grub.cfg was now also setting "ROOT=/dev/sda1" because it didn't find the UUID value.

3. I still wasn't happy with that although now the Ubuntu was booting again just fine. The disk manager said that /dev/sda1 is of "unknown" type. I still managed to get its UUID with "dumpe2fs" and also /etc/fstab was showing the UUID value (in comments) that should be in /dev/sda1.

4. Cheked /dev/disk/by-uuid/ and noticed that the UUID symbolic link for /dev/sda1 was just missing! I don't know why was that, but thought that it might be the problem source. 

Guess what... I just created the symlink <UUID> -> ../../sda1 and then update-grub2 and reboot.

Ubuntu was back to normal again! Disk manager also recognized the /dev/sda1 normally.

:popcorn:

I hope this helps somebody because I saw a lot of similair writings on internet but no solution for my case...

---

### Post by vijay_uforum on 2010-01-22
thanks

---

### Post by vikram0460 on 2010-01-22
thanks..................

---

### Post by ShawnB391 on 2010-01-22
This seems like the solution to my problem, however, I don't fully understand the directions. Could you please describe the steps to me in detail? I am a beginner who is experiencing the same problem stated above.

---

### Post by Köppchen on 2010-01-24
I had exactly the same issue, the uuid of the ext4 was lost some reason. I have used your first steps to recover from the problem (using the device, in my case /dev/sda5). Is there a ticket in launchpad already?

---

### Post by tiroxino on 2010-04-02
I report the same problem. For some reason, the uuid of my /home partition was lost and, in order to solve it, I needed to open fstab, comment the line for /home partition and change it to /dev/sda4 instead uuid. Then I reboot and put back the uuid in fstab. 
It worked, but now I'd like to know why it happened?!

---

### Post by Irony on 2010-04-02
Grub 2 and uuids are rubbish.

---

### Post by pierre.fr34 on 2010-05-08
I had also the same problem. So I changed grub parameters as Karg suggested but in recovery mode. Then I get the opportunity to directly update grub (without booting). After that, it rebooted normally (no need to add symlinks). Really strange !

Anyway, many thanks for your help

(Ubuntu Karmic)

---

