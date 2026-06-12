---
title: "OS Ramdisk"
date: 2010-07-23
forum: General Help
---

### Post by battery360 on 2010-07-23
I'd like to set up an OS ramdisk (8gb) with a script that loads and saves to ram from a solid state drive on start up and shut down. I'm not sure how to approach this, but I've heard it's been done before. Any help or advice would be appreciated. ;)

---

### Post by Zeike on 2010-07-23
It sounds like what you're asking it how to create a swap partition.  The "script" you're asking for already exists.  Its called hibernate.

To create a swap partition just open up gparted, shrink existing partitions if you need to, and add a new swap partition.  You'll have to add it to your /etc/fstab.  Make sure you make it as big or bigger than your RAM.  Then just select hibernate from the power menu and your RAM will be saved to the swap partition and your machine will be powered off.

---

### Post by battery360 on 2010-07-25
I'd like not only the swap, but also the boot partition to be on ram.

The script I'm planning on making would involve creating a ramdisk, copying a partition (or partitions) from a ssd to the ramdisk(s), and then booting off that. I was actually hoping to get Windows Server 2008 running off a ramdisk. On shutdown the ramdisk would overwrite the partition on the ssd.

---

### Post by egalvan on 2010-07-25
> **battery360 said:**
> I'd like not only the **swap**, but also the **boot partition** to be on ram.

What, exactly, are you trying to accomplish?

Do you have a problem that needs fixing?


Especially under *nix, having the swap partition in RAM is aself-defeating, vicious circle with no end.

swap in RAM uses RAM, causing it to run low faster
swap is used when RAM runs low...


Be aware that *nix has always been light-years ahead of Microsoft in RAM utilization (as Microsoft incorporated more and more FOSS memory-handling code into Windows, this gap has lessened)
It doesn't really need RAM disks, which is why they are so rarely used.
Let it do it's thing.


The /boot partition code is almost exclusively used to boot *nix.
What exactly is the need to keep it in RAM?


All that said, there ARE some tricks that use RAM disks...

if a lot of logging is happening, placing /log in RAM can speed up a disk-bound server.

placing /temp in RAM is another trick that is at times used.

there are other dedicated partitions that can be RAM-bound, such as C-compiler intermediary files...


So to return to my original question...

What exactly are you trying to accomplish?

---

### Post by battery360 on 2010-07-25
> **egalvan said:**
> What exactly are you trying to accomplish?
I'm more trying to satisfy my curiosity regarding ramdisks. I'd like to run windows server 2008 off ram and see how programs respond in that sort of environment, maybe try a few games off it.

---

### Post by egalvan on 2010-07-25
> **battery360 said:**
> I'm more trying to** satisfy my curiosity** regarding ramdisks. I'd like to run windows server 2008 off ram and see how programs respond in that sort of environment, maybe try a few games off it.

Ahhh!
 Curiosity! 
The worst of the worst!
 There is no cure!
Once down that road you start, forever will it dominate your destiny!
Next thing you know, you will be giving kernel advice to Linus himself!


Seriously, that is a most excellent reason.

You will be running Windows in a Virtual Machine, I take it?
Sadly, I have no experience in this area.

You will be running Windows in native mode?
Then Windows RAM disks will have to do.

Sorry I can't be of more use...at the moment... from time to time.

---

### Post by battery360 on 2010-07-25
I'd be going for a native install.
Could I just install windows server '08 onto the ssd on an 8gb partition, use grub to make a startup script that creates an 8gb partition in the ram, copies the 8gb partition on the ssd to the partition in the ram, and boots off it?

---

### Post by egalvan on 2010-07-25
> **battery360 said:**
> a native install.
Could I just** install windows server '08 onto the ssd** on an 8gb partition,
 use grub to make a startup script that creates an 8gb partition in the ram,
** copies the 8gb partition on the ssd to the partition in the ram, and boots off it?**

Sorry for the delay... I was off having a rare moment of fun for myself... ;)

I'm not at all familiar with Windows Server... 
I stopped supporting MS at WinXP, so take heed...

Windows did not (does not?) like being installed on anything other than the first bootable partition on the first bootable drive.
It **is** possible to install and boot from other partitions, but it's a hassle.

Second, during the installation process, 
the MS installer hard-codes way-too-many drive references ( such as C:/, C:/Douments and Settings) into the installation code.

If you install Windows on one drive, then shift it to another drive, these hard-coded references will become invalid.

So it's not just a question of getting GRUB to boot the system
 (GRUB2 will boot from just about anything, and will boot just about any OS out there)...
but you have to take into account the changed drive references.
I have no idea how to do that, and (sorry) I have no desire to learn MS stuff any further.

N.B. it's *mayhaps possible* that using the MS equivalent of a sym-link can help...

Heck, virtualization does wonders with this stuff...
That may be the better road to take.
I've read (apocryphal) reports of Windows running faster and more stable as a VM on a Linux host, than on native iron.

And may I assume that your machine has more than 8GB of RAM?

---

### Post by battery360 on 2010-07-26
Hmm.. Would it be possible to make grub make the ramdisk, then boot from the install dvd? Would the ramdisk be detected by the installer or would the ws2008 install dvd just obliterate it? 

I wasn't aware that the installer hardcoded drive references. I've got an archaic p3 running xp downstairs and, due to a mistake during rewiring, my OS drive is now F:\ - and I've had no issues with it.

If there is a problem with the references they'd only be broken, the first run after the install. I've pulled an os drive out of a system (win7), stuck it into an enclosure and booted of it a while ago.. I'm pretty sure some repairing was needed but it worked. 

It's hard to imagine any modern os running faster as a vm, but my system will be a quad quad core (4 x Operon 8356), so.. 
My machine has- *will have* 16gb of ram. It's still under construction, just waiting for a few more parts.

Oh and thanks for the info and your interest!
My knowledge on how to create ramdisks and copy entire partitions is um.. thin. Very thin. Any help with the creation of something that resembles a script would be very much appreciated!

---

