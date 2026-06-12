---
title: "Custom boot script  for Sandisk Cruzer live CD"
date: 2009-08-09
forum: General Help
---

### Post by M4D88 on 2009-08-09
Hey People!

I'm trying to create a custom live CD for my Sandisk USB Cruzer flash drive.

If you didn't know, these flash drives have 2 partitions, the first is a CDFS Partition (CD-ROM) where the Ubuntu live CD is mounted, the 2nd Partition is FAT32.

Im doing a job that requires the same settings to be made over a huge office of PC's all with the same hardware, and all set to boot from USB. 

To save time, I'd rather run around all the machines with this USB flash drive and patch them all by pluging in the drive and restarting the PC.

The job requires me to simply copy some config files from the 2nd partition of the flash drive during bootup over to the local partition on the PC.

The Partitions on the PC are ext3, so Ubuntu automaticly mounts them and can access them with read/write permissions. (sudo Gedit "cofig file")

What i need the Flash drive to do is automaticly.....

- Boot up to the ubuntu desktop

- Open the terminal window 

- Insert the commands to copy files from the 2nd partition
   to the local PC's partition.

- Shutdown the computer

I'm a bit of a n00b with linux commands, but im sure this script wouldnt be hard to write. Could anyone help me with what commands to use in order to setup a this process?

I need this to be completly automated so i wont have to press anykeys, just walk up to the terminal, plug in, reboot and wait a few minitues untill the machine shuts down.

I'd obousley have to create the script then create an ISO of the working configuration  back to the CD-ROM partition on the flash drive.

I know how to do this manualy but theres so manny PC's I wont have the time.

Any help with this would be great =)

Cheers

M4D88

---

