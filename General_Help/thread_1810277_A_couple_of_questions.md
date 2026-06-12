---
title: "A couple of questions"
date: 2011-07-22
forum: General Help
---

### Post by DustinDear on 2011-07-22
My specs:
Phenom II x4 955 @ 4.0ghz
8GB DDR3 2000 RAM
2x 1TB Caviar Black 
ATI 4890 OC

I just installed ubuntu 11.04 alongside my windows 7 installation, and I had a few questions. 

1. When I installed, I shrunk my main partition 16gb and used the "Install Alongside Windows" option. This is what it looks like now.

[http://i.imgur.com/BHWvK.png](http://i.imgur.com/BHWvK.png)

Is that a good size? When I install applications and such, does it fill that area up or my main storage partition? 

2. I'm looking for a way to adjust my fans speeds and monitor temperatures of my hardware, is there something that could accomplish that?

3. What's the best way to access all my documents from the main partition, without having to navigate to Drive/Users/Name/blahblahblah


Thanks :D

---

### Post by e79 on 2011-07-22
> **DustinDear said:**
> 
1. When I installed, I shrunk my main partition 16gb and used the "Install Alongside Windows" option. This is what it looks like now.

Is that a good size? When I install applications and such, does it fill that area up or my main storage partition? 
You might run into problems if you are installing lots of packages/programs on your Windows as well as Ubuntu. I would personally double your Windows AND Ubuntu main partition (C: and  / respectively) size and define your /home and sorage (for Windows) to be on you 'Storage' partition.

> 
2. I'm looking for a way to adjust my fans speeds and monitor temperatures of my hardware, is there something that could accomplish that?I think [lmsensor]("https://help.ubuntu.com/community/SensorInstallHowto") is what you are looking for.

> 
3. What's the best way to access all my documents from the main partition, without having to navigate to Drive/Users/Name/blahblahblahIf you speak from the Ubuntu point of view, opening your documents stored on the NTFS partition used by Windows, simply add a 'Bookmark' in Nautilus. To do so, from Ubuntu, navigate up to the Documents folders of your Storage partition and (in Nautilus), choose 'Bookmark' (at the top) and then 'Add Bookmark'.

Hope this helps

---

### Post by pqwoerituytrueiwoq on 2011-07-22
for number 2
sudo apt-get install sensors-applet
idk if it works with unity or not i know it works wiht my gnome panel on 10.04
also look up fan control in the software center

---

### Post by jramshu on 2011-07-22
I don't think you need 8.6gigs of swap.
JMO.

---

### Post by DustinDear on 2011-07-23
Thanks for all the help!

I'm not in ubuntu right now, but I'll check out those temp programs and the fan one as well.

e79, what do you mean by double my ubuntu and windows partitions? Do you mean double the 16gb to 32? The only other partition besides the swap and ubuntu is the NTFS one. Sorry, I'm new to this stuff. ](*,)]

---

### Post by e79 on 2011-07-23
Yes, both root partition, I would personally double them (or at least 1.5x), since this is where all updates and most programs will be installed unless you specify otherwise. Just to be on the safe side :D

---

### Post by DustinDear on 2011-07-23
> **e79 said:**
> Yes, both root partition, I would personally double them (or at least 1.5x), since this is where all updates and most programs will be installed unless you specify otherwise. Just to be on the safe side :D

Alright, so I should do this within windows right? I tried using Gpart in ubuntu but everything was greyed out.

What should I do from here? Shrink the NTFS another 16?
[http://i.imgur.com/03Rkd.png](http://i.imgur.com/03Rkd.png)

---

### Post by Megaptera on 2011-07-23
DustinDear,
For #3 accessing/sharing docs have a look at this neat solution:

[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by e79 on 2011-07-23
I guess I would first try to resize your Windows installation using the [Disk Management system]("http://www.nirmaltv.com/2009/05/12/how-to-resize-disk-partition-in-windows-7/") that comes with Windows 7. Since your storage space appears to be NTFS, I don't think it should need to be formatted.

As for resizing Ubuntu, I think that Gparted can achieve the same effect, but as Ubuntu use ext4 I guess you would have to format the extra space as well. I frankly never had to do it personally but I suggest you get a look at : [http://ubuntuforums.org/showthread.php?t=1556703](http://ubuntuforums.org/showthread.php?t=1556703)

---

### Post by mcduck on 2011-07-23
The rooot partitin is very small, you are definitely going to run out of space with that. (And the swap is needlessly large as well, you only need as much swap as you have RAM if you want to suspend the machine, and if you don't use suspend then with any modern system you should be fine with a 1 to 2 GB of swap space.)

..and the reason why resizing options in gparted are greyed out is that you can't edit partitions you are using at the moment. The NTFS partition for Windows 7 should be resized from Windows itself, and after you've done that you need to start the computer with Ubuntu's Live-CD (or USB), unmount the Linux root and swap partitions, shrink the swap and then resize the root partition to fill up the space freed from swap and your Windows partition.

None of the partitions should need formatting, but of course you should have backups of any important files you have on that hard drive. On the other hand you should always have backups anyway... ;)

---

### Post by Niocora on 2011-07-23
With 8GB of RAM at 2000MHZ you don't need a swap partition at all. Unless your cache times are slow and you have 1Tb SSD's (:

---

### Post by DustinDear on 2011-07-23
> **mcduck said:**
> The rooot partitin is very small, you are definitely going to run out of space with that. (And the swap is needlessly large as well, you only need as much swap as you have RAM if you want to suspend the machine, and if you don't use suspend then with any modern system you should be fine with a 1 to 2 GB of swap space.)

..and the reason why resizing options in gparted are greyed out is that you can't edit partitions you are using at the moment. The NTFS partition for Windows 7 should be resized from Windows itself, and after you've done that you need to start the computer with Ubuntu's Live-CD (or USB), unmount the Linux root and swap partitions, shrink the swap and then resize the root partition to fill up the space freed from swap and your Windows partition.

None of the partitions should need formatting, but of course you should have backups of any important files you have on that hard drive. On the other hand you should always have backups anyway... ;)

Thanks for the help! 

I went back into windows and shrunk the NTFS partition another 15 gigs, does that sound good? 

Now I'm booted into what I assume is LiveCD, the "try ubuntu" option. The ext4 root was unmounted, and I used "Swapoff" on the swap partition. I shrunk it to 1.5gb. So now I have the 14.65 unallocated and the 6.53 unallocated. I cant seem to figure out how to expand the root into those.

---

### Post by mcduck on 2011-07-23
> **DustinDear said:**
> Thanks for the help! 

I went back into windows and shrunk the NTFS partition another 15 gigs, does that sound good? 

Now I'm booted into what I assume is LiveCD, the "try ubuntu" option. The ext4 root was unmounted, and I used "Swapoff" on the swap partition. I shrunk it to 1.5gb. So now I have the 14.65 unallocated and the 6.53 unallocated. I cant seem to figure out how to expand the root into those.

That sounds large enough, especially if you keep some of your personal files on the NTFS partition anyway.

To grow the Linux root partition you'll first need to move the extended partition (that contains your Linux partitions) so that it starts where the NTFS partition ends. Then you can grow it to fill the space at the ends of the disk. And after that you should be able to move the swap to the end of the extended partition and grow the root partition to use the freed space.

You also asked how to access the files on the NTFS partition the easiest way. I'd do it by configuring the NTFS partition to mount automatically at boot in /etc/fstab, mounting the drive in  a directory inside /mnt. Then I'd create symbolic link from the mount point to a directory in my home. (you could also set it to automount inside /media, but at least I wouldn't want to see an internal drive appear on the desktop all the time like removable drives do, which is what happens for any drive mounted in /media)

---

### Post by DustinDear on 2011-07-23
> **mcduck said:**
> That sounds large enough, especially if you keep some of your personal files on the NTFS partition anyway.

To grow the Linux root partition you'll first need to move the extended partition (that contains your Linux partitions) so that it starts where the NTFS partition ends. Then you can grow it to fill the space at the ends of the disk. And after that you should be able to move the swap to the end of the extended partition and grow the root partition to use the freed space.

You also asked how to access the files on the NTFS partition the easiest way. I'd do it by configuring the NTFS partition to mount automatically at boot in /etc/fstab, mounting the drive in  a directory inside /mnt. Then I'd create symbolic link from the mount point to a directory in my home. (you could also set it to automount inside /media, but at least I wouldn't want to see an internal drive appear on the desktop all the time like removable drives do, which is what happens for any drive mounted in /media)


Sucess! :)

Now have a 31.5gb partition with 1.5 swap and the rest root. 

As far as accessing pictures and music etc. on my NTFS drive, I've made Launchers on the desktop that path to my folders on my NTFS drive. It seems to work fine, or am I missing something?

---

### Post by akakingess on 2011-07-23
Here is a link to help with the fstab configuration:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by mcduck on 2011-07-23
> **DustinDear said:**
> Sucess! :)

Now have a 31.5gb partition with 1.5 swap and the rest root. 

As far as accessing pictures and music etc. on my NTFS drive, I've made Launchers on the desktop that path to my folders on my NTFS drive. It seems to work fine, or am I missing something?

If it works fine, then it's fine. :)

using symlinks would allow you to access the locations exactly if they were in your home, though, so the locations would be accessible and writable from any program. Launchers, on the other hand, only work for human users.

I suppose the best way to put it that symlink brings the target location to where the symlink is, while a launcher only moves the user to where the launcher is pointing to.

---

### Post by DustinDear on 2011-07-23
> **mcduck said:**
> If it works fine, then it's fine. :)

using symlinks would allow you to access the locations exactly if they were in your home, though, so the locations would be accessible and writable from any program. Launchers, on the other hand, only work for human users.

I suppose the best way to put it that symlink brings the target location to where the symlink is, while a launcher only moves the user to where the launcher is pointing to.

Thanks, I think I understand. I'll just stick with this for now, so I dont screw anything up :)


About the temperature monitoring and fan control, I have lm-sensors installed, but typing sensors in terminal only gives me my voltages, CPU, and Motherboard temps, nothing else. Also, I installed the sensors-applet, but can't figure out how to make it appear anywhere. #-o

EDIT: Found AMDOverdriveCtrl  which lets me monitor GPU temp and change fan speed.

---

