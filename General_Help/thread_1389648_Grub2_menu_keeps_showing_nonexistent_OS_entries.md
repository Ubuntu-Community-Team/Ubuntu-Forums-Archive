---
title: "Grub2 menu keeps showing nonexistent OS entries"
date: 2010-01-24
forum: General Help
---

### Post by Objekt on 2010-01-24
When I originally installed Ubuntu 9.10 64 bit, I had the following operating systems already installed:

Kubuntu 9.04
Windows 7
Windows XP

Ubuntu automagically created a GRUB2 menu that offered all of these, plus of course itself, which was fine for a while.

Later on, I deleted and reformatted the partitions that had been dedicated to Kubuntu 9.04.  GRUB2 has failed to keep up.  Despite running "sudo update-grub" multiple times, the GRUB2 menu continues to show entries for Kubuntu 9.04.

How do I get rid of these obsolete entries?  The partitions it was on simply do not exist any longer, so I don't know how GRUB2 is picking it up.

I had already edited my fstab file to reflect the new partitioning scheme, so I don't know where GRUB2 is getting the idea that I still have Kubuntu 9.04 installed.

---

### Post by Thomas Garman on 2010-01-24
Just moments ago I posted a question that is similar, so if either of us gets an answer it would probably be beneficial to others. 

[http://ubuntuforums.org/showthread.php?t=1389652](http://ubuntuforums.org/showthread.php?t=1389652)

---

### Post by Objekt on 2010-01-24
I answered your question, but I still have no idea how to answer mine.

---

### Post by hawthornso23 on 2010-01-24
Don't know the answer either. Just a thought. Have you tried running

```
sudo update-grub2
```

It is supposed to be the same as update-grub for compatibility reasons, but since you updated from Jaunty, depending on how you updated, maybe you still have the old update-grub. If so it'll be updating menu.lst which will have no effect in grub2.

---

### Post by Leppie on 2010-01-24
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by Objekt on 2010-01-24
> **hawthornso23 said:**
> Don't know the answer either. Just a thought. Have you tried running

```
sudo update-grub2
```

It is supposed to be the same as update-grub for compatibility reasons, but since you updated from Jaunty, depending on how you updated, maybe you still have the old update-grub. If so it'll be updating menu.lst which will have no effect in grub2.

No such command.  

I didn't upgrade from Kubuntu 9.04.  Upgrades have never yet worked for me, so I did a fresh 9.10 install.  I had both Kubuntu 9.04 and Ubuntu 9.10 present for a while, but I deleted all the Kubuntu 9.04 partitions & enlarged an existing partition to use the freed space.

I ran the boot info script.  The forum won't let me upload the results file.  Says it is "too big," at 20.5 KB.

OK, I put the "huge" text file into a .zip archive.  Attached.

---

### Post by Objekt on 2010-02-02
Bumpity.  Surely I am not the only one having this problem?  I have "updated" GRUB several times, but it persists in showing entries for non-existent OS's on phantom partitions.

Perhaps this will be cleared up in GRUB2 version 1.98?

---

### Post by oldfred on 2010-02-02
Are you booting thru sda? It looks like the only grub that would work. I just do not know if grub sees the old menu.lst and updates from that or is that the listing you are seeing?

You have both menu.lst and grub.cfg in sdc1? If you are booting with grub2 the menu.lst should not be seen?

Does you grub menu take an extra 20 seconds or so to load?

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
Must know which partition you want to install to, last of several screens:
sudo dpkg-reconfigure grub-pc

---

### Post by Objekt on 2010-02-02
Hm.  Good question.  I may have GRUB remnants in the MBR of sda (a 1 TB SATA drive which formerly housed the Kubuntu 9.04 install).  The Ubuntu 9.10 installation that I'm using now occupies most of sdc.  The only other thing on sdc is an ext3 partition that I use for plain old storage - no boot or other system files present.

Note: there is no "old" menu.lst remaining on sda.  I completely erased the old Kubuntu 9.04 install, and expanded an existing NTFS partition to use the space.

I'm pretty sure I have sda set as the first boot drive in BIOS.  Originally I had just the single 1 TB SATA drive, sda, in the system.  Maybe GRUB2 is getting confused because it goes to sda, finds references to the former installs in the MBR, doesn't find the partitions that should be there, tries sdb etc. until it finally finds the files it needs on sdc?

GRUB2 does take an awfully long time to start up, probably around 30 seconds longer than GRUB did when I had everything on sda.  I thought maybe that was "normal" given GRUB2 is still in beta.  I'll give the linked thread a look.

---

### Post by oldfred on 2010-02-02
If you look at your results.txt the menu.lst is in the same folder as grub.cfg??  that would say either your had both old & new installed and the old grub was not totally removed? I would rename menu.lst. reboot and if it works then delete it or move it somewhere else.

---

### Post by Leppie on 2010-02-02
i think it would be best if you tried re-installing grub2.
even though you did a clean install, in some cases karmic installs with a mix of grub2 and grub-legacy.
to get rid of this mess, make a backup of any grub script you customized and then complete remove grub and install grub2:
```
sudo apt-get purge grub grub-pc gruv-common
sudo rm -rf /boot/grub/
sudo apt-get install grub-pc grub-common
```
after having issued the apt-get install command, dpkg should launch the configuration scripts for grub-pc and grub-common after which your menu should be updated.

---

### Post by Objekt on 2010-02-02
That worked!  I now have correct entries in the GRUB2 menu.

I still have some delays, with several seconds between the end of system devices doing POST and the "GRUB loading..." message appearing.  Then the loading message sticks around for 10 seconds or so before the GRUB menu appears.  I might still need to tinker with GRUB a bit to get rid of the delays.

I did not read the entire linked thread, as it is rather lengthy, but I noticed there was at least one person with the exact same setup as I have: MBR on sda pointing to /boot folder (and accompanying boot-stuff) on sdc.  Apparently, I am lucky to only see a few seconds' delay to the GRUB menu.

---

### Post by Leppie on 2010-02-02
glad it's working now.
grub2 is still a bit buggy, it may just be one of  those things...

---

