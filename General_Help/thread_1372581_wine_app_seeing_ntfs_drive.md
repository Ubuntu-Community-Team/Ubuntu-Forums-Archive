---
title: "wine app seeing ntfs drive??"
date: 2010-01-04
forum: General Help
---

### Post by mr_si on 2010-01-04
I've got a mapping app (Memory Map) + 25Gigs of maps on an NTFS drive on this computer. When I try to find maps it throws up the windows dialogs showing me whatever drives wine has configured eg 
c: (something that Wine has invented and looks like a windows install)
d: (dvd drive)
z: this is the root of the linux drive 

I dont know the linux file system very well I thought NTFS drives would appear under dev or mnt

I have to use the gui to mount the NTFS drive each time (grrrr...) though I have installed NTFSConfig after some slight research that I thought would do the job for me a boot time. 

Is this an issue with Wine, do I need to search through the Z: path until I find the NTFS file system, do I need to add a line to the mount script etc etc

Thanks. 

Ub 9.10, 60Gb ext4, 160Gb NTFS

---

### Post by askreet on 2010-01-04
Lets start with:

Wine has nothing to do with NTFS.  Wine does not mount filesystems.

Second, Ubuntu likes to automount local filesystems and place shortcuts on your desktop.  It does this via GVFS (GNOME Virtual File System).  To see where they are really mounted run 'mount' with no parameters.

You will probably file that /dev/sdb1 (or so) is mapped to /home/user/.gvfs/volume_name OR /media/volume_name depending on your configuration.

You should then be able to point to Z:\home\user\.gvfs\volume_name or Z:\media\volume_name from within your Windows application running inside Wine.

HTH,
Askreet

---

