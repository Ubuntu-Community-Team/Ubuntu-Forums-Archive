---
title: "Need help with dual-boot"
date: 2010-09-19
forum: General Help
---

### Post by d00derino on 2010-09-19
Guys, I'm having a huge problem. I need to dual-boot Ubuntu 10.04 with Fedora 13 for a class. For whatever reason, he wants us to use Fedora in his class and won't let us use any other distro. 

Anyway, I took 10 GB from my Ubuntu laptop for Fedora and installed it. Sadly, Grub didn't find Ubuntu! I found [this link](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub) but it doesn't work for me. 

For one, when I use the Live CD, it doesn't let me run this step:

```
sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda
```

Where I'd be replacing /dev/sda with /dev/sda1 (my Ubuntu partition). I don't get BIOS errors that I can fix with --recheck. I get something that tells me I need to --force it, and that installing Grub to a partition isn't good. Nevertheless, the instructions don't work. 

I'm unable to access my Ubuntu partition unless I do install Grub to a new partition (I messed up and used /dev/sda by accident once), but then it doesn't detect Fedora. 

So I'm confused. Either I add something into the configuration for Fedora or Ubuntu, and while I can find what to add for Ubuntu I can't find the file (I don't have a menu.lst). If I want to add it to Fedora, I can find the file (grub.conf) but can't figure out the code to make it work. 

Any ideas/suggestions? Right now I'm just gonna leave it on Fedora until I get some responses since we need it installed by tomorrow's class. Incase you are asking, I can mount the Ubuntu partition. But neither distro's GRUB will list both distros. 

HELP! I thought Linux(es) were supposed to love one another!

---

### Post by bashphoenux on 2010-09-19
see if this helps
[GRUB 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+guide")

---

### Post by garvinrick4 on 2010-09-19
Run the code: in ubuntu or live cd of ubuntu:
```
sudo fdisk -l
``` (small case L)

If as you say your Ubuntu install is sda1 then: If different use that sda #
```
sudo mkdir /media/root
``````
sudo mount /dev/sda1 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/root
```It will now look for boot in sda1 to put in mbr(your ubuntu install of grub2) always put is sda

If you install a Operating System like Fedora, OpenSuse that uses grub legacy instead of the new grub2 then just choose not to install any grub at all at install (it is there I have done it many times) Then boot into your grub2 install (your ubuntu) and then:
```
sudo update-grub
``````
sudo grub-mkconfig
```It will now be in your grub menu at boot and also made a now grub configuration file just for the hell of it.
This will have all Operating Systems in Grub2 now.
If grub gets screwed up anytime just use your live cd (install cd of Ubuntu using Try Ubuntu)
and reinstall.
1. Make a directory
2. Mount /dev/sda# in with that directory
3. install grub as shown from sda# to sda
4. unmount (umount is right)
You want to see your whole file on your desktop in text file use this. Takes 30 seconds.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by garvinrick4 on 2010-09-19
Here is good sight for post-installation for fedora and use of yum and rpm's instead of apt-get of Ubuntu. Has post Ubuntu also. Ace your class partner.
[my-guides.net]("http://www.my-guides.net/en/")

---

### Post by d00derino on 2010-09-20
> **garvinrick4 said:**
> Here is good sight for post-installation for fedora and use of yum and rpm's instead of apt-get of Ubuntu. Has post Ubuntu also. Ace your class partner.
[my-guides.net]("http://www.my-guides.net/en/")

Oh, I will. The final is recompiling Fedora to be at least 1KB smaller...the class is going to be a breeze. I just hate that this didn't work "out-of-box" and due to the nature of a rapid release cycle, a good majority of information for Linux online is outdated, and it's very hard for someone like me (even as a Computer Science major) to figure out what parts of Ubuntu (or Fedora, or OpenSUSE, etc) in x.yz won't work in x.ab because it is outdated (I don't think that I should have to do preceding research before I even look for my answers).

---

### Post by perspectoff on 2010-09-20
Well, if Fedora is still using Grub Legacy, maybe I'll check out Fedora. I hate Grub2.

I'm extremely surprised, though. Grub Legacy was able to find all operating systems on all partitions, too. 

Are you sure you still have an Ubuntu partition left?

You may want to have a peek at

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

if you intend to make a habit of having multiple OS on your computer.

To save yourself headache in the future, it is useful to have a small 100 Mb primary boot partition, in which a copy of Grub Legacy is stored. It is merely used to chainload other bootloaders, each stored in the partition of the OS that installed it.

Then you will never have to worry about one OS overwriting the bootloader for another OS.

If Fedora is like Ubuntu and you have done a normal installation, it probably changes the Master Boot Record to refer to its own (Fedora) partition as the location where the Grub bootloader is now located. That means you would only have to deal with that configuration file, completely within Fedora, and the Ubuntu configuration becomes irrelevant. 

You can then check the Grub Legacy boot configuration file (which is now stored, I assume, on your Fedora partition, since this was the most recent OS installed) to make sure it is reflecting the identifier for each partition's OS correctly.

That file was /boot/grub/menu.lst in older versions of Ubuntu that used Grub Legacy, and I am not sure where it is in Fedora, but probably somewhere similar.

When examining /boot/grub/menu.lst, you might notice that Grub Legacy does not use UUIDs at all. In that case, the partition for each OS is referred to by their position on the hard drive. The Windows partition is usually /dev/sda1, which in Grub Legacy is notated as (hd0,0). 

If your Ubuntu partition was on partition /dev/sda3, then it will be referred to as (hd0,2). Fedora, if on /dev/sda4, would be (hd0,3).

You can sometimes double check that all these settings are appropriate in the Fedora Grub Legacy menu.lst file.

If the Grub configuration file is indeed using UUID partition identifiers, you can also check that your UUIDs haven't changed:

 sudo blkid

(or whatever the command to use blkid as the root user is in Fedora).

Then you can check the Grub configuration file for UUID consistency.

Grub Legacy can have a quirk or two about chainloading Grub2, which is another possibility as to why your Ubuntu is no longer loading properly. This is especially true if the installation of Fedora has caused any changes to the UUIDs (or other settings) relevant to the Ubuntu Grub2 bootloader, preventing it from being chainloaded properly. (Another possibility is that you have followed a lot of wrong advice and screwed up Ubuntu's Grub2 configuration beyond recognition by now, lol).

Lastly, it is possible to reset the Master Boot Record to point back to Ubuntu's Grub2 bootloader from within Fedora.

Let's say you know that the Ubuntu partition is on /dev/sda3. Remember that this will be referred to by Grub Legacy as (hd0,2).

Start Grub Legacy in Fedora as root (whatever you have to do to run grub as root):

 sudo grub

 > root (hd0,2)
 > setup (hd0)
 > quit

This will reset the MBR to point to whichever bootloader is in partition at /dev/sda3, which I am guessing is your Grub2 in your Ubuntu partition. Then the next time you reboot you should again get the Ubuntu Grub2 bootloader menu.

---

### Post by d00derino on 2010-09-20
> **garvinrick4 said:**
> Run the code: in ubuntu or live cd of ubuntu:
```
sudo fdisk -l
``` (small case L)

If as you say your Ubuntu install is sda1 then: If different use that sda #
```
sudo mkdir /media/root
``````
sudo mount /dev/sda1 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/root
```It will now look for boot in sda1 to put in mbr(your ubuntu install of grub2) always put is sda

If you install a Operating System like Fedora, OpenSuse that uses grub legacy instead of the new grub2 then just choose not to install any grub at all at install (it is there I have done it many times) Then boot into your grub2 install (your ubuntu) and then:
```
sudo update-grub
``````
sudo grub-mkconfig
```It will now be in your grub menu at boot and also made a now grub configuration file just for the hell of it.
This will have all Operating Systems in Grub2 now.
If grub gets screwed up anytime just use your live cd (install cd of Ubuntu using Try Ubuntu)
and reinstall.
1. Make a directory
2. Mount /dev/sda# in with that directory
3. install grub as shown from sda# to sda
4. unmount (umount is right)
You want to see your whole file on your desktop in text file use this. Takes 30 seconds.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

Hmm, I tried this but didn't get Fedora added -- it just lists Ubuntu. However, I didn't re-install Fedora without installing GRUB. I installed from the Live CD and it didn't work in such a manner that I could toggle against installing GRUB. I'll try without the Live CD...I think that was the problem...

---

### Post by garvinrick4 on 2010-09-21
You did go into Ubuntu install after installing grub2 and:
```
sudo update-grub
```Or if you already started to install fedora fresh and then boot into
Ubuntu and 
```
sudo update-grub
```

---

### Post by garvinrick4 on 2010-09-21
Boot for me looked in  sda5 and installed is sda
Redhat label is actually fedora but have fedora on USB external and do not
want same label twice.
All boot in grub menu, when install anything I have found it easier not to install
any grub if it is not grub2.
Have a boot partition in sda1 as SYSTEM still grub installed in sda
Recovery partition in sda4 is Windows 7

---

### Post by d00derino on 2010-09-21
> **garvinrick4 said:**
> You did go into Ubuntu install after installing grub2 and:
```
sudo update-grub
```Or if you already started to install fedora fresh and then boot into
Ubuntu and 
```
sudo update-grub
```

Yes, I followed your directions to the T. My GParted showed a partition with a "!" triangle next to it and was labeled as a LVM (not Red-Hat nor Fedora or anything). 

I deleted the partition last night, or else I'd show a screenshot. After watching about 20 students install Fedora yesterday in class (I wanted to do it before hand so that I can virtual machine in from my good laptop that I bring to every other class) the options from a Live install and the DVD install are completely different. Maybe that's why it's been acting so funny. I'd also have the option to choose a boot device (which I didn't get in a Live install).

---

### Post by garvinrick4 on 2010-09-21
> **d00derino said:**
> Yes, I followed your directions to the T. My GParted showed a partition with a "!" triangle next to it and was labeled as a LVM (not Red-Hat nor Fedora or anything). 

I deleted the partition last night, or else I'd show a screenshot. After watching about 20 students install Fedora yesterday in class (I wanted to do it before hand so that I can virtual machine in from my good laptop that I bring to every other class) the options from a Live install and the DVD install are completely different. Maybe that's why it's been acting so funny. I'd also have the option to choose a boot device (which I didn't get in a Live install).  The LVM is a pain in the rear in fedora, it wants to install by default some how and it is not to be used, it goofs up everything. You can google LVM for info. Ok if I can answer anymore questions just ask and let me know how you did in class. Also grub legacy and grub2  to you can read about in here.

[GRUB 2 bootloader - Full tutorial]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459")

---

### Post by d00derino on 2010-09-21
> **garvinrick4 said:**
> The LVM is a pain in the rear in fedora, it wants to install by default some how and it is not to be used, it goofs up everything. You can google LVM for info. Ok if I can answer anymore questions just ask and let me know how you did in class. Also grub legacy and grub2  to you can read about in here.

[GRUB 2 bootloader - Full tutorial]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459")

That must be it then. I still haven't gotten off my butt to buy blank DVDs (I'm not installing from the Live USB again), but I'll bump this thread if it doesn't work. Thanks a million.

---

### Post by d00derino on 2010-09-22
It's working now. It must have been using that stupid LVM parition. I hated having to go through a DVD!

---

### Post by garvinrick4 on 2010-09-23
> **d00derino said:**
> It's working now. It must have been using that stupid LVM parition. I hated having to go through a DVD!
 I am glad to here you are up and running. CD or USB should have been the same but I have
only used Cd's with Fedora myself. I have lots of different Ubuntu live USB's same as CD's except I get 4 gig of persistence and that makes me like USB's a whole lot better. But first time I used Fedora LVM got me also, that is why I new. Trail and error. Good luck to you
in your class.

---

