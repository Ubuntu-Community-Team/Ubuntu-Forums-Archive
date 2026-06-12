---
title: "grub 2 - loading slow"
date: 2009-11-03
forum: General Help
---

### Post by h0ffmeister on 2009-11-03
Hi,

I've read elsewhere about slow grub 2 load times - I suffer from this with a Windows 7 / Ubuntu 9.10 dual boot setup. Windows installed first, then Ubuntu.

Drives are setup as follows:
hdd1 (sda) Windows OS
hdd2 (sdb) Ubuntu OS
hdd3 (sdc) Windows data
hdd4 (sdd) Ubuntu data

Bios boot priority:
hdd1

Presumably grub overwrote the MBR on hdd1 as if I change this the boot priority to hdd2, nothing happens, so no boot record on hdd2.

What I get is a delay of 15 seconds or so with "Grub loading" shown on screen. Eventually I get the choice of OSes to boot. Both boot without any problems.

I have a dual boot laptop (XP/Ubuntu 9.10) with both OSes on the same physical disk and there is almost no lag between BIOS to OS choice - I can't read the "Grub loading" screen it flashes so quickly.

Have I got something wrong in my config? Has the MBR been written to the correct hdd and is my hdd boot priority correct?

Any advice welcomed.

H0ff.

---

### Post by MarsEvader on 2009-11-04
grub2 is still more problematic than plain grub. Read here [http://aronzak.wordpress.com/2008/09/30/stay-away-from-grub2/](http://aronzak.wordpress.com/2008/09/30/stay-away-from-grub2/). Also read the comments section for help on this blog page. If you struggle too much getting grub2 to load faster you just may have to install plain vanilla grub again. I am not sure what script/application is responsible for creating the menu.lst grub configuration file in Ubuntu, but else just google for menu.lst examples.

---

### Post by HeinzVoerbakje on 2009-11-05
I have the same delay, it's annoying. 

I have Ubuntu installed on sdb2 now, and had the 9.10 beta on sda6, which did not give me that delay, so I reckon it is related to the fact that we have ubuntu on the second harddrive. 

I don't mind going back to the old grub, but how will I do this? Just go to synaptic and remove grub2, install grub? Will grub still be updated when I update my kernel? Won't other things break?

Thanks for the help, HeinzVoerbakje

---

### Post by sliketymo on 2009-11-05
Hre is some good info on Grub2: 

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

---

### Post by HeinzVoerbakje on 2009-11-05
> **sliketymo said:**
> Hre is some good info on Grub2: 

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

Thank you for your reply, but it doesn't help me, it doesn't say anything on removing grub2 in favour of grub legacy. Is it possible do do this?

---

### Post by nulldevice on 2009-11-06
I have the same grub2 problem: 15 sec Grub loading. I have Windows 7 on hda and Ubuntu 9.10 on hdb with an encrypted home partition on a Dell Precision M6400 laptop. I had to use the alternate installer and had to deactivate dmraid otherwise the installer would not show two separate drives but a RAID array, although disabled in BIOS.

I have the same setup on another Desktop PC working without problems though, also Windows on hda and Ubuntu 9.10 on hdb. Grub2 loads immediately here.

It looks like Grub2 is scanning all partitons, but why, and how can I stop it to do so?
I would also not mind to go back to grub but I would prefer to find the cause of this grub2 problem and solve it. Can anyone help?

---

### Post by nulldevice on 2009-11-06
OK, seems to be this problem:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

And as pointed out there the culprit is grub2 and the boot partition being on different drives. As a workaround you can do this:
sudo dkpg-reconfigure grub-pc

Select the disk that has your boot partition as the disk to boot from. Then change the boot order in your bios to boot from that drive. This solved the problem for me, grub2 now loads immediately!

---

### Post by h0ffmeister on 2009-11-06
> **nulldevice said:**
> OK, seems to be this problem:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

And as pointed out there the culprit is grub2 and the boot partition being on different drives. As a workaround you can do this:
sudo dkpg-reconfigure grub-pc

Select the disk that has your boot partition as the disk to boot from. Then change the boot order in your bios to boot from that drive. This solved the problem for me, grub2 now loads immediately!

Thanks, that has worked for me too (but you had a little typo) - should be:
sudo dpkg-reconfigure grub-pc

Followed the screens and then changed the hard disk priority in my bios and now it loads quick as.

---

### Post by HeinzVoerbakje on 2009-11-07
> **h0ffmeister said:**
> 
sudo dpkg-reconfigure grub-pc

Yes, also works for me, thanks for the help! Thread can be marked as solved as for as I am concerned:D.

---

### Post by Jordanwb on 2009-11-08
I ran "dpkg-reconfigure grub-pc" but grub2 is still slow to load.

---

### Post by AldenIsZen on 2009-11-10
> **Jordanwb said:**
> I ran "dpkg-reconfigure grub-pc" but grub2 is still slow to load.

Did you try changing your hard drive boot order in the Bios as mentioned?

---

### Post by Jordanwb on 2009-11-10
> **AldenIsZen said:**
> Did you try changing your hard drive boot order in the Bios as mentioned?

Got three hard drives, only one is in the BIOS hard drive boot order, and that is the one that has Grub2 written to the MBR.

---

### Post by catco_designs on 2009-11-10
I have had similar issues but I installed startup manager from software center and was able to reduce the time on grub timeout by adjusting settings with that program 
once installed it will be in System>Administration menu

---

### Post by AldenIsZen on 2009-11-17
> **Jordanwb said:**
> Got three hard drives, only one is in the BIOS hard drive boot order, and that is the one that has Grub2 written to the MBR.
I was asking as you didn't mention it before. I have since tried the fix, and I haven''t noticed a difference. It still takes 14-15 seconds for the loading grub2 message to go away, with it installed on either drive or only 1. I haven't tried installing to the partition as it said it might not be a good idea for the future, and I wasn't sure if there is a super grub disk for grub2 yet. I will check into that though. I haven't restarted much as of lately.

> **catco_designs said:**
> I have had similar issues but I installed startup manager from software center and was able to reduce the time on grub timeout by adjusting settings with that program 
once installed it will be in System>Administration menu

 just curious, do you recall what settings you adjusted?

---

### Post by Jordanwb on 2009-11-17
> **AldenIsZen said:**
> I was asking as you didn't mention it before. I have since tried the fix, and I haven''t noticed a difference. It still takes 14-15 seconds for the loading grub2 message to go away, with it installed on either drive or only 1. I haven't tried installing to the partition as it said it might not be a good idea for the future, and I wasn't sure if there is a super grub disk for grub2 yet. I will check into that though. I haven't restarted much as of lately.

I put my /boot partition on /dev/sda and it loads instantly. If possibly try that.

---

### Post by andrewabc on 2009-11-17
I ran
sudo dpkg-reconfigure grub-pc

I tried setting grub to SDB (solid state drive where ubuntu 9.10 installed) instead of SDA (hard drive where ubuntu 9.04 and winxp installed). I changed boot disk priority to my SSD and I end up with GRUB never loading. Don't even get the grub loading text, so it just sits there and does nothing. This happens when GRUB is set to SDA and SDB. Booting hard drive first is only way to make GRUB appear.

It takes GRUB 14 seconds to load, and same amount of time for ubuntu to fully load off SSD. It's doubling my boot time :(

---

### Post by AldenIsZen on 2009-11-17
> **Jordanwb said:**
> I put my /boot partition on /dev/sda and it loads instantly. If possibly try that.

 Sounds like an ugly word around, but I will try that. Could take a little work and some backing up, which I have yet to setup. If I had, this might throw a "small" kink in. 

But.. I reckon the best way would be to create a small partition somewhere on the first hard disk, and "DD" (I think it is called) the current /boot folder and remap it to the new partition on /dev/sda? Are there more steps or folders I may be missing anyone knows of, or an easier way? 

Oh, and I think that I need to be sure to copy the "contents" of /boot to the "root" level of the new partition, not just insert a /boot folder. Does that make sense?

edit/ Forgot to mention on the last post, my bios did not appear to allow me to decide which hard disk to boot, just "a" scsi compared to usb, ide, cd-rom, etc.

---

### Post by stempleton on 2009-11-18
Hi everyone,

I'm running dual boot windows 7 and ubuntu 9.10 (separate HDDs) and also had the same problems initially with grub2 - very long waiting time for "grub loading..." at startup. I tried the "dpkg-reconfigure grub-pc" and installed grub onto my second HDD (/dev/sdb) but it did not work when i changed my bios to boot from hd1. However, when reconfiguring grub, it told me to check the contents of "/boot/grub/device.map" and i found that it was loading hd0 as /dev/sda and hd1 as /dev/sdb. When my bios was reconfigured, hd0 becomes hd1 and vice versa. So I changed them in my device.map to suit and voila! it now works perfectly, almost no waiting time (faster than grub legacy) and it boots every time.

The contents of my new device.map are as follows:

(hd0)	/dev/sdb
(hd1)	/dev/sda

Hopefully if you try this solution it may be able to help those of you with similar problems to mine!

Good Luck!

---

### Post by AldenIsZen on 2009-11-18
That did not work for me, but I have a complicated setup with several partitions on 2 disks. It makes since though.

 On SDA I have a Dell utility partition (hidden), then a Windows XP, then in the extended partition three data partitions and finally Windows 7. On SDB I have my swap, then Ubuntu, then an alternate linux installation location, then an extended with several partitions in cluding the linux home ones.

 I realize now that this is more complicated than it needs to be. I plan on sorting it out in time. When I get a few moments (An event happened this morning...) I will try moving the boot to SDA. It would have to be in the extended partition though.

---

### Post by robrobinette on 2009-12-25
Didn't work for me either. I have a netbook with one hard drive and an SDHC card. WinXP is on the HD and Ubuntu 9.10 is on the SD card. The legacy grub used to boot very quickly but now I get "grub loading." for about 15 seconds. I have the HD as the only boot device and tried installing grub2 to sda and sdb with no change.

I might have to pull the HD out and see if it is set in the "Master" mode.

I did see on a forum thread that the grub2 developers have addressed this problem so it might be solved if we can load a newer version of grub2. I don't know if that can be done through the update manager.

---

### Post by m3n3chm0 on 2010-02-08
Hi all,

I've had this problem and tried all the solutions in this forum but without good result.

The solution for me was install 9.04 and then update to 9.10 ... after that the grub2, grub-pc works properly and fast. 

:P

---

### Post by AldenIsZen on 2010-02-08
If I am not mistaken,Grub2 isn't loaded when you upgrade? Or I think it wasn't when 9.10 came out.

---

### Post by Joe Munster on 2010-02-15
> **stempleton said:**
> Hi everyone,

I'm running dual boot windows 7 and ubuntu 9.10 (separate HDDs) and also had the same problems initially with grub2 - very long waiting time for "grub loading..." at startup. I tried the "dpkg-reconfigure grub-pc" and installed grub onto my second HDD (/dev/sdb) but it did not work when i changed my bios to boot from hd1. However, when reconfiguring grub, it told me to check the contents of "/boot/grub/device.map" and i found that it was loading hd0 as /dev/sda and hd1 as /dev/sdb. When my bios was reconfigured, hd0 becomes hd1 and vice versa. So I changed them in my device.map to suit and voila! it now works perfectly, almost no waiting time (faster than grub legacy) and it boots every time.

The contents of my new device.map are as follows:

(hd0)    /dev/sdb
(hd1)    /dev/sda

Hopefully if you try this solution it may be able to help those of you with similar problems to mine!

Good Luck!
+++++++++++++++++++++
THANK YOU. 
You are my hero. THANK YOU. THANK YOU. THANK YOU. 
I also have dual boot on seperate hdd. This fixed a ~5min grub lag.

---

### Post by Vik Vasilev on 2010-02-16
My grub was delaying for 1 to 2 minuites before showing the Os menu, the only thing that helped was downgrading to grub 0.97~

from [http://brettshaffer.com/blog/linux/downgrade-grub-2/](http://brettshaffer.com/blog/linux/downgrade-grub-2/)

[LIST=1]
[*]Make backup copies of the main GRUB 2 folders & files. (Optional)
[LIST]
[*]sudo cp /etc/default/grub /etc/default/grub.old
[*]sudo cp -R /etc/grub.d /etc/grub.d.old
[*]sudo cp -R /boot/grub /boot/grub.old
[/LIST]
 
[*]Remove GRUB 2
[LIST]
[*]sudo apt-get purge grub2 grub-pc
[*][IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=important.png[/IMG] The system will be unbootable until another bootloader is installed.
[*]Once the packages are removed, many files will still remain in ‘/boot/grub’
[/LIST]
 
[*]Install GRUB 0.97
[LIST]
[*]sudo apt-get install grub
[/LIST]
 
[*]With *grub* installed, the user must still create the *menu.lst* and *stage1/stage2* files by running the following two commands.
[LIST=1]
[*]sudo update-grub
[LIST]
[*]Generates *menu.lst*
[LIST]
[*]Tab to “Yes” when prompted.
[/LIST]
 
[/LIST]
 
[*]sudo grub-install /dev/sdX
[LIST]
[*]Choose the correct device (sda, sdb, etc), normally the one on which Ubuntu is installed.
[/LIST]
[/LIST]
[/LIST]

---

### Post by buholoco on 2010-02-26
> **nulldevice said:**
> OK, seems to be this problem:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

And as pointed out there the culprit is grub2 and the boot partition being on different drives. As a workaround you can do this:
sudo dkpg-reconfigure grub-pc

Select the disk that has your boot partition as the disk to boot from. Then change the boot order in your bios to boot from that drive. This solved the problem for me, grub2 now loads immediately!


worked for me too.. 

Thanks.

---

### Post by stuarttaylor on 2010-03-06
I have an option in my bios to change the priority of the hard drives. This option was under the option to select boot-device priority.

After reinstalling grub2 to /dev/sdc (hd2), then setting my drive priority in the bios to boot from the same drive, it worked fine.

In my instance, this had stemmed from when my Windows drive was the first device, and therefore always hosted the boot partition.

My only question now is why on earth I had never considered this earlier.

---

### Post by MetalMusicAddict on 2010-09-26
On a single-drive, clean CLI-only install, Grub2 takes 15 solid seconds to show up. (Lucid and Maverick installs)

_Very_ odd.

---

### Post by martijntje on 2010-09-29
I have that problem too. Not CLI, but it's only one drive. In fact, it's only one partition.

---

