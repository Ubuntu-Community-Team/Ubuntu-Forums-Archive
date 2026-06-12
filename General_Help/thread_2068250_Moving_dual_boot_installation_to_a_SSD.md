---
title: "Moving dual boot installation to a SSD?"
date: 2012-10-08
forum: General Help
---

### Post by geo909 on 2012-10-08
Hi all,

I think my hard disk is going to die sooner or later
(it makes some clicking sounds every now and then
since several months ago).

On another note, I need to format. All this suggest 
that it is a good time to purchase a new hard drive
and do the format once and for good on the new hard 
drive, however I'm on a budget and would really like 
to buy the hard drive a bit later.

I thought of the following scenario: Do the format 
now on the current hard disk and once I purchase a
new hard drive, move the whole installation there
(using a tool like clonezilla, I guess).

Do you think this scenario is possible with clonezilla
or some other tool, given that:
.I'm using a regular disk and I'll buy a SSD.
.I dual boot with WinXP 
.The sizes of those disks are going to be different.

Any advice on that would be really appreciated.

---

### Post by Rebelli0us on 2012-10-08
I've used Gparted copy & paste feature to copy entire partitions (both ext4 & NTFS).

---

### Post by oldfred on 2012-10-08
XP and SSDs do not work well together. You need AHCI in BIOS to use trim on SSD and XP does not directly support AHCI. If you reinstall XP, supposedly you can install AHCI drivers, but I just shut down my XP so I could correctly use my SSD. The procedure to install AHCI drivers after the fact in XP is pretty complicated.

Probably better to leave XP on rotating disk. But you still cannot set AHCI except for the entire system.

---

### Post by geo909 on 2012-10-09
> **Rebelli0us said:**
> I've used Gparted copy & paste feature to copy entire partitions (both ext4 & NTFS).

Thanks! I'll look that up..

> **oldfred said:**
> XP and SSDs do not work well together. You need AHCI in BIOS to use trim on SSD and XP does not directly support AHCI. If you reinstall XP, supposedly you can install AHCI drivers, but I just shut down my XP so I could correctly use my SSD. The procedure to install AHCI drivers after the fact in XP is pretty complicated.

Probably better to leave XP on rotating disk. But you still cannot set AHCI except for the entire system.

Thanks.. Hmm, I think that means that i'll have to do some reading cause I don't understand many things here. 

To make it short, does that mean that it will be complicated to dual book linux+xp on an SSD or that it is going to be complicated to actually *move* linux+xp from my existing installation to a SSD?

---

### Post by pqwoerituytrueiwoq on 2012-10-09
moving XP will require running fixboot from a windows install cd
moving linux is easy (imo)
[http://ubuntuforums.org/showpost.php?p=11931965&postcount=3](http://ubuntuforums.org/showpost.php?p=11931965&postcount=3)
then boot the live cd and install grub (or just the MBR i don't think that is a option in grub2)
you could run xp in virtualbox
don't forget to put your discard and noatime option in fstab for ext4 partitions

---

### Post by Merrattic on 2012-10-09
Even though you can, I wouldn't. Better off doing fresh installs and maybe time to move up to Windows 7 (or run XP in a virtual machine - things will be quicker on an SSD)

---

### Post by oldfred on 2012-10-09
I left my XP install on my old 160GB rotating drive. Since it does not boot with AHCI turned on in BIOS, I do not boot it now. But I was able to go into BIOS, change setting back from AHCI and boot XP. Of course I had not booted for a while and had to run many updates and several reboots. I was then able to go into BIOS turn AHCI back on and use my SSD to boot Ubuntu. But not the easiest way to dual boot.

---

### Post by geo909 on 2012-10-09
Ok, so after reading your replies and looking around a little
bit, I start re-thinking about moving the dual-boot to an 
SSD and in fact trying to have a native installation of XP on
the SSD.

I think I will do a format on my current disk and put just 
linux and try to use XP from my virtual box, see how that goes
(will I have usb support for my peripherals?!).

Then, once I get a SSD I'll try to move the installation and
hopefully that won't be a problem. 

Windows 7 is not an option for me for reasons including that 
I'll have to pay or mess up with warez sites etc and the stuff 
that I have to do outside linux, I can do it great with XP.

I will have a rotating HD as well for my data, so if the virtual 
box option does not work, I will make a partition for XP and go 
with oldFred's option.

Oldfred: Was it easy to do this kind of setup?

---

### Post by pqwoerituytrueiwoq on 2012-10-09
> **geo909 said:**
> 
I think I will do a format on my current disk and put just 
linux and try to use XP from my virtual box, see how that goes
(will I have usb support for my peripherals?!).
there is a oracle plugin for that

i just use a shared folder for flash drives and a shared printer over the local net
share /media

doing what oldfred did is not hard once you figure out where your IDE/RAID/AHCI options (my board only supports raid on ports 1 to 4)
if your motherboard has 2 controllers you could have one use AHCI and the other use IDE, i could do this on my desktop if i had to

---

### Post by oldfred on 2012-10-09
I do installs all the time. Every 6 month version at least 2 times, so I scripted most of my customization and I now install from the rotating hard drive to the SSD using grub2's loopmount. That makes for a really quick install.

The Arch site recommends gpt partitioning for SSDs. Gpt partitioning  is required for drives over 2GB but Windows XP will not even see NTFS on a gpt partitioned drive. So I used gpt for my SSD and just created partitions & installed.  I already configure all my installs of Ubuntu to use the same data partitions and my script auto edits fstab and adds apps and some settings that I want.

---

### Post by geo909 on 2012-10-09
> **pqwoerituytrueiwoq said:**
> there is a oracle plugin for that

i just use a shared folder for flash drives and a shared printer over the local net
share /media



Actually I just realized that a virtual machine most 
probably won't work for me: I need windows for music
production software where it is crucial to have 
almost zero latency for your soundcard. This won't 
work through a virtual machine. I'll use XP on a 2nd
rotating drive.

> 
doing what oldfred did is not hard once you figure out where your IDE/RAID/AHCI options (my board only supports raid on ports 1 to 4)
if your motherboard has 2 controllers you could have one use AHCI and the other use IDE, i could do this on my desktop if i had to

Thanks for the photo! I actually have a laptop and I will install
my second drive in the cd tray using [this]("http://www.ebay.ca/itm/PATA-IDE-SATA-2nd-Hard-Drive-caddy-adapter-Dell-Inspiron-1525-/120981310806?pt=US_Drive_Bay_Caddies&hash=item1c2b0c4d56#ht_6295wt_1188") or something similar.

I hope this won't make it more difficult. It shouldn't though,
it's just another port.. Right?

> **oldfred said:**
> I do installs all the time. Every 6 month version at least 2 times, so I scripted most of my customization and I now install from the rotating hard drive to the SSD using grub2's loopmount. That makes for a really quick install.

The Arch site recommends gpt partitioning for SSDs. Gpt partitioning  is required for drives over 2GB but Windows XP will not even see NTFS on a gpt partitioned drive. So I used gpt for my SSD and just created partitions & installed.  I already configure all my installs of Ubuntu to use the same data partitions and my script auto edits fstab and adds apps and some settings that I want.

Ok, so I'll use gpt for my SSD (when I buy it) and I will use
MBR for the second hard drive where I will install windows XP.

So, just to confirm:

Again, what I'm going to do now is that I'll format my rotating
drive using MBR and I will install both linux and XP (XP will be 
in the first, primary partition). At some point I will buy a SSD. 
I will format the SSD using gpt and I will move my linux 
installation from the (MBR-partitioned) rotating drive to the 
(GPT-partitioned)SSD, while keeping my rotating drive with the XP 
installation; whenever I want to boot windows, I'll get into bios 
and I'll switch from AHCI to IDE (I use windows quite rarely so I
don't care it's not convenient).

So, does the above sounds OK? Any issues about moving an installation from GPT partitions to MBR ones? 

Thanks again..

---

### Post by oldfred on 2012-10-09
Everything looks good except the move from MBR to gpt. I do not even suggest moves when MBR to MBR as a reinstall is really easier and quicker. If your initial install uses a separate /home or separate /mnt/data partition you only need the system install on the SSD. If all data is in data partitions, you can back up the settings in /home easily as they are small. If you have the separate /home all you Linux data and user settings are in the /home and on the reinstall to the SSD you just install the system with Something Else or manual install and also mount but DO NOT format your existing /home.

Create the Windows partition(s) first, Windows needs a NTFS primary partition with the boot flag,  then:

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)


If you want to split /home into user settings only and data in separate data partition(s).
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

---

### Post by geo909 on 2012-10-15
> **oldfred said:**
> Everything looks good except the move from MBR to gpt. I do not even suggest moves when MBR to MBR as a reinstall is really easier and quicker. If your initial install uses a separate /home or separate /mnt/data partition you only need the system install on the SSD. If all data is in data partitions, you can back up the settings in /home easily as they are small. If you have the separate /home all you Linux data and user settings are in the /home and on the reinstall to the SSD you just install the system with Something Else or manual install and also mount but DO NOT format your existing /home.

Create the Windows partition(s) first, Windows needs a NTFS primary partition with the boot flag,  then:

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)


If you want to split /home into user settings only and data in separate data partition(s).
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

Thanks so much and sorry for the late reply!

I think that settles my question.. I'm not sure when I will
buy the ssd (probably when my disk dies); when I'll be back 
with feedback.

Thanks!

---

