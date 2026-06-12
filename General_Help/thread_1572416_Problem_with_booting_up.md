---
title: "Problem with booting up"
date: 2010-09-11
forum: General Help
---

### Post by KL0211 on 2010-09-11
Hello everyone,

I installed Lucid Lynx on my laptop a couple of months ago and for the most part everything was working fine. However, just recently the computer doesn't seem to be booting up at all. I start up the machine and then a black screen appears with the text:

init: ureadahead main process (306) terminated with status 5
the (#) is different in some boot-ups

And the computer just hangs there. typing anything doesn't seem to help at all. I press enter and a new line just appears. I've left it there for hours and still no login screen. If anyone can help me with this problem I would much appreciate it.

---

### Post by Rubi1200 on 2010-09-11
What are the computer specifications such as RAM and graphics card?

---

### Post by TeoBigusGeekus on 2010-09-11
After some googling:
Try to boot up with a live cd and edit your fstab file
(/etc/fstab). Comment out the partitions you added manually after the installation and see if you can now boot. 
Post us the outcome.

---

### Post by Rubi1200 on 2010-09-11
Wouldn't it be better to first post the results of ```
sudo blkid
``` and ```
sudo fdisk -l
``` before making changes?

---

### Post by TeoBigusGeekus on 2010-09-11
> **Rubi1200 said:**
> Wouldn't it be better to first post the results of ```
sudo blkid
``` and ```
sudo fdisk -l
``` before making changes?
Not much of a change actually. Besides, if anything is wrong with his fstab we can solve it later.

---

### Post by KL0211 on 2010-09-11
Thanks for the assist. I'm not sure I understand what you're asking me to do BigusGeekus. I got to my fstab, here is what it provides:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5b8d374-0d86-481d-a212-02cc3f2fc462 none            swap    sw           $

Also, here are the results from "sudo fdisk -l":

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026560

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23951   192379904   83  Linux
/dev/sda2           23951       24322     2978817    5  Extended
/dev/sda5           23951       24322     2978816   82  Linux swap / Solaris

---

### Post by Rubi1200 on 2010-09-11
Either you did not copy and paste fstab correctly or there may be something wrong.

This is what I have on my system:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7e07a924-8356-48d2-a8ec-65bc85589b04 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ed61d4e7-cc92-42f9-a176-4944e8c4e60d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0Your fstab appears to be missing this: > # / was on as well as the UUID.

So, from the LiveCD, go to System > Administration > GParted and then right-click the sda1 partition. Go to Information and copy the UUID.
You can then edit fstab with the correct information and you should be ok again (fingers crossed).

---

### Post by KL0211 on 2010-09-11
So you're saying that
# swap was on /dev/sda5 during installation
should be
# / was on /dev/sda5 during installation ?

Or should I just add that line to the fstab?

---

### Post by Rubi1200 on 2010-09-11
> **KL0211 said:**
> So you're saying that
# swap was on /dev/sda5 during installation
should be
# / was on /dev/sda5 during installation ?

Or should I just add that line to the fstab?
No, please do not do that!

I am saying that **sda1**, your main partition, is missing its UUID. First find out what it is following the instructions above and then we can move ahead.

---

### Post by KL0211 on 2010-09-11
OK so before I go ahead and edit it, let me make sure this is how it should look:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0522298b-ad83-4a22-be90-1b7d83532edf /               ext4     errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5b8d374-0d86-481d-a212-02cc3f2fc462 none            swap    sw           $

---

### Post by Rubi1200 on 2010-09-11
> **KL0211 said:**
> OK so before I go ahead and edit it, let me make sure this is how it should look:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0522298b-ad83-4a22-be90-1b7d83532edf /               ext4     errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5b8d374-0d86-481d-a212-02cc3f2fc462 none            swap    sw           $
If the UUID is correct (i.e. that is the information you gathered from GParted), then yes you should be able to edit and save then reboot and be back into Ubuntu normally.

Just one more question before you go ahead. Do you have other operating systems or only Ubuntu?

---

### Post by KL0211 on 2010-09-11
I only have Ubuntu 10.04 installed.

---

### Post by Rubi1200 on 2010-09-11
> **KL0211 said:**
> I only have Ubuntu 10.04 installed.
Ok, so I would say you can go ahead and edit the fstab file, save, reboot.

If there are problems, let us know.

Good luck!

---

### Post by KL0211 on 2010-09-11
No progress I'm afraid. I still get stuck at the ureadahead termination.

If I'm going to have to reinstall Linux on my system, that's fine. However before I do so, There is a software I installed with Wine that I will need to de-authorize so I don't have to go through headaches in calling customer service. Is there a way I can access that program using LiveCD?

---

### Post by Rubi1200 on 2010-09-11
> **KL0211 said:**
> No progress I'm afraid. I still get stuck at the ureadahead termination.

If I'm going to have to reinstall Linux on my system, that's fine. However before I do so, There is a software I installed with Wine that I will need to de-authorize so I don't have to go through headaches in calling customer service. Is there a way I can access that program using LiveCD?
Did you mount your Ubuntu partition from the LiveCD in order to access /etc/fstab and edit it and then unmount before rebooting?

As far as the Wine question is concerned; I really do not know. I don't use Wine and that is probably a question that will need a separate thread in the Wine sub-forum.

---

### Post by KL0211 on 2010-09-11
> **Rubi1200 said:**
> Did you mount your Ubuntu partition from the LiveCD in order to access /etc/fstab and edit it and then unmount before rebooting?

As far as the Wine question is concerned; I really do not know. I don't use Wine and that is probably a question that will need a separate thread in the Wine sub-forum.

I didn't unmount the partition, however when I booted the LiveCD back up, the changes were still there. Did I miss a step?

Just to make thing a little more clearer, I'll write the steps I took.

1. booted up with LiveCD
2. open up a terminal
3. typed "sudo mount /dev/sda1 /mnt"
4. "cd /mnt/etc"
5. "sudo -e fstab"
6. edited the fstab and saved changes
7. reboot

hope this helps.

---

### Post by Lateralis on 2010-09-11
Which version of the kernel are you using?  Have you tried booting from a different kernel?

---

### Post by KL0211 on 2010-09-11
> **Lateralis said:**
> Which version of the kernel are you using?  Have you tried booting from a different kernel?

I'm using 2.6.32-21-generic. How do I boot from a different kernel?

---

### Post by Rubi1200 on 2010-09-11
> **KL0211 said:**
> I didn't unmount the partition, however when I booted the LiveCD back up, the changes were still there. Did I miss a step?

Just to make thing a little more clearer, I'll write the steps I took.

1. booted up with LiveCD
2. open up a terminal
3. typed "sudo mount /dev/sda1 /mnt"
4. "cd /mnt/etc"
5. "sudo -e fstab"
6. edited the fstab and saved changes
7. reboot

hope this helps.
This should have worked!?!

---

### Post by Rubi1200 on 2010-09-11
> **KL0211 said:**
> I'm using 2.6.32-21-generic. How do I boot from a different kernel?
If you installed a couple of months ago, you surely have more than 1 kernel entry in the GRUB menu?

When GRUB comes up (or use Shift at boot time) see if there are other entries and try booting from one of them (but not Recovery entries yet).

---

### Post by KL0211 on 2010-09-11
> **Rubi1200 said:**
> If you installed a couple of months ago, you surely have more than 1 kernel entry in the GRUB menu?

When GRUB comes up (or use Shift at boot time) see if there are other entries and try booting from one of them (but not Recovery entries yet).

Alright I got into GRUB, it shows 2 kernels: 2.6.32-24 and 21
There is also recovery mode for both.

Both booting gives me the same problem.

---

### Post by Rubi1200 on 2010-09-12
I really don't know if this will help you but it might be worthwhile taking a look at this:
[http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04](http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04)

---

### Post by KL0211 on 2010-09-12
Alright I tried disabling the ureadahead. Made no difference. I tried booting up with Recovery Mode through Grub. Same thing happens except more text is displayed. Here are the last few lines:

[   2.795097] EXT-4-fs (sda1): mounted filesystem with ordered data mode
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
[   5.202741] Adding 2978808k swap on dev/sda5. Priority:-1 extents:1 across: 2978808k

Still stops doing anything at that point.

---

