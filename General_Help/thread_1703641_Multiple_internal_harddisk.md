---
title: "Multiple internal harddisk"
date: 2011-03-09
forum: General Help
---

### Post by krishna1650 on 2011-03-09
Hi all,

I have two internal harddisk. Harddisk 1 has ubuntu, fedora installed and harddisk 2 has ubuntu installed. I normally connect either one, and use it. How can i always keep connect both harddisks, and at the start, select from which harddisk to boot? Or it's not possible? 

Thanks in advance.

---

### Post by krishna1650 on 2011-03-09
Any idea?

---

### Post by Krytarik on 2011-03-10
I assume you have Grub installed on both disks.

- "connect" both disks
- boot into the OS which comes up then
- enter the following command in a terminal:
```
sudo update-grub
```- done (hopefully ;-)).

Guide to Grub2: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Guide to Grub legacy: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by krishna1650 on 2011-03-21
Thanks for reply. But if i connect both, then nothing comes in the screen, i have nothing to select. Can this be due to different grub version (though it's my guess only, in one harddisk gub2 is installed for surely, on other one, i am not sure) or there is other issue?

Thanks again for your reply.

---

### Post by aaryansh on 2011-03-21
Hey there,

I think you should reinstall grub2 again, after connecting both the disks.
you can do it from the ubuntu live cd.

read this - [topic 13 to be exact]
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub)

---

### Post by Krytarik on 2011-03-21
> **krishna1650 said:**
> Thanks for reply. But if i connect both, then nothing comes in the screen, i have nothing to select. Can this be due to different grub version (though it's my guess only, in one harddisk gub2 is installed for surely, on other one, i am not sure) or there is other issue?

I guess it's because the absolute drive order gets changed when both drives are connected. Both Grubs are apparently set up to search for their config files on the first drive. However, I believe you should at least get a Grub prompt, and at least one Grub should work.

So +1 for re-install of Grub2 with a LiveCD into the MBR of a disk of your choice, after connecting both drives:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

After doing so, check/modify the Grub config of the drive which you chose to use, follow my earlier post after "Problem:" ;-)
[http://ubuntuforums.org/showthread.php?p=10569758](http://ubuntuforums.org/showthread.php?p=10569758)

After booting into the native OS of the chosen drive, you need to update Grub like mentioned before.

---

### Post by krishna1650 on 2011-03-23
Problem is that, both my harddisks are shown as /dev/sda. So both root partition of harddisk is shown as /dev/sda1. So how to proceed?

Thanks for help.

> **Krytarik said:**
> I guess it's because the absolute drive order gets changed when both drives are connected. Both Grubs are apparently set up to search for their config files on the first drive. However, I believe you should at least get a Grub prompt, and at least one Grub should work.

So +1 for re-install of Grub2 with a LiveCD into the MBR of a disk of your choice, after connecting both drives:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

After doing so, check/modify the Grub config of the drive which you chose to use, follow my earlier post after "Problem:" ;-)
[http://ubuntuforums.org/showthread.php?p=10569758](http://ubuntuforums.org/showthread.php?p=10569758)

After booting into the native OS of the chosen drive, you need to update Grub like mentioned before.

---

### Post by Krytarik on 2011-03-23
> **krishna1650 said:**
> Problem is that, both my harddisks are shown as /dev/sda. So both root partition of harddisk is shown as /dev/sda1.
That isn't possible at all! :D If you boot with a LiveCD, with both drives connected, and you run the command
```
sudo blkid
```
you should definitely see different device names for them!

---

