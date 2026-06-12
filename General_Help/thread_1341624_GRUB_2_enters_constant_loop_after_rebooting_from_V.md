---
title: "GRUB 2 enters constant loop after rebooting from Vista"
date: 2009-11-29
forum: General Help
---

### Post by pepe_le_piu on 2009-11-29
Hi all!

I have a computer running Vista Home Premium and Karmic (9.10). I've had no problems when rebooting from Karmic, but sometimes, when I reboot from Vista, the MBR seems to get fried. 

The exact order of events is as follows:

1. Work from Karmic.
2. Reboot.
3. Log on to Vista and work for a while
4. Reboot.
5. Computer boots, shows "GRUB loading", reboots

I've followed the recovery procedure described at [https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD](https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD) and it works for fixing the problem. However, I'm getting tired of having to do this every day. 

Any ideas as to why this is happening? Has anyone else run into the same problem?

---

### Post by oldfred on 2009-11-29
I have seen several people with HPs. New grub2 is larger than grub legacy and the windows boot loader. Some software then assumed they had a little space to use to hide serial numbers.

HP ProtectTools and Dell angel write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

---

### Post by jward3010 on 2009-11-30
This is the EXACT same problem I'm having, I'm using a Dell Vostro 1520 and I'm dual booting with an OEM Windows 7. 

It's very occasional, it might happen every 3 or 4 weeks but is becoming seriously annoying as I don't always have a recovery disk with me to start repairing GRUB2. I'll just be out and about and I'll power up in a cafe, next thing I'm watching a constant rebooting sequence and I can't do anything until I get home.

Edit: I've just read that bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941) and it's possibly down to recovery software in Windows (like HP recovery, protecttools). They're constantly wiping out the part of the GRUB loader with there own. Possibly down to the fact that the "core.img" of GRUB2 is larger than the Stage1.5 of GRUB 1 which is why the problem never occured with earlier GRUB 1. Although this isn't the case with me as I have NO recovery software installed and no recovery partition, just OEM Windows 7.

Just like youself I too have to look at the "Recover GRUB2" tutorial each time and it's a major pain in the eyelids.

---

### Post by oldfred on 2009-11-30
Does the Dell recovery tool run updates every 2 weeks and that is when you have troubles? Supposedly that can be a problem also where is messes with the MBR.

---

### Post by pepe_le_piu on 2009-12-01
Ok... I've read the link to the launchpad bug report and, since I don't have time to check every service in msconfig to see what is causing the MBR to change, I took another approach.  

I was running Vista on a Dell Vostro 1320, and the error came up every day or two, tops. I usually use Vista during the day for work and then switch to Karmic in the evening, and I'm carrying around a USB stick with an Ubuntu LiveCD.  

Yesterday my Win7 Upgrade CD's arrived, so I decided to change the way the boot procedure is structured. I assumed (and I hope I'm write) that whatever is screwing up GRUB 2 will not do the same to Windows Boot Manager, so that's what went into the MBR. 

My fix required reformatting the Ubuntu partition to ext3 and installing EasyBCD. If you installed with Karmic's default settings, you're probably using ext4 and will have to do this. This is a limitation (as far as I can tell) of EasyBCD and NeoGrub, so if you figure out another way of making the Windows Boot Manager recognize the Ubuntu partition, you may be able to save yourself the hassle of having to reinstall.

The instructions are detailed at the link below, but I'll give you a general summary of what I had to do:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

1. Fix the GRUB 2 installation for what will hopefully be the last time
2. Back up your Ubuntu partition, if you want/need to. I didn't, but that's just me :).
3. Boot Vista 
4. Download EasyBCD from here: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1). Install it.
5. Run EasyBCD and click the "Manage Bootloader" button. Click on the "Reinstall Vista Bootloader" radio button and then on the "Write MBR" button. 
6. Boot from the liveCD (or USB, or whatever) and work your way to the Partition screen.  Choose the "configure partitions manually" radio button.
7. Format the Ubuntu Partition in ext3. 
8. Continue until the last screen (step 7 of 7) and STOP. In the lower right corner you will see a button labeled "Advanced...". Click it.
9. Change the bootloader location so that it gets installed into the Ubuntu partition. 
10. Reboot. You still won't be able to boot into Karmic, so go right ahead and load Vista. 
11. Open EasyBCD and click on the "Add/Remove Entries" button.
12. Click on the "Linux" tab, pick the partition, tell EasyBCD your dealing with GRUB and give it a name. Then click on "Add Entry"
13. Reboot and enjoy.

Afterwards you can tweak GRUB 2 so that it boots directly into Karmic instead of showing you a menu. 

The above works for Windows 7 as well.

I hope this helps everyone who's having this problem.


EDIT: I'm marking this as [SOLVED] although I still have to test the new configuration for extended periods of time. I'll post any new developments here.

---

### Post by grizzler on 2009-12-01
Looks like a good solution and certainly one I'll keep in mind when I help my neighbour install an Ubuntu dual boot on her new Windows 7 laptop.

I had a similar problem with a nasty reboot loop after I installed a multiple boot system on my own machine (an unnamed desktop box with ECS motherboard) in April 2008. The strange thing is, that was with legacy grub. I ended up using Grub4dos (on which EasyBCD's NeoGrub is based) with the bootloader on the XP partition and that has worked like a charm ever since.

---

### Post by mikitz on 2009-12-17
Oops... I followed the above instructions, but when I select Ubuntu from the boot loader menu I just get the grub command line... :(

Anyone know how to configure grub for lets say /dev/sda5 only instead of doing it for the MBR?

---

