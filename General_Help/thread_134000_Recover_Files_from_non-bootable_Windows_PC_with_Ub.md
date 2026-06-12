---
title: "Recover Files from non-bootable Windows PC with Ubuntu Live"
date: 2006-02-21
forum: General Help
---

### Post by Behel on 2006-02-21
Hi,

I thought this might help some of those who cannot boot their Windows PC anymore but still have valuable data on it and want to recover it.  Of course this can also be used to steal the data on any pc but this is bad bad bad...

This thread is inspired a lot from this blog: [http://jclark.org/weblog/Miscellany/Tech/ubrescue.html](http://jclark.org/weblog/Miscellany/Tech/ubrescue.html)

I am using Ubuntu Live (Breezy) as well but contrary to the previous link, I am not using an internet connexion but simply any USB key (or drives). 

1. First get a Ubuntu Live CD.

2. Launch your pc from the CD. Follow the instructions.

3. When it's up and running, open the terminal and become root:
   sudo su
   Create a folder in /mnt, called for example windrive:
   cd /mnt
   mkdir windrive

4. If you know which partition to mount then go to step 7. Otherwise open the System|Adminitration|Disk manager. Select the harddisk, select the partition tab, and select the desired partition. Enter /mnt/windrive (or the name of the previously created folder) in the path entry. Then click enable. You can browse the partition of the pc to see if the data is what you are looking for.

5. In the terminal, type:
   mount
and remember the name (eg /dev/hda5) and type (NTFS, FAT...) of the partition you want to recover the data from.

6. In the disk manager, disable the partition you selected in step 4.

7. In the terminal, type:
   mount -t ntfs /dev/hda5 /mnt/windrive -o "umask=022"
where ntfs and /dev/hda5 are the name of the partition, as in step 5.

8. Plug your USB key. It should be automatically mounted in /media and be called something like USB\ DISK. Change the permissions:
   chmod 777 windrive
   chmod 777 /media/USB\ DISK

9. Now you can simply drag'n drop all the data from your partition to your USB  key or also create archives directly on you USB key (Useful if some of the documents from windows are recognized as Invalid Encoding by linux).

10. Finally, when you have finished, type:
   umount /dev/hda5

This way, I managed to backup all my precious data from a crashed pc very easily in less than an hour. The conclusion is: always have an Ubuntu Live CD with you... in particular if you play with Windows.

I hope this will be useful to others.

---

