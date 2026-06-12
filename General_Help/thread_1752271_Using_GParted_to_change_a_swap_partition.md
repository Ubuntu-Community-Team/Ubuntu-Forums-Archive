---
title: "Using GParted to change a swap partition"
date: 2011-05-07
forum: General Help
---

### Post by MichaelGld on 2011-05-07
Through a series of misfortunes that I will not bore you with, I have wound up with two swap partitions.  I would like to take the one that is inactive and format it so that I can use it in Linux. 

Can I just right-click on the partition and format it to ext4? Are there any other steps that need to be taken to accomplish this? Here is a screengrab of my Gparted.

---

### Post by coffeecat on 2011-05-07
> **MichaelGld said:**
> Can I just right-click on the partition and format it to ext4?

Very nearly, but there are one or two things you need to check. Because the sda7 swap partition is active and the sda5 one is not, it is probable that there is only an entry for sda7 in your /etc/fstab, but it is worth checking this before you reformat. If sda5 is not spoken for then, yes, simply reformat it with Gparted.

However there are 5MiB unallocated between sda7 and sda5. That's not much but if you want to recover it, you could delete sda5 and then create a new (logical) partition using the whole of the unallocated space. If you do that, there is one thing to beware of. Your sda6 and sda7 partitions *might* get renumbered to sda5 and sda6, with your new one sda7. If your /etc/fstab is using UUIDs that won't matter, but if the first field for the root and swap partitions shows /dev/sda6 and /dev/sda7 respectively, then you would need to edit /etc/fstab.

---

### Post by ajgreeny on 2011-05-07
If I were you I would run a live CD/USB of ubuntu and use gparted to delete both swap partitions.  You would need to right click on them and hit "Swapoff" to unmount them first.  That will give you about 11.5GB unallocated space which will include those two silly little unallocated areas you currently have.

Now click in this unallocated space and make a new partition of 5GB at the end of the empty space, and format it as linux-swap.  You will now have about 6.5GB unallocated next door to sda6 into which you should be able to extend the current sda6.

Now still in the live ubuntu run ```
sudo blkid
``` which will tell you the UUID of the new swap partition, and with ```
gksudo gedit /media/[COLOR=Red]ubuntu[/COLOR]/etc/fstab
``` you can edit the install's fstab file to use the new UUID instead of the old UUID.

Note that what you actually type instead the [COLOR=Red]ubuntu[/COLOR] in red above will be found by searching the installed filesystem from the live version.

---

### Post by MichaelGld on 2011-05-07
Thanks for the reply. I am unsure about the contents of /etc/fstab. Can you help me interpret the file's contents?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
# Commented out by Dropbox
# UUID=f3d5eff7-9c6d-41c1-be07-9dabc1e3364a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c36dbdf6-995d-48fc-bfd4-14f7ca229cab none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=f3d5eff7-9c6d-41c1-be07-9dabc1e3364a / ext4 errors=remount-ro,user_xattr 0 1
``` I would like to do as you suggested, recover the small unallocated space(s). Does my fstab reveal enough about how best to accomplish that?

Thanks





> **coffeecat said:**
> Very nearly, but there are one or two things you need to check. Because the sda7 swap partition is active and the sda5 one is not, it is probable that there is only an entry for sda7 in your /etc/fstab, but it is worth checking this before you reformat. If sda5 is not spoken for then, yes, simply reformat it with Gparted.

However there are 5MiB unallocated between sda7 and sda5. That's not much but if you want to recover it, you could delete sda5 and then create a new (logical) partition using the whole of the unallocated space. If you do that, there is one thing to beware of. Your sda6 and sda7 partitions *might* get renumbered to sda5 and sda6, with your new one sda7. If your /etc/fstab is using UUIDs that won't matter, but if the first field for the root and swap partitions shows /dev/sda6 and /dev/sda7 respectively, then you would need to edit /etc/fstab.

---

### Post by coffeecat on 2011-05-07
Your /etc/fstab shows your root partition and sda7 swap partition referenced with UUIDs, so simply deleting the redundant swap partition and creating a new partition in all the available unallocated space should be OK. However, let's check that those UUIDs are correct to be 100% sure. Please post the terminal output of:

```
sudo blkid
```

---

### Post by MichaelGld on 2011-05-07
Here it is.

```
 michael@michael-desktop:~$ sudo blkid
[sudo] password for michael: 
/dev/sda1: UUID="6dd7f5eb-2be4-4a79-bd4e-7a671aa5897c" TYPE="ext4" 
/dev/sda5: UUID="cb1e2652-7f32-4a87-8dd7-26db0edda146" TYPE="swap" 
/dev/sda6: UUID="f3d5eff7-9c6d-41c1-be07-9dabc1e3364a" TYPE="ext4" 
/dev/sda7: UUID="c36dbdf6-995d-48fc-bfd4-14f7ca229cab" TYPE="swap" 
/dev/sdb1: UUID="EAE4C007E4BFD453" TYPE="ntfs" 
/dev/sdb3: LABEL="DOWNLOADS" UUID="90B4D253B4D23B82" TYPE="ntfs" 
/dev/sdb4: LABEL="VIDEOS" UUID="16FC8F45FC8F1E5D" TYPE="ntfs" 
/dev/sdb5: LABEL="DATA" UUID="9A043C48043C29A1" TYPE="ntfs" 
/dev/sdc1: LABEL="ProDrive" UUID="4ED018EDD018DD51" TYPE="ntfs" 
michael@michael-desktop:~$ 

```Thanks

---

### Post by coffeecat on 2011-05-07
Yes, the UUIDs in the blkid output and in your etc/fstab correspond for your current sda6 and sda7 partitions. You are safe to delete sda5 and re-use the space. But bear in mind what I said about the possible renumbering of the logical partitions when you delete sda5. It doesn't always seem to happen, but it is useful to be forewarned to avoid any possible future confusion.

---

### Post by MichaelGld on 2011-05-07
What can I expect if my logical partitions get renumbered? Is it anything that will cause Ubuntu to have a fit and cause me grief?

Thanks



> **coffeecat said:**
> Yes, the UUIDs in the blkid output and in your etc/fstab correspond for your current sda6 and sda7 partitions. You are safe to delete sda5 and re-use the space. But bear in mind what I said about the possible renumbering of the logical partitions when you delete sda5. It doesn't always seem to happen, but it is useful to be forewarned to avoid any possible future confusion.

---

### Post by coffeecat on 2011-05-07
> **MichaelGld said:**
> What can I expect if my logical partitions get renumbered? Is it anything that will cause Ubuntu to have a fit and cause me grief?

No, we've excluded any problems by checking that /etc/fstab is using the (correct) UUIDs to identify the swap and root partition. The worst that you can expect is that it might cause you some headscratching in the future if you are not aware that this can happen. :) There is a comment in your /etc/fstab:

```
# swap was on /dev/sda7 during installation
```That partition *might* get renumbered to sda6, but the comment will remain as it is now. And the UUID won't change. Just something for you to bear in mind, but Ubuntu won't mind - both /etc/fstab and grub.cfg use UUIDs.

---

### Post by MichaelGld on 2011-05-07
Great! Thank you so much for all the help.

Michael

---

