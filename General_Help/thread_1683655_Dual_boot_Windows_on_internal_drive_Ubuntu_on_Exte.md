---
title: "Dual boot Windows on internal drive Ubuntu on External HDD"
date: 2011-02-07
forum: General Help
---

### Post by Acedrew89 on 2011-02-07
Hi Ubuntu Community,

I have been searching most of the day for a safe tutorial and haven't been able to thus far. I was hoping you could help.

What I want to do is install Ubuntu on my external hard drive, leave Windows on my internal hard drive, and have the ability to swap between the two. Basically, is there a way to make it so I can have it so if I plug in the external hdd and tell my computer to boot from there I can have that boot Ubuntu. Then if I shut down and unplug, have the computer boot Windows from the internal drive?

I feel like this is simple and I shouldn't have as much trouble finding a tutorial on this. I'm sure I could figure it out on my own but I'm a bit weary of going that route, fearing the loss of all of my internal hard drive.

Thanks,
Andrew

---

### Post by korleon on 2011-02-07
Why not just install Ubuntu to the external drive using the same techniques as with pendrives?  Just set your BIOS to look for the external first and when it's plugged in, you'll boot into the awesomeness of Ubuntu.  When it's not well that will be the other OS....

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Acedrew89 on 2011-02-07
> **korleon said:**
> Why not just install Ubuntu to the external drive using the same techniques as with pendrives?  Just set your BIOS to look for the external first and when it's plugged in, you'll boot into the awesomeness of Ubuntu.  When it's not well that will be the other OS....

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Will I be able to see the external drive once I'm in the partitioning process, and if so will it distinguish between the two drives or just see them both as a total 440gigs?

Also, thanks for the quick reply. I think it makes sense, I just want to be sure it will work out well (to a certain degree, obviously you can never be sure until you jump) prior to attempting the install.

---

### Post by efflandt on 2011-02-07
The only hard part, if you are new at Linux or Ubuntu, is making sure that you install grub (boot loader) on your external drive, instead of default to your main internal drive.  That varies between Lucid (10.04) or earlier, and Maverick (10.10) or later.  Some people suggest unplugging your internal drive, so your external drive is the only one visible when you install Ubuntu and grub will automatically be installed there.  One nice thing about Ubuntu using UUID to find partitions is that booting the external drive should even work if the external drive ends up as a different drive (and/or on a different computer).

If you are going to install Ubuntu to an external drive without disconnecting your internal drive, you need to make sure you know how to specify where to install grub during install.  The install should show individual partitions on both drives, with your internal drive being /dev/sda (partitions sda1, sda2, etc).  You external drive might be sdb if installing from CD, sdc if installing from USB flash, or a higher letter if you have other drives or built in multi-card reader.

For **10.10 or later** (Maverick or Natty development) the choice where to install grub is at the **bottom of the manual partitioning screen**.  That is the same page where you manually set up or select partition(s) used for Linux.

For **10.04 or earlier**, you have to use the **Advanced** button on the summary screen after you enter your username and password, to select where to install grub.

Note that even if you set your BIOS to boot USB before internal drive, you might still need to press a key during BIOS splash screen (often F12 or Esc) to boot from USB.  That is probably a safeguard to prevent accidentally booting from an unknown drive.  The only virus I ever caught was a boot sector virus spread by floppy disks long ago.

---

### Post by tednix on 2011-02-07
A few weeks ago I followed these instructions to install Ubuntu on a 60Gb external HDD.
[HTML]http://ubuntuforums.org/showthread.php?t=1650699&highlight=avoid+wubi[/HTML]Be sure to place GRUB on the external drive as suggested.

Set the BIOS to detect USB first.

When the external drive is plugged in the bootloader menu comes up and you can select either Ubuntu or Windows.  If the drive is not plugged only Windows starts.  Because Ubuntu is on an external drive it runs slightly slower than it would if you dual booted from the internal drive but I don't have to worry about GRUB errors screwing up my Windows partition.

---

### Post by Acedrew89 on 2011-02-07
Thank you both EfflandT and Tednix. I am going to go with a mix of both. I'll read the tutorial and then make sure that EfflandT's jives with that then probably go that direction. Unfortunately it is late and I don't want to do this on a sleepy head so I'll try it in the morning and let you know how it went.

Thanks,
Andrew

---

### Post by Acedrew89 on 2011-02-09
Sorry for the delay, yesterday was too hectic to be able to devote time to the installation. 

On the bright side, I did give it a go just a little bit ago. On the down side, Ubuntu isn't recognizing my Seagate 320gig external drive at all except for the 4gigs it had to reformat to place the Ubuntu .iso on there. What I'm thinking is that I need to find a way to reformat the entire 320gigs to something the Ubuntu can read and then I will be all set to go.

Also, Ubuntu is reading a drive by the name of 'casper rw' and I thought that might be the Seagate, but am now realizing that's probably the CD drive. So basically it's not reading the Seagate at all. Any thoughts?

Other than this snag all of your comments have proven true thus far, thank you guys very much.

---

### Post by Acedrew89 on 2011-02-09
The reformating didn't work. Any thoughts?

---

### Post by oldfred on 2011-02-09
A size of 4GB and casper-rw sounds like the FAT partition that the Live installer creates for flash drives.

You should use gparted and totally reformat hard drive with partitions you want. Then use manual install so you  have a choice on where to install grub2.

Another set of instructions.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

My suggestions, but everyone has different needs/suggestions.
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by Acedrew89 on 2011-02-09
I started reformatting the drive but realized I would be reformatting the drive I was using at the moment since I was in Ubuntu. Is that safe? It says I will be losing everything if I continue.

Also, is there a specific format I should reformat it to other than the MS-Dos is defaults to?

Thank you for all of your help.

---

### Post by wilee-nilee on 2011-02-09
You need a cd or a thumb drive for the install. trying to use the HD as the booting device and installing onto it isn't beginners work. 

Burn a live cd or thumbdrive and follow oldfred's post.

---

### Post by Acedrew89 on 2011-02-09
It's funny you should say that. I was just looking into burning the .iso onto a cd. It looks like I just need the live CD to not be on the drive and then I will be able to format it and install on that drive (theoretically).

So, I'm going to go try and burn the .iso to a CD and try that. I'll get back to you with what happens. 

Thanks for everyone's help, this has been a great start to joining the community so far. Seriously, I don't mind I'm having hiccups, and I'm really impressed with how quickly everyone seems to be willing to help out. So, thanks.

---

### Post by Acedrew89 on 2011-02-09
Okay, new hiccup. I'm stuck at "Determing File Systems". I've checked off everything, I've filled all of the fields out and they all have green checks beside them but I can't click the Forward button.

---

### Post by wilee-nilee on 2011-02-09
> **Acedrew89 said:**
> Okay, new hiccup. I'm stuck at "Determing File Systems". I've checked off everything, I've filled all of the fields out and they all have green checks beside them but I can't click the Forward button.

Sounds like you built partitions one needs to be root if you have made a separate home. You do this in the popup to enable them in the dropdown below the partition choice, click on it and choose /

---

### Post by Acedrew89 on 2011-02-10
I did indeed make partitions. I partitioned my 300gig hard drive into;

20gigs - / (root)
6gigs - swap
274gigs - /home

Also, I was using a live CD in my CD drive and after I got past the screen where I was applying the manual partitioning a warning popped up notifying me that the program needed to format my cd-rom but that it was in use (by the Live CD I presume). I clicked try again and it seemed to continue as usual.

I think my next step to this is going to be using a 2gig thumb drive along side the 300gig external hdd.

Thanks,
Andrew

---

### Post by Acedrew89 on 2011-02-10
The thumb drive did it. I've installed and am playing around with it now. The only issue now is that I still can't see my external drive under Computer, but could that be due to the fact that the drive is allocated as I stated above so I'm seeing it as the Home folder?

---

### Post by oldfred on 2011-02-10
If it is the external that you formated then you will not see it separately as it is already mounting / & /home (swap is hidden).

to see drives
sudo fdisk -lu 

To see use of mounted partitions:

sudo df -H

---

### Post by Acedrew89 on 2011-02-10
Perfect. That's what I thought was happening. One very last thing. I partitioned the entire drive for Ubuntu, but can I still put things on there when I'm in Windows? I'd like to put some important items on the hard drive and then reformat Windows, and still be able to have sort of a no-man's-land section to the external hard drive.

(I'm assuming I'll need to repartition a section of the drive for that?)

---

### Post by oldfred on 2011-02-10
Windows will not see Linux partitions, and even though Ubuntu will write into your windows partition, I do not recommend that. Reading is ok from windows system partition.

It is best to have a shared NTFS partition where either system can write into it. When first starting with Ubuntu I put pictures, Firefox & Thunderbird profiles in the shared partition so I had all the same info in both. Since I have not reorganized, I still have my profiles in the NTFS partition even though I rarely boot XP.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by Acedrew89 on 2011-02-10
Thank you very much OldFred. You've completed my setup journey. I appreciate everything you and the rest of the community members have done. This has been a great experience, and I have learned a lot.

Thanks,
Andrew

---

### Post by oldfred on 2011-02-11
You are welcome. Happy Ubuntu-ing.:)

---

