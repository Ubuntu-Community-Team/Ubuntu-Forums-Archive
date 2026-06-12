---
title: "Booting from the harddrive without GRUB on it"
date: 2011-02-05
forum: General Help
---

### Post by Momotombo on 2011-02-05
I have two HDDs in this system. One is a 1tb that seems to be failing - I get "Read Error" when trying to boot from it sometimes, and if I manage to get into Windows the disk eventually stops spinning.

The other HDD has ubuntu on it, which I'm on right now. What's weird is that I can still access files from the other HDD without the disk stopping or anything, but that's for another time. The problem is that the bad HDD has GRUB on it, so if I take it out and put it in another computer for file transfer I suddenly don't have my main system anymore because GRUB won't show up.

How can I get GRUB on the other harddrive? Or rather, how can I boot into ubuntu without the HDD with GRUB?

---

### Post by quadproc on 2011-02-05
You can probably do everything that you need with a Live CD.  Just boot from the Live CD, do your needed repairs, then boot and you should be back to normal operations.  The only real drawback to the Live CD is that it is quite a bit slower.

quadproc

---

### Post by oldfred on 2011-02-05
If you can boot into your system you can just install from that working system. You need the liveCD if you cannot boot.

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
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Then change BIOS to boot Ubuntu drive.

What format is other drive? Running e2fsck or chkdsk may be all you need.
Also check in System, Administration, Disk Utility, click on drive and see what SMART says about drive.

---

### Post by glene77is on 2011-02-05
OldFred,
Good advice.
I would do it this way:
(1) Change BIOS to boot from the second drive.
(2) run the Live-CD, install to the second drive.
Ubuntu will write an MBR which points to the Ubuntu partition track-sector. 
(3) grub will point to /boot/grub/grub.cfg.   
(4) grub.cfg generates the multi-booting menu and re-directs to which OS you select. 

On my 'other' computer, I have Ubuntu the primary boot.  
MBR points to grub.cfg located in the Ubuntu partition.
Grub.cfg allows re-direction to 
(1) Puppy 
(2) Knoppix 6.2
(3) Knoppix 6.4
(4) Ubuntu 10.4
(5) Watt OS R2

Ubuntu wrote the MBR to point into Ubuntu. 

Linux will read/write the NTFS format in the Windows OS,
whereas Windows OS will not recognize the Linux format.  
I have run GIMP and Audacity from Linux onto the files in the Windows OS, with great success. 

Great fun. :)

---

### Post by oldfred on 2011-02-05
While we are a little off topic, I do not like to write into another systems system partition. Or I only read from my XP partition and have set up a shared NTFS partition for any data I may want in either XP or Ubuntu. I started this when I was learning Ubuntu and spouse wanted to check email (Thunderbird) or web (Firefox) and I had to reboot into XP. I added a shared partition and put the profiles into that and then we were not rebooting into XP nearly as much. Then I added Picasa (not Linux version) into wine and now am down to one application in XP and I think It is just about gone.

I also have a /data partition as I have several Ubuntu's installed and can then mount both my shared & data partitions in all of them with out issue of system or user settings being corrupted.

---

