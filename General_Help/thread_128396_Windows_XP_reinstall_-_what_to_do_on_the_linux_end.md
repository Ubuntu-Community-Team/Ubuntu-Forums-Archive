---
title: "Windows XP reinstall - what to do on the linux end"
date: 2006-02-11
forum: General Help
---

### Post by snooo on 2006-02-11
Thanks to being an idiot and forgetting to install anti-virus and firewall software on my un-upgraded Windows XP partition, I am now stuck with a non-working largely borked operating system, tho ubuntu works fine of course :-) 

It seems that the only way out of the problem is to go back and reinstall the system from scratch - except that the Windows XP installer has a habit of overwriting the master boot record. Obviously I'd quite like to keep Ubuntu Breezy as its my main system, so what steps should I take to avoid losing everything? Can I use the Breezy install disk to restore GRUB after XP deletes it?

---

### Post by lha on 2006-02-11
[QUOTE=snooo]Can I use the Breezy install disk to restore GRUB after XP deletes it?[/QUOTE]

[How to restore GRUB]("http://ubuntuforums.org/showthread.php?t=76652")

---

### Post by Irony on 2006-02-11
This has always worked for me;

Get a partition list;

*sudo fdisk -l*

Boot from the install ubuntu CD and at the prompt type;

*boot: rescue*

Go to a  mount point;

*dev/disc/disc0/part1*

At the sh-3.00# prompt type;

*grub-install /dev/hda*

After being returned to the prompt, do;

[I]#umount /dev/hda1
#reboot[/I]

Or Ctrl-Alt-Delete will also probably reboot. At this point, how you open the CD drive depends on the machine. Usually if you hit the open button on the drive as the system has just begun to boot (when you see the BIOS name, CPU, and RAM), it will open. If you can't seem to get it open naturally, enter the BIOS setup and change the boot sequence to bypass the CD, boot normally, login, and eject the CD. Try not to use the pin or hard-reset.

---

### Post by snooo on 2006-02-11
Excellent, shall print that out for future reference. Thanks again.

---

### Post by Irony on 2006-02-12
I should point out that you go to the partition where ubuntu is mounted as root.

For example if ubuntu is on hda4;

dev/disc/disc0/part4

At the sh-3.00# prompt type;

*grub-install /dev/hda*

After being returned to the prompt, do;

[I]#umount /dev/hda4

Ctrl-Alt-Delete[/I]

---

### Post by matthewv on 2006-02-13
I think the easiest way would be to run, with a floppy in the first floppy drive: ```
sudo grub-install /dev/fd0
```
Then, once the windows reinstall is complete, just boot off the floppy, into your ubuntu system, and the run ```
sudo grub-install /dev/hda
```to reinstall grub to the mbr.

---

