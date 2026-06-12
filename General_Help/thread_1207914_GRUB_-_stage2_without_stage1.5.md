---
title: "GRUB - stage2 without stage1.5"
date: 2009-07-08
forum: General Help
---

### Post by Orlin on 2009-07-08
Hi!

After 2 days of recovering partitions destroyed by Vista's Disk Management Console I finally managed to work things out (using mainly TestDisk and manually recreating some EPBR records). There is only one thing left to restore to state before failure. Previously, I had second primary partition (sda2 = /boot) marked as active - and there was installed GRUB. During system start GRUB proceeded directly to stage2 and displayed menu with my Ubuntu 9.04 and Windows. However, after restoring all partitions, GRUB displayed only it's prompt in commandline mode - no menu, splashimage, etc. I could still boot windows [typing: rootnoverify (hd0,0), chainloader +1, makeactive, boot] and all partitions had same device names, but probably UUIDs used in *menu.lst* changed - so I booted Ubuntu 9.04 from CD and executed this commands as root:
```
$ mkdir /mnt/myubu
$ mount /dev/sda7 /mnt/myubu
$ mount /dev/sda2 /mnt/myubu/boot
$ mount --bind /dev /mnt/myubu/dev
$ chroot /mnt/myubu
$ grub-install --recheck /dev/sda
#// this one didn't work - wrote something about not being able to find /boot or non-block device
$ grub-install /dev/sda
#// same message as above, so I tried:
$ grub
#// and in GRUB's commandline:
> root (hd0,1)
> setup (hd0)

```But now I've got first (Vista's) partition marked as active and during computer's start it goes through stage1.5 - not directly to stage2 as it has been before. And here goes my question: **how to restore original GRUB's behaviour - loading directly stage2**, and in case I mark first partition (sda1) as active, it would bring Windows7/Vista boot loader (without any sign of GRUB's existence).

I was also wondering, if the command:
```
# grub-install --root-directory=/boot /dev/sda
``` would do, what I wanted to achieve - but at the moment I have enough experiments :-)

Cheers,
[B]Mirek
[/B]
PS: I'm aware that I will need to "fixmbr/fixboot" with MS tools on sda1 to complete the task.

---

### Post by danwood76 on 2009-07-09
Grub always loads through stage 1 - 1.5 - 2. This is its normal behaviour?

---

### Post by Orlin on 2009-07-09
> **danwood76 said:**
> Grub always loads through stage 1 - 1.5 - 2. This is its normal behaviour?
I always  have read that stage1.5 is optional (at least in some cases) - simplifying: stage1 can point directly to stage2 (but the stage2 file must be in a fixed location and can't be moved - because stage1 operates only using physical block addresses) - or it can call stage1.5 which "understands" file system and is able to locate stage2 - even if it was moved to other physical block (for example after defragmentation of /boot partition).

Here it's better explained: [http://jbakshi.50webs.com/Linux_tutorial/GRUB/GNU%20GRUB%20simplified.html]("http://jbakshi.50webs.com/Linux_tutorial/GRUB/GNU%20GRUB%20simplified.html")

And as I wrote - there was no "Loading stage 1.5..." message before - it went directly to "Loading stage 2...".


[B]M.

UPDATE:
[/B]After some more reading - previously I didn't have GRUB (stage 1) installed in MBR. - so BIOS was selecting first boot  sector of the active partition - and there was my GRUB. I should use command **setup(hd0,1) **instead of **setup(hd0)** - but now I'm not sure how to clean MBR (actually I have few ideas - for example using **dd**, but don't want to damage anything).
My plan at the moment is:
1. fixmbr, fixboot
2. From Live CD reinstall GRUB (using **setup(hd0,1)**) (after backing up /boot partition - just in case)
3. Set sda2 (hd0,1) partition as active and check if everything works fine :-)

---

### Post by danwood76 on 2009-07-10
Yeah but there is surely no issue with it loading stage 1.5 then 2?
I dont quite see where your actual problem lies as it will still have to do that jump weather the BIOS does it or grub does it?

---

### Post by Orlin on 2009-07-12
Probably you're right :-)
I liked 2 things about this solution:
1. If something happened to  GRUB partition I could restore Windows bootloader easily by just setting boot flag to windows partition.
2. It seemed to boot a bit faster (0.5-1s) - but now, after rethinking the whole boot process, I suspect it could be mainly a subjective perception, caused by difference in amount of text outputted before loading the boot menu.

Regards,
**Mirek**

---

