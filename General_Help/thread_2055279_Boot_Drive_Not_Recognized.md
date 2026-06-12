---
title: "Boot Drive Not Recognized"
date: 2012-09-09
forum: General Help
---

### Post by raw157 on 2012-09-09
Hey folks,
I have an HP Ultrabook which was running Windows 7 and I wanted to dual boot it with Ubuntu. Everything was working fine until today, and I have no idea how I did it or how to fix it.

When I turn on the laptop, I now get a Windows Boot Manager screen and an error. 
(Status 0xc000014c) 

I'm not sure how to fix it thought Ubuntu (that's why I"m here). I am at the point now where I have no problem formatting everything and starting all over. 

I have tried to do a clean install of Win7. However, when I go to install the OS, it does not detect the hard drive. The Bios does, as well as the HP utility. Disk Part does not, it only sees the flash drive I'm using for the OS. 

The laptop does have a 32gig SSD portion (which I believe Win7 was installed), as well as a 500 gig HDD. 

If I'm not making sense please ask me questions, I need to get to the bottom of this!
Thanks,
Raw

---

### Post by coldcritter64 on 2012-09-09
As you're getting a broken Windows boot screen. [U][I]Was your Ubuntu install via Wubi?
[/I][/U]
If it was, it may pay you to add the [wubi] tag to your thread title. You may have to repair the MBR from a Windows installation disk or download a Windows boot repair disk if you do not have installation media for Windows.

In case you aren't aware, installing Ubuntu via Wubi, puts the Ubuntu installation into a hidden file on the Windows NTFS file system {and adds an GRUB entry to the Windows bootloader}. If you did manage to reinstall Windows you will have overwritten the Ubuntu installation as well.

---

### Post by raw157 on 2012-09-09
I did not use Wubi. It made a live CD, and booted into it.

---

### Post by oldfred on 2012-09-09
It it like these?

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

The Intel Smart Response is some sort of RAID configuration and Ubuntu's liveCD does not have RAID drivers. And if any drive has left over RAID meta -data gparted or the installer will not work as they do not want to damage the RAID install.

---

### Post by raw157 on 2012-09-09
Yes, very similar.
So if Ubuntu can't do a raid, why isn't windows picking it up?

---

### Post by oldfred on 2012-09-09
Ubuntu can do RAID of many versions. Do not know about Intel Smart Reponse. Others seems to just want to separate the SSD from Windows and use SSD as SSD. If you want RAID drivers out of the box you have to install the alternate installer or the server installer. Alternate installer is just text based and not a liveCD, so it can include more drivers.

---

### Post by raw157 on 2012-09-09
I'm not sure exactly what you mean. 
Is there anyway with Ubuntu or another program I can nuke the disks and start from factory fresh.

---

### Post by oldfred on 2012-09-09
If you add this to your LIveCD, it may show the RAID partitions.

From terminal in liveCD

```
sudo apt-get install mdadm
```

Then post this from liveCD
```

sudo fdisk -lu
```


If you want to break the RAID, so you can use the regular partition tools and see SSD as a totally separate drive. I believe that was what the Dell users links posted above did.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)


I do not know if your HP reinstall automatically sets up the RAID again or not. That may be a question for HP on how there recovery is set up.

---

### Post by raw157 on 2012-09-09
[QUOTE]> **oldfred said:**
> If you add this to your LIveCD, it may show the RAID partitions.

From terminal in liveCD

```
sudo apt-get install mdadm
```Then post this from liveCD
```

sudo fdisk -lu
```If you want to break the RAID, so you can use the regular partition tools and see SSD as a totally separate drive. I believe that was what the Dell users links posted above did.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)


I do not know if your HP reinstall automatically sets up the RAID again or not. That may be a question for HP on how there recovery is set up.

When I look at the drives in Gparted it shows it as 2 seprate drives (before the terminal commands you posted). Should I delete and format the drives and just reinstall?

---

### Post by oldfred on 2012-09-09
That is just showing two drives. I do not know how the HP system is supposed to work. You can just copy text output from terminal to your message. If long or formated use code tags or highlight like copying and click on the # icon in the edit panel.


Post the full BootInfo report's link.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

