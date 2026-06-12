---
title: "Seems an easy problem to solve - get CD-RW device to work"
date: 2011-03-14
forum: General Help
---

### Post by dragonfly41 on 2011-03-14
First post and I'm new to Ubuntu/Linux.   I've come to this forum after struggling to recover from a crashed Vista on Dell Inspiron 1720  laptop.  No Restore Point.   After a crash I was not able to burn a Vista Recovery Disk to my CD-RW drive (media was not recognised to be formatted and burned) so the problems explained below really started in Vista.
 
 In Vista safe mode I managed by luck to install Ubuntu Windows Installer and have been using Demo Mode to get the feel of Ubuntu.   Not yet a full installation until I've recovered my files.   I started an installation but realising this might wipe my windows files I quickly stopped by power off after a second or so.   However I am not able to get back into Vista safe mode .. only into Ubuntu in dual boot mode 
 
 Luckily I'm still able to see in Ubuntu File System the files left from Vista and I've started backing up these to a USB drive.
 However my problem now in Ubuntu is I cannot seem to get my CD-RW device to work. 
I would like to burn Vista_Recovery_Disk.iso file to disk to try to recover Vista. 

I've added a second CD-RW device via USB port .. so I have two CD-RW devices (one internal the other external) not  recognising inserted disks .. in either Vista or Ubuntu.
 Icons for both devices are seen in Ubuntu &#8220;Computer&#8221;.

I've gone to .. Applications > Sound & Video > Brasero Disk Burner
  Burn image .. browse to Vista_Recovery_Disk.iso
  and the message pops up ..
 
 Select a disk to write to
 
 &#8220;No disk available&#8221;
 &#8220;Please replace the disk with a supported CD or DVD&#8221;
 
 Now this test disk I'm using is CD-RW 12x Speed 700 MB which I've just checked can be read in another old laptop.
 
 I tried inserting another blank disk unused .. CD-RW 1x 2x and 4x.
 Same error message seen.
 
 If I go to Brasero > Tools >  
 I cannot even "eject" the non recognised disc and I get the message
 
 The disc in &#8220;HL-DT-ST DVD+-RW GSA-T21N&#8221; cannot be ejected
 
 Reading some threads in this forum I see that libdvd libraries need to be installed but there is no sign of these. 
 
 How can I get either of my two CD-RW devices (one internal one external) to recognise any inserted disk to allow burning?
Do I need to install packages?   What files should I look for?  What tests can I do?
I've dumped out details of both devices if that info is needed.

---

### Post by kanikilu on 2011-03-14
I don't think you need "libdvdread/css" or anything special to burn a simple CD. Since you also couldn't burn a disc in Vista, that tends to make me think there is either a problem with the drive or the media you have. However, it seems like you've tried multiple drives and media types (or at least different discs of the same type), so that doesn't really make sense to me... :confused:

With the external drive plugged in, does ```
wodim --devices
``` list any accessible drives?

It seems like the media you are using is all CD-RW. I don't really see a problem with that, but do you have access to any other media to try, that's completely different brand and type; e.g. DVD+R, CD-R (not re-writable)? I know you said you tried it in an older laptop, but sometimes drives can be picky about certain types or even brands of media.

Lastly, this is a dumb question, but it doesn't hurt to cover all bases. What is the file size of the ISO image you are trying to burn?

---

### Post by dragonfly41 on 2011-03-14
Thanks for your reply.

I agree that the situation is crackers and is probably a mismatch of media
 
Anyway with only my internal CD-RW working here is the result
 
 ubuntu@ubuntu:~$ sudo wodim --devices 
 wodim: Overview of accessible drives (1 found) : 
 ------------------------------------------------------------------------- 
  0  dev='/dev/scd0'    rwrw-- : 'HL-DT-ST' 'DVD+-RW GSA-T21N' 
 ------------------------------------------------------------------------- 

 and when I add the USB port CD-RW device I get this ..
 
 ubuntu@ubuntu:~$ sudo wodim --devices 
 wodim: Overview of accessible drives (2 found) : 
 ------------------------------------------------------------------------- 
  0  dev='/dev/scd0'    rwrw-- : 'HL-DT-ST' 'DVD+-RW GSA-T21N' 
  1  dev='/dev/scd1'    rwrw-- : 'MATSHITA' 'DVD-RAM UJ890AS' 
 ------------------------------------------------------------------------- 
 

  Regarding other media I've been able to mount two different USB drives on the same USB port and in fact copy files from my crashed windows.
 
All drives (CD-RW and USB and other) can be seen in System > Administration > Disk Utility
 
The first CD-RW device under PATA Host Adapter
 The second CD-RW device under Peripheral Devices (USB port)
 
 I've tried opening the test disk in a very old laptop Inspiron 5000 Windows 2000 Professional Client
 but this only has CD R device.   Read only.    

The USB MATSHITA device (which is a recent purchase) did not work too well on this old laptop.  But this may be because it requires USB 2.0 port and the ancient laptop has USB 1.0.
 
The size of the iso is about 170 MB.   Vista_Recovery_Disk.iso.   But I don't get as far as having the inserted CD disk even recognised.

I'm wondering if since Ubuntu is running in a virtual disk environment (C:\Ubuntu) it is inheriting the problems I had in Vista when the CD-RW devices would not work and recognise or read/write disks inserted.   In fact there was no format feature in Vista.

I haven't done a full installation of Ubuntu yet (it's still running in Demo Mode in wubie) and if I do will I have more control over the devices?   But my files will be wiped if I do this.

Thanks again.

---

