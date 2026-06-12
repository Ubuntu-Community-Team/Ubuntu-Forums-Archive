---
title: "Boot failed  -  Stuck at initramfs"
date: 2010-11-22
forum: General Help
---

### Post by theyain on 2010-11-22
Well, to put it simply, I decided to try to reboot earlier, low and behold as I try to boot into Ubuntu, the system tells me that it can't find init.  I'm stuck at initramfs.  I can't mount the root partition as it tells me it can't read /etc/fstab.  

I had decided to touch /etc/fstab, but after doing so I have no idea how to open it as it seems I don't have any kind of editor.

I'm not sure what to do.  Never had a problem like this before.

---

### Post by bonixavier on 2010-11-22
Go to that shell again and see if you still have access to the commands "cat" and "mount"

---

### Post by WorMzy on 2010-11-22
Try booting to an earlier kernel.

[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)

I can't give you step-by-step instructions on how to do this, as I don't use grub2. Hopefully that link will see you through, or someone else will be able to give you proper instructions.

---

### Post by bonixavier on 2010-11-22
> **WorMzy said:**
> Try booting to an earlier kernel.

[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)

I can't give you step-by-step instructions on how to do this, as I don't use grub2. Hopefully that link will see you through, or someone else will be able to give you proper instructions.
If (s)he really ruined fstab, reinstalling grub will likely not fix his problem. He can try to rewrite his fstab or reinstall the system. (That's what I can think of right now, if anyone has a better idea, please share).

---

### Post by WorMzy on 2010-11-22
No no, I'm not suggesting that they reinstall grub, that wouldn't help at all. You can manipulate grub into booting a different kernel/initrd. :)

---

### Post by theyain on 2010-11-22
I still have access to mount and cat.  I know that much.  

I can't really do anything with grub (my only other system installed is Windows 7 Starter :| ) as I have no editor to my knowledge in initramfs and can't access any of the grub files from windows (No worthwhile ext4 driver).

---

### Post by WorMzy on 2010-11-22
Don't worry, you can edit grub "on-the-fly" during the boot-up phase. Since you have two OSs, you presumably get a menu asking you to choose which to boot to, right? That menu is part of grub, and you can edit the menu items right there. Reread the link I posted, it explains how to make modifications to the boot arguments (they're not permanent, so don't worry if you screw it up first time).

You just need to change the "linux" and "initrd" lines, changing the 2.6.31-9 (in the example) to something else, possibly 2.6.31-8. Use TAB completion to show which kernels are available, and try one of them.

---

### Post by bonixavier on 2010-11-22
> **theyain said:**
> I still have access to mount and cat.  I know that much.  

I can't really do anything with grub (my only other system installed is Windows 7 Starter :| ) as I have no editor to my knowledge in initramfs and can't access any of the grub files from windows (No worthwhile ext4 driver).
OK. I'll assume your fstab is unusable, that the shell you're on resembles the usual file hierarchy and that you remember your partitioning. For this example, we'll assume the following scheme (adjust to your case):
```
sda1: /
sda2: swap
sda3: /home
```First things first. You'll have to mount your / partition to any given point. Let's assume you can create a directory there or use a preexisting one. (If you can't, then I wouldn't know).
```
mount /dev/sda1 /mnt
```After you do that, it's time to rebuild your fstab.
```
cat > /mnt/etc/fstab << "EOF"
/dev/sda1  /  ext4  defaults,noatime 0 1
/dev/sda2  none  swap  sw  0 0
/dev/sda3 /home ext4 defaults 0 1
EOF
```See if you can unmount sda1 by typing
```
umount /dev/sda1
```After that, reboot and hope for the best.

Ubuntu has been using UUIDs to identify the partitions in fstab, but hopefully this will do. If it doesn't work, you may have to reinstall Ubuntu.

---

### Post by theyain on 2010-11-22
If anything I can always grab the UUIDs from grub

---

### Post by bonixavier on 2010-11-22
That's true. Did it work?

---

### Post by theyain on 2010-11-22
Will know in a minute

---

### Post by theyain on 2010-11-22
Nope, that did nothing for me -_-.  I'm going to download the iso for ubu, run it through PowerISO and then install it with Wubi. 

Hopefully I'll be able to fix the problem through the crappy ntfs version of it.

---

### Post by bonixavier on 2010-11-22
Good luck. Sorry it didn't work. Just as a hint: for the more complex technical questions, you can try posting on linuxquestions.org. Their average technical literacy is much higher than here.

---

### Post by WorMzy on 2010-11-22
Did you try my suggestion of using an earlier kernel?

If that didn't work either, then try booting up a LiveCD and running the [boot info script]("http://sourceforge.net/projects/bootinfoscript/"). That might shed some light on the problem.

---

### Post by yaami on 2010-11-22
I'm not sure I understand the problem exactly. Does it show any error when it shows the initramfs prompt like given up on root or something along these lines... My laptop suddenly started showing this a month ago (no idea why)... wait for sometime when the prompt shows up and type exit. If it is the same problem as mine add rootdelay=80 (I used 80) to the boot options. 

Again I'm not sure if this is the problem, but just putting it here just in case.

---

### Post by theyain on 2010-11-22
F******k, I know what happened.  I have actual filesystem damage.    I was asking around my house to see if anyone knew what had happened, and low and behold, someone decided that my system was acting slow so he ran fask.  On the root partition.

I don't presume anyone knows how to fix this with out a liveCD? Or another Linux installation?

---

### Post by wei2912 on 2010-11-22
Looks like you may have to replace your hard drive.

EDIT: I don't know if it works.

---

### Post by bonixavier on 2010-11-22
> **wei2912 said:**
> Looks like you may have to replace your hard drive.

EDIT: I don't know if it works.
Nah. If it's filesystem damage and not physical damage, reinstalling will do the trick if no one can come up with a solution.

---

### Post by WorMzy on 2010-11-22
I believe that you can run *some* fsck commands from the ramdisk. I'd recommend using a LiveCD or USB though.

EDIT: Just checked, and you *can't* run fsck from the initramfs prompt.

---

### Post by theyain on 2010-11-22
I wish I could.  My external CD Drive is trashed.

---

### Post by WorMzy on 2010-11-22
That complicates matters. Can you remove the hard drive and use someone else's PC? Or use someone else's PC to create a LiveUSB?

---

### Post by bonixavier on 2010-11-22
If you have another OS there (or another computer) and it's working, you can use it to create a live USB device. If you don't, call your friends.

---

### Post by theyain on 2010-11-23
I have a solution.  I'm using Unetbootin to make a liveUSB drive from an ISO :D

---

### Post by theyain on 2010-11-23
Well, I'm now posting from my Ubuntu install, so I am quite happy. :D

---

### Post by WorMzy on 2010-11-23
Make sure to remove sudo privileges from the person who messed up your first install. ;)

---

