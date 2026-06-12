---
title: "Kernal panic not syncing VFS unable to mount root fs on unknown-block(0,0)"
date: 2009-10-02
forum: General Help
---

### Post by duffboy on 2009-10-02
I have looked around at many posts with this error message:
Kernal panic not syncing VFS unable to mount root fs on unknown-block(0,0)
but have not found an answer to my problem.

I am running Hardy.

I have a systems that was running fine. I added two additional hard drives to the system, changed my fstab, and mounted them just fine. However, after rebooting, I got the error. I commented out my new lines in the fstab using the LiveCD and removed my additional hard drives, but still get this error.

I can load the grub in recovery mode, but get the error right after it tries to mount root with the error:
No filesystem could not mound root, tried cramfs.
I would really appreciate somebody who can help me figure out what I have screwed up. I was just getting excited with my new system and now I am back on my old one. :(

---

### Post by Giblet5 on 2009-10-02
This could be a lot of things.

Is this a new install?

Is this a reboot from a new build of the kernel?

Is this an old install with a tweak to grub's menu.lst file?

Did you build a kernel and forget to build the initramfs image?

Post your partition tables.

---

### Post by duffboy on 2009-10-02
Thanks for your reply Giblet.

> Is this a new install?
Sort of. I have had it running for about a week though.

> Is this a reboot from a new build of the kernel?
No

> Is this an old install with a tweak to grub's menu.lst file?
No

> Did you build a kernel and forget to build the initramfs image?
No

> Post your partition tables. 
I am not sure how to get the full partition table using the LiveCD, however, I was able to run gparted and get the following information.
I only have one device, /dev/sda
Partition     filesystem   Size        Flags
/dev/sda1     ext3         273.81GB    boot
/dev/sda2     extended      5.58GB
  /dev/sda5    linux-swap    5.58GB

Again, thanks for your help, I appreciate it so very much.

---

### Post by Giblet5 on 2009-10-02
OK, you have the easiest install to diagnose...

At the grub menu, when you highlight the ubuntu item, hit the 'e' key.

The second line should be hd(0,0). Is it? You can change it if it isn't, then hit 'b' to attempt to boot.

---

### Post by Giblet5 on 2009-10-02
Also: Is the first disk a SCSI disk or RAID array?

Have you tried reinstalling Grub? (Copied from the grub reinstall guide)

Boot the Live CD.
Bring up a terminal window.
```
sudo mount /dev/sda1 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo cp /proc/mounts /mnt/etc/mtab
```

Now, you have to enter your working environment. The following command will take care of that.

```
chroot /mnt /bin/bash
```

Warning: From this point on, any files you modify will affect your Ubuntu system. You have left the safety of the LiveCD. Exercise caution.

Reinstalling GRUB from this point is easy. Just enter the following command.

```
sudo /sbin/update-grub
sudo /sbin/grub-install /dev/sda
```

Then do a graceful shutdown via ```
sync;sync;reboot
``` and it *should* boot normally.

---

### Post by duffboy on 2009-10-02
Giblit,

Okay, I am officially beyond my comfort zone, thanks for the guidance.

The display is as follows:
root  (hd0,0)
kernal  /bot/vmlinuz-2.6.24-19-server root=UUID=9f66ea0b-f11a-47ef-96fa-2a1a0cad4eec ro quiet splash
initrd  /boot/initrd.img-2.6.24-19-server
quiet

I am not so sure what to do here...

Once again, I really appreciate your time.

---

### Post by Giblet5 on 2009-10-02
Try the grub reinstall above your last post.

I give it 80% odds of fixing the problem.

---

### Post by duffboy on 2009-10-02
Giblit,

Thank you so much for your help. However, I am at the point
```
sudo /sbin/grub-install /dev/sda
```
and I get an error telling me I should run
```
sudo /usr/sbin/grub-install /dev/sda
```
I run that and get the error:
```
sudo: unable to resolve host ubuntu
Could not find device for /boot: Not found or not a block device.
```

I am not yet sure what to do here. Thanks again.

---

### Post by Giblet5 on 2009-10-02
The [grub reinstall info is here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and it's more thorough than what I provided.

Did you get any errors during the mount commands?

Do you have a separate /boot filesystem?

Try booting to the Live CD again, starting a terminal, and ```
sudo bash
```.

Then repeat the steps without the leading "sudo " on each command (because you're already root).

Make sure there are some files in /boot after the chroot command. If not, then you do have a separate /boot filesystem.

```
fdisk -l
``` will show you where it might be.

---

### Post by duffboy on 2009-10-02
Sorry for my late reply, had to do some actual work. :)

I tried the steps as laid out, three times actually, with the same kernel panic result.

I appreciate the help provided so much, you have been really kind.

---

