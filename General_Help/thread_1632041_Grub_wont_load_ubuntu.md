---
title: "Grub wont load ubuntu"
date: 2010-11-27
forum: General Help
---

### Post by Grahaman27 on 2010-11-27
Long story short, I uninstalled some packages dealing with the wireless internet because my internet was not working on my ubuntu, but was for my windows. now my computer wont boot.

when I went to restart (so I could go back and reinstall) my computer booted straight to memtest86. So I tried to fix this many times by installing another version of linux to dual boot so I would have a menu to pick from (dumb thing to do, I know) and i finally, finally got, after installing a few versions, my original 10.10 to show up on the boot menu... but now it shows this screen-

Kernal panic - not syncing: vfs: unable to mount root fs on unknown-block(0,0)

what do I do to fix this?

---

### Post by andrewthomas on 2010-11-27
From a live CD

Go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

follow the instructions and post the results with your reply

---

### Post by drs305 on 2010-11-27
> **Grahaman27 said:**
> Kernal panic - not syncing: vfs: unable to mount root fs on unknown-block(0,0)

what do I do to fix this?

Often this is a path error in either the 'linux' line of the menu entry or an incorrect path was preset. 

The best idea is to either boot a LiveCD and post the contents of RESULTS.txt after running the boot info script from the following link:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

or try to boot from the rescue prompt using the instructions here:
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by dougalkerr on 2010-11-27
Do you have any files on the computer you are worried about losing? IF NOT and presuming you have dumped Windows altogether, then boot into Ubuntu using the LiveCD and then into Administration menu and choose GParted.

Once into this partition manager opt to delete all partitions and then choose new and resize the partition to twice the amount of RAM that you have (say 2048) and choose SWAP for the file system type. Then click OK which will bring you back to the partition table. Then choose the partition that is left on the table and opt for New again and this time just put a forward slash in the Label box and choose ext3 or ext4 from the file system type list and click OK again. Click OK again and accept the message that comes up about the operation you are about to perform - at this point you have nothing to loose and nothing will get broken.

This will have sorted out the hard disk ready for the installation proper for Ubuntu.
Click the Install Ubuntu icon on the Desktop and away you go. Don't look back...

---

### Post by 71GA on 2010-11-27
What u need is a command to restore GRUB. When u get it write it down on a paper, boot from Live CD, open terminal and write down your command. 

The command consists of 4 subcomands, behind each one u hit enter.[INDENT]```

sudo grub
root (hd0,0)
setup (hd0)
exit

```[/INDENT]

---

### Post by Grahaman27 on 2010-11-27
well I will clarify that I use Windows on a completely separate hard drive, so It does not effect this. I originally had it to where there was no grub menu, just booted straight to 10.10. And grub still boots other versions of ubuntu I installed, just not the one I screwed up with.

The 10.10 with the boot problem is on sdb1

the results file is attached and in a zip.

---

### Post by dougalkerr on 2010-11-27
Have you tried the 'sudo update-grub' fro within Terminal when you get into Linux?

---

### Post by Grahaman27 on 2010-11-27
yes I have, no luck.

---

### Post by dougalkerr on 2010-11-27
There is always SuperGrub. Google it if you haven't tried it befoe it has fixed my Grub more than once in the past.

---

### Post by Grahaman27 on 2010-11-27
thanks, Ill give it a shot. And by the way, for anyone reading, I can still access the files from the unbootable partition, so If there is anyway to change the grub config files or whatever, please tell me.

---

### Post by drs305 on 2010-11-27
Right now it is your sdb6 Ubuntu (9.10) that is controlling the boot. The grub on sdb1 (10.10) got installed in the partition boot record, which is not where you want it. Additionally the sdb1 Ubuntu's fstab points to sda1 for /, which won't work since it's not an Ubuntu system partition. Your sdb8 10.10 install isn't looked at.

The RESULTS.txt shows two 10.10 installs, but the sdb1 install's fstab isn't correct so I'll assume sdb8 is the one you really want.

Since the Grub version in 9.10 may not be the same version, the best option would be to boot a 10.10 LiveCD, then run the following:
```
sudo mount /dev/sdb8 /mnt
sudo grub-install --root-directory=/mnt sdb
```
Do not include the partition number in the second command.

If you don't have a LiveCD but can boot to the sdb6 Ubuntu, go ahead and do that and run the same commands. Once installed reboot into your sdb8 install and update-grub.

---

### Post by Grahaman27 on 2010-11-27
uh...  well sdb1 IS what I want... any way to fix that? I installed 10.10 again in hopes it would fix the other 10.10

---

### Post by wilee-nilee on 2010-11-27
> **drs305 said:**
> Right now it is your sdb6 Ubuntu (9.10) that is controlling the boot. The grub on sdb1 (10.10) got installed in the partition boot record, which is not where you want it. Additionally the sdb1 Ubuntu's fstab points to sda1 for /, which won't work since it's not an Ubuntu system partition. Your sdb8 10.10 install isn't looked at.

The RESULTS.txt shows two 10.10 installs, but the sdb1 install's fstab isn't correct so I'll assume sdb8 is the one you really want.

Since the Grub version in 9.10 may not be the same version, the best option would be to boot a 10.10 LiveCD, then run the following:
```
sudo mount /dev/sdb8 /mnt
sudo grub-install --root-directory=/mnt sdb
```
Do not include the partition number in the second command.

If you don't have a LiveCD but can boot to the sdb6 Ubuntu, go ahead and do that and run the same commands. Once installed reboot into your sdb8 install and update-grub.

+1 this is really the only person on the thread really aware and not just giving answers they think will work. Notice their signature its all grub all the time.

---

### Post by drs305 on 2010-11-27
> **Grahaman27 said:**
> uh...  well sdb1 IS what I want... any way to fix that? I installed 10.10 again in hopes it would fix the other 10.10

You can use the same commands I gave you previously, just change to sdb1. 

However, you also need to mount that install's fstab and change the / device. UUIDs would be preferable.

Mount sdb1 and then edit fstab:
```
sudo mount /dev/sdb1 /mnt
gksu gedit /mnt/etc/fstab
```

I would recommend you change the / line in the sdb1 fstab to:
> UUID=f4f11039-f240-4e7f-bc25-7e47dfb367e4  /  ext4    errors=remount-ro 0  1
You might run "sudo blkid -c /dev/null" to reconfirm sdb1's UUID.

If it's still not working, rerun and repost your new RESULTS.txt

---

### Post by Grahaman27 on 2010-11-27
I know, and Its my mistake for installing a second 10.10 for the confusion. but, the sbd8 is right out of the box, where as sdb1 is what i want to boot.

---

### Post by Grahaman27 on 2010-11-27
ok, I tried the above to get the same grub kernel panic error. here is the new results.

---

### Post by drs305 on 2010-11-27
It looks like the drives changed. What was sda is now sdb, and vice versa. 

G2 is still looking at sda6 for it's grub files. Since the designations changed since you ran the last results.txt (sda<>sdb) it's good to use the UUIDs so it won't matter.

Your sda1 install still doesn't look quite right. There are no entries for the 10_linux section of grub.cfg   So even if you boot to sda1, grub isn't going to find anything to boot. 

You need to chroot into your sda1 install. You can do one of two things:

1. Make sure the files in the /etc/grub.d folder are executable, and then update-grub. After this, check the contents of /boot/grub/grub.cfg and make sure you have some entries in the 10_linux section. You would still need to mount /dev/sda1 to /mnt and then run the "grub-install --root-directory=/mnt /dev/sda".

2. I'd recommend just purging/reinstalling Grub2 completely. That will fix the missing executables in /etc/grub.d and correct any other problems. There is a link in my signature line for chrooting and reinstalling. Make sure you are dealing with sda1 now although I'd reconfirm just before executing any commands.

---

### Post by Grahaman27 on 2010-11-27
i tried removing grub and it just says "sudo: aptitude: command not found". Is this possible to do through live CD?

---

### Post by drs305 on 2010-11-27
> **Grahaman27 said:**
> i tried removing grub and it just says "sudo: aptitude: command not found". Is this possible to do through live CD?

*aptitude* probably isn't installed - it was dropped in 10.10. Use apt-get ...

---

### Post by Grahaman27 on 2010-11-27
ok, well now i deleted grub, and am currently running live cd with no grub installed, but when i run "sudo grub-install --root-directory=/mnt/ /dev/sdb" it just says "/dev/sdb does not have any corresponding BIOS drive.
" can you help me with codes specific to my computer? thanks

---

### Post by drs305 on 2010-11-27
> **Grahaman27 said:**
> ok, well now i deleted grub, and am currently running live cd with no grub installed, but when i run "sudo grub-install --root-directory=/mnt/ /dev/sdb" it just says "/dev/sdb does not have any corresponding BIOS drive.
" can you help me with codes specific to my computer? thanks

I mentioned you have to use sda now. The device designation changed from the first RESULTS.txt to the second one. You should be mounting sda1 and running the install command on sda.

```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note though those instructions are mostly for writing G2 to the MBR. If the reason the entries weren't in the 10_linux section of grub.cfg because files are corrupt or missing you need to be accomplishing the entire chroot procedure for purging/reinstalling.

---

### Post by drs305 on 2010-11-28
Reviewing the results.txt, amid all the concern with sda vs sdb and the three linux installs, I didn't notice that the sda1 install which the OP was attempting to use did not contain any kernels. In another thread started by the OP I suggested chrooting and installing 'linux-image'.

---

### Post by drs305 on 2010-11-28
Reviewing the results.txt, amid all the concern with sda vs sdb and the three linux installs, I didn't notice that the sda1 install which the OP was attempting to use did not contain any kernels. In [another thread]("http://ubuntuforums.org/showthread.php?t=1632856") started by the OP I suggested chrooting and installing 'linux-image'.

---

### Post by drs305 on 2010-11-29
Update: The OP solved this problem by chrooting into his Ubuntu sda1 installation and installing "linux-image", which added the kernel and initrd images to /boot. Subsequently running update-grub added the newly-installed kernel to the menu.

---

