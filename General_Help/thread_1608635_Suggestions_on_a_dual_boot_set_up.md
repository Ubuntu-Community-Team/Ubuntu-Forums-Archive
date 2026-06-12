---
title: "Suggestions on a dual boot set up"
date: 2010-10-29
forum: General Help
---

### Post by ChuckNorse on 2010-10-29
Hello I am a super noob to Ubuntu. I am also a noob to computer building. I have successfully (knock on wood) built a media/gaming rig. I want to dual boot with Windows 7 and Ubuntu. I have a 64gb SSD and a 1TB HDD. Here is what I was thinking: Install Windows 7 and games on the SSD for speed and install Ubuntu on the HDD. I want to use Ubuntu for downloading media from the internet as I have heard that it is less susceptible to viruses. I do want have access to all my media from both OS. Should I partition 1/2 the TB for dowloading and the other 1/2 for Ubuntu/home/swap/shared media files? Should I have another hard drive just for shared media files and keep my current HDD for Ubuntu and downloading only? I am ignorant as to how viruses work. Even though viruses may not effect Ubuntu as much, would a virus slip right through Ubuntu unnoticed and then cause problems when I open the file with Windows? Any advise would be greatly appreciated. Also, I bought a magazine with a 10.4 DVD in it to try. Is this a 64 bit edition? I have read that there is a 10.10 out? I have not installed anything yet and I have read you have to install windows first? I am waiting for my copy of windows and I want to play around with Ubuntu. I think that is all my questions finally :) Thank you all for your patience.

---

### Post by malcmail on 2010-10-29
I recently cleaned my windows PC and then set up a dual boot with Ubuntu 10.04. The install for 10.04 was an absolute skoosh and did the partition for me to allow dual boot. I'm not sure how it would work with 2 different drives so best wait for someone else to come along.

If you want to try out Ubuntu and keep changes you make / programs you install check out [www.pendrivelinux.com](www.pendrivelinux.com). Put a computer on a USB as I explained it recently :)

---

### Post by davidvandoren on 2010-10-29
I would disconnect the hdd and install windows 7.
Then disconnect the ssd and connect the hdd and install ubuntu. 
Finally connect them both and press depending your motherboard F11 or F12 to choose the drive I want to boot from.

Otherwise first widows 7 and then ubuntu.


Sorry I did not notice.
If you don't have windows 7 yet you can install ubuntu on the hdd first and later disconnect the hdd and install windows 7.

Both will use their own bootmanager this way

---

### Post by Lamez on 2010-10-29
I would use the SSD for both of your OSs and TB drive for storage. The best way to do this is first put 7 on a partition on its own, leaving an unacollated section for Ubuntu, if you already have 7 installed, shrink the partition.

Then install Ubuntu on the seperate partition.

Ubuntu will override 7's bootloader and detect 7 on the drive, if you do it vice-versa you will run into loads of headaces. Trust me.

---

### Post by ChuckNorse on 2010-10-29
> **davidvandoren said:**
> I would disconnect the hdd and install windows 7.
Then disconnect the ssd and connect the hdd and install ubuntu. 
Finally connect them both and press depending your motherboard F11 or F12 to choose the drive I want to boot from.

Otherwise first widows 7 and then ubuntu.


Sorry I did not notice.
If you don't have windows 7 yet you can install ubuntu on the hdd first and later disconnect the hdd and install windows 7.

Both will use their own bootmanager this way

Thank you for the advice. Will I be able to access files from the ubuntu drive with windows? I want to keep the SSD restricted to games and windows and I would like to be able to keep all my windows documents on the HDD. I will be also have Adobe CS5 on Windows and will want to keep all my projects and caches on the HDD. Thanks again.

---

### Post by ChuckNorse on 2010-10-29
> **Lamez said:**
> I would use the SSD for both of your OSs and TB drive for storage. The best way to do this is first put 7 on a partition on its own, leaving an unacollated section for Ubuntu, if you already have 7 installed, shrink the partition.

Then install Ubuntu on the seperate partition.

Ubuntu will override 7's bootloader and detect 7 on the drive, if you do it vice-versa you will run into loads of headaces. Trust me.

Thank you for the reply. Please forgive my ignorance, but is it possible for a virus from ubuntu to infect the whole SSD? Does the separate partitions prevent that? I want to do a lot of downloading with ubuntu.

---

### Post by davidvandoren on 2010-10-29
> **ChuckNorse said:**
> Thank you for the advice. Will I be able to access files from the ubuntu drive with windows? I want to keep the SSD restricted to games and windows and I would like to be able to keep all my windows documents on the HDD. I will be also have Adobe CS5 on Windows and will want to keep all my projects and caches on the HDD. Thanks again.

I don't know how good windows is by now reading Linux partitions
As far as I know not at all or only with third party software.

My suggestion is to create a fat32 partition for sharing files between linux and windows the newer formate ntfs allows you to have files bigger than 30G but I think Linux still has some bugs with this also. "At least it's said so"

Easiest way to formate this one, for a newbie, is to use a windows XP or 2000 CD first, and formate the hdd to whatever formate you want to use, by simply initiating the install and ejecting the CD, once it starts to copy files to the drive.


Sorry forgot 
If you are familiar with geparded, use this of course to do the formatting.

---

### Post by 3Miro on 2010-10-29
Here something about the viruses that you can read: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Basically, viruses attach to files. If you download an infected file under Ubuntu, it will have no effect on your system. The infected file will just stay there. However, when you go under windows, then the virus may get active and do whatever damage.

If you want to "share" partitions between Linux and windows, you can use either the windows format NTFS (which is not very fast, has to be defragmented and so on) or install software under windows that will let it read ext Linux partitions. The second method requires more work and I don't know how good the windows software is.

---

