---
title: "Before coming back to the fold"
date: 2011-07-20
forum: General Help
---

### Post by fidelandche on 2011-07-20
Hi all,

It has been a while since I last used only Ubuntu, I went back to Windo$e because of certain things that would not work on a Ubuntu box (My Garmin Sat Nav being one) So I am fed up with using a very closed and slow system, I have downloaded the latest version of Ubuntu and got it on disc, I have tried it via the live CD and it is Greeeeeeeat (as Tony the tiger says) So my question is this, can my sat nav now work with Ubuntu? (it is a Garmin Nuvi 205w) I just need to get the Garmin communicator plug in to work, also I have a electricity monitor that I use to monitor my use (it is called Onzo)would I be able to upload my usage, it works on a uploader programme?. And one final question..... Is there any way to save all the saved passwords on Chrome and pass this information on to the Linux version of chrome?

Cheers

Andy

---

### Post by seawolf167 on 2011-07-20
Take a look at these two links and see if they help you. I haven't done either myself so I can't say if/how well they work though.

[Garmin Communicator ]("http://www.andreas-diesner.de/garminplugin/doku.php/installation#installation_on_ubuntu")on Ubuntu

[Chrome Exporting ]("http://webtrickz.com/export-chrome-datasettings-from-windows-to-ubuntu/")to Ubuntu from Windows

---

### Post by Grenage on 2011-07-20
Failing that, is a Windows through virtualbox a viable option for infrequently used applications?

---

### Post by fidelandche on 2011-07-20
> **Grenage said:**
> Failing that, is a Windows through virtualbox a viable option for infrequently used applications?

I have tried using VB before, it did work OK but I had to do a lot of messing about just to get those annoying applications to work.

---

### Post by fidelandche on 2011-07-20
> **seawolf167 said:**
> Take a look at these two links and see if they help you. I haven't done either myself so I can't say if/how well they work though.

[Garmin Communicator ]("http://www.andreas-diesner.de/garminplugin/doku.php/installation#installation_on_ubuntu")on Ubuntu

[Chrome Exporting ]("http://webtrickz.com/export-chrome-datasettings-from-windows-to-ubuntu/")to Ubuntu from Windows

The only problem with the Garmin link,is that it only works with sat nav's for running, cycling etc.

---

### Post by Grenage on 2011-07-20
I feel your pain; seawolf167's Garmin link looks rather hopeful, and the power monitor may well be simple enough to run (easily) with WINE.  I'm still using Windows for programming my Logitech Harmony remote.

---

### Post by seawolf167 on 2011-07-20
> **fidelandche said:**
> The only problem with the Garmin link,is that it only works with sat nav's for running, cycling etc.

I'm not sure how often you use the programs - but since you said the VM doesn't work so great, for the time being you could always dual boot, then if you find a way or get the programs working on the Ubuntu side of things you can remove Windows.

---

### Post by fidelandche on 2011-07-20
> **seawolf167 said:**
> I'm not sure how often you use the programs - but since you said the VM doesn't work so great, for the time being you could always dual boot, then if you find a way or get the programs working on the Ubuntu side of things you can remove Windows.

I did consider dual booting, but not sure of how much of the HD to give over to windo$es. Any one with any ideas?

---

### Post by seawolf167 on 2011-07-20
Windows programs eat disk space like nobody's business, so it greatly depends what you are going to install on Windows (especially modern games). You can always set a partition size based on your best guess, then resize later (maybe by reducing your /home partition) if you need more space.

---

### Post by fidelandche on 2011-07-20
> **seawolf167 said:**
> Windows programs eat disk space like nobody's business, so it greatly depends what you are going to install on Windows (especially modern games). You can always set a partition size based on your best guess, then resize later (maybe by reducing your /home partition) if you need more space.

I guess what I am looking for is the minimal amount of disk space for windo$s, just so I can connect my sat nav and other bits that need windo$s and that's about it. I would use Ubuntu for everything else. I am just unsure of how to partition during the install process.

---

### Post by seawolf167 on 2011-07-20
Resize your current Windows partition by right clicking "My Computer", select "Manage" then "Disk Management" and use the built-in Windows partition editor to resize Windows. Then after that is finished, boot off your Ubuntu cd and select to manually partition, and in the newly create unallocated space, create at least (IMO) three partitions. One for / (root), one for /home and another for swap.

As for sizes, how large is your hard drive?

---

### Post by fidelandche on 2011-07-21
Hi,

My HD is 160GB. How much do I allocate to each partition?

---

### Post by fidelandche on 2011-07-21
I have had a look and it will only let me shrink the HD by 110MB, so how do I shrink it to make it smaller? I have about 62% free of disk space.

---

### Post by HermanAB on 2011-07-21
Regarding the Garmin:
[http://www.aeronetworks.ca/howtos/garmin-howto.pdf](http://www.aeronetworks.ca/howtos/garmin-howto.pdf)

---

### Post by seawolf167 on 2011-07-21
> **fidelandche said:**
> Hi,

My HD is 160GB. How much do I allocate to each partition?

You'll want to adjust this for any other programs/games you have on your Windows installation that may take up space, but this could work

15 GB - / (root)
2 GB - swap
53 GB - /home
90 GB - NTFS (Windows, since you mentioned that you have 62% free)

As for setting up the partitions, select to manually edit the partition table during the installation process, then set up your Ubuntu partitions, types and sizes in there. Remember to shrink the Windows partition using the Windows partition editor - there are tons of how-tos online for this, a google search for "how to resize Windows partition" will probably give you a ton of results.

---

### Post by fidelandche on 2011-07-21
> **seawolf167 said:**
> You'll want to adjust this for any other programs/games you have on your Windows installation that may take up space, but this could work

15 GB - / (root)
2 GB - swap
53 GB - /home
90 GB - NTFS (Windows, since you mentioned that you have 62% free)

As for setting up the partitions, select to manually edit the partition table during the installation process, then set up your Ubuntu partitions, types and sizes in there. Remember to shrink the Windows partition using the Windows partition editor - there are tons of how-tos online for this, a google search for "how to resize Windows partition" will probably give you a ton of results.

This probably sounds like a real newbie question, but here goes...I am going to remove all the programs that I will not need from windows and try again too re-partition the HD, but what is the purpose of having the different partitions? I understand having the NTFS partition as I have to run Windo&s:( but when I last used Ubuntu I just had that as my only OS and did not make any other partitions, that's why I am a bit confused over partitions.

---

### Post by seawolf167 on 2011-07-21
Here is an example. Say you want to install a new version of Ubuntu in the future, with only a single partition (aside from swap), you will have to backup your /home folder, reinstall Ubuntu, then restore your /home folder contents. If you create a separate /home folder partition, now when you install, you don't have to touch your /home folder, only reinstall the Ubuntu OS and mount your existing partition. This means all your files, folders, settings, etc. stay there any you don't have to reconfigure or restore your /home folder items.

swap is for hard disk swapping when the physical RAM runs out, and this is created automatically anyways by the Ubuntu installer even in the "basic, easy" mode. The problem is that IMO the installer always creates wayyy too much swap space. My computer never accesses swap but I gave it 2GB just in case.

I hope that helps explain things a bit.

---

### Post by fidelandche on 2011-07-21
Ok, I think I understand. So when I install am I right in thinking that only swap and the home partition are created along side NTFS? So when I manually install the partitions and make another home folder, I back up everything to this folder instead of the home folder which is created by the install? Also you said 15GB for -/(root) what is this folder for? Is it not created during the "basic,easy" mode/install?

---

### Post by seawolf167 on 2011-07-21
/home is not a default created separate partition; you need to add the 3 non-NTFS partitions listed from my previous post, there will be a total of 4 partitions on your disk

/ (root - type ext4)
/home (type ext4)
swap (type swap)
windows (type NTFS)

/ (root) is your base system

---

### Post by fidelandche on 2011-07-21
Just like to say to Seawolf167, thanks for all your help.

Cheers

Andy

---

### Post by seawolf167 on 2011-07-21
Not a problem! If you have everything answered, please mark this thread as solved under "Thread Tools"

---

