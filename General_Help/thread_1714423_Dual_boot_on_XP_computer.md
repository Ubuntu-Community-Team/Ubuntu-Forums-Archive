---
title: "Dual boot on XP computer"
date: 2011-03-25
forum: General Help
---

### Post by tc101 on 2011-03-25
I have an XP computer that I use for work.  I would like to install ubuntu on it so I could dual boot to XP or ubuntu.  Is this easy to do?  It is very important that I don't mess up anything in the XP installation.

---

### Post by .:PiXi²:. on 2011-03-25
You can do this using the Wubi installer.
Check [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")

---

### Post by oldfred on 2011-03-25
If it is a work computer that you should not mess with, I would consider an external drive. Even then you have to be careful to use manual install so you get the option on where to install the grub boot loader to. It likes to default to sda which is usually the internal drive. 

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Will the computer boot an external USB drive? If older and XP it may be too old to boot USB drives.

---

### Post by tc101 on 2011-11-22
I am surprised no one pointed me at this simple solution when I asked the original question:

Windows Dual Boot -  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Is there any problem with doing it that way?

---

### Post by garyed on 2011-11-22
You shouldn't have any problems but there's always a possibility something can go wrong. As long as you're prepared then go for it, its rather simple. I would recommend first to delete the windows paging file & then do a disk defragmentation under Windows before installing Ubuntu. I can't remember if XP can shrink the partition like Windows 7 can but Windows likes to spread files out all over the whole disk. You can always put the paging file back later.

---

### Post by tc101 on 2011-11-22
Thanks for the info.

---

### Post by Mark Phelps on 2011-11-23
Windows XP does not have the Disk Management utility that allows you to resize partitions.

But since you're going to dual-boot, I would recommend the following:
1) Download Partition Wizard, the ISO image file, and burn it to CD
2) Boot from the CD and use it to shrink your XP partition to make some room
3) Boot back into XP, download and install the FREE version of Macrium Reflect.  Connect an external drive and image off XP to the drive. Use the option to create and burn a Linux Boot CD

Now, you have a way to restore your XP install in just a few minutes -- in case something goes terribly wrong during the dual boot setup.

---

### Post by mastablasta on 2011-11-23
> **Mark Phelps said:**
> Windows XP does not have the Disk Management utility that allows you to resize partitions.

 
 
yes it does - it's called Windows disk manager. [http://support.microsoft.com/kb/309000](http://support.microsoft.com/kb/309000)
Edit: or disk management or whatever more here on GUI interface: [http://www.theeldergeek.com/disk_management.htm](http://www.theeldergeek.com/disk_management.htm)
 
A simple version (or is that fdisk) is also found on windows install CD
 
one can also use gparted (provided on ubuntu CD) but you need to defragment the disk a couple of times and run a check disk (chkdsk) afterwards just to be sure.

---

### Post by underquark on 2011-11-23
Sooner or later your Windows machine will crash/break (and not just because it's running Windows) and your company IT guys will blame you for installing ubuntu.  Why not create a boot USB stick (choose from ubuntu, Puppy, DSL or many fine 'nix's) and, effectively, take your own little OS with you to use on whatever machine you're sitting at?  You can still store files on your hard drive but no programs, OS or other code that can get blamed if anything goes wrong with the machine.

---

### Post by tc101 on 2011-11-23
> Sooner or later your Windows machine will crash/break (and not just because it's running Windows) and your company IT guys will blame you

Good point.  I should have mentioned that my relationship to the company has changed since I made the OP in March.  I am not working for them now.  They let me keep the computer.  It is possible that I work for them again some time in the future and I would like to keep the current XP set up, but it is not nearly as important as it was back in March.

---

### Post by Mark Phelps on 2011-11-23
> **tc101 said:**
> ...It is possible that I work for them again some time in the future and I would like to keep the current XP set up ...

Then do the Macrium Reflect and imaging stuff I mentioned.  This will allow you to restore the current XP state if you need to reset it back to this later.

---

### Post by tc101 on 2011-11-23
Sounds good.  Thanks.

---

### Post by tc101 on 2011-11-23
One other related question.  Is there any  possibility that any malware from the original XP could have any effect when I do my initial boot into Ubuntu?

---

