---
title: "Hibernate (Win8) stopped working (grub2, 12.04, dual boot, dmraid, EFI)"
date: 2012-10-05
forum: General Help
---

### Post by shappie on 2012-10-05
Hi all,

I'm running Ubuntu 12.04.1 on my laptop (Sony Vaio Z13) in dual boot with Windows 8 Release Preview. Both 64 bits and using an EFI bootloader. The 'bios' is put in UEFI mode to. The laptop contains 2 ssd's in raid0 (dmraid). 

Because my laptop doesn't have an optical drive i first tried to use a USB stick to install ubuntu, but that failed (dmraid support, kernel panics and some more stuff). I then put a alternate iso on my usb, but that failed too because it started looking for the cd again (bug is easily found by google, but no solution worked for me). I then used an external USB optical drive with the alternate iso which worked. I installed the grub2 bootloader onto the disk, but it didn't show after a reboot. I fixed this problem using these tips: [http://askubuntu.com/a/157062](http://askubuntu.com/a/157062).

I now finally got grub2 working (sort of) and can choose between Win and Ubuntu at boot. The problem is that when i'm using grub2 as default bootloader Win8 is unable to return from hibernate. My laptop starts, shows the grub2 screen, boots Win8, but then it shortly hangs and i get a clean restart instead of restore from hibernate.

I've read a lot of topics regarding this topics individually but it looks like almost nobody got them all at the same time (dmraid, efi, win8, grub2, sony h2o insyde bios). Please don't tell me to use linux software raid (instead of dmraid), drop efi or the win8 dual boot. I can't use linux software raid because of the dualboot and would like to keep using EFI because of the incredible startup/sleep/hibernate speed combined with Win8.

I use hibernate on a daily basis, so hopefully somebody could help me out here.

Thanks in advance,

Mart

---

### Post by albandy on 2012-10-05
Please, in an ubuntu terminal type:
```

sudo fdisk -l

```
and paste the result.

---

### Post by shappie on 2012-10-05
I'm sorry i forgot to include it the first time, here it is: 
[http://paste.ubuntu.com/1261574/](http://paste.ubuntu.com/1261574/)

---

### Post by albandy on 2012-10-05
> **shappie said:**
> I'm sorry i forgot to include it the first time, here it is: 
[http://paste.ubuntu.com/1261574/](http://paste.ubuntu.com/1261574/)

I see this: 
ARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

So open it with gparted. 
Go to System --> Administration --> gparted and make an screnshot

if you don't have gparted installed:
sudo apt-get install gparted

---

### Post by shappie on 2012-10-05
See attachment.

GParted only shows 3 disks in the top right corner dropdown. The current raid array (mapper/isw....) and sda/sdb. Sda and sdb only show an error and unallocated space, because they are of no use by themselves, they are combined in a RAID0 array.

edit: The first 4 partitions are created by Win8 and i shrinked the Win8 OS partition to create the ext4 and swap partitions for ubuntu.

---

### Post by albandy on 2012-10-05
Ok, try setting the partition labeled as WIN8 to bootable.

---

### Post by shappie on 2012-10-05
I put the boot flag on the partition labeled as WIN8 and rebooted. Unfortunately i got a 'no operating system found' error. So there is no bootloader currently being loaded at boot. 

I can still access Ubuntu manually from the grub2 on my Ubuntu Live usb stick (c for command line: set root, linux..., initrd... boot). So i could remove the 'boot' flag.

---

### Post by albandy on 2012-10-05
Ok I will try to replicate your configuration in a virtual machine to see what is happening.

---

### Post by shappie on 2012-10-05
> **albandy said:**
> Ok I will try to replicate your configuration in a virtual machine to see what is happening.
Thanks in advance! I'm unable to make any sense of this too, hopefully you'll figure it out :)

---

### Post by ucracker on 2012-10-06
Hello ! I have the same issue, but my windows is windows 7 x64.

Same problem: can't get out from hibernation.

---

### Post by oldfred on 2012-10-06
If using UEFI the boot flag has to be on the efi partition. And it is not really a boot flag although gparted calls it that. 

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

I do not know if with UEFI this issue still applies as you should be able to directly boot. But if you write into a hibernated system from another system whether Linux or another Windows you will corrupt the hibernated system.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by ucracker on 2012-10-08
Had to find an alternative, and turned off UEFI, and now hibernation works perfectly in dualboot.

---

### Post by shappie on 2012-10-08
I've allready turned off the 'hybrid hibernation/off state' in the Win8 power settings, since i read some stuff about this causing problems in dualboot. Unfortunately this doesn't seem to help.

I could live with the fact that i cannot run Ubuntu while Win8 is hibernated, i use Win8 most of the time because i need to use Win-only software for university. When i'm planning on using Ubuntu i could just shutdown Win8 (without hybrid hibernation/off state) before booting into linux. It's just that even when you just put Win8 into hibernate and then (without booting Ubuntu in the meantime) try to restore from hibernation it fails. Probably grub2 is messing things up here?

---

### Post by albandy on 2012-10-09
> **shappie said:**
> I've allready turned off the 'hybrid hibernation/off state' in the Win8 power settings, since i read some stuff about this causing problems in dualboot. Unfortunately this doesn't seem to help.

I could live with the fact that i cannot run Ubuntu while Win8 is hibernated, i use Win8 most of the time because i need to use Win-only software for university. When i'm planning on using Ubuntu i could just shutdown Win8 (without hybrid hibernation/off state) before booting into linux. It's just that even when you just put Win8 into hibernate and then (without booting Ubuntu in the meantime) try to restore from hibernation it fails. Probably grub2 is messing things up here?

Maybe Virtualbox can be a good solution for you.

I'm a java developer and usually I work in Linux only, but when I need to run Windows applications I run it under virtualbox.

If you have a good computer, with virtualization extensions, your virtual machine will work very fast.

---

### Post by shappie on 2012-10-09
> **albandy said:**
> Maybe Virtualbox can be a good solution for you.

I'm a java developer and usually I work in Linux only, but when I need to run Windows applications I run it under virtualbox.

If you have a good computer, with virtualization extensions, your virtual machine will work very fast.
I've used VirtualBox numerous times on my desktop to test distro's and new beta's, but it's currently not what i'm looking for. 

I currently boot ubuntu manually using grub2 on a usb drive, which probably is a better solution than using a VM for the moment.

Shouldn't it be possible to just use ubuntu and Win8 in dualboot with hibernate working?

---

### Post by oldfred on 2012-10-09
While it should be possible, it still is dangerous. 

Each hibernation expects data to be in the same place. If you modify anything in the hibernated system from the other system you loose the changes and corrupt the hibernation. Even if Windows 7 & Windows 8 dual booted.

The only way to have both systems stay updated together is the virtual solutions.

---

### Post by shappie on 2012-10-09
> **oldfred said:**
> While it should be possible, it still is dangerous. 

Each hibernation expects data to be in the same place. If you modify anything in the hibernated system from the other system you loose the changes and corrupt the hibernation. Even if Windows 7 & Windows 8 dual booted.

The only way to have both systems stay updated together is the virtual solutions.
I understand there is a risk of corrupting files when trying to run Ubuntu while Win8 is hibernated. But i think it's strange to just remove the whole ability to use hibernation for Windows because you could possibly run Ubuntu and corrupt files. I think the solution to this problem is to prevent Ubuntu from booting when Win8 is hibernated, not to totally disable hibernation. It would be even better to just hide the grub2 menu when one OS is in hibernate state, this way you boot up fast from hibernation and there is no risk of corrupting files.

I'm currently able to manually boot (set root, linux, initrd and boot) from grub2 on an Ubuntu live usb drive, which i think is a better temporary solution than running a VM. There are other reasons i don't like to use a VM for this, but that's not really relevant. The problem still exists and a VM is merely a workaround, not a real solution.

But you said it should be possible, is there any way for me to find out how?

---

### Post by oldfred on 2012-10-09
Users seem to not be able to use  grub to chainload to Windows 8 when hibernated. Normally Windows in the MBR just jumps to the PBR - partition boot sector to load Windows. Grub just skips the MBR and directly jumps to PBR. But something with Windows 8 has changed.

The only way I have seen it work so far is to leave Windows 8 totally in control of its hard drive. Then from BIOS use another MBR to boot Ubuntu. If you have two hard drives that is easy or you can install grub2 to a USB flash drive or CD  and use that to boot Ubuntu. Not the easiest and you then have to manually update your grub entry as it will not be automatically updated.

How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb

Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

You can create grub2 boot entries that do not require editing on every kernel update:

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by shappie on 2012-10-10
Thanks for all the info! I've managed to make a grub2 USB disk, which automatically boots my Ubuntu installation. 

At first i had some problems, but i think that's because i did the grub-install on my EFI enabled laptop. When i put a live-cd in my desktop and from a live session did a grub-install on the USB stick it booted just fine!

I still can't find a way to boot from SD card, i always get the message "Operating system not found". When i put my SD card in an USB cardreader it boots just fine. But that's not related to Ubuntu.

Thanks again for support! I'll leave the thread open for others that encounter the same problem or when there's a fix available in the future. For the time being i can live with this workaround :)

---

### Post by oldfred on 2012-10-10
The instructions I gave you was for a BIOS/MBR boot, now not sure if correct. But you seemed to have UEFI boot. 

So did you install a efi boot to external device or MBR?  Or maybe Ubuntu was installed in BIOS mode and Windows in UEFI and that was part of the issue?

Might be best just to document system to run BootInfo report and post link.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by shappie on 2012-10-11
I ran boot-repair on my laptop and got the following link: [http://paste.ubuntu.com/1273524/](http://paste.ubuntu.com/1273524/)

I didn't apply any changes to my current boot manager and/or configuration, because i don't got a lot of time at the moment and need Win8 on a daily basis for university. So i don't got time to mess things up and fix it again unfortunately.

On startup boot-repair told me it detected an EFI system, so i guess everything is installed fine. So probably it's a grub2 bug, or it got something to do with my sony efi bios. The 'Insyde H2O' EFI bios is programmed to start Windows no matter what the bootloader says, so i changed the Win8 bootloader file to the grub file to get it to boot ([howto]("http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi/157062#157062")). It's weird Win8 boots just fine, but can't get out of hibernation.

---

### Post by oldfred on 2012-10-11
I do not really understand RAID, and you have RAID, UEFI/efi boot with gpt partitions inside the RAID. Or a pretty complex set-up.

You did not have the flash drive plugged in when you ran BootInfo report? It only shows the two drives that are part of the RAID.

Did you configure system with RAID. I am not a fan of RAID on desktops, but expect it on servers. It is more for uptime, performance and with some configurations the ability to hot-swap drives.

 Some users think RAID is a way to have backups, but it is not. When you delete a file (that your did not intend to delete) it is also gone on the mirror. Only way to recover then is from the backup.

On a desktop you cannot type faster, your Internet is not faster, and if you have a SSD you have a very fast hard drive, so RAIDed SSDs is a real luxury for not a lot of gain.

And this site says never to use RAID 0.

Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by shappie on 2012-10-11
As i mentioned in my start post i don't plan on abandoning RAID0 or changing to Linux software RAID. Besides this, i don't think this problem got much to do with dmraid actually. It's got more to do with EFI, grub2 and Win8 i guess.

I got a laptop with 2x64 GB SSD that came preconfigured with RAID0. I don't care a lot about the added risk, because i use regular backups and will never loose any valuable data if my laptop crashes. The other reason is 64GB isn't enough for my Win8 installation (with all the software and data included), so i need RAID0 to extend the storage. At last it's really fast, which is quite nice too.

But if we can't find a solution a.t.m. it's not that big of a deal. Booting from USB disk is working fine for the time being, and hopefully this gets fixed in the future.

---

### Post by YannBuntu on 2012-10-12
Maybe related:
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

