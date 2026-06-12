---
title: "I want to remove Windows from my dual-boot system, but there's a complication."
date: 2006-03-27
forum: General Help
---

### Post by dwasifar on 2006-03-27
When I installed Ubuntu, I installed it to a new, unpartitioned drive on a WinXP box.  The result is that the Windows partition is entirely on drive 0, and the Ubuntu partitions are on drive 1.  (IDE1 master and IDE1 slave respectively.)

Now I would like to remove the Windows drive from the machine entirely and make this a dedicated Ubuntu box.  But if I understand correctly, I will have a problem with that.  I am afraid that all the boot loader stuff is in the boot sector of drive 0 - the Windows drive.  

Is there an easy way to get Windows out of this box?  I'd like to save the drive and its data if possible to put in a USB enclosure as a backup.

---

### Post by morpheus2485 on 2006-03-27
[QUOTE=dwasifar]When I installed Ubuntu, I installed it to a new, unpartitioned drive on a WinXP box.  The result is that the Windows partition is entirely on drive 0, and the Ubuntu partitions are on drive 1.  (IDE1 master and IDE1 slave respectively.)

Now I would like to remove the Windows drive from the machine entirely and make this a dedicated Ubuntu box.  But if I understand correctly, I will have a problem with that.  I am afraid that all the boot loader stuff is in the boot sector of drive 0 - the Windows drive.  

Is there an easy way to get Windows out of this box?  I'd like to save the drive and its data if possible to put in a USB enclosure as a backup.[/QUOTE]


here's what I would try:

I would disconnect the hard drive that has windows on it (just for safety).

Then change the jumpers on the ubuntu hard drive to master (there should be a diagram on the hard drive, and if you have problems with it there is likely a walk through for your moddle of hard drive googleable)

boot the computer with your ubuntu CD

 hit escape and skip to the section that configures grub 

have the boot cd install to the master boot record of your computer.

if somelthing goes awry, you can just reset the jumpers to their orriginal positions, reconnect the XP drive and boot the computer normally.

---

### Post by DOtSlaSHuCantCME on 2006-03-27
[QUOTE=dwasifar]When I installed Ubuntu, I installed it to a new, unpartitioned drive on a WinXP box.  The result is that the Windows partition is entirely on drive 0, and the Ubuntu partitions are on drive 1.  (IDE1 master and IDE1 slave respectively.)

Now I would like to remove the Windows drive from the machine entirely and make this a dedicated Ubuntu box.  But if I understand correctly, I will have a problem with that.  I am afraid that all the boot loader stuff is in the boot sector of drive 0 - the Windows drive.  

Is there an easy way to get Windows out of this box?  I'd like to save the drive and its data if possible to put in a USB enclosure as a backup.[/QUOTE]




This is from a GruB restore guide.


1. pop in the live cd, boot from it until you reach the desktop
2.open a terminal window or switch to a tty.
3.type"grub"
4.type "root (hd0,6)" ,or whatever your harddisk +boot partition numbers are.
5.type"setup" (hd0)" ,or whatever your harddisk nr is
6.Quit grub by typing "quit".
7.reboot.

:-k  things to keep in mind :-k = do i have to set my drive as master now ,if it was set as slave before.

if your going to use second drive  as storage ,fat32 and umask will be your best friend.

:-k  Im not quite sure on the effect on your "fstab" file,im thinking you do the grub install and then edit your fstab, then remove drive, i would just comment out (#)the drive you will be removing for now,then reboot.Would ubuntu automaticly configure your fstab after reboot? im not sure thats why i would do it this way.

---

### Post by JoshHendo on 2006-03-27
If you erase the windows drive, and GRUB doesn't work, you should be able to restore it. [http://ubuntuos.com/2006/03/howto-restore-grub.html](http://ubuntuos.com/2006/03/howto-restore-grub.html)

---

### Post by dwasifar on 2006-03-27
Well, I did it, with a combination of advice from all three of you.  I'm still not quite sure what made it work, but it does work.  The drive that contained Ubuntu is now IDE1 Master, and loads up as /dev/hda1.  The Windows drive is physically out of the machine.  It will go into an external USB enclosure in case I ever need files off it.

Thanks, guys.  Much appreciation for the assist.  :)

---

### Post by Requiem on 2006-03-27
[QUOTE=dwasifar]The Windows drive is physically out of the machine.[/QUOTE]

Remember, trying to boot this drive will fail, it still has its mbr set to grub...

---

### Post by dwasifar on 2006-03-27
[QUOTE=Requiem]Remember, trying to boot this drive will fail, it still has its mbr set to grub...[/QUOTE]
I know, and even if it had Windows in the boot sector, it would still fail to run on any hardware other than the machine I took it out of.  Have you ever transferred a WinXP primary drive to another machine and tried to boot it?  Doesn't work -Windows chokes on the driver mismatches.   

My plan is to install this drive in a USB enclosure as a backup, to get files off it if I need them.  

If I ever wanted to boot it on the Ubuntu machine again I'd have left things as they were.  If I change my mind about it, I think SYS C: from a DOS prompt probably still works.

---

