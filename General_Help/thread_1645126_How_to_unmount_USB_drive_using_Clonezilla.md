---
title: "How to unmount USB drive using Clonezilla"
date: 2010-12-14
forum: General Help
---

### Post by brambaut on 2010-12-14
Hi,

Let me first of all briefly introduce myself.
I'm an Belgian architect currently working as a volunteer nearby the end of the world somewhere in the bush of Tanzania. Besides my job here to coordinate the construction of a boarding secondary school, I've been asked to improve the primary school as well. Since we want to start up a computer class in january, we collected 40 good second hand computers from a company which erased (of course) all hard disks.

In order to easely setup those 40 computers (for me as being not at all a computer hero and moreover here in the bush where electricity cuts are a daily habbit), I received 3 cd's of Clonezilla Live as well as 3 USB drives with the images. I'm following the instructions I found on the internet, but got allways this error after I've chosen which image file I want to restore:

"[COLOR=Red]Error! No unmounted partition(s) are found! To use Clonezilla to save ar clone a partition, the source partition must be unmounted! Press enter tot exit...[/COLOR]"

>** So: what am I doing wrong or how do I have to unmount my source partition (which is my USB drive)?**

Thanks a lot for all your help!

Hereby shortly my procedure:

> Boot from cd with Clonezilla Live
> Choose Clonezilla default settings
> Choose language: English
> Choose "Don't touch keymap"
> Start Clonezilla
> Choose "device-image (work with disks or partitions using images)"
> Choose "local_dev (use local device (e.g.: hard dirve, USB drive))"
> I insert my USB drive, wait for about 5 seconds and press enter
> Choose "sdb1 4013MB_vfat(In_Cruzer_Blade)_usb-ScanDisk_Cruzer_Blade_20044318200C93636F1C0:0"
> Choose "/ Top_directory_in_the_local_device"
> The file system disk space usage: press enter to continu
> Choose Beginner mode
> Choose "restoreparts (restore_an_image_to_local_partitions)
> Choose the image file to restore: 2010_09_02-19-img 2010-09-03_15:30_sda1
> Excluding busy partition or disk...
  Error! No unmounted partition(s) are found! To use Clonezilla to save ar clone a partition, the source partition must be unmounted!
  Press enter tot exit...


ps: I'm sorry if I didn't post this thread in the right forum categorie, but I just googled my error and found another thread here...and since internet is here in the bush of Africa not only extremely slow (using a USB 3G modem on my laptop) but also super expensive, I couldn't spent more (air)time on figuring out where to post my thread!

---

### Post by brambaut on 2010-12-15
nobody around who can help me, please?
thanks!

---

### Post by bwaanaa on 2010-12-20
Hi:
 
Glad to hear you are setting up computers inn Tanzania. Iam from Tanzania,, living in Canada now. I understand your problems with setting up.
 
I just had a similar problem with the message No unounted drives found and thats how I found your link. I don't know Linux at all but here how I got rid of the error, by sheer luck! I am using external hard drive (USB). After getting the error message on my laptop,  I connected it back to my computer with Windows XP it didn't recognize it either. I then disconnected from the pc and removed the power plug from the drive (I hope your usb is not a flash drive) and then connected to usb port in the computer (with XP), with the power plug still disconnected. I then connected the ac power to the drive and luckily the sytem saw the drive. I let it load the files and then clicked on "Safely Remove USB" icon (which unmounts the drive automatically). I then connected the drive to my laptop to continue the cloning using Clonezilla. 
 
The only diference I see is that you connect the drive just before it detects it , whereas I connect it right at the beginning when I actullay boot the system. But I don't think that should make any difference. 
 
I am sorry I don't know anythig about Linux so I can'tbe much help. I hope you have a USB with power connection and mya be that will fix the problem.
 
Good luck.

---

### Post by brambaut on 2010-12-22
Salama Bwanaaa,

Asante sana kwa jibu yako - thanks for your reply!

Unfortunately, it did not solve my problem. I'm using a USB flash drive. When I enter it in another computer, windows does recognize it. However, I can not "safely remove it" using the icon in the task bar, because I'm allways getting the "The device cannot be stopped right now" message.

Then, I tried to copy the whole directory from this USB flash drive to another USB hard disk. But again, Windows fails somehow to remove it safely (and so to unmount it?).

Any other tips in solving this urgent topic?
Is there another way to unmount my USB flash drive?
Thanks a lot!

---

### Post by argedion on 2010-12-22
First Welcome to the forums. 

Second Your problem really isn't an Ubuntu problem and you would probably have more luck going to [http://clonezilla.org/forum/](http://clonezilla.org/forum/) for help.

When Windows does not "Safely remove a drive" then you can shut Windows down. This forces Windows to unmount all it's drives "Safely" 

Alternatively you should find a good tutorial on clonzilla before trying to use it.

You should also check the usb drive and make sure it is not damaged.

---

### Post by slice16 on 2010-12-22
Hi brambaut,

It looks like you are choosing the wrong options. Am I right in presuming you want to restore an image from USB to the local drive? 

I cant remember the full procedure (not done it for ages). I will run through this tonight (and get the write up on my blog, as I keep forgetting), which should help.

Thanks,

Paul

---

### Post by brambaut on 2010-12-22
@argedion: I did the same post on clonezilla.org/forum, but it took more than a week to get the first reply. Moreover their website loads rather slow (for my 3G Mobile Internet Connection) and their banners are eating thousands of Tanzanian Shillings in airtime... Anyway, thanks for your advice!

@slice16: you're right: I want to restore an image from a USB flash drive to the local hard drive. Thanks a lot in advance for all efforts to run through the procedure tonight.

---

