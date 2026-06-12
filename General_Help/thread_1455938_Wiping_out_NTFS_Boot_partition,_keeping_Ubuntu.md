---
title: "Wiping out NTFS Boot partition, keeping Ubuntu"
date: 2010-04-16
forum: General Help
---

### Post by geudrik on 2010-04-16
I think I know the answer to this question, but it never hurts to ask..

I have a 500gig drive, with 60 allocated to Ubuntu (I had Vista on there previously, and have been dual-booting for a while now)

I'm ready to format the drive, as I care not for anything on there.  The file:
```
grldr
```
is the Grub Boot Loader, I know.  

My question is: Can I format the drive (partition: dev/sda1) making sure to save the grldr file.  After format completes (going from NTFS to ext3) can I simply throw the Boot flag back onto the drive, and merely copy the GRUB loader back to the partition?

---

### Post by colorlessprism on 2010-04-16
are you wanting to reformat the entire drive to reinstall linux? if so then you should not have to worry about grub since the new install will take care of it. if you are wanting to reformat the vista space to ext3 you could use gparted and format the partition and if ubuntu does not automount the partition you could edit fstab and add it there.

---

### Post by geudrik on 2010-04-16
I only want to wipe out the NTFS partition.  I have Gparted installed in Ubuntu, and it won't let me wipe the partition (even with NFTSprogs) - so, I was going to do it manually...

Copy the grub loader to my Ubuntu Desktop
Then reformat in EXT3 (acronis disk director [Highly reccommend this software])
Then, set bootflag back to SDA1 and copy the grub loader back to the partition.

I'll include a screenshot of how my disks are now to make it more clear. I can't afford the time invested into this install to start from scratch >.< Takes too damn long :P  [Eye Candy - Woo!]

Just to make sure I make my self clear:
* Do not want to start over
* Want to blow out 400gig NTFS partition, turning it into EXT3
* Current NTFS partition is /dev/sda1
* Current NTFS partition has boot flag set, and grldr

Want to:
* Keep existing file structure, and current Ubuntu install intact /dev/sda2 [  /dev/sda5(Root) /dev/sda6(swap)  ]
* Maybe just expand my primary partition to absorb the NTFS partition?

So what should I do? :P



Edit: After I unmount, I can format to Ext3 - If I commit this change, will grub still be available, or, can I just recopy it back (the binary file: grldr) after setting the newly formatted 400g Ext3 partition with a Boot flag?

---

### Post by srs5694 on 2010-04-16
I'm not entirely sure what that grldr file is, but I think it's unlikely that it's GRUB from the Ubuntu installation. AFAIK, Ubuntu puts all the important GRUB files in the /boot/grub directory in Linux, although there are also parts that are installed in the MBR and possibly in a few unallocated sectors immediately following the MBR. GRUB can also reference files elsewhere -- most notably kernel files in /boot. AFAIK, neither Ubuntu nor the version of GRUB that it uses puts any files in your Windows partition.

It's conceivable that the file is installed by a variant of GRUB designed explicitly for Windows. A Web search suggests it may be related to the [GRUB4DOS/WINGRUB project,](http://sourceforge.net/projects/grub4dos/) for instance. That same Web search suggests that a file of this name is included in some pirated versions of Windows, but I don't know if these versions use GRUB4DOS/WINGRUB or if this is a coincidental name overlap. With this information, you may have a better idea of what's going on than I do; if you recall installing GRUB4DOS/WINGRUB *after* installing Ubuntu, the grldr file might be important. OTOH, if you installed Ubuntu after Windows and if you've never explicitly installed anything GRUB-related in Windows or if you did so before installing Ubuntu, then the file is probably detritus or unimportant.

In any event, I suggest re-installing GRUB from Ubuntu (by typing "sudo grub-install /dev/sda") and then testing that you can still boot. If you can't boot at this point, you can use your install disc, or an emergency disc like [Super GRUB Disc,](http://www.supergrubdisk.org/) to restore your system to bootability.

Once you're sure GRUB is working from your Linux installation, you can create whatever type of filesystem you like on /dev/sda1. There should be no need to back anything up, unless you decide you want to rescue some user files. At this point, you can mount the partition wherever you like. I recommend transferring the contents of /home to the newly-prepared partition, renaming /home to something else (/home-old, say), creating a new /home directory, and editing /etc/fstab to permanently mount the new partition at /home. When you reboot, you can test that everything works and, if it does, delete the /home-old directory. This procedure will enable you to more easily upgrade or replace your main Ubuntu installation while preserving your user files.

---

### Post by colorlessprism on 2010-04-16
by formatting the NTFS partition you should still be just fine. i would also consider a backup strategy for the future

EDIT: srs5694 offered up a great solution, i have removed mine to avoid confusion

---

