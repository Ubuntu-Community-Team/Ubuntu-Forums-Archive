---
title: "Disk Access With Windows 7 inside Virtualbox?"
date: 2009-08-29
forum: General Help
---

### Post by KyranC on 2009-08-29
Hi all! (First post woooo!)
I just bought a new system (specs at the bottom) and I'm excited to be able to do more intensive things than I was previously able to with my weaker laptop. I'm already dual booting on my laptop and I go though periods of favoring either Xp or Ubuntu. The thing that keeps me stuck with Windows is the audio applications, such as Pro Tools, Fl Studio, Traktor, and my new favorite, Reaper, as well as Photoshop (GIMP doesn't quite cut it for me). 

I've read up on virtualization and have tried a microXP virtual machine in Virtualbox on my laptop with some success. Now I'm faced with partitioning my new hard drives, migrating my files, and deciding on what my future configuration will be. 

Ideally, I'd like to boot into Ubuntu, installed on the SSD, and run a Windows 7/XP virtual machine, also located on the SSD. I'd like both OSes to have access to the 2 TB data drive and be able to share the files. This would mostly be audio, either being streamed through iTunes/Rhythmbox or being used in an audio application. I'm guessing Ubuntu's NTFS support is better than Window's Linux support?

My question is this: Is it possible/feasible to have one partition on the data drive being read by the host and guest operating system at the same time while maintaining stability? How should I go about partitioning and mounting it?

I'm sure I have more questions but I can't think of them right now.

Thanks in advance for any help!

ps Go easy, I'm a nub :P

System specs:
Intel Core i7 920 2.67 Ghz quad core processor
6 gigs Mushkin 1600 Mhz RAM
80 GB Intel SSD
2 TB HDD
Radeon HD 4800 Graphics

---

### Post by SoftwareExplorer on 2009-08-29
Ok, when you have a virtual machine, it will have a 'hard drive' that is actually a file. The problem is that this file really isn't very easy to access without starting the virtual machine. So if you want to share stuff between a windows system in virtualbox and Ubuntu on the real hard disk, why not just make a shared folder on ubuntu? That way, windows will be able to see the files and so will ubuntu. Whenever Windows is running, ubuntu will be also, so windows will always have access to the files. And ubuntu would have access to the shared files weather or not windows is running. By the way, the filesystem of network shares doesn't matter. If you don't know how to share files on ubuntu, just ask, it isn't hard at all.

---

### Post by earthpigg on 2009-08-29
> why not just make a shared folder on ubuntu?

kinda sorta. what i would do:

1. not use the open source edition (OSE) of VirtualBox. download the ubuntu .deb for the closed source version from [http://www.virtualbox.org/](http://www.virtualbox.org/) .... first, uninstall vbox OSE, then restart, then install vbox closed, then restart again. i know restarting is non-linuxey, but vbox includes kernel modules that are normally only loaded at boot.

2. install xp as a vbox guest machine.

3. install 'guest additions' into the XP guest. with  devices -> install guest additions. a "CD" will appear in the XP guest machine as if it where just inserted. install its software.

4. shut down guest machine. in the vbox gui for that guest machine, designate a folder in your host machine as shared. security concern: whatever folder you designate will be vulnerable to windows messing up. meaning, a virus on the guest machine could corrupt anything in the designated shared folder. it sounds like what you want is to share your ubuntu home folder with windows, but be aware that everything in your home folder is no susceptable to Windows doing whatever it is that Windows does.

5. start your windows guest machine again. verify that everything worked.

---

### Post by KyranC on 2009-08-29
Duh of course it's that easy! My brain was still in Dual boot mode #-o
So I could install Intrepid, create the VM and mount my NTFS data drive in Ubuntu, then select it as a shared drive in Virtual box, correct? Would the VM file benefit from being located on my SSD? Should that be formatted as ext3? (Or ext4 even?)

Thank you for clarifying! :P

---

### Post by SoftwareExplorer on 2009-08-29
> **KyranC said:**
> Duh of course it's that easy! My brain was still in Dual boot mode #-o
So I could install Intrepid, create the VM and mount my NTFS data drive in Ubuntu, then select it as a shared drive in Virtual box, correct? Yes. > **KyranC said:**
> Would the VM file benefit from being located on my SSD? Should that be formatted as ext3? (Or ext4 even?)

Thank you for clarifying! :P
Maybe, not sure thought. The filesystem is up to you, but it shouldn't matter as long as ubuntu can read it.

---

