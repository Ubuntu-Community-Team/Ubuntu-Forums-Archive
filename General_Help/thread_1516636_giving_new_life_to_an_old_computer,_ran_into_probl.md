---
title: "giving new life to an old computer, ran into problems"
date: 2010-06-24
forum: General Help
---

### Post by Messyhair42 on 2010-06-24
I'm installing Lucid onto an old computer (AMD K6, 200 MB ram 4 GB + 40 GB HD) to give it new life to give it to family member. i had to use the alternate CD to install b/c the memory was too low to use the standard. I tried to boot it after installation and no BIOS configuration I know of will boot it. BIOS options are IDE/SCSI and boot order (A,C,CDROM,D,E,LAN). I installed to the 40 GB drive using guided partitioning and from the boot screen i believe it is the Primary Slave. now i did not personally finish the installation so i didn't view the GRUB installation. I was able to boot it from a Knoppix ver 6 disk to look at the hard drive layout but i couldn't view partitions and didnt know terminal commands to pull up HD information. any help would be appriciated

---

### Post by MedianMajik on 2010-06-24
One big problem you have right now is with memory.  200mb is under the requirements for standard Ubuntu, which uses Gnome to create the user interface (it asks for 512mb or more).  It is for this reason that [Xubuntu]("http://www.xubuntu.org/") is around for pcs with about 192mb ram (there are many other even lighter distributions you can use).  Check out the [Wiki entry]("https://help.ubuntu.com/community/Installation/LowMemorySystems") and keep something like Knoppix, Puppy, or Damn Small Linux handy.

---

### Post by nexes128 on 2010-06-24
Does the system at least try a boot (do you see the ubuntu boot logo). Where 200mb may be under the min req's I have had systems boot full ubuntu install with 128 (very long and slow but it worked)

---

### Post by Messyhair42 on 2010-06-25
so i was able to reinstall xubuntu 10.04 on the system but i still can't get it to boot. i went back to configuring the BIOS but no avail. i was using Knoppix again to look at the new OS but i'm unfamilar with the changes to the boot structure on 10.04.

---

### Post by Helios747 on 2010-06-25
xubuntu might be too much for that computer.

you might want to try Crunchbang (based off of ubuntu 9.04)

or Puppy Linux.

---

### Post by Messyhair42 on 2010-06-25
the distro is not what i'm concerned about atm, its getting some sort of reaction out of the OS.

---

### Post by rollin on 2010-06-25
Hey messy, I recently had some  issues trying to get an old system to work with 10.04. Only got it fixed when some genius advised the OS graphics driver had changed in 10.04 from the version in 9.10 down.

Obviously I'm not sure if this is the same issue for you but everything worked ok for me on the old box when I ran a live cd 9.10 and installation.

Take a look at the thread if you want: [http://ubuntuforums.org/showthread.php?t=1514491](http://ubuntuforums.org/showthread.php?t=1514491)
based on this I'd recommend trying a live 9.10 cd as it worked for me with the older OS driver installed. Good luck m8.

---

### Post by burton247 on 2010-06-25
On my old laptop I had loads of trouble getting OS's to boot. Just had to try a few before one would work.

+1 to crunchbang as it runs openbox

You could try the minimal ubuntu install or debian. If they don't boot try another OS. If they do install something like openbox or similar. If you dont wna config it go lxde.

Oh course you could go all the way and do an arch install, if you can't get that to boot I'll be surprised

---

