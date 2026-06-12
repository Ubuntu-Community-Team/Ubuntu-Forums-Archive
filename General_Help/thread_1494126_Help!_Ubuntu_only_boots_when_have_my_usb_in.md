---
title: "Help! Ubuntu only boots when have my usb in"
date: 2010-05-26
forum: General Help
---

### Post by phr33k-dc on 2010-05-26
Hi,

Just done a install of ubuntu 10.04 via usb method. Started off by going into the live session and messing around for a while then proceeded to do an install. All went fine (i think) so i restarted my machine so i could go into the real thing (removed usb at this point). Got past the manufacturer logo then just got a blank screen with that flashing underscore in the top left. changed the BIOS back to boot from harddisk as 1st priority but still nothing. Plugged in my usb and i can boot into my real account not the live account, so its like its using the booting ability of the usb to boot up.
Im unable to do a fresh install because whenever i boot up, it boots into my real account not the live one.
Really stuck here any help would be really appreciated.
Thanks

---

### Post by phr33k-dc on 2010-05-26
bump

---

### Post by phr33k-dc on 2010-05-26
Hi,

Just done a install of ubuntu 10.04 via usb method. Started off by going into the live session and messing around for a while then proceeded to do an install. All went fine (i think) so i restarted my machine so i could go into the real thing (removed usb at this point). Got past the manufacturer logo then just got a blank screen with that flashing underscore in the top left. changed the BIOS back to boot from harddisk as 1st priority but still nothing. Plugged in my usb and i can boot into my real account not the live account, so its like its using the booting ability of the usb to boot up.
Im unable to do a fresh install because whenever i boot up, it boots into my real account not the live one.

Really stuck here any help would be really appreciated.

---

### Post by phr33k-dc on 2010-05-26
tried going into 'disk editor' and clicking 'make bootable' but got the following error:

---

### Post by -Jeremy- on 2010-05-26
My guess would be that you installed the boot loader on the usb stick, if that's the case you can load Ubuntu with the usb stick in you pc and then install grub on your hard disk. After that you should no longer need your usb stick.

---

### Post by phr33k-dc on 2010-05-26
Thanks a million for your reply Jeremy. 

Could you tell me how to do that?

really mean it thanks

---

### Post by WinRiddance on 2010-05-26
> **phr33k-dc said:**
> bump

I don't think that you actually installed Ubuntu yet because it sounds like the computer is looking for an Operating System to boot into once you start up the machine. If there's no OS installed but the computer is able to recognize the boot options of the LiveCD, it'll prompt for that or just stop.

If Ubuntu was actually installed on the hard disk, there should be no problem.

During the installation ... did you actually have to go through the steps of selecting a partition for Ubuntu, getting a partition formatted, was there a swap partition assigned for Ubuntu ??? Did you have to assign a user name and a password for yourself ??? If none of that rings a bell then the system was never installed since Ubuntu needs to know where to install itself ... which of course requires designated hard disk space, an empty partition, whatever.
.

---

### Post by bcbc on 2010-05-26
go to terminal prompt:
```
sudo fdisk -l
# identify your hard drive e.g. /dev/sda 
sudo grub-install /dev/sda

```
This works because you are booting your actual install on the hard drive. If you were on the live cd, you'd have to mount your hard drive partition and supply the --root-directory parameter as well.

---

### Post by phr33k-dc on 2010-05-26
> My guess would be that you installed the boot loader on the usb stick, if that's the case you can load Ubuntu with the usb stick in you pc and then install grub on your hard disk. After that you should no longer need your usb stick. 

Anyone else know how to do this? Thanks

---

### Post by phr33k-dc on 2010-05-26
Thanks for the reply.

I went through the whole installation process. im nearly 100% sure i did the proper installation, for example if i was still in the live usb, how come the install ubuntu option is gone? 

Does this pic mean anything? I went into 'disk utility' and checked the bootable option for got an error message

---

### Post by darkod on 2010-05-26
Sounds like grub2 is not correctly installed. Can you run the script as explained here and post the content of the results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by phr33k-dc on 2010-05-26
Thanks darkod,

eh i ran the script and i got 'no such file or directory'

that sounds bad

---

### Post by phr33k-dc on 2010-05-26
sorry missed out a bit, where do i douwnload the script from?

---

### Post by phr33k-dc on 2010-05-26
its ok here it is!

---

### Post by WinRiddance on 2010-05-26
Well, when I compare your pic to what I have, on mine it shows a bootable file system under the flag on the left. On yours it shows nothing at all, just a blank, which still leads me to think that perhaps there's nothing installed to boot into? On mine the partition is labeled as Lucid-Lynx but on yours there's nothing there either. So you either didn't label that partition or there's nothing installed there? The only thing that I can tell for sure, based on your picture, is that the partition has been formatted as an ext4 partition. Although, if the LiveDisk no longer shows the option to install then I guess it could indeed be a Grub issue instead. Fixing Grub is a bit above my experience though. Sorry, and good luck to you!

---

### Post by phr33k-dc on 2010-05-26
ok thanks anyway. im really stuck here

---

### Post by darkod on 2010-05-26
It's better if you posted the content of the results inside CODE tags, not as attachment. Anyway...

=> No boot loader is installed in the MBR of /dev/sdb
=> No boot loader is installed in the MBR of /dev/sdc

You have no bootloader installed at all.

Also, it seems there was /dev/sda device and now it's not there. Maybe this was your usb stick?

Can you boot into live mode, and post the result of:

sudo fdisk -l (small L)

stay booted into live mode, I'll give you few commands to run. I just have to see the output of fdisk first.

---

### Post by rob45 on 2010-05-26
did you use install ubuntu from within your live session?

---

### Post by phr33k-dc on 2010-05-27
Thanks, eh no i think the /dev.sda is 1 of my main harddrives.
Eh i cant boot into live mode because whenever i plug in my usb as far as i know it boots into my real thing, or maby not, maby im in the live session but i dnt think so,

Re rob45:ye i used ubuntu install from my live session

---

### Post by phr33k-dc on 2010-05-27
bump

---

### Post by phr33k-dc on 2010-05-27
bump

---

### Post by lisati on 2010-05-27
Threads merged. Please do not start multiple threads on the same question.

It's also considered to be good form here if you wait 24 hours (that's one day) before bumping a thread.

---

### Post by phr33k-dc on 2010-05-27
Sorry, just in a real pickle. up all night trying to fix it

---

### Post by lisati on 2010-05-27
> **phr33k-dc said:**
> Sorry, just in a real pickle. up all night trying to fix it

That's ok. 

We're all volunteers here, and sometimes the people who might be able to help you are either not online or they're looking at something else.

All the best.

---

### Post by phr33k-dc on 2010-05-27
Thanks lisati, i understand completely.

Is it possible to reinstall ubuntu without using usb or cd? because i cant boot into my live usb

---

### Post by lisati on 2010-05-27
> **phr33k-dc said:**
> Thanks lisati, i understand completely.

Is it possible to reinstall ubuntu without using usb or cd? because i cant boot into my live usb

If using a CD or a USB stick aren't options, you might want to check out "[wubi]("https://help.ubuntu.com/community/Wubi")"

---

### Post by phr33k-dc on 2010-05-27
im on ubuntu, but i cant boot in unless i have my usb inserted,
and cant boot into live session either. 

its ok lisati, il try again tomorrow....

thanks for your help

---

### Post by phr33k-dc on 2010-05-27
Solved it.

did a fresh install

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

---

### Post by mistakos on 2011-01-23
hi.. i have the same problem with you, but no windows computer to make the network install you have done. 

As far as I understood from this thread, the problem is that the /dev/sda1 is not bootable. I have a laptop so there is no other HDD. How is it possible to make it bootable? 

I also cannot boot without the USB stick and i also cannot do a fresh install, as when i put the USB and it boots from the usb, i enter to ubuntu without any problem. 

When i restart and plug the usb out, no booting. just the cursor blinking.. 

Please help!!!

---

### Post by oldfred on 2011-01-23
mistakos, Welcome to the forums.

It would have been better just to have started your own thread. Without all the details it sounds like you need to install grub to the USB flash drive's MBR. That assumes you can directly boot from USB. Then you install windows or whatever boot loader you have for the hard drive to the hard drive's MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From Ubuntu you can install lilo to the sda MBR and install grub to sdb (if the flash drive is sdb).

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

First install grub to sdb and make sure it boots:

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by mistakos on 2011-01-23
sudo grub-install --recheck /dev/sdb
sudo update-grub


this did the trick!! thank u oldfred!!!

---

