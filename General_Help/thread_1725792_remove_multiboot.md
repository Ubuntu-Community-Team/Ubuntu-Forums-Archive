---
title: "remove multiboot"
date: 2011-04-10
forum: General Help
---

### Post by cheezsoup on 2011-04-10
Hi there.
    I have installed Ubuntu (10.10 the 64 bit version) this appears as a multiboot, what I should have done was run 10.10 as a live CD but I have installed it. 
    The multiboot gives options for Ubuntu, Ubuntu configuration ??? Memtest , Memtest x86, Windows7, Windows Vista (this last appears to go to some sort of repair option for Windows7.  Now I want to remove this multiboot so the system will automatically boot into Windows7.  How would I go about this? 

      I have had a quick look on the web and the advice seems to be remove the Ubuntu partition (not sure how I would do this) and insert the install disc for Windows 7 (I do not have a Windows7 install disk.  Ststem came with Windows7 already installed with a backup of the O/S on a partition).  Is there some sort of tool to do this or will I have to get my "hands dirty" and do this (whatever this is) myself ?

System Hewlett packard 
Hard disk 500GB
RAM 3GB
Original O/S  Windows7
Ubuntu installed  following instructions at [http://www.ubuntu.com/](http://www.ubuntu.com/)


I think I have given all information but any more you need just ask.

---

### Post by Quackers on 2011-04-10
Boot into Windows 7 and go to Control Panel > Backup & Restore Centre and in the left pane click on "make a recovery cd". Pop a blank cd in the drive and you will then make what is more commonly called a Windows repair disc.
With this disc you can put Windows back in the mbr of the hard drive (instead of grub2).
Once that's done, and Windows is booting normally, you can boot from the Ubuntu live cd, select "try ubuntu" and load the live desktop. You can then start gparted and delete the Ubuntu partitions if you wish.

---

### Post by cheezsoup on 2011-04-11
Followed your instructions to produce a "repair disk" have also downloaded one from this crowd [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) neither of which seem to do anything beyond telling me to ensure I haven't plugged a camera in and to contact the manufacturer. Would it be possible for you to give step by step (I am a bear of little brain) instructions on how to put Windows7 back into the MBR and remove it from GRUB?

---

### Post by oldfred on 2011-04-12
If you run autorepair 3 times it will probably work. Or use command line and run 
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub

More detail & links to windows sites with even more detail:
oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by cheezsoup on 2011-04-12
> **oldfred said:**
> 
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub



  **YAHOOTIE it works!!!!!**
  Thanks a lot old fred and quackers

I was surprised at how quick the /fixMBR actually works.  When I have an attack of the braves will try deleting the Ubuntu partition (it seems mixed in with the windows one) but as yet it doesn't appear to give any problems and as I do not (probably will not) miss the space shall leave well alone for the foreseeable.  Ubuntu didn't start properly anyway and wife couldn't get on with a (two second) multiboot screen so Ubuntu had to go (install shall still run Ubuntu as a live CD have Ubuntu allready has the drivers for my scanner and printer so apart from the speed hit there is no need to install.

---

### Post by oldfred on 2011-04-12
Glad you got it working.

When I first starting learning Ubuntu, we had XP. I always had to reboot to XP or leave it in XP so my wife could use it. But I then created a shared NTFS partition and put photos, Firefox profile & Thunderbird profile in the shared. Then the main applications were identical in both and I only rebooted for Quicken & Turbotax. I am working on getting off Quicken (I have said that for two years), but I have 20 years of data in Quicken (from DOS even).

---

