---
title: "Grub/BIOS Interfering with Vista Install DVD?"
date: 2010-04-15
forum: General Help
---

### Post by itendo on 2010-04-15
I know this is a bizarre place to be posting about installing Vista, but i think the culprit may be some bizarro GRUB fallout. for reference to [COLOR="Navy"]how i finally restored GRUB see here [http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)[/COLOR] .

I recently got my computer back into a workable state after almost a month of work and fail. Originally I was dual booting Vista & Ubuntu, then after a platter went bad across both partitions. i basically had to go back to scratch ([you can find out more deets here]("http://forums.techguy.org/linux-unix/914870-solved-grub-mbr-help-needed.html")). Anyway, I have Ubuntu 9.10 installed and it is running fine, once it boots. 

my rig is a homebrew with an i7 920, intel dx58so mobo, 2x2g DDR3 ram, 850W Thermaltake, ATI 4870

I am facing two primary problems. A) my BIOS post time has gone from 3 to about 15-20 seconds, and OS boot from GRUB menu went from about 8 to 30 seconds.* B) [COLOR="darkred"]i am running into an error trying to install vista from my OEM DVD (Home Premium 64-bit); it gets to the green (kernel) loading bar part of the menu, then hangs indefinitely (for at least 25 minutes). i thought this may have to do with bios and an ide/ahci/sata driver loading issue but in ide mode it still isnt responding. (this disk is clean, and i have used it three times previously to reinstall.)[/COLOR]

[COLOR="DimGray"]A) i am considering updating my BIOS (which has been updated quite a few times over the past 15 months) to see if that will resolve/reset the problem. however, i am doubtful that it will and fearful that it will only cause more problems. however, could it be a physical problem with the board? i did a complete teardown and rebuild and nothing seemed to be out of order but i wouldnt have known what to check other than big problems.

B) i would hope that updating the BIOS might purge whatever difficulty the Vista DVD is having with my system and loading it. does anyone know what else may contribute to the green bar not loading? there seems to be no explanation for why it hangs there at the green loading bar in this situation. or at least i havent been able to find a similar situation. among the fixes, was the purchase of a brand new HDD (WD 1T Caviar Black) and it wouldnt install in a basic config with just the HDD and a stick of ram.[/COLOR]

*UPDATE

After a Successful flash procedure, and then an unsuccessful reboot, I flipped BIOS Jumper to config, got into BIOS and it appeared to be a false warning and the BIOS booted in config correctly, i made a few adjustments to fit my machine. Flipped the jumper back to normal, restarted, presto GRUB2 is back.

In summary i flashed to the latest BIOS revision (5112) and the boot to Post seems to have lessened somewhat, but the OS boot time is still pretty awful. Minor concerns, but it seems to be pointing at something that i think is causing my main problem:

[COLOR="DarkRed"]What is happening that makes it so, when i insert the Vista DVD, it hangs at the green bar loading screen and it wont let me install the OS? Do i just need to check that /one/ setting i didnt think of or am misconfiguring? Am i having a driver conflict with Recognizing the HDDs, a permissions problem since I am running GRUB2 and it wont let me own the hard drive, a problem with the SATA drivers and my DVD Drive?[/COLOR]

Please Help.

---

### Post by Mark Phelps on 2010-04-15
Noticed your sig line mentions two 1TB drives -- so, are you running a RAID config?

In terms of the Vista install, are you attempting to install it to free space, or have you already formatted a partition (NTFS) -- and if the second is true, did you use Gparted to do that format?

I'm asking the last question because when I first installed Vista some years back, I had formatted a partition (NTFS) with Partition Magic -- and Vista didn't like it. I had to end up removing the partition and letting Vista do its own formatting.

---

### Post by itendo on 2010-04-16
thanks!

the hdds are not in raid, they are just hanging out. also, i have unformatted space available for the vista partition (both formatted unformatted, and unallocated). it may be worth it to try wiping one of the hard drives first from grub and then doing doing a zero erase to see if having just it (and no other grubbed drives) installed will allow me some leverage.

time to migrate my 200 gigs of media again to free up that hdd. fortunately this hdd was what i installed vista on when i first (and every subsequent time)built the system so it should work again. i wish there was an icon for a hopeful hmmm.

---

### Post by itendo on 2010-04-19
update. effectively solved, but not really, and definitely not tidily:

a) used seatools to perform a full erase of the seagate drive (took about 3 hours). 
b*) unplugged seagate, tried to run memtest from WD only boot and got an error "too small lower memory ([x] > [y])"
c) unplugged the WD drive
d) booted vista installer dvd, works; running updates on windows.

I am not sure why the full erase worked, aside from that it would have erased the mbr/grub record. so i think this was a grub issue all along. [COLOR="DarkRed"]i have no explanation for why this fixed it, but now i am facing a new problem.[/COLOR]

because of the heavy-handedness of this solution, my drives currently exist only independent of each other. however, i want access to both drives and the ability to dual boot. my fears: in all likelihood, if the drives were to boot together a) there would be a conflict, or b) one mbr/boot loader would try to overwrite the other. so i will choose the windows boot loader for the sake simplicity (and windows boot loader being a finicky punk that cant update itself!). any suggestions on how to reconcile this problem from where it stands now? 

essentially, i need to rewrite the mbr on the WD drive to match up with the Seagate mbr. i am afraid of just booting two boot-loaders without knowing which will take precedence (and risk grub winning and my inherited grub menu becoming 3pgs long). if anybody knows of a good bootable tool i would appreciate it. 

the apparent best option to me: its ubuntu and is completely up and going in less than an hour, so i can just migrate my mp3s etc some other way and then reinstall. i dont know whats broken about my current config. I dont want to run into any further problems after i get Vista squared away. So I think this might be my best option considering i dont have much invested in the ubu install, and [COLOR="Blue"][i am unsure what my original GRUB install method did to render the problem in the first place]("http://grub.enbug.org/Grub2LiveCdInstallGuide").[/COLOR] 

[COLOR="Green"]Any feedback would be appreciated, or just a +1 encouragement![/COLOR]

---

### Post by srs5694 on 2010-04-19
First, some basics:

A Master Boot Record (MBR) is the first sector on a hard disk. On most x86 and x86-64 PCs, a disk's MBR holds two things: a boot loader (LILO, GRUB, the Windows boot loader, etc.) and the primary partition table. MBRs are static data structures, although the boot loader code is software. If you've got two disks, the MBRs don't need to be (and aren't normally) synchronized in any way, nor do they work together (except to the extent that the OS reads both MBR partition tables and uses them both to decide what filesystems to read). Only one MBR boot loader will be used by the BIOS, but some boot loaders (such as LILO and GRUB) can redirect the boot process to another MBR.

In a dual-boot configuration, you must decide which boot loader will be the primary boot loader -- that is, the one that's installed to the MBR of the boot disk. (BIOS settings determine which disk is the boot disk.) In a Windows/Linux dual-boot configuration, you can do one of two things (or more if you use a third-party boot loader, which I won't describe):


[list]
[*]Put the Windows boot loader in the MBR and store GRUB in the boot sector of a Linux partition. The Linux partition must then be a primary partition on the first disk that's marked as active in the MBR's partition table.
[*]Put GRUB in the MBR. The active partition marking in the partition table then becomes irrelevant, and Linux can reside on either physical disk.
[/list]


If you install Linux first and Windows second, you'll end up with the Windows boot loader in the MBR, since Windows puts its boot loader in the MBR whether you want it to do so or not. Most Linux distributions give you a choice about where to put GRUB. If you install Linux first and put GRUB in the MBR, Windows will overwrite GRUB and you'll be unable to boot Linux. If you install Linux second, then GRUB might or might not overwrite the Windows boot loader in the MBR, depending on the options you pick.

---

### Post by itendo on 2010-04-20
Thanks for the rundown. So if i have two hard disks, each with an OS installed while the other disk did not exist, and have only been run independently of each other (one or the other unplugged); what would happen if i boot both plugged in? would an automated recovery/write happen or would it just boot whichever hdd is set to first in boot order? (best guess is fine) 

Also, any recommendation on where to read up on how to "Put the Windows boot loader in the MBR and store GRUB in the boot sector of a Linux partition" ?

---

### Post by oldfred on 2010-04-20
With two MBR's I would just keep window in the windows hard drive and grub in the MBR of the UBuntu drive. You then in BIOS set the Ubuntu drive as the primary master (old IDE term) or SATA boot drive. With a sudo update-grub your grub will find your windows install and add it to its menu to let you boot it. If you ever have problems you can use f12(or single boot key) to boot your windows directly or change boot order in BIOS to boot windows.

There was a minor bug in grub 1.97 that if it was not on the same drive as the Ubuntu install it took 20-30 sec longer to load. One more reason to have grub on the same drive.

---

### Post by itendo on 2010-04-20
sounds good, i will probably run the update tomorrow once i am sure the vista install is updated correctly and humming along. i am very ready to mark this [solved]...

---

