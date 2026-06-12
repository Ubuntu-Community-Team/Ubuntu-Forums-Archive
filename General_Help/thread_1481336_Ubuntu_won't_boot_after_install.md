---
title: "Ubuntu won't boot after install"
date: 2010-05-12
forum: General Help
---

### Post by BobbyDing on 2010-05-12
Hi folks.
Linux newbie here. Very green.

I have been having issues installing ubuntu. The machine has an Asus MB A7V8X-X with 1gb ram, Geforce 400 MMX video card, Standard EIDE and PCI busses, 20gb HD. The machine runs XP just fine. I actually have two of these machines that are identical with the exception of the drive brands. I have tried both drives.

When I boot from an ubuntu install CD (9.10 or 10.04) and ask it to install it tells me after a bit that there were install issues and that it is booting directly to a live desktop. The issues don't stay on the screen long enough for me to write down. If then I install from that desktop to the HD, all goes fine. I tell it to use the entire drive. Warm reboots work fine with ubuntu coming up happy. But after a power down and restart, the machine sits for a while and finally comes back with the following:

udevadm settle - timeout of 180 seconds reached, the event cue contains:
	/sys/devices/pci0000:00/0000:0011.1/host/target0:0:0/0:0:0:0/block/sda (755)
	/sys/devices/pci0000:00/0000:0011.1/host/target0:0:0/0:0:0:0/block/sda/sda1 (756)
	/sys/devices/pci0000:00/0000:0011.1/host/target0:0:0/0:0:0:0/block/sda/sda2 (757)
	/sys/devices/pci0000:00/0000:0011.1/host/target0:0:0/0:0:0:0/block/sda/sda5 (758)

Gave up waiting for root device. Common problems:
	- boot args (cat /proc/cmdline)
	- Check rootdelay= (did the system wait long enough?)
	- Check rootdelay= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/96b486e8-1df5-4e2b-bb21-5968015f6ad8 does not exist.
Dropping to shell!

Busybox V1.13.3 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for list of built in commands.

(initramfs)


It looks to my green eyes like it cannot find the boot files/dev. I have tried several attemps at installing... Always with the same results.  Any help would be appreciated.

Thanks!

Bob

---

### Post by notbitmonk on 2010-05-12
To me it looks like it can not find the disk.  I do no know if this will work but try using the LiveCD and open /proc/cmdline. Then edit the location of the disk.  I can only guess that you can change the UUID by LABEL and then enter the label of the disk.  The machine is not booting anyways, so I think that it is a reasonable chance (that you will take).

---

### Post by abtu on 2010-05-12
> 

Gave up waiting for root device. Common problems:
    - boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check rootdelay= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/96b486e8-1df5-4e2b-bb21-5968015f6ad8 does not exist.
Dropping to shell!

Busybox V1.13.3 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for list of built in commands.

(initramfs) I got the same issue. :mad:

I have searched hours for a simple answer to no avail. ](*,)I did find the the following [link]("http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html") which did explain the problem, but being a newbie, I do not know how to access the "initrd.img file" to fix it.

Hopefully, someone here can break it down further and give us step by step instructions. [-o<

Update: Just used keyword "BusyBox" in search box and got about 250 responses.

---

### Post by BobbyDing on 2010-05-13
> **notbitmonk said:**
> To me it looks like it can not find the disk. I do no know if this will work but try using the LiveCD and open /proc/cmdline. Then edit the location of the disk. I can only guess that you can change the UUID by LABEL and then enter the label of the disk. The machine is not booting anyways, so I think that it is a reasonable chance (that you will take).
 
 
I will give that a try soon. Question... What do you mean exactly by LABEL? Do you mean referencing the icons (for lack of a better word) in the other folders under /dev/disk? For instance it now points to an icon in the folder '/dev/disk/by-uuid/uuidname'. Do you mean try /dev/disk/by-path/pathname' instead? Sorry for the questions. Newbie.
 
I tried recovery mode. It seems to loose the hard drive just after the USB drivers load.
 
Thanks... Any other suggestions very welcome!

---

### Post by BobbyDing on 2010-05-15
The problem remains. In short...The machine will only boot into the installed ubuntu if I reboot it from a live CD session or wait 10 minutes after the error occurs, then type 'EXIT'.

I tried adding 'rootdelay=90' to the grub line, as well as reloading grub. No change.

Any thoughts?

Thanks!

---

### Post by BobbyDing on 2010-05-18
Well, I've been working with this the last three days. The best I can say is that I've made some 'discoveries'. I've included a list at the bottom of all the things I have tried already. Just to recap, Ubuntu won't boot without doing this:

[COLOR="DarkOrange"]Gave up waiting for root device. Common problems:
- boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check rootdelay= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/96b486e8-1df5-4e2b-bb21-5968015f6ad8 does not exist.
Dropping to shell!

Busybox V1.13.3 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for list of built in commands.

(initramfs)
[/COLOR]

(plus a bunch of errors streaming for about 5-8 minutes).

It happens with 9.04 though 10.04 (haven't tried earlier versions) so it's not a grub version issue. It happens with grub1 and grub2. With 9.04 if I wait 5 minutes and type 'exit' it will boot just fine. I found that if I added 'rootdelay=250' to 9.04 it will still stall during boot, but will eventually boot up after the rootdelay times out. If I 'Restart" from a running ubuntu session (livecd or HD, must be ubuntu) it will reboot just fine (and fast) from the HD. Up within 30 seconds. 

With 10.04 it's a bit different. It takes about 8 minutes for the system to finish it's string of errors, and typically it won't boot even after I type 'exit'. But I can 'cntl-alt-del' and it will shut down what it's booted so far, restart, and come rite up (less than 30 seconds).

Bear with me here, I am still pretty green to linux...In both cases, the USB is the last thing to load before the errors start popping up. Which means that grub has succeeded in passing along the first part of the boot process and is loading basic drivers. So it found the HD by UUID for that. But it seems to be one of those drivers that won't allow the kernel (or grub at that point) to see the HD again till it releases it (I'm guessing that the second part is the kernel load). 

[COLOR="Blue"]So....What would be holding up the IDE during a cold boot, that wouldn't be there (or would not be in the way) during a warm reboot of ubuntu?[/COLOR]

Gerneral info: 
Asus MB A7V8X-X with 1gb ram, Geforce 400 MMX video card, Standard EIDE and PCI busses, 20gb HD 

Boots up fine under XP. No issues.
Have identical PC to this here, and it has the same issues with ubuntu.

Happens with grub1 or grub2.

All these have been tried/added/removed so far.

01) tried disabling USB in bios.
02) ran spinrite on HD. No errors.
03) tried setting CS for HD & DVDROM instead of master/slave.
04) moved from primary to secondary IDE buss.
05) could not find bussmastering in bios to try disabling it.
06) disabled S.M.A.R.T.
07) chroot to update grub (full procedure in another thread)
08) added acpi=off nolapic pci=noacpi rootdelay=xxx  
09) also added pci=nomsi all_generic_ide floppy=off irqpoll
10) removed "splash" and "quiet"
11) checked  /boot/grub/device.map (only listed _hd(0) /dev/sda_ )
12) changed from using UUID to sda1 all through grub.
13) upgraded bios to most recent (2004).
14) tried booting with a USB drive connected.
15) loaded to another identical system (diff HD). Same issue.
16) Replaced old 80 conductor IDE cable with new.
17) wiped HD with wiping software and re-installed.


Any suggestions?

Bobby

---

### Post by BobbyDing on 2010-05-20
Anybody?

---

### Post by BobbyDing on 2010-05-26
A friend gave me an old Compaq 800mhz machine that I was about to toss out, when I decided to try one last time to install ubuntu using the 15gb drive from the old Compaq. It is a WD drive. I dropped it in and started the ubuntu 10-04 install disk. To my amazement it had no issues finding the drive (It always took forever to find my quantum and maxtor drives). Once the install was complete I powered off the system, waited 5 minutes and started it back up. This is where I would get the issues listed above. BUT, no issues. Ubuntu was up and running in less than 30 seconds!! I did a system update and again powered the pc off for several minutes. Again it came rite up.

So it seems that while XP had no issues with any of my other drives, the linux drivers liked the WD drive over the quantum and/or maxtor!!! Or maybe it is just my bios that has the issues?

In any case....Hooray for me!

Now I need to find a larger WD drive to install a dual boot ubuntu/xp system.

Thanks for all the help. I hope this thread helps others.

Bob

---

### Post by Martin Schniewind on 2010-06-24
Same here, (except nothing from 8.04 to 10.04 would start from Desktop CD neither).

Changing the harddrive had no effect.

For me the boot options "noapic nolapic" did it.

---

