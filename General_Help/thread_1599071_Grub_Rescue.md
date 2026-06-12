---
title: "Grub Rescue"
date: 2010-10-17
forum: General Help
---

### Post by ThePsychoAxeman on 2010-10-17
Hi!
I installed Ubuntu 10.04 using Wubi on my laptop today. It was working fine until I updated it to 10.10 and rebooted.
Now it shows the following error - 

error : no such device : 709c91d0-39d4-4584-aceb-8554f1d63d6a.
grub rescue> _

I know that this can be solved by using a Recovery CD, but the problem is that my CD drive doesn't work, and I'm not sure whether the "Aspire 3020/5020 Series Recovery CD" is the disk I'm looking for.
Also, I'm locked out of the BIOS because I don't know the password.
I'm using Windows XP Professional.

Please help!
Thanks!

---

### Post by Quackers on 2010-10-17
Welcome to Ubuntu Forums.
Have a look at this thread
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by kio_http on 2010-10-17
This means that GRUB2 has successfully been installed on your MBR or EFI partition (Depending on partition scheme). However the device where your Grub Settings are (Probably Ubuntu partition) can't be found.

---

### Post by ThePsychoAxeman on 2010-10-17
Thanks!
I checked it out, but I couldn't understand anything in it.

---

### Post by Quackers on 2010-10-17
Is this one any better?  :-)
[http://ubuntuforums.org/showthread.php?t=1584208&highlight=error+device](http://ubuntuforums.org/showthread.php?t=1584208&highlight=error+device)

Do you have a Windows repair/recovery disc?

---

### Post by ThePsychoAxeman on 2010-10-17
Thanks, but I still don't understand anything.
I guess I'm stupid. 

I'm not sure. As I said earlier, I have 2 disks which say "Aspire 3020/5020 Series Recovery CD". I'm not sure if they recover data or what. It probably won't help anyway because me CD/DVD drive doesn't work.

---

### Post by Quackers on 2010-10-17
Those would be the recovery discs. They will recover your computer to the way it was the day you bought it.
You would possibly be able to repair the Windows bootloader with it. I don't know if that is the fix for your problem (I haven't got a wubi install).
It is also possible to install the Ubuntu .iso on a thumb drive, or similar. You would then effectively have a bootable cd, but on a thumb drive for repair purposes. I don't have a link to that but a search will give more details.

---

### Post by ThePsychoAxeman on 2010-10-17
Thanks!
Hmm... Can you tell me how I can create a bootable CD on a thumb drive? Thanks!

---

### Post by Quackers on 2010-10-17
Post number 8 in this link gives a couple of options.
[http://ubuntuforums.org/showthread.php?t=1525476&highlight=install+ubuntu+thumb+drive](http://ubuntuforums.org/showthread.php?t=1525476&highlight=install+ubuntu+thumb+drive)

---

### Post by ThePsychoAxeman on 2010-10-17
I checked out the first link you sent me again.
After typing "ls", I got (hd0)

The next step is - "If all you get is (hd0) you most likely have a partition table or disk error. Seek assistance elsewhere! (fsck, e2fsck, TestDisk, etc.)"

I didn't get two co-ordinates. I don't know what to do now.  

Oh, and what's the minimum capacity of the thumb drive needed to install Ubuntu on it?I only have two 2GB USB drives.

---

### Post by raafaell on 2010-10-17
take a look [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") if you want to BOOT from the Pen Drive, in order to boot from the pen drive you are going to need the [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#download").. and the ubuntu installation **ISO** file.

> It is possible to have Ubuntu or Kubuntu on a USB drive (AKA USB Stick or Thumb drive or Flash drive) or USB hard disk drive with persistent mode. This means that you can boot from a USB drive and keep customisations such as keyboard layout, numlock, preferences, additional packages saved on the drive. This can be done using linux or windows. You will need a USB drive of **1 GB or more**. This page is written after having tested the instructions on a Peak III **1 GB drive**. The preparation of the drive is explained using 'fdisk' because I had errors with 'gparted' and i could not give the partitions a volume name. I used Ubuntu to make the drive. In Kubuntu it is more or less the same. Where you see 'ubuntu' replace it by 'kubuntu'. I will mark the other differences.

---

### Post by Quackers on 2010-10-17
Sorry, but I don't know. The file is about 700mb afaik but I suspect that 4GB is generally used, though 2GB may be enough.
Hopefully somebody else can confirm/correct me.

---

### Post by ThePsychoAxeman on 2010-10-17
Thanks for the links! (Epic avatar by the way!)

---

### Post by ThePsychoAxeman on 2010-10-17
Can anyone explain how this works - [http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)
Thanks! :)

---

