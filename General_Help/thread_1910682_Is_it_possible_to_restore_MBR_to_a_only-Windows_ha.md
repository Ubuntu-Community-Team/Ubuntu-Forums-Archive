---
title: "Is it possible to restore MBR to a only-Windows hard disk using Ubuntu?"
date: 2012-01-17
forum: General Help
---

### Post by Sopalajo de Arrierez on 2012-01-17
Hi, friends.
	I have a computer with Windows XP installed, and, at Boot sequence, I get "Disk Boot Failure. Insert boot disk and press Enter" message :-(.
	Of course I can repair this using classic Windows XP Installation CD, but I would like to repair it using Ubuntu to learn the method (you know: "Don't learn to hack, hack to learn ;-)" ), and, in extension, to log remotely (via SSH or telnet) into the computer, so all fixings can be done without my presence.

	I have tested "ms-sys", but it seems not to be working :-(, even when it says "changes done" and all that stuff: my HD keeps at "Disk Boot Failure" state.
	I have found somewhere about package "mbr", but Ubuntu 11.10 seems not having it.
	Yes, I can use Super Grub Disk to fix MBR and GRUB, I do know, but, if possible, I prefer Ubuntu.

	Do you have any ideas, please?

	Thanks a lot.

---

### Post by Mark Phelps on 2012-01-17
I believe you can use Boot-Repair to do that (see below) but know of no way you can do this remotely:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Sopalajo de Arrierez on 2012-01-19
> **Mark Phelps said:**
> I believe you can use Boot-Repair to do that (see below) but know of no way you can do this remotely:


   Mmm... yes, this could do the trick.
   No problem about remotely management. Linux solves this easily using VNC4Server or TightVNC.

   Thanks, Mark Phelps ;-)

---

### Post by oldfred on 2012-01-20
Windows has a two step boot process. The MBR just looks for the active partition (boot flag) and jumps to the partition (PBR) with the boot flag. The active partition must be a primary NTFS partition with the boot loader and some info on partition size/location in the PBR. Scan of PBR will show bootmgr or ntldr depending on version of Windows. Often a resize of Windows will cause it to want to run chkdsk and part of chkdsk resets the partition info in the PBR.

You can use the lilo boot loader from Linux repairCDs or download it into Ubuntu. Lilo works just like Windows in jumping to a PBR, but will also boot from a logical and non-NTFS partition also.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by Sopalajo de Arrierez on 2012-01-20
> **oldfred said:**
> 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

   Mmm... this could be worth, too.
   But, if I do this LILO installation, will LILO Boot Loader became installed in my hard disk? I don't want this results.
   Or may I just use the "lilo -M" capability?

---

### Post by oldfred on 2012-01-20
You only get the part of Lilo that is in the MBR, you actually do not want the rest of lilo.

Similar discussion in this thread.

[http://ubuntuforums.org/showthread.php?t=1911968](http://ubuntuforums.org/showthread.php?t=1911968)

---

