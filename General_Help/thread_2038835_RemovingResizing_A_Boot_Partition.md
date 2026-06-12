---
title: "Removing/Resizing A Boot Partition"
date: 2012-08-07
forum: General Help
---

### Post by crscardellino on 2012-08-07
Hello Ubuntu users, here is my problem, I hope you can help.

I have a Laptop with Ubuntu 11.10, Debian 6 and Windows XP installed on it.

The fact is that I have a 90 GB partition for Windows, a 30 GB partition for Ubuntu and a 30 GB partition for Debian.

Now, I'm not using Debian at all in this laptop (i mostly use Ubuntu for work), so I want to remove the Debian partition (and its corresponding swap partition) and resize the ubuntu partition to 60 GB (over the Debian partition).

When I open gParted, i got something like this:

[FONT="Courier New"] ----------------------------------------------------------------
|  /dev/sda1 (Win, 90 GB) | /dev/sda7 (Ub 29 GB) | /dev/sda8 ->
 ----------------------------------------------------------------

----------------------------------------------------------------
-> (swap, 1 gb) | /dev/sda5 (Deb 29 GB) | /dev/sda6 (swap 1 gb) |
----------------------------------------------------------------
[/FONT]
Now, sda5 to sda8 are in an extended /dev/sda2 partition of 60 GB.

What i want to do is format the sda5 and sda6 and merge this to sda7 (moving sda 8 to the end of the partition), but i have 2 problems:

In order to remove the sda5 and sda6 partitions i have to unmount any logical partition above 5 or 6 respectively.

Besides, the /dev/sda5 partition has the boot flag so if I moved or resize it could end in a boot failure.

I really have no idea how to fix neither of this two problems. ¿Anyone can help me?

Thanks in advance for your time.

---

### Post by btindie on 2012-08-07
Get a copy of the GParted live CD and boot from that, that way you won't get the problem with your partitions being mounted.

You may want to back up that partition first before playing with it in case something goes wrong. I never do, it just depends how adverse to risk you are!

Once you're running under GParted Live, delete sda5/sda6 and apply. Then resize sda7, you may need to move it forward first to occupy the space that sda[56] once used. Apply the boot flag to that partition, it'll probably be sda5 now. And that should be it.

If you were using LVM then it'd have been a lot easier...

---

### Post by crscardellino on 2012-08-07
Thanks for your reply. I'm gonna try it.

One last question thought, what will happen with grub? Now it shows the entries for Ubuntu, Windows and Debian. Is the Ubuntu Grub (not the Debian one), I will have to reconfigure it after applying the changes?

---

### Post by btindie on 2012-08-07
If you haven't done it already, you may want to boot into Ubuntu and [run]("https://help.ubuntu.com/community/Grub2/Setup#File_Structure") ```
sudo grub-probe -t device /boot/grub
``` to find out where grub is installed for that OS. It may be to the Partition Boot Sector or it may have originally been to the MBR which was later overwritten by Grub for Debian.

If the original Windows MBR is still in place, thereby using the boot flag in the partition table you may want to install Grub to the Partition Boot Sector. Once you've repartitioned the disk you'll need to reinstall Grub as the location of the files would have changed. [Link]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition")

To do that you could [chroot]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#chroot") into the partition from the GParted Live CD or boot from a USB stick that has grub on and tell it to use the kernel/initrd from Ubuntu

---

### Post by oldfred on 2012-08-07
Boot flag only controls booting, if you are using Windows boot loader. And the Windows MBR will not boot from an logical partition, so I doubt you are booting with Windows boot loader. Lilo & others will use a boot flag in a logical partition.

Best to see what you have installed where:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

If you just want to be sure you can boot Ubuntu using grub2's boot loader in the MBR. Boot into Ubuntu and run this which installs grub2's boot loader.

sudo grub-install /dev/sda

---

