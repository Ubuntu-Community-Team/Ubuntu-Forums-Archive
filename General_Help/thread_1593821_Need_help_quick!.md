---
title: "Need help quick!"
date: 2010-10-11
forum: General Help
---

### Post by jungleexplorer on 2010-10-11
Okay. I am using a very old computer with only two USB ports. It's not mine, I am in another person's house.  In needed to type an important letter that I had started on another computer using word and saved it to my usb flash drive that I keep on my key chain. Both the USB ports on the computer were used up with a keyboard and a mouse, so I had to unplug the keyboard to plug my USB drive in to access the document using OpenOffice Writer. But of course I needed the keyboard to type with once I got the document open, so I had to pull out the USB drive to plug the keyboard back in.  Not being familiar with Ubuntu and drive mounting, I though it would be like Windows.  I was wrong.  After hours of typing I tried to save the document. Now OpenOffice Writer is stuck trying to save the file to a drive that has been unplugged but that Ubuntu still shows as mounted because I did not know that Ubuntu Hardy Heron does not auto unmount a drive when it is pulled out like windows does. I plugged the USB drive back in thinking that Ubuntu would recognize it as the same drive and reuse it as the same drive that is already mounted enabling Writer to finish saving. But I was wrong again. Ubuntu mounted it as a separate drive. I thought that if I could unmount the first drive an then plug the thumb drive in it might do it, but there is no way on earth to unmount the stupid drive while Writer is trying to write to it.

I don't know what to do.  I cannot lose what I have written.  I cannot unmount the drive. And I cannot seam to find a way to stop Writer from trying to save to a drive that does not exist.  Apparently there does not seem to be a "Timed Out" feature built into Writer if saving fails like there is in Word.

Any Ideas?  Please help me!

---

### Post by jungleexplorer on 2010-10-11
Can someone please help me.  Is there a way to stop OpenOffice Writer from trying to save to a drive that does not exist and get it back to the main screen so I can save the document to a different drive?

---

### Post by demosthenese on 2010-10-11
File->Save As and choose a different location, such as Desktop.

---

### Post by gnicko on 2010-10-11
Wow!

---

### Post by jungleexplorer on 2010-10-11
> **demosthenese said:**
> File->Save As and choose a different location, such as Desktop.

I wish I could do this, but Writer is stuck trying obey the last save command. It is not crashed.  It's just stuck with that little round timer thing going round and round.  In Word, if something like this happened, then after a while Word would time out and say that the file could not be saved to the chosen location and ask if you wanted to retry or cancel. It does not appear that Writer has a Timed Out function, because it has been trying to save the file for hours.  I have tried all the keyboard shortcuts I can think of to stop it. But nothing works.  I hope there is a really smart person out there that can help.

---

### Post by JustinR on 2010-10-11
> **jungleexplorer said:**
> I wish I could do this, but Writer is stuck trying obey the last save command. It is not crashed.  It's just stuck with that little round timer thing going round and round.  In Word, if something like this happened, then after a while Word would time out and say that the file could not be saved to the chosen location and ask if you wanted to retry or cancel. It does not appear that Writer has a Timed Out function, because it has been trying to save the file for hours.  I have tried all the keyboard shortcuts I can think of to stop it. But nothing works.  I hope there is a really smart person out there that can help.

Hi, if your use the 'Force Quit' GNOME panel applet to close Writer, when you reopen it should open up a 'Document Recovery' dialogue, from there just save it to a different location. _Although this is sort-of risky._

Also - you can't auto umount a drive after you've pulled it out. The feature in Windows your talking about disables the cache on the flash drive to be able to pull it out without safely removing it.

**Edit:** If you use the 'umount **-f** /dev/sd**X**' option, it forces the USB flash drive to unmount, even if it's not plugged in I believe.

---

### Post by jungleexplorer on 2010-10-11
> **JustinR said:**
>  If you use the 'umount **-f** /dev/sd**X**' option, it forces the USB flash drive to unmount, even if it's not plugged in I believe.

Thanks. I tried this in the terminal and got the response:

"umount: only root can do that"


What did I do wrong?

---

### Post by WRDN on 2010-10-11
> **jungleexplorer said:**
> Thanks. I tried this in the terminal and got the response:

"umount: only root can do that"


What did I do wrong?

"umount" is an administrative program. As such, you need administrative rights. Put "sudo" before the command and it should work:

```
sudo umount -f /dev/sdX
```

Change X in "sdX" as appropriate.

---

### Post by JustinR on 2010-10-11
> **WRDN said:**
> "umount" is an administrative program. As such, you need administrative rights. Put "sudo" before the command and it should work:

```
sudo umount -f /dev/sdX
```

Change X in "sdX" as appropriate.

+1, Sorry about that - you should put sudo in front of the command.

---

### Post by jungleexplorer on 2010-10-11
> **WRDN said:**
> 

Change X in "sdX" as appropriate.


I am not very knowledgeable using the terminal. I don't know what you mean by the above statement. The drive is showing up on the desktop with the name UBUSB.   In the properties is say the location is "Computer:///"
 What do I do?

---

### Post by JustinR on 2010-10-11
> **jungleexplorer said:**
> I am not very knowledgeable using the terminal. I don't know what you mean by the above statement. The drive is showing up on the desktop with the name UBUSB.   In the properties is say the location is "Computer:///"
 What do I do?

Can you go to System > Administration > Disk Utility.

Find your flash drive, and you'll find that /dev/sdX thing next to 'Device:'

---

### Post by jungleexplorer on 2010-10-11
> **JustinR said:**
> Can you go to System > Administration > Disk Utility.

Find your flash drive, and you'll find that /dev/sdX thing next to 'Device:'

There is no "Disk Utility" under Administration. This computer is running Ubuntu 8.04 Hardy Heron.

---

### Post by JustinR on 2010-10-11
> **jungleexplorer said:**
> There is no "Disk Utility" under Administration. This computer is running Ubuntu 8.04 Hardy Heron.

Sorry about that, can you go to Applications > Accessories > Terminal:
```

fdisk -l

```

You should be able to find your flash drive there, if not, you can post a screenshot and we can figure it out. Tip: Next to 'Disk:' It displays the size of the disk in MB - so you should be able to find your flash drive.
If you find it the device name will be next to 'Disk:'

---

### Post by jungleexplorer on 2010-10-11
Ok.  The drive is "sda2"

I typed the following command in the terminal.

"sudo umount -f /dev/sda2"

This is the response I got,

"umount2: Invalid argument
umount: /dev/sda2: not mounted"

---

### Post by JustinR on 2010-10-11
> **jungleexplorer said:**
> Ok.  The drive is "sda2"

I typed the following command in the terminal.

"sudo umount -f /dev/sda2"

This is the response I got,

"umount2: Invalid argument
umount: /dev/sda2: not mounted"

Okay, can you list the folders that are in '/media'.

---

### Post by jungleexplorer on 2010-10-11
> **JustinR said:**
> Okay, can you list the folders that are in '/media'.

I am sorry to be so ignorant about this, but how to I find this information?

---

### Post by JustinR on 2010-10-11
> **jungleexplorer said:**
> I am sorry to be so ignorant about this, but how to I find this information?

Just go to Places (On the GNOME top panel)> Computer > Filesystem > media

---

### Post by jungleexplorer on 2010-10-11
Ok here they are in order'

cdrom
cdrom0
cdrom1
floppy
floppy0
UBUSB
UBUSB_

---

### Post by JustinR on 2010-10-11
> **jungleexplorer said:**
> Ok here they are in order'

cdrom
cdrom0
cdrom1
floppy
floppy0
UBUSB
UBUSB_

Okay, can you go to Applications > Accessories > Terminal:

```

sudo umount /media/UBUSB
sudo umount /media/UBUSB_

```

If both commands complete with out error - then OpenOffice should give you an error saying it can't write to the file, and then you can save it somewhere else. But if the commands give you an error, try this:
```

sudo umount -f /media/UBUSB
sudo umount -f /media/UBUSB_

```

---

### Post by jungleexplorer on 2010-10-11
OK. The second code (sudo umount -f /media/UBUSB_) worked but the first code came up with this response:

dad@dad-desktop:~$ sudo umount -f /media/UBUSB
umount2: Device or resource busy
umount: /media/UBUSB: device is busy
umount2: Device or resource busy
umount: /media/UBUSB: device is busy

---

### Post by JustinR on 2010-10-11
Okay well the 'umount' command isn't of use to us any more - and the flash drive is still mounted.

The only way to fix this is to restart Ubuntu. But I would try to use 'Document Recovery' in OpenOffice.

Although, I would check these directories to see if there is an autosave file of your document:

/home/USERNAME/.openoffice.org/3/user/temp
/home/USERNAME/.openoffice.org/3/user/backup
/home/USERNAME/.openoffice.org/3/user/registry/cache

To get to these directories go to your desktop, then double click your home folder and press 'CTRL + H'.

---

### Post by jungleexplorer on 2010-10-11
SUCCESS!!  Yipeee!  Dude, you are the man!  I cannot thank you enough for all your help man.  Listen, I have never done this before, but you saved my bacon dude, and I want to give you a gift via paypal.  If you will P.M. the necessary information I send it right away.  You can PM on the Ubuntu forums can't you?

---

### Post by JustinR on 2010-10-12
> **jungleexplorer said:**
> SUCCESS!!  Yipeee!  Dude, you are the man!  I cannot thank you enough for all your help man.  Listen, I have never done this before, but you saved my bacon dude, and I want to give you a gift via paypal.  If you will P.M. the necessary information I send it right away.  You can PM on the Ubuntu forums can't you?

I'm glad it worked! And its fine - I'm glad I helped someone out, there's no need to repay me. I just like working with Ubuntu!

---

