---
title: "Gave up waiting for root device...drops to BusyBox"
date: 2010-05-04
forum: General Help
---

### Post by Solrac924 on 2010-05-04
Please help.

have had Hardy Heron for the last 2 years & loved it. recently attempted to upgrade to Lucid Lynx but it's not booting up. it just shows "Gave up waiting for root device" and drops to BusyBox. waiting doesn't do anything. 

i see the GRUB options but none of the 3 10.04 LTS's boot up. i've read a number of threads but i don't think my Ubuntu drive is being read. i say this 'cause cat/proc/partitions doesn't list my Ubuntu drive/partition. Also when booting up in the Live CD, GParted only lists the Windows partition. neither does sudo fdisk -l.

have been fiddling with this since the weekend and have run out of things to try. Please help.

---

### Post by P4man on 2010-05-04
If you upgraded from Ext2/3 to Ext4, then you have to manually update grub (see release notes). Im guessing thats whats happening here, grub (1, legacy) is unable to read your ext4 / or /boot partition?

---

### Post by Solrac924 on 2010-05-04
thanks. don't mean to sound like a noob, but how do i go about doing this?

should i boot into the live CD & enter grub-install in the terminal?

---

### Post by P4man on 2010-05-04
Can you verify you have grub legacy (0.97 or something, and not 1.97) ? It should show it in the grub menu if that is still loading.

If that is indeed the case, boot a livecd with ubuntu 9.10 or 10.04 and follow these instructions (option 2):
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Dont forgot to replace /dev/sda7 with your actual drive.

---

### Post by WorMzy on 2010-05-04
It could be a problem with dmraid. Next time you boot the Live CD, try enabling nodmraid in the options (this is before it asks whether you want to try or install). I think you need to press F7 or something to enable advanced options.

After you've booted with nodmraid, see if you can now see your partitions.

---

### Post by Solrac924 on 2010-05-04
@P4man: i haven't checked out my GRUB version yet. 

as for replacing sda with my drive, i don't know my drive#. i don't even think my computer knows what it is either. it can't be seen. it's not picking it up.

@WorMzy: i think you may be on the right track. i just don't see where i have an opportunity to hit F7. the Lucid Lynx live CD is the first i've seen not to have those options.

i do appreciate the help. what else can i try?

---

### Post by WorMzy on 2010-05-04
I've had the same problem involving the Live CD, it doesn't always give you the option to change the boot options. I've found the best way to ensure that you get the option is to press up and down keys alternatively as soon as your PC starts booting the CD and the screen turns purple. You have to press F6 for boot options though, not F7, I've just checked. :)

---

### Post by Solrac924 on 2010-05-06
hey thanks. yeah, i now see the classic options & F6 DID show nodmraid. when i continued to boot the Live CD, i tried seeing all partitions again with *sudo fdisk -l* to no avail. 

i didn't change anything in the BIOS. i hope i hard drive didn't give out. what else could it be?

---

### Post by Solrac924 on 2010-05-07
ok, seriously, $20 to whoever can solve this for me.

---

### Post by P4man on 2010-05-08
Does the bios still recognize the hdd? Did you boot the livecd with nodmraid? I think you are looking at a hardware issue... alternatively you could try installing testdisk from the ivecd and run it, see it picks anything up.

---

### Post by Solrac924 on 2010-05-08
yes, the BIOS recognizes the HDD. does that mean it's OK after all?

yes, i did boot the live CD with nodmraid but it still doesn't pick up the drive.

i really hope it's not a hardware issue and that the HDD didn't go out. it's hard to accept that it was working fine right before the Ubuntu update.

i've tried running testdisk but it shows it has to be installed. one can't install it when only running a liveCD, right?

---

### Post by P4man on 2010-05-08
No you can install it from the livecd, no problem (if its a cd, then it will just not be installed anymore next time you boot it, it will "install" to ram).

As for the drive, seems unlikely its a hardware issue that crops up just during the upgrade, but i wouldnt rule it out. You may check the drive health from system > adminstration > disk utility provided its seen there.

---

### Post by MarkFromNJ on 2010-07-06
I have an Acer Aspire 1810TZ that is exhibiting the same problem, "gave up waiting for root device". I tried to delete the uuid line in grub (suggestion from another post), no success. I tried to boot into the recovery mode - also did not work. My Grub version is 1.98 so it's not a Grub v1 problem. As the last guy said, it just can't see the drive.

I can boot into Windows fine so the drive itself is readable. 

When I booted Linux in recovery mode, it found the SATA devices - all 7 of them (sda1-sda7) but then it complained about not being able to access an ATA device after doing some ACPI stuff. I am not sure why it wants ATA as the drive is SATA and this machine has no ATA controller. I don't have the exact message (sorry.... noob mistake) but is seemed to read the drive, then try to either reset it or apply something to do with ACPI and at that point it failed with an ATA error.

I tried rebooting from USB, deleting the Linux partitions, and re-creating and formatting them, and then re-installing. Same issue.

The only hint is that when I rebooted windows the first time it complained that its NTFS partition was not clean. But after the second Linux install which also didnt work, Windows (7) booted without complaint. Not sure if that is coincidence or not as I may have forced windows to shut down, but I don't think so.

Any help would sure be appreciated, thanks
Mark

---

### Post by likes2skate on 2011-05-26
Earlier this week, I encountered this problem on my file server, which was running nfs and samba. 

When I first encountered the problem, I assumed that my (old) hardware was to blame.  

To solve the problem, I was trying to set up a new file server.  I am on on Lucid 10.04, and I was trying that.  So I swapped everything -- hard drive, motherboard, memory, and even display card.  

This week, I must have gone through 20 server installs.  The problem was coming back every time.

So I even went back to 8.04.  But the problem came back when I installed nfs-kernel-server and did aptitude safe-upgrade.

I think nfs-kernel-server is causing the problem.  

I now have my file server working by NOT INSTALLING nfs-kernel-server, and not doing aptitude safe-upgrade.  

I am accessing the file server from my kubuntu workstation using mount -t cifs.

This week, I have spent a lot of time on this, and I finally have a working file server.  I will not do aptitude safe-upgrade until I have enough spare time to deal with a ruined file server -- by starting over if need be.  I do not think aptitude safe-upgrade will ruin my file server, but I do not want to chance it right now -- I spent way too much time on this!!!!

But at least my file server is now working.

I hope my solution helps someone.

---

