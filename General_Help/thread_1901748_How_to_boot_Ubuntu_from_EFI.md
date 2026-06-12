---
title: "How to boot Ubuntu from EFI?"
date: 2011-12-29
forum: General Help
---

### Post by tdn on 2011-12-29
I have just tried installing Ubuntu 11.10 on a newly bought Lenovo ThinkCentre Edge with EFI boot enabled. The machine came preloaded with Windows 7. I first opted to install Ubuntu 11.10 side-by-side with Win 7. Installation of Ubuntu finished with success, however, when I rebooted, it kept booting Windows. I could not make it boot Ubuntu.

I then reinstalled Ubuntu 11.10. This time I opted for the Use Entire Disk option and thus wiped Windows 7 from the machine. Hoping this would work, I was surprised to see that it still did not work. Even though the installation process went without any problems/errors, when rebooting it now just gives me "No bootable operating system. Insert bootable disk and press any key..."

I figure this is because of EFI. I have checked the System Setup (F1 during POST) to find a BIOS option to disable EFI/UEFI boot, however, there is no such option for this machine.

So my question is, how do I install Ubuntu on a machine with EFI? 
 - Or, since Ubuntu is probably already installed: how do I make it boot Ubuntu?


*EDIT 2012-01-02*:
I went and bought a CDROM and installed Ubuntu from it. That made it work. Appearently, the Ubuntu ISO is broken in such a way that installation from USB does not work on (at least some) EFI systems.

---

### Post by wyliecoyoteuk on 2011-12-29
You need to disable secure boot in the BIOS, if that is possible.
You may need to enter a special BIOS code to get to it.
If you cannot disable it, then you can't install anything but Win7.
This might help.
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by tdn on 2011-12-29
> **wyliecoyoteuk said:**
> You need to disable secure boot in the BIOS, if that is possible.
You may need to enter a special BIOS code to get to it.
If you cannot disable it, then you can't install anything but Win7.
This might help.
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)


WTF? Are you serious? I cannot use this computer with anything but Win 7? I find it hard to believe this that this practice is legal.

I just checked the BIOS settings. There is nothing about Secure Boot. Where can I find out about "a special BIOS code" disable this setting?

---

### Post by tdn on 2011-12-30
Update:
So I called the hardware vendor to ask for help on this issue. They do not know of any such "secure boot" setting in the BIOS that would prevent Linux from booting.
They suggested that I called Lenovo support, and I did. At Lenovo support they did not know anything about a BIOS setting called secure boot. The also did not know of any limitations that would prevent Linux from booting.

I asked for the BIOS manual, and the provided this:
[http://download.lenovo.com/lenovo/content/vru/websupport.html](http://download.lenovo.com/lenovo/content/vru/websupport.html)

Steps to get to BIOS manual:
 - Go to [http://lenovo.com/websupport](http://lenovo.com/websupport)
 - Click ThinkCentre / ThinkPad
 - Click Denmark on the Europe country list
 - Click Quick Find and supply the model number: 1577-G3G
This will give you the support page for ThinkCentre Edge 71 (1577-G3G).
 - At the right side of the page, click "Hardware Maintenance Manuals" in the section "Guides and Manuals".
 - Here you will find BIOS manual.


I did this.
The BIOS manual does not mention EFI, UEFI nor secure boot.

---

### Post by Mars11 on 2011-12-30
Did you install with a USB? I've heard it's GRUB installation doesn't work.

---

### Post by Paqman on 2011-12-30
Check out the UEFI page on the Ubuntu wiki, tons of info there, although much of it seems Mac-specific.

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by tdn on 2011-12-30
> **Mars11 said:**
> Did you install with a USB? I've heard it's GRUB installation doesn't work.



I did install via USB. I followed the official steps from ubuntu.com. Why would that not work? Is there a bug report on this?

---

### Post by tdn on 2011-12-30
> **Paqman said:**
> Check out the UEFI page on the Ubuntu wiki, tons of info there, although much of it seems Mac-specific.

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Thanks. I already read that. I could not find anything helpful there. You're right, it has tons of information. Maybe I just missed the important bits. Care to point me to the section that is relevant for this problem?

---

### Post by Paqman on 2011-12-30
> **wyliecoyoteuk said:**
> You need to disable secure boot in the BIOS, if that is possible.
You may need to enter a special BIOS code to get to it.


Rubbish. "Secure Boot" is a planned feature of a future version of Windows that would force OEMs to provide EFI that would only boot a "signed" OS. It's not actually implemented on any systems, and it's not known what form it will take if/when it does.

---

### Post by Mars11 on 2011-12-30
If you have an extra CD lying around try that, or follow [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") guide to install GRUB.

---

### Post by tdn on 2011-12-30
> **Paqman said:**
> Rubbish. "Secure Boot" is a planned feature of a future version of Windows that would force OEMs to provide EFI that would only boot a "signed" OS. It's not actually implemented on any systems, and it's not known what form it will take if/when it does.


Thanks for clearing this up.

This gives me some hope that it will be possible to get this machine up and running.

---

### Post by Paqman on 2011-12-30
> **tdn said:**
> Care to point me to the section that is relevant for this problem?

I've never encountered an EFI system, so I can't really walk you through the details, but it looks very much like you'll have to start at the top and wade through it, ignoring all the Mac bits. 

It doesn't look like fun. I'm kind of hoping for your sake that the info is outdated and there's now a simple piece of hand-waving magic that can be applied.

---

### Post by tdn on 2011-12-30
> **Mars11 said:**
> If you have an extra CD lying around try that, or follow [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") guide to install GRUB.

I tried following the "terminal way" method in the guide you linked to. It failed. See this paste:
[http://paste.adora.dk/P2278.html](http://paste.adora.dk/P2278.html)


So maybe this is related to GPT?

---

### Post by Mars11 on 2011-12-30
[s]Try just going into the terminal and typing "sudo grub-install /dev/sda".[/s]

---

### Post by tdn on 2011-12-30
> **Mars11 said:**
> [s]Try just going into the terminal and typing "sudo grub-install /dev/sda".[/s]

Isn't that exactly what I did? Did you see the error in the paste?

---

### Post by Mars11 on 2011-12-30
Yeah...sorry, I didn't read the bottom. :\

---

### Post by Mars11 on 2011-12-30
Could you try going into GParted and giving me a screenshot? I want to see what your disks look like.

---

### Post by tdn on 2011-12-30
> **Mars11 said:**
> Could you try going into GParted and giving me a screenshot? I want to see what your disks look like.


Sure, right here:
[http://i.imgur.com/fHd2Y.png](http://i.imgur.com/fHd2Y.png)

---

### Post by tdn on 2011-12-30
Would it help if I did a:

dd if=/dev/zero of=/dev/sda bs=4k count=10k

And thus wiped the partition table/GPT?

And then reinstalled Ubuntu?

---

### Post by Mars11 on 2011-12-30
Uh...sure, give it a shot. It's not like you have anything to loose.

---

### Post by Mars11 on 2011-12-30
When you reinstall Ubuntu, do the custom option and only set up two partitions, the data and a swap. The set sda as the boot device.

---

### Post by tdn on 2011-12-30
> **Mars11 said:**
> Uh...sure, give it a shot. It's not like you have anything to loose.

Trying...

---

### Post by m_duck on 2011-12-30
With 11.10 and the Precise daily builds, I found that as long as the hard disk had a GPT partition table on it beforehand, the resulting installed system would be EFI booted. This was on a Macbook Pro 7,1 with Apples crazy version of EFI too, so I would be shocked if the same didn't apply on a Lenovo?

---

### Post by tdn on 2011-12-30
> **m_duck said:**
> With 11.10 and the Precise daily builds, I found that as long as the hard disk had a GPT partition table on it beforehand, the resulting installed system would be EFI booted. This was on a Macbook Pro 7,1 with Apples crazy version of EFI too, so I would be shocked if the same didn't apply on a Lenovo?

What is precise daily builds? And where do I get them?

---

### Post by satanselbow on 2011-12-30
Ok... I looked in on this thread last night and decided I couldn't help as have minimal experience of Lenovo machines / EFI...

The "problem" however is the fact that your disk is GPT partitioned but you do not have a "bios_grub" partition - which is where grub installs on GPT...

As you have rather been chasing smoke and have hosed pretty much everything :D

Boot into a live CD and use gparted to clean up your disk and recreate a clean GPT partiton schema. 

In any case once you have created your GPT Partition table in gparted:

gparted -> Device -> Create Partition Table ->GPT


Create an 8MB FAT32 partition at the beginning of the drive (ie sda1) and set both the "bios_grub" and "hidden" flags. This is where ubuntu installer will locate grub.

Are you planning to dualboot with W7? in which case you will want to install that next (after partitioning but before (chronologically) Ubuntu).

I would also suggest you create your planned partition layout for W7 (create NTFS partition in gparted and then reformat it with the Windows installer) + Ubuntu ( root / swap / home) and make a note of device/partition numbers so you can refer to them during installation :popcorn:

---

### Post by Elfy on 2011-12-30
> **tdn said:**
> What is precise daily builds? And where do I get them?

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

The alpha1 is here - [http://cdimage.ubuntu.com/releases/precise/alpha-1/](http://cdimage.ubuntu.com/releases/precise/alpha-1/)

Been following this as well - hope to see a good outcome.

---

### Post by satanselbow on 2011-12-30
> **tdn said:**
> What is precise daily builds? And where do I get them?

"Precise" is the next - as yet unreleased - version of Ubuntu due in April 2012.

I'm surprised you are being recommended to install it given it is far from stable and may result in daily breakage (which is a recognised sport round these parts).

If you need a stable system install the latest released version ie 11.10.

---

### Post by bui89 on 2011-12-30
I tried advices from satansbelow. but it didn't help :(
I was creating 8 mb fat32 partition but it created 32 mb :(

---

### Post by tdn on 2011-12-30
> **tdn said:**
> Trying...


This did not help at all. I will try what satanselbow suggested.

---

### Post by tdn on 2011-12-30
> **satanselbow said:**
> Ok... I looked in on this thread last night and decided I couldn't help as have minimal experience of Lenovo machines / EFI...

The "problem" however is the fact that your disk is GPT partitioned but you do not have a "bios_grub" partition - which is where grub installs on GPT...

As you have rather been chasing smoke and have hosed pretty much everything :D

Boot into a live CD and use gparted to clean up your disk and recreate a clean GPT partiton schema. 

In any case once you have created your GPT Partition table in gparted:

gparted -> Device -> Create Partition Table ->GPT


Create an 8MB FAT32 partition at the beginning of the drive (ie sda1) and set both the "bios_grub" and "hidden" flags. This is where ubuntu installer will locate grub.

Are you planning to dualboot with W7? in which case you will want to install that next (after partitioning but before (chronologically) Ubuntu).

I would also suggest you create your planned partition layout for W7 (create NTFS partition in gparted and then reformat it with the Windows installer) + Ubuntu ( root / swap / home) and make a note of device/partition numbers so you can refer to them during installation :popcorn:


Ok. So I did this.
However, it fails at creating a ned partition table GPT>
[http://i.imgur.com/ugQIV.png](http://i.imgur.com/ugQIV.png)
Error while creating partition table.

---

### Post by satanselbow on 2011-12-30
> **bui89 said:**
> I tried advices from satansbelow. but it didn't help :(
I was creating 8 mb fat32 partition but it created 32 mb :(

Might be an idea to start your own thread as your issues are unlikely to be exactly the same as the OP's.

---

### Post by tdn on 2011-12-30
It says this in terminal:
Partition(s) 3 on /dev/sda have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.


So I guess I will reboot and try again.

---

### Post by satanselbow on 2011-12-30
> **tdn said:**
> It says this in terminal:
Partition(s) 3 on /dev/sda have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.


So I guess I will reboot and try again.

Did you boot into a liveCD/USB ???? If you have previously mounted those partitions in the same session it may give that message.

You should always clean boot into a liveCD to do partition work ;)

---

### Post by tdn on 2011-12-30
> **satanselbow said:**
> Ok... I looked in on this thread last night and decided I couldn't help as have minimal experience of Lenovo machines / EFI...

The "problem" however is the fact that your disk is GPT partitioned but you do not have a "bios_grub" partition - which is where grub installs on GPT...

As you have rather been chasing smoke and have hosed pretty much everything :D

Boot into a live CD and use gparted to clean up your disk and recreate a clean GPT partiton schema. 

In any case once you have created your GPT Partition table in gparted:

gparted -> Device -> Create Partition Table ->GPT


Create an 8MB FAT32 partition at the beginning of the drive (ie sda1) and set both the "bios_grub" and "hidden" flags. This is where ubuntu installer will locate grub.

Are you planning to dualboot with W7? in which case you will want to install that next (after partitioning but before (chronologically) Ubuntu).

I would also suggest you create your planned partition layout for W7 (create NTFS partition in gparted and then reformat it with the Windows installer) + Ubuntu ( root / swap / home) and make a note of device/partition numbers so you can refer to them during installation :popcorn:



Ok. So now I did that.
 * I wiped the disk with dd first.
 * Then created new GPT partition table.
 * Then rebooted.
 * Then created a new 500 MB FAT 32 partition at the beginning. You said 8 MB, however, minimum size is 32 MB. Also, I read somewhere that Windows 7 might require 200 MB on this partition, so I just decided to take som extra space.
 * I then created a new partition with ext4 fs for /
 * Then created a new 4096 MB partition for swap.

So now what?
What to do during install?

---

### Post by tdn on 2011-12-30
Oh, I also set the bios grub flag as well as the hidden flag for the first FAT32 partition. Should I also set boot flag?

---

### Post by tdn on 2011-12-30
My disk layout in gparted can be seen in screenshot here: [http://i.imgur.com/8tsUa.png](http://i.imgur.com/8tsUa.png)

---

### Post by tdn on 2011-12-30
OK. So I started the installer and went to the step to set up the disk for installation. This is the layout from the installers perspective:
[http://imgur.com/a/dwOuM](http://imgur.com/a/dwOuM)
(two bottom screenshots)

Is that right?
What to do now?

I guess I have to set mountpoint and such?

I see that I can chose Use as: EFI for the /dev/sda1. Should I do that?

---

### Post by Blaze33 on 2011-12-30
Seems like you're the one who asked this: [http://askubuntu.com/q/91484/7567](http://askubuntu.com/q/91484/7567)
As i said there, have a look at this page : [http://superuser.com/q/372962/37511](http://superuser.com/q/372962/37511)

Also, the EFI partition should only have the boot partition when using a GPT partition scheme (at least it works like this on my pc). Just tell the installer to use sda1 as EFI partition, sda2 as root / and sda3 as swap (as far as i remenber you'll find this in the advanced options).

---

### Post by Blaze33 on 2011-12-30
My hdd looks like this: [http://i.imgur.com/NM8Ux.png]("http://i.imgur.com/NM8Ux.png")

---

### Post by satanselbow on 2011-12-30
[QUOTE=satanselbow]Create an 8MB FAT32 partition at the beginning of the drive (ie sda1)[/QUOTE]

Apologies that should read "Unformatted" - my bad... I've been working with USB sticks all morning and got FAT32 on the brain :(

That would then allow you to create the required 8MB partition.

Windows uses it's "extra" partition for a different reason ie bootstrapping the OS. The small partition is a "replacement"  for the harddisk's MBR which is not present on a GPT partitioned platter and gives grub an alternate place to live ;)

You seem to be worried about Windows requirements but are not planning on installing Windows :confused:

From the screenshots you posted you have not left any room to install Windows **WHICH SHOULD BE DONE 1ST** and will be installing your Ubuntu into one huge partition which is not really recommended - although a matter of personal preference if you have a solid off disk data backup solution ;)

A partition of 20-30GB would be ample for Ubuntu root ( / ) with the rest of the disk for /home + swap as you have it currently ;)
Using a separate root+home+swap scheme will make system recovery and data backup a lot easier later.

---

### Post by tdn on 2011-12-30
> **satanselbow said:**
> Apologies that should read "Unformatted" - my bad... I've been working with USB sticks all morning and got FAT32 on the brain :(

That would then allow you to create the required 8MB partition.

Windows uses it's "extra" partition for a different reason ie bootstrapping the OS. The small partition is a "replacement"  for the harddisk's MBR which is not present on a GPT partitioned platter and gives grub an alternate place to live ;)

You seem to be worried about Windows requirements but are not planning on installing Windows :confused:

From the screenshots you posted you have not left any room to install Windows **WHICH SHOULD BE DONE 1ST** and will be installing your Ubuntu into one huge partition which is not really recommended - although a matter of personal preference if you have a solid off disk data backup solution ;)

A partition of 20-30GB would be ample for Ubuntu root ( / ) with the rest of the disk for /home + swap as you have it currently ;)
Using a separate root+home+swap scheme will make system recovery and data backup a lot easier later.


Originally, I wanted to install Ubuntu along side with Win 7. However, as this did not turn out to go as smooth as I had wished, I am now trying to just get Ubuntu up and running. Putting Windows 7 on will be an optional next step.

I am aware that the current disk layout does not make room for Windows. However, if need be I can always resize the ext4 filesystem for root to make room for Windows.

I have noted that the partition should not be FAT32. So, do I need to start over?

I tried using the layout I described earlier with screenshots for a new installation. It could not boot. Now I am trying to select "Use as:_EFI Boot" in the installer.

---

### Post by tdn on 2011-12-30
That did not work either.

I do not get it. Why do I have to jump through all these hoops just to make Ubuntu boot? This seems like something that should be solved in the installer. :(



Right now, I have been told a lot of things to do to solve this. I am missing a clear overview of what works.

So far, I have not had any luck booting Ubuntu.


If someone can provide a clear concise description of steps needed to make this work, I will appreciate it.

Thanks.

---

### Post by Mars11 on 2011-12-30
I seriously would try installing from a LiveCD. That always fixed my booting problems.

---

### Post by tdn on 2012-01-02
> **Mars11 said:**
> I seriously would try installing from a LiveCD. That always fixed my booting problems.

Well, I had to go buy a blank CDROM. Then it actually worked!
Thanks.

---

### Post by dcstar on 2012-01-02
> **tdn said:**
> Well, I had to go buy a blank CDROM. Then it actually worked!
Thanks.

Then please **MARK** the thread (read below).

---

### Post by Mars11 on 2012-01-02
Haha, no problem. I've always had problems installing from a flash drive since Natty. Now mark the thread as solved.

---

### Post by tuberosity on 2012-01-10
Although I agree that this issue can be considered solved per se,I am experiencing similar problems and I think this should be reported as a bug.
That way at least two examples can be submitted(The OP's and mine) for further review and fixing.



Is this already reported? How should I report this?(I have a launchpad ID and have experience reporting papercuts before, but nothing like this)
Should I start another thread for this?

Thanks.

---

### Post by Manyette on 2012-01-10
Paqman, while UEFI itself is not yet implemented, some Acer machines, and perhaps others (mine was one of them) will not allow any CD that has the Linux boot line load and run. My guess is that thet they have used bhe BIOS hook to do this.  I had to destroy (format) the hard disk before I could boot ANY linux deisk, while any other CD/DVD would boot just fine. So far as I know, only ny ACER 5250 had this implementedm, but there could be others.

---

### Post by tuberosity on 2012-01-11
For me, the issue has not been solved by CDROM installation.

 For now, I've given up hope, and I am waiting for precise. My primary goal right now is to inform the relevant authorities and experts so whoever can fix this is "in the know",

Should I open a new thread?

---

### Post by Manyette on 2012-01-11
Again, I have to emphasize that my CD install would NOT work until the systems hard disk had been formatted, to remove whatever had been placed there by the Windoze softward!

---

### Post by oldfred on 2012-01-11
Developers are rarely if ever in the forum. They work off bug reports and usually only those with multiple posts so it is confirmed. You can report the bug but it may help to try to find others with same issue and get them to also report it. Not sure what you report against. It may be the installer Ubiquity, partman-efi or grub2?

bug reports info on how to do:
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
Check bugs on grub2
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

Some UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

---

### Post by tuberosity on 2012-01-11
So you
1)Formatted drive
2)Installed Ubuntu
3)Installed Windows?

Then in 1) I assume you actually mean, deleted all partitions right?

---

### Post by Manyette on 2012-01-11
Yes but point 3 was unnecessary, since I run only *nix. But the main point was to remove the hook that Win had placed on the drive.

---

### Post by brentosw on 2013-02-04
Hi there,

There are some quirks with the Lenovo UEFI implementation that have been documented elsewhere.

After struggling with this for a few days, I've made the following guide. Where it differs from the discussion so far is that it's a 100% UEFI solution. Provided you have GRUB2, the solution will work at least for Lenovo BIOSs similar to the one on the current ThinkStation S30.



_Original location:_
[http://forums.lenovo.com/t5/Linux-Discussion/UEFI-Mode-installation-of-Linux-distributions-on-Thinkstation/td-p/1018555](http://forums.lenovo.com/t5/Linux-Discussion/UEFI-Mode-installation-of-Linux-distributions-on-Thinkstation/td-p/1018555)

---

