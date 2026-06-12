---
title: "changing mount names for Portable USB Hard Drives"
date: 2010-12-03
forum: General Help
---

### Post by agrayray on 2010-12-03
I have two 1TB Passport Drives that I use in my Ubuntu 10.04 64 bit install for pretty much everything.  

When I plug these into my laptop, Ubuntu automatically creates a name 'My Passport' for them if I only attach one USB drive, however if attach both I get one as "My Passport" and one as "My Passport_".  Futhermore both show up in "Places" as "My Passport".

My problem is that I these mappings change all the time for me as I can not get in habit of plugging in at same order or whatever assign the names and the drive that was "My Passport" last time becomes "My Passport_" the next time and so on.  This is causing a lot issues with me because too many other software pieces use hardcoded paths to USBs (for ex VMware).

Also its pretty annoying playing the check and guess name selecting from Nautilus.

Is there a way I get past this so that each USB mounts with a set name/directory in media that I can forever use.

BTW, I would really like not to change anything on the USB drives as I use them on many other computers also.

Also I frequently connect my USBs before boot so it has to be a solution that works without changing something after the computer has booted.

Thanks in advance!

---

### Post by coffeecat on 2010-12-03
"My Passport" is probably a partition label. If a partition label is present, Ubuntu will create a dynamic mountpoint in /media with the same name which gets deleted when you unmount. If you then mount another drive/partition with the same label and with the first still mounted, the new mountpoint is called 'label_'. 

The answer is to change the partition label on each to something unique. You can do this in Ubuntu using Disk Utility, or if they are NTFS drives and you are using Windows on one of your computers, you can change the label in 'My Computer'. Simply right-click on the drive in 'My Computer' ('Computer' in Vista/W7) and choose 'rename'.

Changing the partition label will not affect its functionality in other computers. In fact it will be a help. Whether you are using Ubuntu, most other Linux distros, MacOS or Windows, the partition label is used to identify the drive/partition. In Windows you get a drive letter allocated, but you'll see the partition label as well.

---

### Post by agrayray on 2010-12-04
thanks cat..changed my partition label and now ubuntu mounts all them uniquely...awesome thanks!

---

