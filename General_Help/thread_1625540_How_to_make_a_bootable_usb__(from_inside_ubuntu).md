---
title: "How to make a bootable usb  (from inside ubuntu)"
date: 2010-11-19
forum: General Help
---

### Post by a quarter past seven on 2010-11-19
How do i make a boot-able usb disk in ubuntu,

i have an ISO i need to burn but i can only find instructions on how to do it in windows, is their a Linux equivalent to universal usb installer as it doesn't find any usbs when i run it in wine, also ive tried using start up disk creator but it only wants to find a mobile broadband dongle so is their any other way to do it?

its offline ntfs password recovery im trying to burn to usb and im on a net-book by the way

cheers,

---

### Post by dino99 on 2010-11-19
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by eotakos on 2010-11-20
I have a couple of questions concerning the ubuntu live usb, and since this thread seems pretty fresh and active (I suppose), I thought posting here...

so my case of "usb stick" is a portable usb hard drive, with 3 partitions, of which the first is NTFS so it can be seen by windows machines...

a) Indeed when installing the ubuntu live on the usb, the selection of the device on which the installation is to be operated, seems to be referring to a partition, but... is there any chance that the procedure messes up with the other partitions on the same -hardware- device as well?

b) after installing the ubuntu live, does the usb device continue to be seen by windows machines? //  is there any specific partition arrangement I could try in order to achive that? because my experience says that windows sees an fat32 or ntfs partition, only when it is the first one on the usb device... I guess ubuntu live won't use any of these kinds of fs. On the other hand, is it imperative that the ubuntu live is installed at the first partition of the drive? (I guess not, but it's best to make sure)


thank you very much for any answers in advance

---

### Post by a quarter past seven on 2010-11-20
> **eotakos said:**
> I have a couple of questions concerning the ubuntu live usb, and since this thread seems pretty fresh and active (I suppose), I thought posting here...

so my case of "usb stick" is a portable usb hard drive, with 3 partitions, of which the first is NTFS so it can be seen by windows machines...

a) Indeed when installing the ubuntu live on the usb, the selection of the device on which the installation is to be operated, seems to be referring to a partition, but... is there any chance that the procedure messes up with the other partitions on the same -hardware- device as well?

b) after installing the ubuntu live, does the usb device continue to be seen by windows machines? //  is there any specific partition arrangement I could try in order to achive that? because my experience says that windows sees an fat32 or ntfs partition, only when it is the first one on the usb device... I guess ubuntu live won't use any of these kinds of fs. On the other hand, is it imperative that the ubuntu live is installed at the first partition of the drive? (I guess not, but it's best to make sure)


thank you very much for any answers in advance


i dont think it matters about the partition or the file sysstem of the usb as youre not entering windows so it doesnt need be able to recognise the usb youre booting up straight into the usb and bypassing windows, 
and no it doesnet matter which partition you have it on just burn the .iso to the usb then its ready to be used i dont know how or if you can choose which partition you to burn it to though,

take a look at 

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

and it'll take you through it

---

### Post by C.S.Cameron on 2010-11-20
Ubuntu live installs to FAT32. It should be the first partition on the drive.
You can add home-rw and casper-rw partitions if you need more than 4GB persistence.
You can read and write to the Ubuntu FAT32 partition using Windows.
When booting the drive you can access the stuff you have written to it with Windows by going to the File System / cdrom folder.
With 10.10 this folder is now read only but you should be able to write to it using "gksu nautilus".

edit:
I think the first partition - Windows thing only applies to USB flash drives, not USB mechanical ones.

---

### Post by wilee-nilee on 2010-11-20
Which password are you missing?
[http://www.psychocats.net/ubuntucat/resetwindowspassword/](http://www.psychocats.net/ubuntucat/resetwindowspassword/)

Same site tells you how to reset the password for Ubuntu as well.

---

### Post by a quarter past seven on 2010-11-20
> **wilee-nilee said:**
> Which password are you missing?
[http://www.psychocats.net/ubuntucat/resetwindowspassword/](http://www.psychocats.net/ubuntucat/resetwindowspassword/)

Same site tells you how to reset the password for Ubuntu as well.


i know you wasent talking to me but, im trying to get back into my windows vista machine ive tried ntfs offline data recovery tool but the only drivers it picks up is the usb i tried all the possible options but it could only pick up the usb as a drive, any ideas on how to get it to pick up the windows partitions? ive had a look around and cant find anything to help

---

### Post by wilee-nilee on 2010-11-20
> **a quarter past seven said:**
> i know you wasn't talking to me but, im trying to get back into my windows vista machine ive tried ntfs offline data recovery tool but the only drivers it picks up is the usb i tried all the possible options but it could only pick up the usb as a drive, any ideas on how to get it to pick up the windows partitions? ive had a look around and cant find anything to help

The link I gave was for you and will get you in, read it carefully you just need a Live Ubuntu CD I think. there is also Hirens it has a password eraser. This is all the help I can give as really you intentions may be honorable but I can't confirm that. This is the web and others do try to get into others computers. This sort of access is all over the web and how to do it.;)

---

### Post by a quarter past seven on 2010-11-21
> **wilee-nilee said:**
> The link I gave was for you and will get you in, read it carefully you just need a Live Ubuntu CD I think. there is also Hirens it has a password eraser. This is all the help I can give as really you intentions may be honorable but I can't confirm that. This is the web and others do try to get into others computers. This sort of access is all over the web and how to do it.;)


ok cheers for the help i suppose it doesn't mean much coming from a stranger on the inter-web but my intentions were honourable

---

### Post by eotakos on 2010-11-21
> **a quarter past seven said:**
> i dont think it matters about the partition or the file sysstem of the usb as youre not entering windows so it doesnt need be able to recognise the usb youre booting up straight into the usb and bypassing windows 

this is nice thinking, my intention to be able to see the disk through windows, is just that!, and not to boot live ubuntu through windows. I wouldn't question a procedure that is proven and it works. I wanted more information about the procedure, so I can use the feature, while adopting it to my needs, i.e. have a ubuntu live usb stick, but at the same time have a usb-stick storage space to use with windows ;)



C.S.Cameron :  thank you for all the info. indeed useful :-)

---

