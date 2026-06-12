---
title: "Installed windows 7 now grub can't see ubuntu"
date: 2011-10-13
forum: General Help
---

### Post by porchrat on 2011-10-13
My apologies if this sounds a little weird and doesn't make sense but I'm taking some allergy pills that have made me so sleepy that I'm not sure my brain is working correctly.

I've recently installed windows 7 on a machine that has been running 10.04. Obviously from that moment on grub was gone and the machine only booted windows.

I run 2 HDDs (windows7 is on sda1 with only one partition and ubuntu is on sdb with many partitions one of which (sdb1) was a 1GB partition that used to house grub)

So I tried using boot-repair-disk to reinstall grub. Once it was done running I restarted and grub was back. Now however grub only recognises windows7 and won't see the ubuntu install.

At the same time when I go look at my sdb drive the sdb1 partition is still a partition with an NTFS filesystem which leads me to believe that the windows7 boot stuff sits on that drive.

Anyone have any ideas on how I can get ubuntu recognised by grub again?

---

### Post by elliotn on 2011-10-13
u need to update grub or reinstall grub from liveCD

---

### Post by linux2001 on 2011-10-13
Boot with live CD or in single mode and do
```
#grub-install /dev/sda
```

---

### Post by elliotn on 2011-10-13
If you have the ubuntu altenate cd its easy, u just go to rescue broken system

---

### Post by porchrat on 2011-10-13
> **elliotn said:**
> u need to update grub or reinstall grub from liveCD

Meh looks like I've screwed it all up now anyway. I tried deleting that NTFS partition on sdb1 (I don't want anything Windows related on sdb) and now Windows7 won't boot off of grub (which makes sense considering I've basically just deleted the very bootable stuff it is supposed to be pointing to).

I think I'm going to unplug the SATA connector to sdb then reinstall Windows7. Then I'm going to plug sdb back in again and try to get grub back on using the liveCD. It shouldn't be too difficult to find a guide and at least that way I can make sure Windows doesn't put any of it's rubbish on sdb1.

Wow I hate Windows :mad:

---

### Post by porchrat on 2011-10-13
OK I figured out the problem. It looks as though when I installed Windows7 (despite me telling it to install to sda only) it realised that I was booting the system off of sdb. So it installed a small bootable partition in sdb1. sdb1 also happened to be where I have put /boot.

So the reason grub can't find ubuntu is because sdb1 (it's /boot directory) was formatted and written to by Windows7.

Is there a way to add that /boot information back to sdb1 or am I just better off reinstalling ubuntu itself?

---

### Post by comradeluigi on 2011-10-13
> **porchrat said:**
> OK I figured out the problem. It looks as though when I installed Windows7 (despite me telling it to install to sda only) it realised that I was booting the system off of sdb. So it installed a small bootable partition in sdb1. sdb1 also happened to be where I have put /boot.
 
So the reason grub can't find ubuntu is because sdb1 (it's /boot directory) was formatted and written to by Windows7.
 
Is there a way to add that /boot information back to sdb1 or am I just better off reinstalling ubuntu itself?
 your better off reinstalling ubuntu

---

### Post by digitaljeannie on 2011-10-13
From everything I understand about the process of dual-boot, If you install Windows after installing Ubuntu, you've lost Ubuntu and need to do a fresh install after you've installed Windows.

---

### Post by wackawacka on 2011-10-13
perhaps consider having one hard drive be the OS hard drive (partitioned for both systems) and the other drive be the "files" hard drive (partitioned with ntfs and ext4) instead of segregating.  

keep your friends close (files) and keep your enemies closer (windows)... haha

all kidding aside, over time, you save yourself a lot of grief by having a structure like this.

i know it's unorthodox and i'm sure i'll hear some opinions about it, but it's just a suggestion, i'm not forcing you to do anything.  haha

---

### Post by oldfred on 2011-10-13
I prefer to have an operating system on every drive, but make sure to install its boot loader to that same drive, so when one drive fails I can still boot the other drive.

With multiple installs and multiple drives you do need to keep track of where things get installed. As you found out it is not always where you think.:)

I use boot script as it shows MBR, PBR boot files & partition tables so I can document system. I always run it before & after any install, so I know what went where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

You can repair Ubuntu, but will have to chroot into it and reinstall grub & the kernels if sdb1 was /boot. If just a grub2 partition then you can reinstall grub2 to that partition.

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

#reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

If you still have kernels in your install this may repair it.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Or this may boot you into install and let you repair it from there.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

### Post by porchrat on 2011-10-16
Thanks oldfred I'm going to keep that in mind for this sort of thing in the future. I share your view on where my bootloaders go. I want each OS on a separate drive with all of it's components on that drive. Each drive should be bootable in isolation.

As a final update this is what I did:

I decided to physically unplug the second drive and reinstall Windows7. This ensured that there was no way that Windows could place anything on the ubuntu drive.

I then plugged that second drive back in and reinstalled Ubuntu on it. Everything is working fine again.

In the future when I reinstall Windows I'm going to unplug that second drive to prevent this mess ever happening again. That is what I have done in the past and I don't know why I didn't do it this time around. Oh well. Once bitten, twice shy.

Thank you all for your contributions it is much appreciated. I continue to learn so much from this forum. Keep up the good work. :D

---

### Post by oldfred on 2011-10-16
Glad you got it working.

Unplugging drives works.

Sometimes it makes a difference which drive you are booting with in BIOS. Windows 7 will install its (hidden) boot partition and MBR to that drive.

And Installing Ubuntu grub2 defaults to sda as that is usually the boot drive. So if you do not unplug drives, you have to have BIOS set to boot correct drive and in Ubuntu use manual mode so you get the choice where to install grub2's boot loader.

---

