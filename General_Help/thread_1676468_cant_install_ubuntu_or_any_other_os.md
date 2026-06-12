---
title: "cant install ubuntu or any other os"
date: 2011-01-27
forum: General Help
---

### Post by emerald876 on 2011-01-27
Hey, sorry if this is in the wrong section, it's my first post here and I don't know my way around here just yet. But anyways:

          I tried to install ubuntu 10.10 alongside an existing xp install. That didn't work, and it corrupted my windows install. I booted to an ubuntu live demo, and then just got the files off of the windows hard drive. Now, since I wanted to install a new OS when I accidentally corrupted my windows, I boot up with the cd in the drive, and I go through the whole installation, it seems to go through just fine, but when it asks me to restart the computer, when I reboot it, there seems to be no ubuntu partition or anything that I can boot to. This happens also when I try to do a live demo installation, also.

Any help, anyone? I also tried this with an XP cd and the cd just wouldn't boot.

---

### Post by Mark Phelps on 2011-01-27
Not clear what you want as your end result:
1) Windows XP and Ubuntu
2) Ubuntu only

The phrase "live demo installation" is a contradiction of terms.  Either you use the LiveCD mode (demo), or you do an installation.

Which is it you are trying to do?

If you can't read any CDs, that implies a hardware problem with your optical drive.

If you can read the CDs but your PC isn't booting from them, that imples that your hard drive is set first in your boot sequence in the BIOS.  You would have to go into your BIOS settings and change that to boot from the CD drive first.

---

### Post by emerald876 on 2011-01-27
I guess I didn't explain my situation clear enough. I tried to install ubuntu, and I didn't know if you didn't press a button when the purple screen shows up, it automatically overwrites all info on the hard drives. I tried to dual boot but I didn't know you had to press a button to initiate a choice. 

I stopped it because it took a while, and I thought it got hung up on the loading, but it was installing. It started to overwrite windows system files, and I was screwed. I couldn't boot into windows, so I tried an ubuntu demo from the disk, and got the necessary files that I needed, and tried to install ubuntu. It seemed to install fine, and when it asked me to reboot to complete the installation, it doesn't show up in the boot menu. GRUB isn't even installed. 

I tried to install TinyXP as well, but it wouldn't even boot from that disc, and I just tried to install ubuntu again from the demo, where it has an option to install ubuntu, I did that, but again, GRUB wasn't installed and I couldn't boot into ubuntu.

I need to format my hard drive too, so how would I also go about that without an OS?

---

### Post by oldfred on 2011-01-27
Are you sure it did not install grub? If you are having a boot issue and only have one system installed you do not see a grub menu, it just starts booting the default install.

If you  hold down the shift key from BIOS boot until a menu appears, can you then boot the recovery mode?

If you want to totally reparition use gparted from the liveCD.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by emerald876 on 2011-01-27
When I don't have a CD in the drive, and I go boot, it always seems to give me "Bootmgr not installed" or something to that extent. I just used GParted to format all my hard drives, and now I am going to try the installation again.

---

### Post by TBABill on 2011-01-27
> **emerald876 said:**
> I guess I didn't explain my situation clear enough. I tried to install ubuntu, and I didn't know if you didn't press a button when the purple screen shows up, it automatically overwrites all info on the hard drives. I tried to dual boot but I didn't know you had to press a button to initiate a choice. 
 
I stopped it because it took a while, and I thought it got hung up on the loading, but it was installing. It started to overwrite windows system files, and I was screwed. I couldn't boot into windows, so I tried an ubuntu demo from the disk, and got the necessary files that I needed, and tried to install ubuntu. It seemed to install fine, and when it asked me to reboot to complete the installation, it doesn't show up in the boot menu. GRUB isn't even installed. 
 
I tried to install TinyXP as well, but it wouldn't even boot from that disc, and I just tried to install ubuntu again from the demo, where it has an option to install ubuntu, I did that, but again, GRUB wasn't installed and I couldn't boot into ubuntu.
 
I need to format my hard drive too, so how would I also go about that without an OS?This is a bit odd for a LiveCD. How it "should" work is you insert it into the drive after changing your BIOS to allow the system to boot first from CD or DVD, then look at the hard drive for an OS. So if it detects an OS on the disk it just boots from it. Nothing installed at all. Plus, you said when the purple screen shows up you have to press a button to prevent it from overwriting all of your info. That's not how it works.
 
When you boot a liveCD you should come to a screen that offers you two choices - install Ubuntu or try the liveCD. If you choose the live mode, all you do is sit and wait (5 min or so I believe) for the OS to load from the CD or DVD. 
 
This info doesn't assist with your current scenario, but it sounds like you chose to install without making sure you verified what partition the OS was going to install to, such as choosing for it to use the entire drive or to overwrite the partition with Windows on it. With Windows only on a machine you have to be very precise in what you tell the installer to do because just clicking through without doing so will result in a single partition with the OS on it and another swap partition. 
 
If you stopped the process part-way through then you'll likely have to reinstall Windows from your recovery disk. And if you want Ubuntu on the system with Windows, then install AFTER you reinstall Windows, carefully choosing to have it install it side by side with Windows and possibly resize the partition to whatever size you want. That's a critical step and one you may want to read up on from [https://help.ubuntu.com](https://help.ubuntu.com) and look for installation information.
 
If you get stuck along the way to recovery, post back with what you have done and what you need...lots of great folks to help along the way.

---

### Post by oldfred on 2011-01-27
bootmgr missing is a windows error.

When you said all your drives, do you have more than one hard drive or just partitions. Windows incorrectly refers to both partitions and hard drives as drives.

---

